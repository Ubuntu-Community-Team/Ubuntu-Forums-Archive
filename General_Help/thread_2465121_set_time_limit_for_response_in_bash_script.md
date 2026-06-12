---
title: "set time limit for response in bash script"
date: 2021-07-22
forum: General Help
---

### Post by coley9225 on 2021-07-22
Hello again friends and neighbors. I come (again) humbly asking for help with a script. I have written some math quiz scripts for my grandkids( the add 1 is posted below) to help them learn basic math skills. I am fortunate enough to have a gifted granddaughter( 8 years old) and she loves working with these scripts. I have decided to 'turn up the heat' on her. The script I've posted below uses a function to do the actual problem, checks if correct and enter into proper variable. I want to restrict the time she has to answer to, say, 90 seconds. If she answers, it should stop the timer and check answer. If she fails to answer in the 90 seconds, then I want to 'echo "sorry, you have taken too long to answer. This problem will be counted incorrect."' and the add 1 to $I and loop through to next problem. I don't know if I worded this in a way you can understand my goal, so if more info is needed, please ask. I need this for a much larger version of this, 5 levels, each harder than the previous level, with 5th level being timed. As always, any help would be appreciated.
```
#!/bin/bash

function_1 () {
	x=$[RANDOM%$R1] y=$[RANDOM%$R2]
	sum=$(($x + $y))


	echo "What is $x + $y?"
		read answer
	echo "You answered $answer."
	if [[ $answer = $sum ]] ;
		then echo "That is correct!! Great job."
		C=$(( $C + 1 ))
	else
		echo "Sorry,that is not right. The correct answer is $sum."
		I=$(( $I + 1 ))
fi
}




now=$(date +"%m-%d-%y_%I:%M_%p")
echo "This test was taken $now"
I=0
C=0


echo "Hello, why don't you tell me your name."
	read name
	name=$name


echo "Hello $name. My name is Alex and I'll be giving you your test today."


file=$name-$now
touch /home/charles/Tests/$file.txt




echo "OK $name, how many problems would you like to do today?"
	read number
	TP=$number
echo "Very good, we will do ${TP} problems today."


echo "What's the biggest you want your numbers to be?"
	read limit
	R1=$limit
	R2=$((R1+1))
echo "OK, your numbers will not be larger than $limit."


echo "OK, let's get started."


PC=1
	while [[ $PC -le $TP ]]
	do
	PC=$(( $PC + 1))
		function_1
	done


score=$(( ($C*1000/$TP+5)/10 ))


echo "OK, let's see how you did today."
sleep 1


echo "On todays quiz, you got $C problems correct, you got $I wrong."
echo "Your score today is $score."


cp /home/charles/Tests/temp_file.txt /home/charles/Tests/$file.txt
sleep 3


echo "Would you like to print a copy of the test?"
	read answer
	answer=${answer^^}
	answer=${answer:0:1}
		if [[ ${answer} = 'Y' ]] ;
			then lp /home/charles/Tests/${file}.txt
			echo "It should be printing."
			echo "I'll see you next time."
			sleep 3
			exit
		else echo "OK. The file is saved and can be printed anytime.
		I'll see you next time."
fi
exit



```

Please, if you modify this script, comment out my lines you replace, but leave them there so I can study what you have done. Asking for help does no good if I come back next month to ask for the same helpagain. I'm trying to learn it, not have someone write it for me. Thank you for any help you give.

---

### Post by ActionParsnip on 2021-07-22
Looks like someones homework to me....

---

### Post by coley9225 on 2021-07-22
I've done many, many searches, and all I found is a way to timeout and end script. If you can point me in the right direction, I'll follow the path and see where that leads me. It's all part of the learning process, and I'm not afraid of doing it the hard way, but I've searched using every wording I can think of and followed every link that even remotely sounds close, all to no avail. I've only been a linux user for a couple of years so I am still in the learning stage, although already better with lubuntu than I ever got with windows.

---

### Post by The Cog on 2021-07-22
Use 'man bash' command (or google for 'man bash') and search for "SHELL BUILTIN COMMANDS". There are lots of references to it before you find the actual section, it's about ¾ the way down. There's a section on the **read** command.

---

### Post by coley9225 on 2021-07-22
The cog, I found the solution on stack exchange, and it is close to your suggestion. However, after trying that it would just sit there. I reread the posts and it explained the time shell keyword(builtin) will not work. You must use /usr/bin/time. I made an alias time='/usr/bin/time' and tried again and it works. My revised function_1 code is post below to show what worked. The commented lines at bottom are from the post on stack exchange so ai would have it there for a reference. Thanks for the tip though, i appreciate any tips I can get, that's why I browse the forums several times a day. thanks the actionparsnip for the kick in the rear to get me motivated to dig deeper..lol.
my revised function code is:
```
#!/bin/bash

	x=$(shuf -i 0-50 -n1) y=$(shuf -i 0-50 -n1)
	sum=$(($x + $y))


function_1 () {
	echo "What is $x + $y?"
		read -t 5 answer
    if [[ $answer = "" ]] ;
        then echo "Sorry, you have takn too long to answer. This problem
will be marked as incorrect. Let's move on"
        I=$(( $I + 1 ))
	#echo "You answered $answer."
    elif [[ $answer = $sum ]] ;
		then echo "You answered $answer. That is correct!! Great job."
		C=$(( $C + 1 ))
	else
		echo "You answered $answer. Sorry,that is not right.
The correct answer is $sum."
		I=$(( $I + 1 ))
fi
}


function_1




#read -t 5 -p "Prompt " RESP
#if [[ $? -gt 128 ]] ; then
#    echo -e "\nTimeout"
#else
#    echo "Response = \"$RESP\""  # adding quotes so empty strings are obvious
#fi



```
I copied my original script( in original post) and modified the function and ran it and it works like a charm. Now I can finish my "torture chamber" math test for my grandkids. Ain't computing fun!!! Till next time.

---

