<h1>ExpNo 7 : Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game</h1> 
<h3>Name:Sairam V</h3>
<h3>Register Number:212225230237</h3>
<H3>Aim:</H3>
<p>
Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game
</p>
<h1>GOALS of Alpha-Beta Pruning in MiniMax Search Algorithm</h1>

<h3>Improve the decision-making efficiency of the computer player by reducing the number of evaluated nodes in the game tree.</h3>
<h3>Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning and the Minimax algorithm with Python Code.</h3>
<h1>IMPLEMENTATION</h1>

The project involves developing a Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning with the Minimax algorithm. Using this algorithm, the computer player analyzes the game state, evaluates possible moves, and selects the optimal action based on the anticipated outcomes.

<h1>The Minimax algorithm</h1>

recursively evaluates all possible moves and their potential outcomes, creating a game tree.

<h1>Alpha-Beta pruning</h1>

Alpha–Beta (𝛼−𝛽) algorithm is actually an improved minimax using a heuristic. It stops evaluating a move when it makes sure that it’s worse than a previously examined move. Such moves need not to be evaluated further.

When added to a simple minimax algorithm, it gives the same output but cuts off certain branches that can’t possibly affect the final decision — dramatically improving the performance
<hr>

## Program:
```
import math

board = [" "] * 9

def win(p):
    for a,b,c in [(0,1,2),(3,4,5),(6,7,8),
                  (0,3,6),(1,4,7),(2,5,8),
                  (0,4,8),(2,4,6)]:
        if board[a] == board[b] == board[c] == p:
            return True
    return False

def minimax(maximizing, alpha, beta):
    if win("O"): return 10
    if win("X"): return -10
    if " " not in board: return 0

    if maximizing:
        best = -math.inf
        for i in range(9):
            if board[i] == " ":
                board[i] = "O"
                best = max(best, minimax(False, alpha, beta))
                board[i] = " "
                alpha = max(alpha, best)
                if beta <= alpha: break
        return best

    best = math.inf
    for i in range(9):
        if board[i] == " ":
            board[i] = "X"
            best = min(best, minimax(True, alpha, beta))
            board[i] = " "
            beta = min(beta, best)
            if beta <= alpha: break
    return best

def best_move():
    best, move = -math.inf, 0
    for i in range(9):
        if board[i] == " ":
            board[i] = "O"
            score = minimax(False, -math.inf, math.inf)
            board[i] = " "
            if score > best:
                best, move = score, i
    return move

def show():
    print("\n".join([
        " | ".join(board[0:3]),
        "---------",
        " | ".join(board[3:6]),
        "---------",
        " | ".join(board[6:9])
    ]))

while True:
    show()
    p = int(input("Enter position (1-9): ")) - 1

    if board[p] != " ":
        print("Invalid move!")
        continue

    board[p] = "X"

    if win("X"):
        show(); print("You Win!"); break
    if " " not in board:
        show(); print("Draw!"); break

    board[best_move()] = "O"

    if win("O"):
        show(); print("Computer Wins!"); break
```
<h2>Sample Input and Output:</h2>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8d5e329a-9aff-41a6-bcf0-46efa10e1b92)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/438b242d-54ba-443e-b040-a936e6ae3b55)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/99a33390-fa11-4ade-a19f-e93bcd7aaec9)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/440797bd-53cb-49c1-b18d-89776864c3e7)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/81575a16-26b2-46f1-a8ac-27c9ed0a0fe5)
## Output:
<img width="1414" height="548" alt="image" src="https://github.com/user-attachments/assets/839491ca-7a67-4d58-9c65-ecaff26d01de" />

## Result:
The alpha-beta pruning algorithm was successfully solved and created a tic-tac-toe game.
