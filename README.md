# Hangman

##### This program is game called hangman, which ask us to fill the missing letters in a word within a specified chances. It already contain a wordlist of more than 200 words and you can increase it by adding words to the list in wordlist.py 


## PROGRAM

          import wordlist
          import random
          import arts
          import os

          gameover = False
          disword =""
          display =[]
          flag = 0
          dis =[]

          word =random.choice(wordlist.wordlist)
          length =len(word)
          missing1 =random.randint(0,length-1)
          missing2 =random.randint(0,length-1)

          for l in word:
            dis += l
            display += '_'
          display[missing1] = dis[missing1]
          display[missing2] = dis[missing2]

          for j in display:
              disword += j +" "


          while not gameover:

            os.system('clear') or os.system('cls')
            print(arts.logo+"\n")
            print(f"Find the MISSING letter in the word:\n{disword}")
            print(f"{arts.stages[flag]}")
            guess =input("Guess the Letter : ").lower()
            disword=""
            if not guess in word:
              flag +=1
            if guess in display:
              flag +=1
            for i in range(length):
              if word[i]== guess:
                display[i] = guess
            for d in display:
              disword += d + " "

            if dis==display or (flag > len(arts.stages)-2):
                gameover = True   
            else:
                gameover = False


          if dis == display:
            print(f"Congrats!!! You found the letters in {word}")
          else:
            print(f"You did not found  the letter in the {word}")
  
## OUTPUT

          _                                             
          | |                                            
          | |__   __ _ _ __   __ _ _ __ ___   __ _ _ __  
          | '_ \ / _` | '_ \ / _` | '_ ` _ \ / _` | '_ \ 
          | | | | (_| | | | | (_| | | | | | | (_| | | | |
          |_| |_|\__,_|_| |_|\__, |_| |_| |_|\__,_|_| |_|
                              __/ |                      
                             |___/    

          Find the MISSING letter in the word:
          p o l _ a 

            +---+
            |   |
            O   |
           /|\  |
           /    |
                |
          =========

          Guess the Letter : l
          You dids not found  the letter in the polka
