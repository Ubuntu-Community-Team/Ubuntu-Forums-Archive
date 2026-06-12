---
title: "Lock computer every night at 10 to force me to go to bed?"
date: 2008-04-04
forum: General Help
---

### Post by Sonja on 2008-04-04
Is there a way to tell Ubuntu to automatically lock me out at a certain time every night, e.g. 10 p.m., to force me to go to bed and stop being on the computer?

I have ADHD and have extreme difficulty switching gears. I need help to transition form activity time to bedtime, otherwise I will never stop!!

Is is possible to program an Ubuntu app to play a certain song just once 5 minutes before it locks down or blocks me out like this? A sort of way to condition myself... time to go to bed, though association and repeated conditioning with that song?

Thanks everyone!

---

### Post by jakupl on 2008-04-04
I usually use this :)

You can open the terminal and write

```
sudo shutdown -P hh:mm
```

fx. if you want it to shutdown at 10 pm write:
```
sudo shutdown -P 22:00
```

I will see if i can make it play a song at a specific time.

---

### Post by patrickfromspain on 2008-04-04
search how anacron or cron work. There you will able to set the command aplay /path/to/song at a specific time

---

### Post by jakupl on 2008-04-04
Heh :) I was just checking cron out... cant make it work though... well I'll look at it tomorrow.

---

### Post by jakupl on 2008-04-04
```
jakup@bobby:~$ 42 0 * * * root (aplay /home/jakup/Desktop/Tónleikur/Jack\ Johnson/On\ and\ On/*.ogg)
bash: syntax error near unexpected token `('
```

I can't find the fault

---

### Post by Lord Illidan on 2008-04-04
Spaces can throw some command line apps off balance. Enclose the path in double quotes.

EDIT : Oh, and what's up with the brackets?

Also, if you're playing songs, I wouldn't suggest aplay. Try ogg123 or mplayer.
[Here's a link]("http://www.linux.com/feature/124907") you might find useful! Good Luck!

---

### Post by ed-koala on 2008-04-04
I'm wondering if some programmer can write a program that runs on boot, checks the time of day, and if it is between 10pm and 6am it shuts the PC back down.  That'd do it. lol

---

### Post by sswittch on 2008-04-04
that would royally #$@% you off if the use for the computer was urgent or if you were working on something and the computer turned off on you though.

---

### Post by gsmanners on 2008-04-04
I'd probably put a password on grub if I wanted to have that much control.

---

### Post by jakupl on 2008-04-05
[QUOTE="Lord Illidan "]EDIT : Oh, and what's up with the brackets?[/QUOTE]

That is how it is described [here]("http://wiki.linuxquestions.org/wiki/Scheduling_Tasks").

---

### Post by jakupl on 2008-04-07
okay Sonja. this gets a bit complicated, but stay with me. I will try to explain is as simply as possible

I don't know what your user is called, so I will simply call it "sonja". change it if that is not your username.

lets say you have a song that you want to play at 21:55 every day. We will call it::
```
/home/sonja/Music/song.ogg
```

###################################

CREATE A SCRIPT TO TURN THE SONG ON

###################################
This is how:

1. Go to your home folder, make an empty file (press File ---> Create Document ---> Empty File)

2. Open the empty file and write the following in it:

```
#!/bin/bash
/usr/bin/totem /home/sonja/Music/song.ogg
```

(*you need to customize the path above, to the song you want to hear.*)

save and exit.

3.  Rename the file to ```
.songtoplay
```

(*this will make the file hidden, so it wont bother you later. If you suddently cant see it, press View --> Show hidden files)

4. Rightclick on the file, Press Properties ---> Permissions, and mark "Allow executing file as program"

5. Just to make sure, Now press the file, then press "Run it terminal". If you can hear the song, all is good and you can proceed. if not, than tell me.

###########################################
MAKE CRON RUN THE SCRIPT AUTOMATICALLY
###########################################

1. go to the terminal (Application ---> Accessories ---> Terminal)

2. write in terminal:
```
crontab -e
```

you will see a place where you can write whatever you want.

3. Write the following:

```
55 21 * * * export DISPLAY=:0 && /home/sonja/.songtoplay
```

press "Control + X" to exit, press "Y" to save, press "ENTER" to confirm.

this should get you back to the normal terminal and it should read:

```
crontab: installing new crontab
```
if so, then all is well.

Now you will hear the specified song at 21:55 every day.

----------------------------------------------------------------------------

To make the computer turn off at 22:00, the easyest way would simply be to write in terminal

```
sudo shutdown -P 22:00
```

every day... or to install GShutdown - A very easy program to turn the computer off whenever you want it to. though you have to activate it everytime you turn the computer on.

you CAN use the cron program... to make it automatic. just tell me if that's what you want. Cus then you will have to do it all over again.
enjoy :)

---

### Post by mbeierl on 2008-04-07
You could also put the shutdown into root's crontab to avoid having to do the sudo shutdown every time you start the pc.  Just do a
```
sudo crontab -e
```
and follow the above instructions to add the following entry:
```
0 22 *   *   *    /sbin/shutdown -P +5 "Time for bed"
```
That will initiate a 5 minute shutdown (+5) with the message "Time for bed"

---

### Post by kostkon on 2008-04-08
For a GUI option, you could check [*GShutdown*]("http://gshutdown.tuxfamily.org/en/index.php"). It's available in the repos (version 0.1) or you can download a newer version of it (0.2) [from its site]("http://gshutdown.tuxfamily.org/en/download.php").

---

