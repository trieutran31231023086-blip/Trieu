# Trieu
bai tap LTCB
import random

def guess_number_game():
    balance = 100  # số tiền ban đầu
    game_cost = 5  # mỗi ván chơi mất 5$
    total_wins = 0
    total_losses = 0

    print(" Welcome to Guess The Number Game!")
    print("Bạn bắt đầu với 100$. Mỗi game sẽ tốn 5$.\n")

    while balance >= game_cost:
        # chọn mức độ
        print("\nChọn mức độ:")
        print("1. Hard (3 lần đoán)")
        print("2. Medium (6 lần đoán)")
        print("3. Easy (10 lần đoán)")
        level = input("Nhập lựa chọn (1/2/3): ")

        if level == "1":
            max_attempts = 3
        elif level == "2":
            max_attempts = 6
        elif level == "3":
            max_attempts = 10
        else:
            print(" Lựa chọn không hợp lệ, mặc định Easy (10 lần).")
            max_attempts = 10

        # trừ tiền chơi
        balance -= game_cost
        secret_number = random.randint(1, 100)
        attempts = 0
        win = False

        print(f"\n Tôi đã chọn một số từ 1 đến 100. Bạn có {max_attempts} lần đoán!")

        # vòng lặp đoán số
        while attempts < max_attempts:
            try:
                guess = int(input(f"({attempts+1}/{max_attempts}) Nhập số bạn đoán: "))
            except ValueError:
                print("⚠ Vui lòng nhập một số nguyên!")
                continue

            attempts += 1

            if guess == secret_number:
                print(" Chính xác! Bạn đã thắng!")
                win = True
                total_wins += 1
                break
            elif guess < secret_number:
                print("⬆ Số cần tìm lớn hơn.")
            else:
                print("⬇ Số cần tìm nhỏ hơn.")

        if not win:
            print(f" Bạn thua. Số đúng là {secret_number}.")
            total_losses += 1

        print(f" Số dư hiện tại: {balance}$")

        # hỏi người chơi có muốn tiếp tục
        if balance < game_cost:
            print("\n⚠ Bạn không còn đủ tiền để chơi tiếp.")
            break

        cont = input("Bạn có muốn chơi tiếp không? (y/n): ")
        if cont.lower() != "y":
            break

    # báo cáo kết quả
    print("\n Kết quả cuối cùng:")
    print(f"- Thắng: {total_wins} lần")
    print(f"- Thua: {total_losses} lần")
    print(f"- Số dư còn lại: {balance}$")
    print("Cảm ơn đã chơi! ")



    import random

def tai_xiu_game():
    print("🎲 Chào mừng đến với game Tài/Xỉu!")
    
    # Người chơi nhập số tiền ban đầu
    while True:
        try:
            balance = int(input(" Nhập số tiền bạn muốn chơi (>= 10$): "))
            if balance >= 10:
                break
            else:
                print(" Số tiền phải >= 10$.")
        except ValueError:
            print(" Vui lòng nhập số nguyên.")
    
    total_games = 0
    total_wins = 0
    total_losses = 0

    # Vòng lặp chơi game
    while balance > 0:
        print(f"\n Số dư hiện tại: {balance}$")
        
        # Người chơi chọn mức cược
        while True:
            try:
                bet = int(input("Nhập số tiền bạn muốn cược: "))
                if 0 < bet <= balance:
                    break
                else:
                    print(" Cược phải > 0 và ≤ số dư.")
            except ValueError:
                print(" Vui lòng nhập số nguyên.")
        
        # Người chơi chọn Tài hoặc Xỉu
        choice = input("Bạn đoán (Tài/Xỉu): ").strip().lower()
        if choice not in ["tài", "tai", "xỉu", "xiu"]:
            print("⚠ Lựa chọn không hợp lệ, mặc định là 'Tài'")
            choice = "tài"
        if choice in ["tai", "tài"]:
            choice = "tài"
        else:
            choice = "xỉu"
        
        # Tung xúc xắc
        dice1 = random.randint(1, 6)
        dice2 = random.randint(1, 6)
        total = dice1 + dice2
        
        # Kết quả
        result = "tài" if total > 5 else "xỉu"
        print(f" Kết quả: {dice1} + {dice2} = {total} → {result.upper()}")
        
        total_games += 1
        if choice == result:
            print(" Bạn đoán đúng! Thắng cược.")
            balance += bet
            total_wins += 1
        else:
            print(" Bạn đoán sai. Thua cược.")
            balance -= bet
            total_losses += 1
        
        # Kiểm tra còn tiền không
        if balance <= 0:
            print("\n⚠ Bạn đã hết tiền, game over.")
            break
        
        # Hỏi chơi tiếp không
        cont = input("Bạn có muốn chơi tiếp không? (y/n): ")
        if cont.lower() != "y":
            break

    # Thống kê kết quả
    print("\n KẾT QUẢ CUỐI CÙNG:")
    print(f"- Tổng số ván: {total_games}")
    print(f"- Thắng: {total_wins}")
    print(f"- Thua: {total_losses}")
    print(f"- Số dư còn lại: {balance}$")
    print(" Cảm ơn đã chơi!")

# Chạy game
if __name__ == "__main__":
    tai_xiu_game()

# chạy game
if __name__ == "__main__":
    guess_number_game()
