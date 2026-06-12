---
title: "printing terminal stout to text file"
date: 2021-11-24
forum: General Help
---

### Post by coley9225 on 2021-11-24
[INDENT]I've written some math quiz scripts for my grandkids, and started using ansi codes to output colored text in the terminal. The script creates a temp file and a permanent file, then copies tempt to perm file. I've included 1 script below. The problem I'm having, is that the file shows the ansi code. I've included a copy of 1 such file below. The ideal case would be to be able to print in color, but the main goal is to find a way for it not to show the ansi codes in the file. With the ansi codes included, it gets hard to read. I could edit the codes out in a text editor and then print, but this is a short script, and I've got 1 that is multiple levels and has a lot of stout, thus making the editing a long process. So the question is, is there an easy way to eliminate the ansi codes prior to saving the file.
My script is:
```
#!/bin/bash

#This script waas written for my grandchildre. It is a quiz with addition
#problems. The user can set the number of problems, and maximum number size.
#To use the script as written, you must install cowsay and lolcat, which can be
#installed with 'sudo apt install cowsay' and 'sudo apt install lolcat'.
#I have commented out the make file and copy functions because the file saves and
#prints all the ansi codes and I haven't yet figured out a way to avoid that( any
#help here would be appeciated).
function_1 () {
	x=$[RANDOM%$R1] y=$[RANDOM%$R2]
	sum=$(($x + $y))
    good=$(shuf -n1 /home/charles/Scripts/Bash_in-progress/right_answer.txt)
    bad=$(shuf -n1 /home/charles/Scripts/Bash_in-progress/wrong_answer.txt)
	echo  -e "${blue}What is $x + $y?${nc}" | cowsay
		read answer
	echo "Let's see here, you answered $answer. So I do this...caarry that..." | cowsay | lolcat
	sleep 3
	if [[ $answer = $sum ]] ;
		then echo -e "${green}${good}${nc}" | cowsay
		C=$(( $C + 1 ))
		echo "Press enter to continue"
read -r -s -p $"Press <ENTER> to continue....\n"
clear
	else
		echo -e "${red}${bad}${nc}" | cowsay -f dragon
		sleep 2
		echo -e "${red}The correct answer is ${green}$sum.${nc}" | cowsay
		I=$(( $I + 1 ))
		echo "Press enter to continue"
read -r -s -p $"Press <ENTER> to continue....\n"
clear
fi
}


green='\033[0;32m'
red='\033[0;31m'
blue='\033[0;94m'
nc='\033[0m'
now=$(date +"%m-%d-%y_%I:%M_%p")
echo "This test was taken $now"
I=0
C=0


echo -e "${blue}Hello, why don't you tell me your name.${nc}" | cowsay
	read name
	name=$name
clear
echo -e "${blue}Hello $name. My name is Alex and I'll be giving you your test today.${nc}" | cowsay


#file=$name-$now
#touch /home/charles/Tests/$file.txt




echo -e "${blue}OK $name, how many problems would you like to do today?${nc}" | cowsay
	read number
	TP=$number
clear
echo -e "${blue}Very good, we will do ${TP} problems today.${nc}" | cowsay


echo -e "${blue}What's the biggest you want your numbers to be?${nc}" | cowsay
	read limit
	R1=$limit
	R2=$((R1+1))
clear
echo -e "${blue}OK, your numbers will not be larger than $limit.${nc}" | cowsay


echo "OK, let's get started." | cowsay | lolcat


echo "Press enter to continue"
read -r -s -p $"Press <ENTER> to continue....\n"
clear
PC=1
	while [[ $PC -le $TP ]]
	do
	PC=$(( $PC + 1))
		function_1
	done


score=$(( ($C*1000/$TP+5)/10 ))


echo "OK, let's see how you did today." | cowsay | lolcat
sleep 1


echo -e "${green}On todays quiz, you got $C problems correct, you got $I wrong.${nc}" | cowsay
echo -e "${green}Your score today is $score.${nc}"


#cp /home/charles/Tests/temp_file.txt /home/charles/Tests/$file.txt
#sleep 3


#echo "Would you like to print a copy of the test?"
#	read answer
#	answer=${answer^^}
#	answer=${answer:0:1}
#		if [[ ${answer} = 'Y' ]] ;
#			then lp /home/charles/Tests/${file}.txt
#			echo "It should be printing."
#			echo "I'll see you next time."
#			sleep 3
#			exit
#		elif [[ ${answer} = 'N' ]] ;
            then echo "OK. The file is saved and can be printed anytime."
#fi
		echo -e "${green}You did well today.${nc}" | cowsay
		sleep 4
		clear
		echo -e "${green}If you didn't do as good as you wanted, don't worry about it. A little more pratice and you will be perfect next time.${nc}" | cowsay
		echo "Press enter to continue"
read -r -s -p $"Press <ENTER> to continue....\n"
clear
		echo -e "${green}After all that work, I'll ask the conductor to give you a ride home.${nc}" | cowsay
		sleep 3
		echo "Hey Mr. Conductor, can you give $name a ride home today?" | cowsay | lolcat
		sleep 5
		clear
		echo "Of course I can, ALL ABOARD" |cowsay -f elephant | lolcat
		sleep 5
		clear
echo -e "${green}OK,I'll see you next time.${nc}" | cowsay
sleep 5
sl
clear
exit
```
And the saved file is:

```
This test was taken 08-07-21_12:09_PMHello, why don't you tell me your name.
Hello Coley. My name is Alex and I'll be giving you your test today.
OK Coley, how many problems would you like to do today?
Very good, we will do 5 problems today.
What's the biggest you want your numbers to be?
OK, your numbers will not be larger than 10.
OK, let's get started.
What is 2 + 0?
You answered 2.
[0;32mThat is correct!! Great job.[0m
What is 6 + 7?
You answered 13.
[0;32mThat is correct!! Great job.[0m
What is 9 + 9?
You answered 17.
[0;31mSorry,that is not right. The correct answer is [0;32m18.[0m
What is 5 + 4?
You answered 9.
[0;32mThat is correct!! Great job.[0m
What is 8 + 1?
You answered 9.
[0;32mThat is correct!! Great job.[0m
OK, let's see how you did today.
On todays quiz, you got 4 problems correct, you got 1 wrong.
Your score today is 80.
Would you like to print a copy of the test?
request id is TS3300USB-21 (1 file(s))
It should be printing.
I'll see you next time.
```
The script responds different color based on it is comments and questions, correct answer, or incorrect answer. The idea is to be able to print the test and use it as a study guide. Any tips would be great, aand as always, thanks in advance for the help.[/INDENT]

---

### Post by coley9225 on 2021-11-24
:(Sorry about that. I made the post with code tags, and checked a preview and lost the original. I copied the post and pasted in the preview page and it did awaay with the code tags. Next time I won't preview post.

---

### Post by KBar on 2021-11-24
You can edit your post. Try using [http://pastebin.com](http://pastebin.com)

---

### Post by deadflowr on 2021-11-24
> I made the post with code tags, and checked a preview and lost the original. I copied the post and pasted in the preview page and it did awaay with the code tags. 
Fixed it for you.

---

### Post by coley9225 on 2021-11-24
Thank you @deadflowr, I won't be using the preview option anymore...lol. Live and learn, it's the linux way.

---

### Post by Holger_Gehrke on 2021-11-24
Once you have the file with all the embedded terminal control codes in it you can use the **s**treaming **ed**itor sed to remove them.
```

sed 's/\d27\[0;32m//g;s/\d27\[0;31m//g;s/\d27\[0;94m//g;s/\d27\[0m//g' /home/charles/Test/${file}.txt|lp -

```
This may look rather daunting, but is actually quite simple: each 's/*something*//g' is a **s**ubstitute command for sed, telling it to search for '*something'* and substitute nothing for it. The 'something' sed searches for is a regular expression, and since '[' has a special meaning in regular expressions it must be escaped by prefixing it with a '\'. The '\d27' is the way to write the escape character. The 'g' at the end of each command is there in case there are multiples of one item that need replacing in one line (sed works on a line by line basis; without the 'g' it would only remove one occurrence of each control sequence per line). sed sends the results of it's work to standard output, so we pipe that into 'lp' and give '-' as a parameter to tell it to print it's standard input.
In theory you could also use something like '\d27[^m]*m' as the term to replace (all sequences begin with escape and end with an 'm' with characters that aren't 'm' in between) and have only
```

sed 's/\d27[^m]*m//g' /home/charles/Test/${file}.txt|lp -

```
but I'm not completely certain that this will always do the right thing; there might be sequences that don't end with an 'm' - in which case sed would remove to much - or there might be sequences which do have an 'm' before the end - in which case sed would remove to little.

Holger

---

### Post by The Cog on 2021-11-24
Holger_Gehrke has much the same approach than I would take, although I'm not sure while he's sending it straight to the printer. 
He gives a nice description of the sed operation, but for some reason I feel compelled to search for ESC followed by [ rather than just ESC as the trigger. In your case that won't make any difference, but it just feels more right to me.
Instead of copying the temp file to the permanent file, I would pass it through sed like this, using sed to strip the ansi code and write the output to the permanent file:
```
sed 's/\d27\[[^m]*m//g' ~/Tests/temp_file.txt > ~/Tests/$file.txt
```

---

### Post by coley9225 on 2021-11-25
Great tips. I've been putting learning sed for a while, seems the time has come to study it a little more. What i'm going too do is use sed commands as suggested and redirect that to the permanent file, as my printing is done from there it will work quite well for my purposes. I will have to rewrite the script for a printable version(keeping this 1 because it's cool), because I've add a 'press enter to continue',cowsay, lolcat and sl, which all produce unwanted stuff in the saved file. I will take the suggestions as a kick in the rear to learn 'sed' a little better. Thanks for the help.

---

### Post by Holger_Gehrke on 2021-11-26
Why not simply use the script as is and pipe the commands whose output you want in the file through 'tee' to send them both to the screen and to the file ? The option '--append' of tee does just what the name suggests.

Also: I see you're reading the files with good and bad messages every time you ask a question. Why not read all the messages into an array using mapfile (a bash builtin; also known as readarray) once during initialization and then select a random one ?

Holger

---

### Post by coley9225 on 2021-11-27
OK. I tried to reply but the reply was to long, so I'm going to try pastbin, never tied before so I hope this works.

Thanks for the tips Holger. As for your first idea. I've made an alias for this script, [COLOR=#ff0000]alias add_test="cd /home/charles/Tests/scripts && ./add-with-file.sh | tee /home/charles/Tests/temp_file.txt"[/COLOR]. This saves me a lot of typing. By running this I pipe the script to the tee command, so similar to you suggestion. If your saying I can do this on an as-wanted bases from within the script, please point me in the direction of some further reading. I was looking for a way to do that originally.
As to your second idea. As I was searching for a way to use random lines from an external text file, I did see references to using an array, randomizing the array, then use the lines 1 by 1 until all are used, eliminating back to back same answers. After all the lines are used, I would have to re-randomize the lines and begin using them again. I do get times when it will reply the same on 2 or 3 problems in a row, and using an array should solve that problem. If you could point toward further reading on that it would be great.
I'm using the command that The Cog suggested,[COLOR=#ff0000] sed 's/\d27\[[^m]*m//g' ~/Tests/temp_file.txt > ~/Tests/$file.txt,r [/COLOR][COLOR=#000000]and it works fine for removing the ansi codes, But at every instance of the clear command, I still get strange stuff. I'm going to rewrite the script to a more print-friendly version, at this point it's more of a learn to do this thing. Now for the stuff that's new to me. I think I have the files, 1 as output from the tee command, before using sed, and 1 as saved after running sed. I edited the after version with[[ I want to remove this line]] to make it easier to spot the strange stuff I still getting. Also, you'll notice that with the ASCII art in place, the file would make for a rather large print job, which is what lead to the decision to rewrite the script.
The raw file, before editing with sed: [/COLOR]http://pastebin.com/6GXNTGaG
And after using sed: [http://pastebin.com/S778ad4F]("http://pastebin.com/5778ad4F")
Hopefully I did that right and you can see the files. As always, thanks for all the help.

---

### Post by Holger_Gehrke on 2021-11-28
What I meant was to have 'tee' multiple times inside the script. For example instead of 
```

echo  -e "${blue}What is $x + $y?${nc}" | cowsay

```
you'd do
```

echo  -e "${blue}What is $x + $y?${nc}" | tee --append ~charles/Tests/$file.txt | cowsay

```
and get just the text without the ASCII-cow. This would also clean up most of the control sequences since for example 'clear' works by printing the sequence for 'move cursor to the home position', 'clear screen above the cursor', and 'clear screen below the cursor'. That's why I mentioned the option '--append' in my earlier post.

As for using arrays for the messages: you can either use 'declare -a goodmsgs; mapfile goodmsgs < /home/charles/Scripts/Bash_in-progress/right_answer.txt' (don't try to use mapfile in a pipeline; each element of a pipeline runs in it's own subshell so the changes to the array variable would get lost). Or you could pull the messages into the script and do something like 'declare -a goodmsgs=("First message" "Second message" "Message number three")'. To avoid repeat messages, something like this should work:
```

declare -a goodmsgs=("First message" "Second message" "Message number three") # set up the array with the messages
gml=$((${#goodmsgs[@]}-1))                                                    # limit for the random numbers for selecting from the array; we never select the last element; "used" messages get moved to the end
index=$(($RANDOM%$gml))                                                       # select an element ...
echo ${goodmsgs[${index}]}                                                    # ... print it ...
tempvar=${goodmsgs[${index}]}                                                 # ... store it in a temporary variable ...
goodmsgs[${index}]=${goodmsgs[$((${#goodmsgs[@]}-1))]}                        # ... overwrite it with the contents of the last element ...
goodmsgs[$((${#goodmsgs[@]}-1))]=$tempvar                                     # ... then store the used message in the last element of the array.

```
The thing to remember to understand this is that array indices in the shell (and in C) run from 0 to one less than the number of elements (so 0,1,2 for a three element array ...).

Holger

---

### Post by coley9225 on 2021-11-28
Thanks Holger. I've looking for a way to use tee within the script. Your tips helps a lot, and being able to print only the needed stuff to the file saves me from having to rewrite the entire script. I'll also be taking a much closer look at the array script addition you gave, this looks like another perfect change. I really appreciate all the help, not just from you but the forums in general.

---

### Post by Holger_Gehrke on 2021-11-28
Another thing: hard-coding terminal escape sequences is not a good idea. They are hard to read. Also while actual hardware terminals have become a historical curiosity they do exist and not all of them use the same escape sequences. Ubuntu comes with a database of terminal codes (terminfo) and a program named 'tput' to translate terminal independent mnemonics into actual escape sequences. So
```

green='\033[0;32m'

```
can slightly more readably be written as
```

green=$(tput setaf 2)

```
'setaf' in this means 'set a foreground colour' (three guesses what 'setab' means ...).
There's manual pages both for 'tput' and 'terminfo'. The latter has a long list of terminal capabilities and the mnemonics for them.

Holger

---

