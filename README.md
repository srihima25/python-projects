# python-projects
Daily Python mini projects to improve problem-solving skills and programming concepts.
import random


def select_difficulty():
    level = input("Enter difficulty (E for Easy / H for Hard): ").strip().upper()

    if level == "E":
        return 10
    elif level == "H":
        return 5
    else:
        return -1


def play_game():
    print("\nNUMBER GUESSING GAME")
    print("The system has selected a number between 1 and 100.")

    secret_number = random.choice(range(1, 101))
    attempts = select_difficulty()

    if attempts == -1:
        print("Invalid difficulty selected!")
        return

    while attempts > 0:
        try:
            guess = int(input(f"Enter your guess (Attempts left: {attempts}): "))
        except ValueError:
            print("Invalid input. Please enter a number.")
            continue

        if guess == secret_number:
            print("You guessed the correct number!")
            return

        difference = abs(secret_number - guess)

        if difference <= 5:
            print("Very close.")
        elif difference <= 15:
            print("Close.")
        else:
            print("Far.")

        if guess > secret_number:
            print("Try a smaller number.")
        else:
            print("Try a bigger number.")

        attempts -= 1

    print("You lost the game.")
    print("The correct number was:", secret_number)


def main():
    while True:
        play_game()

        choice = input("Do you want to play again? (yes/no): ").strip().lower()
        if choice != "yes":
            print("Game ended.")
            break


main()

