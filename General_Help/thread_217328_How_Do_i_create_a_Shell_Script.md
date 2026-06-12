---
title: "How Do i create a Shell Script"
date: 2006-07-17
forum: General Help
---

### Post by CameronCalver on 2006-07-17
[B]The Problem:
Ok i need something that will run simple little things like killall esd and then esd[/B]

I understand it is pretty simple but i dont have a clue ok can some1 plz help me


[B]Thanks In Advance
,Cameron[/B]

---

### Post by bruenig on 2006-07-17
open a blank text file
```
gedit whateverthenameis
```
start the file with this
```
#! /bin/bash
```
and then put the commands you want that script to do under that, for example
```
#! /bin/bash
cd /home
``` will make you change to the /home directory. When done with the commands save the file.

Next make the script executable ```
chmod +x whateverthenameis
```
Then run it by entering the path to it or if you are in the directory that it is located, you can just enter ./whateverthenameis

You may have to do sudo gedit or sudo chmod +x depending upon where you are saving the script (pretty much anywhere except the /home/USERNAME directory) and may need to do sudo whateverthenameis if the script does things that requires root priveledges. Probably easier just to sudo everything.

---

### Post by CameronCalver on 2006-07-17
so does that meen if i would like to run just say ut2004 but before running run killall esd then esd i would do 

```
#! /bin/bash
        killall esd
        esd
        cd /home/cameron/games/ut2004
         ut2004
```


then do all the chmod stuff

---

### Post by bruenig on 2006-07-17
that seems right however the last part of the script seems unnecessary. If you are going to run ut2004 assuming it is in the directory /home/cameron/games/ut2004, you could circumvent the cd altogether and put something like this
```
#! /bin/bash

killall esd
esd
/home/cameron/games/ut2004/ut2004
```

But you write it how you want. You understand the concept which is the point. Save the file chmod +x it and then run it.

---

### Post by CameronCalver on 2006-07-17
i have uncovered a problem when you killall esd then type esd it makes those sound but the terminal never quits so it will not run the program till it finshes the esd part but that will never happen 

you try it do 

```
killall esd
```

then do 
```
esd
```

and it will just say 

```
cameron@ubuntu:~$ killall esd
cameron@ubuntu:~$ esd

```

also how do i put an icon on the shell file and how do i put it in the applications games menu maybe using alacarte menu editor but what would the command you would put in alacarte  eg

name ut2004
icon....
comment
command ? maybe /home/cameron/scripts/ut2004script

ut2004script being the shell name

i know i could solve that by doing two seperate scripts but what i was going to make the script just an icon but i dont want to run the esd one then the actual game one

---

### Post by bforbes on 2006-07-17
Change esd to
```

esd &

```
That will cause it to run in the background.

---

### Post by CameronCalver on 2006-07-17
**THANK YOU **

Thankyou very much now i can  run things and i will have sound thank you very much for your help

---

### Post by CameronCalver on 2006-07-17
Just a couple of more things
can i get it so in a terminal before it runs the program it says for example
are you cameron y or n if you say n it will close and if you say y it will run is that possible

---

### Post by Lunar_Lamp on 2006-07-17
Slightly more complex, but not too tricky:

```
#!/bin/bash

echo "Are you cameron? (y/n)"

read answer

if [ "$answer" = "y" ]; then
	INSERT_COMMANDS_HERE_TO_DO_IF_YES

else exit

fi
```

Then just create a launcher on your toolbar or in your program list, with the path to the executable file, and make sure you click the "open in terminal" option.

---

### Post by bforbes on 2006-07-17
An experienced hacker may be able to get around this security setup.

---

### Post by Lunar_Lamp on 2006-07-17
PFT!  They'd have to lie and say they were Cameron, and as we all know, experienced hackers don't lie!

---

### Post by bruenig on 2006-07-17
> **bforbes said:**
> An experienced hacker may be able to get around this security setup.

lol, yeah this security setup reminds me for some reason of microsoft bob's security whereby a password misentered three times elicits a prompt allowing you to change the password to something 'easier'

---

### Post by roostishaw on 2006-07-17
> **bforbes said:**
> An experienced hacker may be able to get around this security setup.

:D

---

### Post by CameronCalver on 2006-07-17
its not ment to be security just fun and how would i make it do this

Question do you want to look at a photo of 1.car y/n
if y ask what type 1. toyota 2.honda 3.ford if 1/2/3 if 1 open that pic 
and if answered no to the first question say do you want to look at 1.boat. 2 .motorbike 1/2 if 1 what type etc

---

### Post by CameronCalver on 2006-07-17
would this work 

```
#!/bin/bash

echo "do you want to look at a photo of a car? " (y/n)

read answer

if [ "$answer" = "y" ]; then

echo "what type honda/toyota/holden

if [ "$answer" = "honda" ]; then
/home/cameron/honda

if [ "$answer" = "toyota" ]; then

/home/cameron/toyota

if [ "$answer" = "holden" ]; then

/home/cameron/holden

if [ "$answer" = "n" ]; then

echo "do you want to look at boat/motorbike
etc etc
```

---

### Post by bruenig on 2006-07-17
You have to end an if-then clause with fi, also you need to do another read command after echo ''what type honda/toyota/holden" also the read command doesn't have to be answer, it can be anything. Might help to clear up long scripts. You can do something like
```
#!/bin/bash

echo "do you want to look at a photo of a car? " (y/n)

read answer

if [ "$answer" = "y" ]; then

echo "what type honda/toyota/holden"

read choice

if [ "$choice" = "honda" ]; then
/home/cameron/honda

fi

if [ "$choice" = "toyota" ]; then

/home/cameron/toyota

fi

if [ "$choice" = "holden" ]; then

/home/cameron/holden

fi

else echo "do you want to look at boat/motorbike"

fi

etc etc
```

I think that is right, not the master of scripts myself. Somebody should clear it up if necessary.

---

### Post by CameronCalver on 2006-07-18
ok it worked alright so i decided i want to make one myself and this is what i came up with 
```
#!/bin/bash

echo "do you want to gedit something or play a game? (gedit/game)"

read answer

if [ "$answer" = "gedit" ]; then

echo "do you want to gedit cameon1 or cameron2 (cameron1/cameron2 "

read choice

if [ "$choice" = "cameron1" ]; then
gedit /home/cameron/scripts/random/cameron1

fi

if [ "$choice" = "cameron2" ]; then

gedit /home/cameron/scripts/random/cameron2

fi

if [ "$answer" = "game" ]; then

echo "do you want to play flight gear or solitar (flight/solitare"

read choice

if [ "$choice" = "flight" ]; then
fgfs

fi

if [ "$choice" = "solitare" ]; then

sol

fi

```

but when i answer the first question it just quits

---

### Post by mlind on 2006-07-18
> **CameronCalver said:**
> ok it worked alright so i decided i want to make one myself and this is what i came up with 

but when i answer the first question it just quits

You should probably indent your code to make it more readable, so that
control structure gets more obvious.

```

#!/bin/sh

echo "do you want to gedit something or play a game? (gedit/game)"
read answer
if [ "$answer" = "gedit" ]; then
        echo "do you want to gedit cameon1 or cameron2 (cameron1/cameron2)"
        read choice
        if [ "$choice" = "cameron1" ]; then
                gedit /home/cameron/scripts/random/cameron1
        elif [ "$choice" = "cameron2" ]; then
                gedit /home/cameron/scripts/random/cameron2
        fi
elif [ "$answer" = "game" ]; then
        echo "do you want to play flight gear or solitar (flight/solitare)"
        read choice
        if [ "$choice" = "flight" ]; then
                fgfs
        elif [ "$choice" = "solitare" ]; then
                sol
        fi
fi

```

---

### Post by CameronCalver on 2006-07-18
just a couple of things what is elif and why do you have two fi at the end

and what is the dif from /bin/bash and /bin/sh

and for some reasons yours always work and when i try to make one it never works can you tell me y look at this one
```
#!/bin/sh

echo "are you male or female? (m/f)"
read answer
if [ "$answer" = "m" ]; then
        echo "how old are you (1.10-14 or 2.14-18)"
        read choice
        if [ "$choice" = "1" ]; then
                echo "yougn one are you 
        elif [ "$choice" = "2" ]; then
                echo ok hey you got your license yet
        fi
elif [ "$answer" = "f" ]; then
        echo "do you go to school (y/n)"
        read choice
        if [ "$choice" = "y" ]; then
               echo ok cya 
        elif [ "$choice" = "n" ]; then
                echo you better or you will be dumb
        fi
fi
```

---

### Post by kabus on 2006-07-18
> **CameronCalver said:**
> I understand it is pretty simple but i dont have a clue ok can some1 plz help me


[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

> **CameronCalver said:**
> would this work 


It would be a lot more elegant to use a [case statement]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html").

---

### Post by CameronCalver on 2006-07-18
what would be a simple one that would say do you want to play song 1  and it is in /home/camerom/music/1.ogg and what does elif do

---

### Post by mlind on 2006-07-18
> **CameronCalver said:**
> what would be a simple one that would say do you want to play song 1  and it is in /home/camerom/music/1.ogg and what does elif do

With little tweaking, this could work
```

#!/bin/sh

if [ -z "$1" ]; then
        echo "Usage: $0 filename"
        exit 0
elif [ ! -e "$1" ]; then
        echo "$1 doesn't exist"
        exit 1
fi

gst-launch-0.10 playbin uri=file://"$1"

```

elif means "else if", a condition.

---

### Post by CameronCalver on 2006-07-18
ok so can you re write that if the file is called 1.ogg and it is in /home/cameron/music

---

### Post by bruenig on 2006-07-18
> **CameronCalver said:**
> why do you have two fi at the end

you have an if statement within another if statement. So the first fi closes the nested if statement and the second fi closes the if statement that the first one is enclosed in.

---

### Post by CameronCalver on 2006-07-18
> **mlind said:**
> With little tweaking, this could work
```

#!/bin/sh

if [ -z "$1" ]; then
        echo "Usage: $0 filename"
        exit 0
elif [ ! -e "$1" ]; then
        echo "$1 doesn't exist"
        exit 1
fi

gst-launch-0.10 playbin uri=file://"$1"

```

elif means "else if", a condition.

this is all getting a bit confusing

---

