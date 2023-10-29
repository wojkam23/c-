#include <iostream>
#include <cstdlib>
#include <vector>
using std::vector,std::cin,std::cout,std::endl;

enum class Element { kN, kX, kT, kP };

const int row = 10;
const int col = 10;

void displayBoard(vector<vector<Element>>& board) {
    vector<char> displaySymbols = { '.', 'X', 'T', 'P' };

    for (int i = 0; i < board.size(); ++i) {
        for (int j = 0; j < board[0].size(); ++j) {
            cout << displaySymbols[static_cast<int>(board[i][j])] << " ";
        }
        cout << endl;
    }
}

vector<vector<Element>> placeTraps(vector<vector<Element>> board) {
    for (int i = 0; i < 5; ++i) {
        int x = rand() % row;
        int y = rand() % col;
        board[x][y] = Element::kX;
    }
    return board;
}

vector<vector<Element>> placeTreasure(vector<vector<Element>> board) {
    int x = rand() % row;
    int y = rand() % col;
    board[x][y] = Element::kT;
    return board;
}

int main() {
    vector<vector<Element>> board(row, vector<Element>(col, Element::kN));
    
    board = placeTraps(board);
    board = placeTreasure(board);

    int playerX = rand() % row;
    int playerY = rand() % col;
    board[playerX][playerY] = Element::kP;

    while (true) {
        displayBoard(board);

        char move;
        cout << "Enter a move (U/D/L/R): ";
        cin >> move;

        int newPlayerX = playerX;
        int newPlayerY = playerY;

        if (move == 'U' && playerX > 0) {
            newPlayerX = playerX - 1;
        }
        else if (move == 'D' && playerX < row - 1) {
            newPlayerX = playerX + 1;
        }
        else if (move == 'L' && playerY > 0) {
            newPlayerY = playerY - 1;
        }
        else if (move == 'R' && playerY < col - 1) {
            newPlayerY = playerY + 1;
        }

       
        board = placeTraps(board);

        if (board[newPlayerX][newPlayerY] == Element::kT) {
            cout << "You found the treasure! You win!" << endl;
            break;
        }
        else if (board[newPlayerX][newPlayerY] == Element::kX) {
            cout << "You stepped on a trap! You lose!" << endl;
            break;
        }

        board[playerX][playerY] = Element::kN;
        board[newPlayerX][newPlayerY] = Element::kP;
        playerX = newPlayerX;
        playerY = newPlayerY;
    }

    return 0;
}
