---
title: "Is there a way to affect X from one of the 'side-terminals' ?"
date: 2007-01-12
forum: General Help
---

### Post by Ecthelion on 2007-01-12
Hey,

Just something I wondered. I have sometimes problems with my x (for example, I sometimes play tremulous. If I play tremulous with beryl opened, then x get's stuck when I try to end the game)
And now I wondered... Is there a way to affect the x (gnome) using a side-terminal.
With side-terminal I mean a terminal you get by pushing Ctrl-Alt-<F1 - F6>
If anyone know the correct name of these terminals... :)  Tell me.

With "affecting the x" I mean, for example:
When I'm in the graphical, I can do (in terminal) the following to change from beryl to metacity:
```
killall beryl-manager
metacity --replace
```

I can't do the latter in a side-terminal, since this would execute something graphical. And that doesn't work in a side-terminal.
Is there a way to give a command in one of these 'side-terminals', and to have that command executed in the graphical interface (Crtl-alt-f7) ?

The reason why I wonder is because this would be usefull when I have those x-problems. Then I could go to a side-terminal and fix it instead of having to restart it (the x).
:D  Just annoying to hav to restart all your programs then ;-) :cool:

---

### Post by po0f on 2007-01-12
Ecthelion,

You should be able to kill Beryl from a virtual console (side terminal ;)) no problem, but to start Metacity from one, just use:
```
[FONT="Courier New"]$ DISPLAY=:0 metacity --replace &[/FONT]
```

---

### Post by Ecthelion on 2007-01-12
That was what I was looking for.

Thanks!

---

### Post by Ecthelion on 2007-01-14
Is there a way to send command from graphical to virtual terminal?

My problem is now that I've made a script to start beryl...
But that script never ends... => Because the command "beryl-manager" never ends too...
So I would like to send it to a virtual terminal where I don't care if it runs...

---

### Post by po0f on 2007-01-14
Ecthelion,

Your script calls 'beryl-manager'?  Just add an ampersand* (&) to the end of the line that calls 'beryl-manager'.  This tells the shell to put the command in the background, and frees the shell for further use.

Post your script and I'll tell you exactly where to put it.

[EDIT]

* s/apostrophe/ampersand/, stupid me.

---

### Post by Ecthelion on 2007-01-14
> Your script calls 'beryl-manager'?
It's a bit more complicate.... :mrgreen: 

In fact there are two scripts.
The first one uses an option of the second one...
See for yourself :) 


> #!/bin/bash
#Script made the 12/1/2007 by Ecthelion
echo "Control if Beryl is running and put it out if needed";
(bash /home/ecthelion/Beryl_ON_OFF -Off) & sleep 3;
echo "Start tremulous"
tremulous;
echo "Tremulous has been closed, put beryl back on" 
(bash /home/ecthelion/Beryl_ON_OFF -On) & sleep 3;
exit;


Tremulous is an open-source game...
I made these script because if tremulous is run with beryl it crashes when you try to close it...

> #!/bin/bash
#Script made the 12/1/2007 by Ecthelion

(NO_ARGS=0
echo "You are running the beryl_on_off script";
if [ $# -eq "$NO_ARGS" ]  # Script invoked with no command-line args?
then
	if ps -A | grep "beryl-manager" > /dev/null;
	then 			#Shutdown Beryl
	killall beryl-manager;
	metacity --replace;
	else			#Startup Beryl
	beryl-manager;
	fi
fi 

while getopts ":O:" Option
do
  case $Option in
    O     ) 	if [ "ff" = "$OPTARG" ]
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
		echo "Wrong option choosen, possible options are  -On / -Off";
		#echo "Given option was: \"$OPTARG\" ";
		fi ;;
    *     ) echo "Unimplemented option chosen." ;;   # DEFAULT
  esac
done
exit 0
) &

As you see I already tried running them as jobs (using the &).
But you can try for yourself: doing "killall beryl-manager" and then "metacity --replace &" works allright.
But when you do "beryl-manager &" after that, you don't get the next line in terminal. Probably because there's a lot that has to be loaded.
In fact that's why there's often "& sleep 3". That's to make sure nothing starts while other things are loading.

---

### Post by po0f on 2007-01-14
Ecthelion,

Why can't you just use beryl-manager to start Metacity?  Just right-click on it, and navigate to "Select window manager" and choose Metacity.  Then just run your game.  Unless beryl-manager has been drastically changed since the last time I used it (~2 months ago), this should work.

---

### Post by Ecthelion on 2007-01-15
> Why can't you just use beryl-manager to start Metacity? Just right-click on it, and navigate to "Select window manager" and choose Metacity. Then just run your game. Unless beryl-manager has been drastically changed since the last time I used it (~2 months ago), this should work.

I can do that of course... But the reason why I made these scripts is because I foret to do that quite often. (when I think of gaming...)
And I had to turn the power off each time I forgot... Not very healthy.

---

### Post by Ecthelion on 2007-01-15
Since this gets more related to "howto mak a script t shutdown beryl", I've started a new thread.
[http://ubuntuforums.org/showthread.php?p=2015148](http://ubuntuforums.org/showthread.php?p=2015148)

Please help me finish that script :KS 

Thanks for the help,

Ecthelion

---

