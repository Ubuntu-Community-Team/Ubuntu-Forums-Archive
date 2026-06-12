---
title: "Bash Script error :("
date: 2013-02-25
forum: General Help
---

### Post by johnryaniii on 2013-02-25
```
 #!/bin/bash
echo "-------------------------------------"
echo "----Welcome to Shattered Forrest-----"
echo "-------Choose Wisely your Path-------"
echo "-------------------------------------"
sleep 2;
echo -e "What is your travelers name: \c"
read name

echo "Your path begins now $name"
sleep 2;
echo "As a young traveler in your twenties your goal in life has always been to travel the world." 
sleep 5;
echo "Growing up you managed to vanquish any queries that came your way, but your real goal was to travel the unknown."
sleep 5;
echo "The village you grew up in was a simple village, but you yearned to learn more."
sleep 5;
echo "When you came of age you traveled outside the village and into the banished forrest, mythically named Shattered Forrest."
sleep 5;
echo "Your journey begins here at the foothold of the Shattered Forrest." 
sleep 5;
echo "You know not of what is to come."
sleep 5;
echo "Good luck $name and may the wind guide you!"
sleep 5;
clear;
echo "Walking the forbidden path to the Shattered Forrest you come across an abandoned armory"
sleep 3;
echo "As you shuffle through the old equipments of passed soldiers you stop to think what weapon you desire."

# Declare variable choice and assign value 4
choice=4
# Print to stdout
echo "1. Rusty Short Sword"
echo "2. Cracked Dagger"
echo "3. Withered Bow"
echo -n "Choose your weapon [1,2 or 3]? "

# Loop while the variable choice is equal 4
# bash while loop
while [ $choice -eq 4 ]; do

#read user input
read choice
# bash nested if/else
if [ $choice -eq 1 ] ; then

	echo "You have chosen the: Rusty Short Sword"
else
	if [ $choice -eq 2 ] ; then
		echo "You have chosen the: Cracked Dagger"
	else
		
		if [ $choice -eq 3 ] ; then
			echo "You have chosen the: Withered Bow"
		else
			echo "Please make a choice between 1-3 !"
			echo "1. Rusty Short Sword"
			echo "2. Cracked Dagger"
			echo "3. Withered Bow"
			echo -n "Choose your weapon [1,2, or 3]?"
			choice=4
		fi
	fi
fi
done

sleep 2;
echo "A fine choice indeed."
sleep 4;

echo "Your journey continues"
echo "."
sleep 1;
echo ".."
sleep 1;
echo "..."
sleep 1; 
echo "...."
sleep 1;
echo "....."
sleep 1;
echo "......"
sleep 1;
echo "....."
sleep 1;
echo "...."
sleep 1;
echo "..."
sleep 1;
echo ".."
sleep 1;
echo "."


echo "In the distance you see a dark shadow approaching."
sleep 2;
echo "Could it be?"
sleep 3;
echo "Is this the the shadowy figure the village spoke of."
sleep 2;
echo "A Myth..a simple folks tale you thought..
sleep 2;
echo "How could this be..."
slepe 2;
echo "You stand frightened for your life, the shadowy figure is approaching with haste!!"
sleep 4;

TODO=3

echo "1. Drop Weapon & Flee"
echo "2. Stand & Fight"
echo -n "What will you do [1 or 2]? "

while [ $TODO -eq 3 ]; do

read TODO

if [ $TODO -eq 1 ] ; then

		echo "Perhaps you are not ready for the Shattered Forrest. Game over: Drop Weapon & Flee"

	else

		if [ $TODO -eq 2 ] ; then
			echo "You will Stand & Fight!: Stand & Fight"
	
		else
				echo "1. Drop Weapon & Flee"
				echo "2. Stand & Fight"
				echo -n "What will you do [1 or 2]? "
				TODO=3
		fi
	fi
done

```

I'm getting a syntax error on when it comes to my $TODO variable. I've been at it for an hour. I was looking for someone to brush over and maybe point out my error. :confused:

Basically just look at the bottom portion of the code. starting with TODO=3

---

### Post by Vaphell on 2013-02-25
syntax highlighting would show you where the problem is (" not matched)
```
...
echo "Is this the the shadowy figure the village spoke of."
sleep 2;
[COLOR="Blue"]echo "A Myth..a simple folks tale you thought..[/COLOR][COLOR="Red"]"[/COLOR]
sleep 2;
echo "How could this be..."
[COLOR="Red"]slepe[/COLOR] 2;
...
```

besides, parametrize all these sleeps, it must be ungoldy annoying to debug with all that waiting every single time.
At the top define some functions that do the printing so you don't have to tweak everything all over the place (not to mention your code would shrink a lot), eg

```
echo1() { echo "$@"; sleep 1; }
echo3() { echo "$@"; sleep 3; }
echo5() { echo "$@"; sleep 5; }

echo1 "some text"
echo3 "some other text"
echo5 "yet another text"
```
while you work on the code you set the values to 0.1 or whatever and only when you think it's ready you change it to proper values.

---

### Post by Warren Hill on 2013-02-25
Try this instead.  I spotted two syntax errors.

```
#!/bin/bash
echo "-------------------------------------"
echo "----Welcome to Shattered Forrest-----"
echo "-------Choose Wisely your Path-------"
echo "-------------------------------------"
sleep 2;
echo -e "What is your travelers name: \c"
read name

echo "Your path begins now $name"
sleep 2;
echo "As a young traveler in your twenties your goal in life has always been to travel the world."
sleep 5;
echo "Growing up you managed to vanquish any queries that came your way, but your real goal was to travel the unknown."
sleep 5;
echo "The village you grew up in was a simple village, but you yearned to learn more."
sleep 5;
echo "When you came of age you traveled outside the village and into the banished forrest, mythically named Shattered Forrest."
sleep 5;
echo "Your journey begins here at the foothold of the Shattered Forrest."
sleep 5;
echo "You know not of what is to come."
sleep 5;
echo "Good luck $name and may the wind guide you!"
sleep 5;
clear;
echo "Walking the forbidden path to the Shattered Forrest you come across an abandoned armory"
sleep 3;
echo "As you shuffle through the old equipments of passed soldiers you stop to think what weapon you desire."

# Declare variable choice and assign value 4
choice=4
# Print to stdout
echo "1. Rusty Short Sword"
echo "2. Cracked Dagger"
echo "3. Withered Bow"
echo -n "Choose your weapon [1,2 or 3]? "

# Loop while the variable choice is equal 4
# bash while loop
while [ $choice -eq 4 ]; do

#read user input
read choice
# bash nested if/else
if [ $choice -eq 1 ] ; then
    echo "You have chosen the: Rusty Short Sword"

else
    if [ $choice -eq 2 ] ; then
        echo "You have chosen the: Cracked Dagger"
    else

        if [ $choice -eq 3 ] ; then
            echo "You have chosen the: Withered Bow"
        else
            echo "Please make a choice between 1-3 !"
            echo "1. Rusty Short Sword"
            echo "2. Cracked Dagger"
            echo "3. Withered Bow"
            echo -n "Choose your weapon [1,2, or 3]?"
            choice=4
        fi
    fi
fi
done

sleep 2;
echo "A fine choice indeed."
sleep 4;

echo "Your journey continues"
echo "."
sleep 1;
echo ".."
sleep 1;
echo "..."
sleep 1;
echo "...."
sleep 1;
echo "....."
sleep 1;
echo "......"
sleep 1;
echo "....."
sleep 1;
echo "...."
sleep 1;
echo "..."
sleep 1;
echo ".."
sleep 1;
echo "."


echo "In the distance you see a dark shadow approaching."
sleep 2;
echo "Could it be?"
sleep 3;
echo "Is this the the shadowy figure the village spoke of."
sleep 2;
echo "A Myth..a simple folks tale you thought.."
sleep 2;
echo "How could this be..."
sleep 2;
echo "You stand frightened for your life, the shadowy figure is approaching with haste!!"
sleep 4;

TODO=3

echo "1. Drop Weapon & Flee"
echo "2. Stand & Fight"
echo -n "What will you do [1 or 2]? "

while [ $TODO -eq 3 ]; do

read TODO

if [ $TODO -eq 1 ] ; then

    echo "Perhaps you are not ready for the Shattered Forrest. Game over: Drop Weapon & Flee"

    else

        if [ $TODO -eq 2 ] ; then
            echo "You will Stand & Fight!: Stand & Fight"

        else
            echo "1. Drop Weapon & Flee"
            echo "2. Stand & Fight"
            echo -n "What will you do [1 or 2]? "
            TODO=3
        fi
fi
done
```

Line 102

echo "A Myth..a simple folks tale you thought.."

quote missing from end

Line 105 after

echo "How could this be..."
sleep 2

You had

echo "How could this be..."
slepe 2

---

### Post by johnryaniii on 2013-02-25
Thank you both.

Good idea on the functions

---

