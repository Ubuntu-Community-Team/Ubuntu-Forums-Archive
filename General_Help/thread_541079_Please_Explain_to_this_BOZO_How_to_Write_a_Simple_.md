---
title: "Please Explain to this BOZO How to Write a Simple Script!"
date: 2007-09-02
forum: General Help
---

### Post by OzzyFrank on 2007-09-02
I'm trying to give some very basic scripting a go, like trying to run 2 or more commands that I can run via terminal in a sequence. I figured a basic command (or 2 strung together) like **cd /media/cdrom0 && md5sum -c md5sum.txt** - that works fine in a terminal - should be fine in a launcher, but it wasn't (and I did make sure it was set to "Application in terminal"). So I have tried to make a script, but have no idea what I am doing (just working off more complex examples and trying to wing it). I tried this:

[COLOR="Navy"]!/bin/sh
cd /media/cdrom0
md5sum -c md5sum.txt
fi[/COLOR]

but terminal opens with a "There was an error creating the child process for this terminal" error, and the terminal has no prompt. Can someone please spare the time to point out how to successfully string a bunch of commands together in a script file? Cheers

---

### Post by walkerk on 2007-09-02
> **OzzyFrank said:**
> I'm trying to give some very basic scripting a go, like trying to run 2 or more commands that I can run via terminal in a sequence. I figured a basic command (or 2 strung together) like **cd /media/cdrom0 && md5sum -c md5sum.txt** - that works fine in a terminal - should be fine in a launcher, but it wasn't (and I did make sure it was set to "Application in terminal"). So I have tried to make a script, but have no idea what I am doing (just working off more complex examples and trying to wing it). I tried this:

[COLOR="Navy"]!/bin/sh
cd /media/cdrom0
md5sum -c md5sum.txt
**fi**[/COLOR]

but terminal opens with a "There was an error creating the child process for this terminal" error, and the terminal has no prompt. Can someone please spare the time to point out how to successfully string a bunch of commands together in a script file? Cheers

get rid of fi.. thats how you end an if/elif/else conditional..

---

### Post by walkerk on 2007-09-02
script.sh
```
!/bin/sh
cd /media/cdrom0
md5sum -c md5sum.txt
```

> 
not sure why you are moving to the directory... this should work
```
#!/bin/bash
md5sum -c /media/cdrom0/md5sum.txt
```

make it executable
```
chmod +x script.sh
```

now call for it in the launcher or move to its directory and run it
```
./script.sh
```
or
```
sh script.sh
```

---

### Post by der_joachim on 2007-09-02
```

#!/bin/sh

```

Oh, and you should either either create an if-loop or remove the *fi*.

[edit]Hmm, Walkerk beat me to it.[/edit]

---

### Post by banewman on 2007-09-02
try it without the - fi - on the end. That is the opposite to if and only used when if is used.:)
The first line should be - #!/bin/sh and you have to set the permission for the file to execute - 
 sudo chmod  a+x  /path/to/file.

---

### Post by steveneddy on 2007-09-02
Here is an example of an if/and statement:

```


#!/bin/sh

# click to start, click to stop

#if pidof compiz.real | grep [0-9] > /dev/null
if pidof compiz.real
then
 exec metacity --replace
else
# exec compiz --replace -c emerald
  exec compiz --indirect-rendering --replace -c emerald
#  exec fusion-icon
fi


```


The comments are the sections or lines that start with "#" - the pound sign. The 'puter won't recognise these lines, so this is the raw file I use to experiment with different launching scripts, and all I have to do is comment out the old one and keep it there in case I need to reference the old line or the new one doesn't work correctly.

It states that the machine looks for compiz.real - to start compiz-fussion - and looks to see if metacity - the default window manager - is running. **If** it is, it starts Compiz.

Or **else** - if compiz is running, it starts metacity.

I put in a launcher the path to the file, made the file executable, and gave it an icon.

---

### Post by banewman on 2007-09-02
OzzyFrank - don't know how your post ended up being last but let us know if you had any luck. :)
Had just changed my settings for the forums....

---

### Post by OzzyFrank on 2007-09-02
OK, tried removing** fi ** & adding the** #** to **#!/bin/sh** and yes I had set permissions and made it exectable... to no avail. As for why change directory, because I already tried **md5sum -c /media/cdrom0/md5sum.txt** in the terminal and it didn't work... I think it scanned through the txt file in about a nanosecond and that was it! But in the terminal **cd /media/cdrom0 && md5sum -c md5sum.txt** worked no problems. So figured making a script based on that would be the best thing.

Right, just tried opening a terminal in my scripts folder, and followed the** ./script.sh** suggestion and that is working. Now, what would the correct syntax be for a desktop launcher to get this to happen? The file is ~/Scripts/md5-cd.sh.Thanks guys.

---

### Post by banewman on 2007-09-02
I'm fairly new to this as well but have had success making launchers for scripts where the output is not going to be in terminal - if the output is to be in terminal I can only run them from terminal. Still searching but suspect that there is an obvious reason for it.

---

### Post by OzzyFrank on 2007-09-03
OK, the launcher to the script works, so it was one of those rare moments Ubuntu could have actually done with a reboot after some updates and new apps. Seriously LOVE how 95% of new apps and updated ones work 100% without the need for a reboot... so can forgive the odd time something appears screwy for the rest of the session. Usually isn't the terminal though, hehe!

OK, but now I have the terminal hopping up and doing the scan, but then it disappears. Tried a 2nd disc and did the same, so concluded the terminal was being closed as it was "the end of the job" so to speak (I'm familiar with the occasional need to put "pause" into MS-DOS batch files for this same reason). So did the old** ./md5-cd.sh** from a terminal in that folder and sure enough all is fine, and the terminal stays, allowing me to verify all went well and then run it on more CDs. So my next question is what last line do I have to add to that script to get the terminal to hang around, so I can verify the disc scanned positive and then continue using that terminal.

**WARNING**: If you do not answer this, I will start a new thread, nyuck nyuck nyuck nyuck!! (OK, it isn't THAT bothersome, but I am SO close to having a simple desktop launcher to give me the perfect md5 checker for Ubuntu CDs). Cheers

---

### Post by mckryptyk on 2007-09-04
Here you go, 

```
#!/bin/sh
# Written by mckryptyk for ubuntuforums users
# GPL Version 2 and all that blah blah ....
# Function to check Written CD and create md5sum of it.

echo "Testing the CD integrity ... Please Wait."

sleep 5

clear

#"cd /media/cdrom0"

dd if=/dev/cdrom bs=2048 count=1 | md5sum >> /home/$USER/Desktop/md5sum.txt

echo "Testing Completed ..." 

sleep 5

clear

echo "Please Check the md5sum.txt File on your Desktop."

echo ""

cat /home/$USER/Desktop/md5sum.txt

sleep 10 

exit


```

As an exercise left to the Original Poster (OP) feel free to tack on a "compare" between the "md5sum.txt" and the "MD5SUM" found on the CD. (hint use {if / fi / elseif} and {echo} to let the user know before exiting. (file cleanup would be nice too :) )
 

>  I'm fairly new to this as well but have had success making launchers for scripts where the output is not going to be in terminal - if the output is to be in terminal I can only run them from terminal. Still searching but suspect that there is an obvious reason for it. 

You might want to try zenity for this, please see [Here.]("http://freshmeat.net/projects/zenity")

Cheers.

---

### Post by banewman on 2007-09-04
```
#!/bin/sh
echo $(home/me/myprog.sh) > /home/me/myprog.txt
$(gedit /home/me/myprog.txt)
```

This is the best I could come up with after a couple of hours research today. From a launcher it will run myprog.sh and then print the output to myprog.txt and display myprog.txt on the desktop. Leaving myprog.txt on the desktop and running the script from the launcher again brings up a panel in the text saying that the file has changed - I then click reload and the output from the second run is then displayed - the first run output having been replaced with the second. To leave all script runs in the text file add another ">" to the second line. Not exactly what you were after but involves only two clicks to run and display each job. :)

---

### Post by mckryptyk on 2007-09-04
> **banewman said:**
> ```
#!/bin/sh
echo $(home/me/myprog.sh) > /home/me/myprog.txt
$(gedit /home/me/myprog.txt)
```

This is the best I could come up with after a couple of hours research today. From a launcher it will run myprog.sh and then print the output to myprog.txt and display myprog.txt on the desktop. Leaving myprog.txt on the desktop and running the script from the launcher again brings up a panel in the text saying that the file has changed - I then click reload and the output from the second run is then displayed - the first run output having been replaced with the second. To leave all script runs in the text file add another ">" to the second line. Not exactly what you were after but involves only two clicks to run and display each job. :)

Try this instead:

1) Create a custom launcher on your top panel, where it says "application" change to "application in terminal"

2) Click browse and select your script. Click Ok.

3) "chmod +x" your script

4) Add a "sleep 100" to the end of of your script, then below it an "exit". Save.

Click and Run.

** Try to find out how to read in lines from the keyboard. Imagine typing "Q" to quit. :) ** 

Cheers.

---

### Post by banewman on 2007-09-05
All very helpful and I have learnt from your posts, mckryptyk, but they don't address the issue that OzzyFrank was trying to resolve. The terminal doesn't stay up and useable when a script is run from a launcher. I was trying to find a way around this that was simple if not elegant - my experience in programming being limited. Thanks for the effort, I tried your last suggestion but again the terminal is not usable when a script is run from a launcher. Maybe it is not designed to do this and I'm wasting time trying to force it? :)

---

### Post by mckryptyk on 2007-09-05
I thought you were trying to have a script run from launcher, display it's progress, let the user know what happened (success/failure),  then either the user closes it or it closes after a period of time (sleep, then exit).

I figured if you want a terminal to run commands on besides scripts, why not just use a terminal? 
You can have the launcher for dedicated scripts instead.(just my way of looking at it, thats all)

There really is a wealth of information available on the internet when it comes to learning how to script, but the biggest thing for most people is seeing other peoples scripts.

Download a few from the internet, and read them, it will accelerate your learning of bash. 
** Do not run them unless you have read them and understand them 100%**

Let me know if I am mistaken, about the launcher thing as I will lend a hand.

Cheers.

---

### Post by OzzyFrank on 2007-09-05
Yeah, I figured if the default was to close the terminal after the command is finished, there might be a command to leave the terminal open. That way I can hit the up arrow and run the same command again, and again. And why start if off with a launcher not a terminal? Simplicity. I made launchers to other commands and scripts, so why stop? Besides, it does run in a terminal, just saves me copying and pasting (or manually typing) the command(s).

---

### Post by mckryptyk on 2007-09-05
The answer is in the "Use "Q" to quit." You can have the terminal drop to a prompt after you push any key.

(I'll write more later, I'm time-limited right now :).)

Cheers.

---

