# Welcome to the Python Text Adventure Game - Surviving in Jurassic Park

Bugs that are not yet worked out: 
When asked if the user wants to play again at the very end and the user types 'No' instead of ending/stopping the game, it prints out the text as it should but also jumps to stage 4. That needs to be solved.

The game is based on the movie Jurassic Park (Spielberg, S. (1993). Jurassic Park. Universal Pictures.) and itsstory is slightly changed for the purpose of this game. The background story for the game is the following:

You are a visitor of the park and admiring the fascinating landscapes of the island as well as the breathtaking creatures in form of dinosaurs. It is a warm and sunny day, a light wind is blowing and you enjoy adventure – when all of a sudden you can hear loud noises. You try to identify what those noises are and where they come from. In that exact moment you realize that these are the sirens and alarm systems of the park…

A COLLAPSE OF THE SECURITY SYSTEM – OH NO! 

All gates of the dinosaur enclosures open up while you are in the middle of the park by yourself. Every single one of those massive creatures can now get in the same area of the park in which you are currently in. Now you have to get to an exit as soon as possible and try to avoid encounters with all different kinds of dinosaurs. 

In order to get to the outer safe circle of the park you have to choose the best possible way, solve several quizzes and make difficult decisions – and all of that under time pressure before the hungry Tyrannosaurus Rex can find you…

Will you survive? 


#import time and random packagess
import time
import random


###########################################################################  
###########################################################################
###########################################################################

# functions defining

###########################################################################  
###########################################################################
###########################################################################



### functions for the end of the game (winning, failing, new_try) 
    
# function for winning the game
def winning():
    
    print("""
    ----------------------------------------------------------------------------
    --                                                                        --
    --                            YOU WIN!!!!                                 --
    --                                                                        --
    ----------------------------------------------------------------------------
    """)
    
    print("""
    ----------------------------------------------------------------------------
    --                                                                        --
    -- You survived the Jurassic Park and escaped all dinosaurs successfully. --  
    --                             Well done.                                 --
    --                                                                        --   
    --                          Congratulations                               --
    --                                                                        --
    ----------------------------------------------------------------------------
    """)

    # calling function new_try() to let users play again when they want to
    new_try()
    

# function for losing the game    
def failing():
    
    print("""
    ----------------------------------------------------------------------------
    --                                                                        --
    --                            GAME OVER!!!                                --
    --                                                                        --
    ----------------------------------------------------------------------------
    """)
    
    # calling function new_try() to let users play again when they want to
    new_try()
    

# function for another try
def new_try():

    time.sleep(6)
    
    #ask for user input and capitalize their input
    new_try = input(prompt = """\nDo you want to play again? 
Please enter the word 'Yes' or 'No': """).capitalize()    

    #if statement for decision making
    if new_try == 'Yes':
       
        #when user wants to play again, call function first_encounter_decision() to start all over 
        first_encounter_decision()
        
    elif new_try == 'No':
        
        #when user wants to end, wish him a nice day
        print('\nHope to see you again one day in Jurassic Park!')
        
    else:
        input(prompt = '\nPlease check your spelling.')
        
        new_try()

        
##############################################################################
##############################################################################

### funtions for each stage (quizzes and tasks) 

# stage 1 survival decision scenario
def first_encounter_decision():
    
    print("""\nWhat do you want to do? You ask yourself:""")
    
    #ask for user decision
    decision1 = input(prompt = """\nChoose your decision (Type the number of the action you want to take):
    1. Turn around and run back to where you came from
    2. Stand still, do not move and hold your breath
    3. Make yourself big, yell at them and move forward""")
    
    #different outcomes for each decision
    #decision 1
    if decision1 == '1':
        
        print('\nYou chose to play safe. So you are running as fast as you can to get away from them...')
        
        time.sleep(2)
        
        print("""\nIt seems to work. Wise decision making! You just survived your first dinosaur encounter but you also lost valuable time. Hurry up now!""")
        
        time.sleep(2)
        
        print("""\nYou have won the first challenge and with that a key. Take the key and put it in your pocket. Don't loose it, you will need it later! """)
        
        time.sleep(3)
        
        print('\nNow on to the next challenge: ')
        
        time.sleep(1)
        
        #calling guess_the_code() function
        guess_the_code()
        
    #decision 2   
    elif decision1 == '2':
        
        print("""\nYou chose to stand still. But they come closer to you, passing right next to you. One compy even sniffs on you...""")
        
        time.sleep(2)
        
        print("""\nEventually they are losing interest in you and move forward. Lucky you! But now you have to hurry up! You have just lost crucial time... Keep on running.""")
        
        time.sleep(2)
        
        print("""\nYou have won the first challenge and with that a key. Take the key and put it in your pocket. Don't loose it, you will need it later!""")
        
        time.sleep(3)
        
        print('\nNow on to the next challenge: ')
        
        time.sleep(1)
        
        #calling guess_the_code() function
        guess_the_code()
    
    #decision 3
    elif decision1 == '3':
        
        print("""\nYou chose to be aggressive because you think you are brave and start yelling at the compys. You make yourself big and approach them. They are looking at you and start making noises...""")
        
        time.sleep(3)
        
        print("""\n... and they are coming for you. 5 compys against you - a 5'5 human being. Well that was the stupidest idea you ever had. You don't stand a chance. Congratulations, your life ended underneath 5 heavy dinosaurs...""")
        
        #calling failing() function
        failing()
        
    
    else:
        
        #remind user to enter a number from 1-3 
        print('\nYou did not enter a number from 1 and 3!')
        
        first_encounter_decision()

        
#stage 2 guessing game
def guess_the_code():
    
    #get a random number from 0-9
    code_number = random.randint(0, 9)
    
    print("""\nYou have just arrived at another door. It is locked but it seems to only have a one digit code (So it can only be a number from 0-9). You have three chances to guess the correct number or else the dinosaurs get you. """)

    # Allow the player three chances to guess the correct number
    for attempt in range(1, 4):
        
        #use try / except to only allow numbers as an entry
        try:
            guess = int(input(prompt = '\nEnter your guess: '))
            
        except ValueError:
            print(prompt = '\nWrong input. Please enter a number.')
            continue 

        # Check if the guess is correct
        if guess == code_number:
            print("""\nGood job! You guessed the correct number. The door opens and you get a second key. Take it with you, don't loose it and keep on running...""")
            
            time.sleep(3)
            
            #proceed to next stage
            quiz_germany()
            
        elif guess > code_number:
            print('\nThe number is lower.')
            
        elif guess < code_number:
            print('\nThe number is higher.')
        else:
            print('\nIncorrect guess. Try again.')
    
    #if user takes more than 3 attempts to guess the right number
    else:
        print(f"""\nSorry, you've taken too long. The correct number was {code_number}.
Damn... you lost too much time and you can't go back. The Tyrannosaurus Rex will get you soon...
        """)
        
        time.sleep(5)
        
        print('\nHe got you. You ended up as dinosaur dinner...')
        
        #calling the failing function because user lost the game in this scenario
        failing()



# stage 3 quiz
def quiz_germany():

    #create an empty list to store the number of correct answers later
    correct_answers_lst = []

    print("""\nYou are now in the area where your German colleague was responsible 
for setting up the security framework. Do you know enough about Germany to pass this challenge?
You need to answer at least three of those four questions right in order to get the key. 
    """)

    #four different questions
    answer1 = input(prompt = """\nQuestion 1: How many people live in Germany? (Type in the number of the answer you choose) 
1. 23 million
2. 87 million
3. 159 million
                """)
    
    answer2 = input(prompt = """\nWhat is the capital of Germany?""").capitalize()
        
    answer3 = input(prompt = """\nIs Germany bigger or smaller than Brazil?""").lower()
    
    answer4 = input(prompt = """\nWhat do Germans prefer to drink when partying?""").lower()
    
    #checking answers
    #if the answer is correct, append the list with the value 1
    if answer1 == '2':
        correct_answers_lst.append('1')

    elif answer1 == '1' or answer1 == '3':
        ''

    else:
        print('\nPlease choose a number from 1 to 3 to answer the question.')
        answer1 


    if answer2 == 'Berlin':
        correct_answers_lst.append('1')

    else:
        ''


    if answer3 == 'smaller':
        correct_answers_lst.append('1')

    else:
        ''


    if answer4 == 'beer':
        correct_answers_lst.append('1')

        

    print('\nChecking your answers...')

    time.sleep(2)

    #checking the length of the list to count correct answers
    #when three or four correct answers
    if len(correct_answers_lst) > 2:
        print("""\nGood knowledge! You have unlocked the box and another key. 
Take it but don't loose it.""")

        choose_key()

    #when less than three correct answers
    elif len(correct_answers_lst) < 3:
            print("""\nYou didn't answer enough questions correctly. 
Luckily there is a backup question that will let you open the door when answering correct. 
But hurry up, you can hear a massive dinosaur coming your way.
                """)
            
            #create a backup questions that will help to pass the stage if correctly answered
            backup_question = input(prompt = '\nHow often did Germany win the football world cup?')

            #when correctly answered
            if backup_question == '4':
                print("""\nGood knowledge! You have unlocked the box and get another key.""")

                #proceed to next stage
                choose_key()

            #when wrong answer
            else:
                print("""\nThat is wrong... and it was your last chance. Oh no! 
You turn around and see this massive animal - a Tyrannosaurus Rex.
You try to run away from it but there is no place to hide or get safe, 
he is coming closer and he looks hungry...
                """)
                time.sleep(6)

                print("""\nThat's it, you ended up as a dinner for a Tyrannosaurus Rex. Not really nice...""")

                #call failing function because user lost the game
                failing()



    else:
        print("""\nThat is wrong... and it was your last chance. Oh no! 
You turn around and see this massive animal - a Tyrannosaurus Rex.
You try to run away from it but there is no place to hide or get safe, 
he is coming closer and he looks hungry...
        """)

        time.sleep(7)

        print("""\nThat's it, you ended up as a dinner for a Tyrannosaurus Rex. Not really nice...""")

        #call failing function because user lost the game
        failing()        
        
        
# stage 4 guess the number      
def choose_key():
    
    print("""\nYou take off running again and you know it is not that far anymore but you are close to the enclosure of the Tyrannosaurus Rex.""")
    
    time.sleep(2)
    
    print("""\nNow you are on to the last challenge: You are in front ot the final door of the outer security ring that leads to safety. You have collected three keys along the way but only one of them will help you to pass it. Hurry up, the Tyrannosauros Rex is on the way to you to get you... Which key are you choosing? Make the right decision, time is crucial now! """)
    
    time.sleep(5)

    #get a random number from 1-3 in order to choose one of the three keys
    number = random.randint(1,3) 
    chances = 3


    #looping until a user is out of guesses
    while chances > 0:
        choice = input(prompt = """\nChoose the right key for the last door (1, 2 or 3)?""")

        # converting choice for numerical comparison
        choice = int(choice)

        # conditional statement based on user input
        if choice == number:
            
            print('\nUnlocking...')
            
            time.sleep(2)
            
            print('\nYes! That was the right key.')
            
            time.sleep(1)
            
            print("""\nThe door opens. Hurry up and jump into safe space! Do not forget to close the door!!!""")
            
            time.sleep(3)
            
            #calling winning function as user wins the game
            winning()


        #when user input is not equal to the random number
        elif choice != number:
            
            #reduce chances (3) by 1 for each wrong guess
            chances -= 1

            if chances == 2:
                print('\nUnlocking...')
                
                time.sleep(2)
                
                print("""\nThat was the wrong key. You have 2 more keys remaining. But hurry up and choose wisely. The dinosaur has almost broken through the gate. You only have one more chance!
                """ )

            elif chances == 1:
                print('\nUnlocking...')
                
                time.sleep(2)
                
                print("""\nOh no... Wrong key again!""")
                
                time.sleep(1)
                
                print("""\nThat is unfortunate! The Tyrannosaurus Rex has broken through the gate and got you... You ended up as dinner for a dinosaur! Damn """)

                #calling failing function as user lost the game
                failing()

            else:
                print('Error')

        else:
            print("\nSomething went wrong.") 
            

###########################################################################  
###########################################################################
###########################################################################

# Game Code starts here

###########################################################################  
###########################################################################
###########################################################################

print("""\nLet's play!""")

time.sleep(1)


print("""\nYou know the way to the exit so you take off running. Let's see if you've got what it takes! Be aware, hurry up or you will end up as dinosaur dinner... """)

time.sleep(3)

print("""\nYou are running. After a minute you can suddenly feel the ground shaking. What is that? Is it already the Tyrannosaurus Rex? """)

time.sleep(5)

print("""\nYou are lucky! It's just a group of 3 tiny compys. You've learned that they shouldn't be too dangerous if you don't provoke them. They are coming in your direction. """)

time.sleep(5)

# calling function first_encounter_decision()
first_encounter_decision()
