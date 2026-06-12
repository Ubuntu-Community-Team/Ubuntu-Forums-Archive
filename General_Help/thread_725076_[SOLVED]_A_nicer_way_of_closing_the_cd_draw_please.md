---
title: "[SOLVED] A nicer way of closing the cd draw please"
date: 2008-03-15
forum: General Help
---

### Post by cogvos on 2008-03-15
Dear all,

Not sure if this is possible, looking around the net suggests not without delving into the word of scripting. Anyway I would like to add an icon to my desktop which allows me to close the cd draw. Why? Well my PC has a stupid posh looking door thing on it which flips open when the cd is ejected and then, since the button close button is on this door (well done Compaq!) cannot be closed again as the button on the door is not in contact with the one on the drive. The only way I can close the drive in push the tray back till it gets the message and closes.

You can eject a cd using the icon for the CD on the desktop. However this then disappears leaving no way of closing the door. What I would like is an icon for the cd when one is inserted, but an icon for the drive when one is on so I can click on it and select close. Or just an icon on the desktop marked close. I don't care.

Apple Macs have a button which opens and closed the door, that'd be nice, anything that means that I no-longer have to force the door closed. Any ideas, I'm not a programmer (any more) so a little package to download would be ideal.

J.

---

### Post by banewman on 2008-03-15
You can make an icon or panel launcher for that.
The command is - 
eject -t
to close the tray
eject
to open it - try in a terminal first.
:)

---

### Post by cogvos on 2008-03-15
Many thanks for the info. could you quickly tell me;

Does eject just work for cds? There's a munti-media card reader (SD etc) attached to the PC and I would not want to eject any cards by accident. 

How do I attach the command to an icon, or launcher. Sorry I am very new at this.

Is it possible to have the icon act like a toggle? So the same icon opens the door if it's closed and closes it if it's open?

J.

---

### Post by Joeb454 on 2008-03-15
You could make a script which act's as a toggle, i'd imagine it'd be something like 
```

#!/bin/bash

TRAY=0
if [ $TRAY==0 ]; then
     eject -t
     TRAY=1
else
     eject
     TRAY=0
fi;

```

---

### Post by cogvos on 2008-03-15
Many thanks for the suggestions.

Although eject and eject -t do work I have a couple of odd problems.

If a CD is in the drive an icon for it is displayed on the desktop. If I use eject -t then the CD's icon disappears. I expected that! However it does not get re-displayed if I then close the drive door. The cd is read, but it does not appear to get mounted. The only way I can get the icon back on the desktop is log off and back on again. Hardly ideal.

Any ideas?

Also I am afraid that the bit of code that Joeb454 supplied does not work as TRAY is always 0. I think the problem is the partly the first line and also that the variable dies with the process. So it's always 0 even without the 1st line as its recreated each time the script is run. Does anyone know how to set a variable in a script so that it stays set, or better still read the status of the cd drive door.

I did find a tool called CD Eject Tool V2.8, but its windoz only.

Hope someone can help

J.

---

### Post by Joeb454 on 2008-03-16
Hey, sorry for that, just found the error, please find the corrected version below (it ***should*** work, I can't test the close command because I'm on a laptop right now, but it definitely opens. I've also attached the script itself, which you will likely need to make executable :)

For anybody interested, the error was that because $TRAY == 0 at the beginning, it tried to close the tray, not open it. Also, to keep the variable, piped the variable $TRAY to a file in ~/ :)

```

#!/bin/bash

TRAY=0
if [ 'cat ~/.traystatus'==0 ]; then
     eject
     TRAY=1
     echo $TRAY > ~/.traystatus
else
     eject -t
     TRAY=0
     echo $TRAY > ~/.traystatus
fi;

```

---

### Post by cogvos on 2008-03-19
Hi there,

Many thanks for sending an update, I'll give it a go at the weekend. Out of interest (As I am not up on BASH scripts, or indeed any scripts!) what does the tilde (~) do in the line echo $TRAY > ~/.traystatus ?

Also do you know if this will be clever enough not to get confused at the very start if the tray is open? Since traystatus will not exist I'm guessing that the first if will return 0 (rather than file not found?) so it will try and open the tray, when it's already open? Equally if I close it using the script, but then open it some other way will it then try and open it again if I try and use the script? Sorry this is sounding complicated...

Anyway it will enable me to open and close the tray by clicking on an icon, though I guess that I may have to click twice if the above happens? So many thanks again.

J.

---

### Post by Joeb454 on 2008-03-21
It probably will get confused if you've opened the tray manually.

And the tilde means your home directory, e.g. the tilde on my machine right now means /home/joe/ :)

---

### Post by cogvos on 2008-03-21
Hi Joeb454
Many thanks once again.

In playing around and searching the net I came across a small C programme that reads the status of the cd draw and returns a text string depending on if the door is open, closed with a disk in it or closed without a disk. 
Its on [http://www.kudla.org/index.php?wl_topic=4](http://www.kudla.org/index.php?wl_topic=4) and the actual code is here [http://www.kudla.org/index.php?wl_mode=more&wl_eid=88&wl_topic=4](http://www.kudla.org/index.php?wl_mode=more&wl_eid=88&wl_topic=4)

Along with a rather nice explanation.

So taking your script I compiled it as cd_status had a play and came up with the following

#!/bin/bash
if ['./cd_status'=='CDS_TRAY_OPEN']; then
	eject 
echo "eject"
else
echo" close"
	eject -t
fi;

Which... Doesn't work.

cd_status works fine if you call it from a terminal. But I keep getting ' 
./cd_toggle: line 2: [./cd_status==CDS_TRAY_OPEN]: No such file or directory

when I try the script

'Cos I can't figure out how to get the script to execute the programme and allow me to read the result.... <sigh>

Both the script and the programme are in the same directory. I also tried using the ~ and typing the full path to the programme from home, also without success. It keeps looking for a programme which includes the test (==bla bla).

If I change the code to have spaces 
if ['./cd_status' == 'CDS_TRAY_OPEN']; then
I get 
./cd_toggle: line 2: [./cd_status: No such file or directory
:confused:
What am I doing wrong? I'm baffled!
J.

---

### Post by cogvos on 2008-03-24
The solution, sort of...

The usual warnings apply. This works for me it might not for you. I am not responsible for any problems/data loss or anything else that might occur if you try and use this. It's supplied as is without any guarantee for fitness of purpose of any kind. I am very new at this and may have made a goof so it is very much 'work in progress'.:oops:

Especially important. I do not know what will happen if you have more than one cd/DVD/Blue Ray or other drive which the shell command eject might work on. This works on a Compaq Presario with Ubuntu 7.10 and a  single internal DVD drive. Will it work with USB drives? Sorry I don't know.

To get an icon to open and close the cd draw on a double clock I did the following;

First download the souce code I mentioned above ... 

[http://www.kudla.org/index.php?wl_mo...=88&wl_topic=4](http://www.kudla.org/index.php?wl_mo...=88&wl_topic=4)

and change the printf lines to return numbers not words as below. 
Thus we have

case CDS_TRAY_OPEN:
    printf("1");
    break;

case CDS_NO_DISC:
    printf("2");
    break;

... and so on. Though you don't actually need to change any lines other than the 1st printf since that is all we need.

save the result, compile it and call the executable cd_status

You can see if it works by simply calling it with ./cd_status and seeing the result change with the cd door open and closed.

make a new directory immediatly below your home one and call this cd_tray

make a text document called cd_toggle and copy and paste the following into it

#!/bin/bash
status=`~/cd_tray/cd_status`
if [ $status -eq 1 ]; then	
eject -t;
else
eject;
fi;


save this.

So what we have is a directory called cd_tray containing an executable program and a script. Make the script executable (right click on the icon in the directory and select the relevant property)

now ./cd_toggle should open and close the cd tray.

The script calls the programme which tests the status of the CD tray (the second line) and stores the reult in the variable status 

I haven't a clue what would hapen if you have more than one CD/DVD etc drive even less of a clue what would happen if one was closed and one open! Beware.

It then checks if the returned value is 1 - that is the door is open - and if it is calls eject -t, which closes it.
Otherwise the door is closed and the script opens it with eject.

I tried using == instead of -eq but this just did not work, and I do not know enough to say why sorry.

To attach this to an icon right click on the desktop click 'create launcher' and then browse to the script cd_toggle in the directory cd_tray

You can pick a new icon by clicking on the picture in the top left corner. Click OK and you are done.

There is probably a clever way of just doing this in C but I don't know how to. 
I guess there is a way of getting it to work with multiple drives... but I don't know how to.
As mentioned it works for me and I no-longer have to prod the cd tray till it gets the message and closes.

My thanks to Rob Kudla for releasing his code as freeware under the GNU license and to joeb454 for pointing me in the right direction to start with.

J.

---

