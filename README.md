# TIC-TAC-TOE
Overview of Tic-Tac-Toe
Tic-Tac-Toe is a two-player game where players alternate marking spaces in a 3x3 grid. One player uses "X" and the other uses "O". The goal is to get three marks in a row, column, or diagonal. If all nine squares are filled without a winner, the game is a draw.

Code Breakdown
1. Header File:
cpp
Copy
Edit
#include <iostream>
using namespace std;
#include <iostream> is used to enable input and output functionality.
using namespace std; allows the program to use standard functions like cout and cin without needing the std:: prefix.
2. Function to Draw the Board:
cpp
Copy
Edit
void drawBoard(char board[3][3])
This function prints the current state of the board.
The board[3][3] parameter represents a 3x3 grid containing the current moves of both players.
Inside the function:

cpp
Copy
Edit
cout << "-------------\n";
for (int i = 0; i < 3; i++) {
    cout << "| ";
    for (int j = 0; j < 3; j++) {
        cout << board[i][j] << " | ";
    }
    cout << "\n-------------\n";
}
The for loops iterate through each row and column to display the board.
The board is framed using dashes (-) and vertical bars (|) for better readability.
Example Output:

markdown
Copy
Edit
-------------
| X | O | X | 
-------------
| O | X | O | 
-------------
| X | O | X | 
-------------
3. Function to Check for a Win:
cpp
Copy
Edit
bool checkWin(char board[3][3], char player)
This function determines if a player has won.
The player parameter indicates which player’s symbol (X or O) is being checked.
Logic:

cpp
Copy
Edit
for (int i = 0; i < 3; i++) {
    if (board[i][0] == player && board[i][1] == player && board[i][2] == player)
        return true;
    if (board[0][i] == player && board[1][i] == player && board[2][i] == player)
        return true;
}
The first for loop checks all three rows.
The second for loop checks all three columns.
cpp
Copy
Edit
if (board[0][0] == player && board[1][1] == player && board[2][2] == player)
    return true;
if (board[0][2] == player && board[1][1] == player && board[2][0] == player)
    return true;
The two if statements check the diagonals.
If any of these conditions are met, the function returns true; otherwise, it returns false.

4. Main Function:
cpp
Copy
Edit
int main()
This is the main part of the program where the game loop runs until a player wins or the game ends in a draw.

5. Initializing the Game:
cpp
Copy
Edit
char board[3][3] = { {' ', ' ', ' '}, {' ', ' ', ' '}, {' ', ' ', ' '} };
char player = 'X';
int row, col;
int turn;
A 3x3 character array board is initialized with spaces to represent an empty board.
Variable player is initialized to 'X', meaning the first player will use the symbol X.
Variables row and col store the user’s input for each move.
Variable turn tracks the number of moves played.
6. Welcoming the Player:
cpp
Copy
Edit
cout << "Welcome to Tic-Tac-Toe!\n";
Displays a welcome message when the game starts.
7. Game Loop:
cpp
Copy
Edit
for (turn = 0; turn < 9; turn++)
A for loop runs for a maximum of 9 iterations (one for each square on the board).
Each iteration represents one turn.
Inside the loop:

cpp
Copy
Edit
drawBoard(board);
The drawBoard() function is called to display the current state of the board.
8. Player Input:
cpp
Copy
Edit
while (true) {
    cout << "Player " << player << ", enter row (0-2) and column (0-2): ";
    cin >> row >> col;

    if (board[row][col] != ' ' || row < 0 || row > 2 || col < 0 || col > 2) {
        cout << "Invalid move. Try again.\n";
    } else {
        break; // Valid input, exit the loop.
    }
}
A while (true) loop is used to get valid input from the player.
The player is prompted to enter the row and column (values between 0 and 2).
If the chosen cell is already occupied or out of range, an error message is displayed, and the player is asked to try again.
If the input is valid, the loop is exited using break.
9. Making a Move:
cpp
Copy
Edit
board[row][col] = player;
The player's symbol (X or O) is placed in the selected cell.
10. Check for a Win:
cpp
Copy
Edit
if (checkWin(board, player)) {
    drawBoard(board);
    cout << "Player " << player << " wins!\n";
    break; // Exit the loop after a win.
}
The checkWin() function is called to check if the current player has won.
If a win is detected, the board is displayed, and a message announces the winner.
The break statement ends the game loop.
11. Switching Players:
cpp
Copy
Edit
player = (player == 'X') ? 'O' : 'X';
The ternary operator is used to switch the current player from X to O and vice versa.
12. Displaying the Final Board:
cpp
Copy
Edit
drawBoard(board);
After the game loop ends, the final state of the board is displayed.
13. Check for a Draw:
cpp
Copy
Edit
if (turn == 9 && !checkWin(board, 'X') && !checkWin(board, 'O')) {
    cout << "It's a draw!\n";
}
If all 9 turns have been played and no player has won, a draw is declared.
14. Program Termination:
cpp
Copy
Edit
return 0;
The main() function returns 0, indicating that the program has executed successfully.
Example Gameplay:
markdown
Copy
Edit
Welcome to Tic-Tac-Toe!
-------------
|   |   |   | 
-------------
|   |   |   | 
-------------
|   |   |   | 
-------------
Player X, enter row (0-2) and column (0-2): 0 0

-------------
| X |   |   | 
-------------
|   |   |   | 
-------------
|   |   |   | 
-------------
Player O, enter row (0-2) and column (0-2): 1 1
...
Player X wins!
Conclusion:
This C++ Tic-Tac-Toe program is simple, interactive, and demonstrates fundamental programming concepts like arrays, loops, conditional statements, and functions. It ensures that players can only make valid moves and announces the winner or a draw as soon as the game ends.
