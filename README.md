




















#word master 고등 complete 영단어 테스트 프로그램

import random

day1 = [
    "evidence:증거,흔적",
    "beneficial:유익한,이로운",
    "value:가치,가치관",
    "pandemic:대규모유행병",
    "public:대중의,공공의"
]

day2 = [
    "healthcare:의료,건강관리",
    "hardwired:타고나는",
    "selfesteem:자존감,자부심",
    "assume:가정하다,추측하다",
    "gene:유전자"
]

day3 = [
    "entitle:자격을주다",
    "souvenir:기념품",
    "coverage:보호,보상범위",
    "scientific:과학의,과학적인",
    "monopoly:독점,독점권"
]

day4 = [
    "contrast:대조하다,대비하다",
    "lifeexpectancy:평균수명",
    "relieved:안심한,안도한",
    "imply:암시하다,함축하다",
    "fund:기금,자금"
]

def choose_word_list():
    # 사용자에게 어떤 리스트를 선택할지 물어봄
    while True:
        choice = input("어떤 날짜를 선택하겠습니까까? (1, 2, 3, 4): ")
        if choice == '1':
            return day1
        elif choice == '2':
            return day2
        elif choice == '3':
            return day3
        elif choice == '4':
            return day4
        else:
            print("1, 2, 3, 4를 입력하세요.")

def play_game():
    # 사용자가 선택한 단어 리스트
    chosen_word_list = choose_word_list()

    # 사용자에게 뜻을 보여줄 단어 리스트
    remaining_words = chosen_word_list.copy()

    # 틀린 단어를 저장할 리스트
    wrong_words = []

    while remaining_words:
        # 랜덤으로 단어 선택
        selected_entry = random.choice(remaining_words)
        selected_word, korean_meaning = selected_entry.split(':')

        # 사용자에게 뜻을 보여주고 입력 받기
        user_guess = input(f"{korean_meaning}의 영어 스펠링을 맞춰보세요: ").lower()

        # 게임 종료 확인
        if user_guess == 'exit':
            print("게임을 종료합니다.")
            break

        # 정답 확인
        if user_guess == selected_word:
            print("정답입니다!")
            remaining_words.remove(selected_entry)
        else:
            print(f"틀렸습니다. 다음에 다시 시도하세요.")
            # 틀린 단어를 저장하고 원래 리스트에서 삭제
            wrong_words.append(selected_entry)
            remaining_words.remove(selected_entry)

    # 모든 단어를 맞춘 경우
    if not remaining_words and not wrong_words:
        print("축하합니다! 전부 다 맞췄습니다.")
    elif wrong_words:
        wrong_count = len(wrong_words)
        print(f"\n틀린 단어가 {wrong_count}개 있습니다. 이제 틀린 단어들로 다시 시험을 보겠습니다.")

        for wrong_entry in wrong_words:
            selected_word, korean_meaning = wrong_entry.split(':')
            user_guess = input(f"{korean_meaning}의 영어 스펠링을 맞춰보세요: ").lower()

            if user_guess == 'exit':
                print("게임을 종료합니다.")
                break

            if user_guess == selected_word:
                print("정답입니다!")
            else:
                print(f"틀렸습니다. 다시 시도하세요.")
    else:
        print("틀린 단어가 없습니다.")

    print("\n선택한 리스트의 모든 단어:")
    for word_entry in chosen_word_list:
        print(word_entry)

    print("게임이 종료되었습니다.")

# 게임 실행
play_game()
