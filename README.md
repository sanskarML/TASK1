#include <iostream>
#include <cstdlib>
#include <ctime>

int main() {
    // Seed the random number generator with the current time
    std::srand(static_cast<unsigned int>(std::time(nullptr)));

    // Generate a random number between 1 and 100
    int secretNumber = std::rand() % 100 + 1;

    int guess;
    int attempts = 0;

    std::cout << "Welcome to the Number Guessing Game!" << std::endl;

    do {
        std::cout << "Enter your guess (1-100): ";
        std::cin >> guess;

        if (std::cin.fail()) {
            std::cin.clear();
            std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
            std::cout << "Invalid input. Please enter a number between 1 and 100." << std::endl;
        }
        else {
            attempts++;

            if (guess < secretNumber) {
                std::cout << "Too low! Try again." << std::endl;
            } else if (guess > secretNumber) {
                std::cout << "Too high! Try again." << std::endl;
            } else {
                std::cout << "Congratulations! You guessed the number in " << attempts << " attempts." << std::endl;
            }
        }
    } while (guess != secretNumber);

    return 0;
}
