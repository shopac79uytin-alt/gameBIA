# Game Cờ Caro đơn giản bằng Python (3x3)

def print_board(board):
    print("\n")
    print(f" {board[0]} | {board[1]} | {board[2]} ")
    print("---|---|---")
    print(f" {board[3]} | {board[4]} | {board[5]} ")
    print("---|---|---")
    print(f" {board[6]} | {board[7]} | {board[8]} ")
    print("\n")

def check_win(board, player):
    win_conditions = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8],  # Hàng ngang
        [0, 3, 6], [1, 4, 7], [2, 5, 8],  # Hàng dọc
        [0, 4, 8], [2, 4, 6]             # Đường chéo
    ]
    for condition in win_conditions:
        if board[condition[0]] == board[condition[1]] == board[condition[2]] == player:
            return True
    return False

def play_game():
    board = [" " for _ in range(9)]
    current_player = "X"
    
    print("Chào mừng đến với Game Cờ Caro!")
    print("Chọn ô từ 1 đến 9 theo sơ đồ sau:")
    print(" 1 | 2 | 3 ")
    print("---|---|---")
    print(" 4 | 5 | 6 ")
    print("---|---|---")
    print(" 7 | 8 | 9 \n")

    for turn in range(9):
        print_board(board)
        try:
            move = int(input(f"Lượt của người chơi {current_player}. Chọn ô (1-9): ")) - 1
            if move < 0 or move > 8 or board[move] != " ":
                print("Ô không hợp lệ hoặc đã được chọn. Thử lại nhé!")
                continue
        except ValueError:
            print("Vui lòng nhập một số nguyên từ 1 đến 9!")
            continue

        board[move] = current_player

        if check_win(board, current_player):
            print_board(board)
            print(f"Chúc mừng! Người chơi {current_player} đã CHIẾN THẮNG! 🎉")
            return

        current_player = "O" if current_player == "X" else "X"

    print_board(board)
    print("Hòa mất rồi! 🤝")

if __name__ == "__main__":
  play_game()
