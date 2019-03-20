# interstate-love-song.py
Interstate Love Song

def get_interstate_number():
    interstate_number = 0
    while interstate_number <= 0:
        interstate_number = int(input("Please enter a US Interstate Highway route number: "))
    # while loop is so that when inputs of 0 and less are selected, will ask the user again to input until a positive value is inputted
    # value is returned
    return interstate_number

def is_primary(number):
    if number < 100:
        return True
    return False
    # if a number is less than 100, means that it is two digits, meanings its a primary interstate and outputs True
    # of greater than or equal to 100, it's an auxilary interstate and outputs False
    
def compass_orientation(number):
    if number % 2 == 1:
        return "north-south"
    # if statement is given a primary interstate number and if that number modulo 2 equals one that means its an odd number and "north-south" is returned
    elif number % 2 == 0:
        return "east-west"
    # elif statement is given a primary interstate number and if that number modulo 2 equals zero that means its an even number and "east-west" is returned

def is_arterial(number):
    if number % 5 == 0:
        return True
    return False
    # a primary interstate number is given and if that number modulo 5 equals zero that means its a multiple of 5 and is a long distance arterial highway and returns True

def auxillary_type(number):
    number = number // 100
    # given a auxillary interstate number to access the first digit of the number you would floor by 100 and that truncates everything except the first number
    if number % 2 == 0:
        return "radial"
    # the truncated number would then by modulo by 2 and if that equals zero that means its an even number and is a radial highway
    elif number % 2 == 1:
        return "spur"
    # if the number is not equal to zero above, the truncated number would then by modulo by 2 and if that does not equal zero that means its an odd number and is a spur highway
def parent_highway(number):
    number = number % 100
    return number
    # to access the last two numbers of a auxillary number that number would be modulo by 100 which will give us a parent number

def main():
    highway_number = get_interstate_number()
    # gets user input of highway number, must be positive to move on
    is_primary_number = is_primary(highway_number)
    # determines if number is a primary number
    if is_primary_number == True:
        arterial = is_arterial(highway_number)
        orient = compass_orientation(highway_number)
    # if its a primary number, then we would determine the arterial type and its orient which the above variables call the respective functions will do
        if arterial == True:
            print("Interstate {0} is a long distance arterial highway oriented {1}.".format(highway_number, orient))
        elif arterial == False:
            print("Interstate {0} is oriented {1}.".format(highway_number, orient))
        # if arterial is true ut will print "long distance" along with the highway number and orient
        # if arterial is false then it will just print the highway number and its orient
    if is_primary_number == False:
        auxillary = auxillary_type(highway_number)
        parent = parent_highway(highway_number)
        print("Interstate {0} is a {1} highway of Interstate {2}.".format(highway_number, auxillary, parent))
        # if primary number is false, then that means its a auxillary number and will determine its auxillary type and parent number by using variables auxillary and parent and calling functions
        # prints the highway number, auxillary, and parent
        



main()


#1.) President Dwight D. Eisenhower is credited as the biggest proponet of foundation of US Interstate system
#2.) Interstate I-405 is that most=heavily trafficked in terms of vehicles per day
#3.) Death Cab for a Cutie was formed in Bellingham, Washington. It's unlikely he's talking about I-405 in Calfornia because the I-405 stretches to Seattle which is in Washington
