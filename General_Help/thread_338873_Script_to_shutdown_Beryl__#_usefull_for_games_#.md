---
title: "Script to shutdown Beryl  # usefull for games #"
date: 2007-01-15
forum: General Help
---

### Post by Ecthelion on 2007-01-15
.

[EDIT] [COLOR="Red"]**Nevermind the first post. The second post contains the working scripts. If you are looking for those, scroll down!**[/COLOR] [/EDIT]


After asking some questions related to scripting on the forum, I still didn't succeeded to make it.
The plan is to make 1 script that can shutdown beryl, and put it back on, as is requested.
This works.

When the script gets executed without argument, it should test if beryl runs. If beryl runs, shut it down, if beryl doesn't run, start it up.
This also works.
Nevermind the first post. The second post contains the working scripts. If you are looking for those, scroll down!
The problem I'm having now is related to the "beryl-manager" command.
Some commands keep running after executed, which blocks the terminal. So all the commands after that one don't get executed.
Putting the command between () and using & didn't worked so far.

Last thing I tried was to find out how to send that particular command to a virtual terminal. I don't care if that terminal gets blocked. I don't see it 8) . (Is this short-sighted?)
After that I figured out that I could also open an extra terminal in the graphical to executed the command. For example: "gnome-terminal -e beryl-manager". But then I need to find a way to kill this particular terminal after 3 or 4 seconds.
All suggestions are welcome.

The first script is an example of how you could call the Beryl_ON_OFF script.

> 
#!/bin/bash
#Script made the 12/1/2007 by Ecthelion
echo "Control if Beryl is running and put it out if needed";
(bash /home/ecthelion/Beryl_ON_OFF -Off) & sleep 3;
echo "Start tremulous"
tremulous;
echo "Tremulous has been closed, put beryl back on"
(bash /home/ecthelion/Beryl_ON_OFF -On) & sleep 3;
exit;
When running this script beryl should b killed and the game should start.
This currently don't happen because no command after "(bash /home/ecthelion/Beryl_ON_OFF -Off) & sleep 3;" gets executed... That's what needs to be fixed...


This is the script which turns of beryl or puts it back on. The script works. Only problem is that it doesn't seems to get executed all the way to "exit".
Which is bad because any script running this one would get blocked.
> #!/bin/bash
#Script made the 12/1/2007 by Ecthelion

(NO_ARGS=0
echo "You are running the beryl_on_off script";
if [ $# -eq "$NO_ARGS" ] # Script invoked with no command-line args?
then
if ps -A | grep "beryl-manager" > /dev/null;
then #Shutdown Beryl
killall beryl-manager;
metacity --replace;
else #Startup Beryl
beryl-manager;
fi
fi

while getopts ":O:" Option
do
case $Option in
O ) if [ "ff" = "$OPTARG" ]
then
if ps -A | grep "beryl-manager" > /dev/null;
then
echo "Beryl will be shut down";
killall beryl-manager;
metacity --replace ;
else
echo "Beryl is not running"
fi

elif [ "n" = "$OPTARG" ]
then
if ps -A | grep "beryl-manager" > /dev/null;
then
echo "Beryl is already running"
else
echo "Starting Beryl...";
beryl-manager;
fi

else
echo "Wrong option choosen, possible options are -On / -Off";
#echo "Given option was: \"$OPTARG\" ";
fi ;;
* ) echo "Unimplemented option chosen." ;; # DEFAULT
esac
done
exit 0
) &

These script can be usefull for gamers... Just replace "tremulous" by the command that runs the game you want, and your game won't block because of beryl anymore...
But for now it doesn't work yet..

The threads where I was helped to get this far are:
[http://ubuntuforums.org/showthread.php?t=336111](http://ubuntuforums.org/showthread.php?t=336111)  #Howto use "if" in terminal
[http://ubuntuforums.org/showthread.php?t=336891](http://ubuntuforums.org/showthread.php?t=336891)  # Is there a way to effect X from one of the 'side-terminals' ?

Any help would be appreciated.

Ecthelion.

---

### Post by Ecthelion on 2007-01-15
Alright I've solved the problem.
Here are the script...
They work for me.

If anyone has problems with these or questions, feel free to ask...

Script StartTremulous:
> #!/bin/bash
#Script made the 12/1/2007 by Ecthelion
br=0
if ps -A|grep "beryl-manager" > /dve/null
then br=1
fi
**(bash /home/ecthelion/Beryl_ON_OFF -Off)** & sleep 3;
echo "Control if Beryl runs and put it out if needed";
**tremulous;**
echo "Tremulous was closed" 
if [ $br = 1 ]
then
(bash /home/ecthelion/Beryl_ON_OFF -On) & sleep 3;
fi
exit;


Script Beryl_ON_OFF
 > #!/bin/bash
#Script made the 12/1/2007 by Ecthelion
br=0
if ps -A | grep "beryl-manager" > /dev/null
	then br=1
fi

(NO_ARGS=0
echo "You are running the beryl_on_off script";
if [ $# -eq "$NO_ARGS" ]  # Script invoked with no command-line args?
then
	if [ $br = 1 ]
	then 			#Shutdown Beryl
		killall beryl-manager;
		killall beryl;
		#killall emerald;
		gnome-terminal -e "metacity --replace" && sleep 1 &
		echo "Metacity vervangt Beryl" & sleep 2;
		killall gnome-terminal;
	else			#Startup Beryl
		gnome-terminal -e "beryl-manager" & sleep 2
		#gnome-terminal -e "beryl-manager" && sleep1 &
		#gnome-terminal -e "emerald --replace" & sleep 2
		echo "Emerald & Beryl zijn geladen" & sleep 5; 		
	fi
fi 

while getopts ":O:" Option
do
  case $Option in
    O     ) 	if [ "ff" = "$OPTARG" ]
		then
			if [ $br = 1 ]
			then
				echo "Beryl wordt afgesloten";
				killall beryl-manager;
				gnome-terminal -e "metacity --replace" & sleep 1
				#killall metacity;
			else
				echo "Beryl staat niet aan"
			fi
			
		elif [ "n" = "$OPTARG" ]
		then
			if [ $br = 1 ]
			then
				echo "Beryl draait reeds"
			else
				echo "Bezig met opstarten van Beryl";
				gnome-terminal -e "beryl-manager" & sleep 10
				
				
			fi
			
		else
		echo "Verkeerd argument ingegeven, kies voor -On / -Off";
		#echo "Ingegeven argument zou dit moeten zijn: \"$OPTARG\" ";
		fi ;;
    *     ) echo "Unimplemented option chosen." ;;   # DEFAULT
  esac
done
exit 0
) &



Some comments on the script:
**(bash */home/ecthelion/*Beryl_ON_OFF -Off)** & sleep 3;
Replace /hom/ecthelion/Beryl_ON_OFF by the location and name you gave the _second_ script

**tremulous;**
You can replace this by a command for any other game. F.e. for Wow this would be:
/usr/X11R6/bin/wine "/media/storage/Games/World of Warcraft/WoW.exe" -opengl

**killall metacity;**
Nevermind the fact that metacity gets started and killed immediatly.
This is to kill the terminal in which metacity runs. As you will see metacity will still be up after this.

**note: the script is written for gnome, if you use kde you'll have to change some of it**

---

### Post by beefcurry on 2007-01-23
Very nice :D, thanks.

---

### Post by Ecthelion on 2007-01-29
Thanks.

I made some modification in the Beryl_ON_OFF script (the one in the second post)
There where some problems after I did an Beryl update...
Normally it should work just fine now.

If there are problems, please tell me.

I've also changed the gamestarting script to let it only start beryl when closing the game if beryl was running before starting the game

---

### Post by jrstravino on 2007-02-25
My script for the game "sauerbraten" (cube2)...
This simple, but work for me. :) 

```
#!/bin/bash
#Script Beryl/on/off by jrstravino

#Beryl off;
killall beryl-manager;
killall beryl;
gnome-terminal -e "metacity --replace" && sleep 3 &
killall gnome-terminal;

#run game;
/home/tux/sauerbraten/sauerbraten_unix -w800 -h600 -b16 -z24 -a1 -f1;

#Beryl on;
gnome-terminal -e "beryl-manager" & sleep 2
fi
exit;
```

---

### Post by sisco311 on 2007-02-25
my script for tvtime:
```
killall beryl&
metacity --replace&

sox -w -r 16000 -t alsa hw:1,0 -r 16000 -t alsa hw:0,0 &
tvtime

wait tvtime
killall sox

beryl&
emerald --replace&

```

---

### Post by jrstravino on 2007-02-25
Thanks sisco311,,,

```
#!/bin/bash
#Script Beryl/on/off by jrstravino

# Beryl off;
killall beryl&
metacity --replace&

#run game;
cd /home/tux/sauerbraten
sh sauerbraten_unix -w800 -h600 -b16 -z24 -a1 -f1;

wait sauerbraten_unix
killall sauerbraten_unix

#Beryl on;
beryl&
emerald --replace&
```

---

### Post by Ecthelion on 2007-02-26
Good scripts indeed.
Mine can be replaced by those...
But I made my script to be multi-functional.

For example I hav a starter on my top panel that executes Beryl_ON_OFF
so that it switches between on and off
In games I can call on that script to put beryl on and off etc...
Also it checks if beryl runs before quitting before quitting it... So if beryl doesn't run at startup, it doesn't get executed at shutdown.
Etc...

But of course, the most important about scripts is... if they work.  :KS

---

### Post by nsleiman on 2007-04-12
Maybe you can help me in this:

When i log into the xgl-session and fire up beryl, if i want to log out the system freezes and i have no other way thn pressing the power button till it shuts down :( this causes me many fsck's and wasting of time,

is it possible to use such scripts for a smoother session-end ?

---

### Post by Ecthelion on 2007-04-13
Well I guess the only way we will know that is if we try...

But don't start to use scripts immediately. First try to do it by hand...
(script are in fact normal commandos put in a file)

Well I would say, try the graphical method first. I have Beryl with AIGLX so I'm not sure if you also have this option, but if you do
Right-click on the beryl icon > change window manager > metacity

If you don't have this option do this in terminal:
killall beryl-manager
metacity --replace

If logging out doesn't freeze after this, then you could try making a script to log out/shut down.

---

### Post by nsleiman on 2007-04-13
i succedded :) i just changed some setting in kdmrc and put an autostart script in .kde/Autostart.

Xgl+kdm+Edgy+ATI, it really rocks :)

---

