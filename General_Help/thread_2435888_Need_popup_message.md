---
title: "Need popup message"
date: 2020-01-28
forum: General Help
---

### Post by John Jason Jordan on 2020-01-28
I have Xubuntu 18.04, up to date. I have created an rsync script that runs in a cron job at 3am. When it finishes I want it to pop up a message with the rsync exit code that I will see when I sit down at the computer in the morning. I tried gxmessage and xmessage, and notify-send, and they work OK when I send them as me, but the script has to be run by root, and I can't figure out how to make root create a popup on my user desktop. The script runs, but the popup does not appear for me. 

There has to be a way to do this. Any suggestions welcome!

---

### Post by dragonfly41 on 2020-01-28
I'm sure that there must be several ways of firing up a popup message.
One automation tool I use to integrate with desktop is Actiona (found in software repo).
Create a script containing a MessageBox action and save as **popup.ascr**.
Then fire it from Grsync by the command **actexec popup.ascr**.
Sudo should not be necessary (although you can simulate typing a password from a variable, but not recommended)..

---

### Post by HermanAB on 2020-01-28
Zenity is what you are looking for - a GUI for scripts:
[https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html](https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html)

I would make the root script write the status to a file, then when you log in, have a script run to check that log and pop-up a notice.

---

### Post by John Jason Jordan on 2020-01-28
> **dragonfly41 said:**
> I'm sure that there must be several ways of firing up a popup message.
One automation tool I use to integrate with desktop is Actiona (found in software repo).
Create a script containing a MessageBox action and save as **popup.ascr**.
Then fire it from Grsync by the command **actexec popup.ascr**.
Sudo should not be necessary (although you can simulate typing a password from a variable, but not recommended)..

Good idea, but you can't insert the rsync exit code into the message.

---

### Post by John Jason Jordan on 2020-01-28
> **HermanAB said:**
> Zenity is what you are looking for - a GUI for scripts:
[https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html](https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html)
I would make the root script write the status to a file, then when you log in, have a script run to check that log and pop-up a notice.

Zenity won't work either; already tried it, along with all the other popup message tools I could find.

The problem is that the rsync script is run as root, that is, the cron job is in root's crontab, not mine. And as far as I can tell from my research so far, cron jobs are not run in X, mine or root's. So the trick is to get root to popup a display on *my* desktop. In other words, the popup tool is irrelevant to the problem; none of them are going to work on my desktop if the action is called from a root cron job.

I tried adding this to the beginning of the popup command in the rsync script: $XAUTHORITY=/home/jjj/.Xauthority gxmessage ... etc. It almost works, but I get the error message:

/home/jjj/Software/./Backup_script_for_Home.sh: line 9: /home/jjj/.Xauthority=/home/jjj/.Xauthority: No such file or directory

I checked and the .Xauthority file is really there, and a search revealed that there are no other .Xauthority files or folders anywhere on ~/. I can only think that root is unable to look in ~/. That doesn't make much sense, but it's all I can think of.

---

### Post by sudodus on 2020-01-28
> **HermanAB said:**
> Zenity is what you are looking for - a GUI for scripts:
[https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html](https://www.aeronetworks.ca/2015/09/zenity-progress-dialogue.html)

I would make the root script write the status to a file, then when you log in, have a script run to check that log and pop-up a notice.

> **John Jason Jordan said:**
> Zenity won't work either; already tried it, along with all the other popup message tools I could find.


I think HermanAB's method is good. Please look at it again! The cron script (by root) is to write to a file, and zenity is to read that file, when you log in. And that zenity process will be yours (not run by root).

---

### Post by ajgreeny on 2020-01-28
Unless things have changed when using cron which I'm not aware is the case, you must first export to your display the GUI application you want to use by adding the prefix of ***export DISPLAY=:0 &&*** prior to your cron command for the GUI part.  Without this no GUI application will start as far as I'm aware.

No poster, nor you, has mentioned this requirement so far so I wonder if this is the cause of your failure.

---

### Post by dragonfly41 on 2020-01-28
> [COLOR=#000000]Good idea, but you can't insert the rsync exit code into the message.[/COLOR]

I'm not sure if you experimented with Actiona.
Without actually writing the script I would use these steps.

Save the output of the cron job to a file.
Optionally, If you prefer pretty output, install **aha** this can be in html, or leave it as txt.
Just use a pipe operator.    command | aha myoutput.html

In actiona GUI write these actions (Qt objects).

Line: 001 Read text file (Output parameter: variable $mycronjob)
Line: 002 MessageBox (Message: variable $mycronjob, Advanced: Mode Auto/HTML/Text)
Line: 003 Exit Actiona

Simples.

Note that you can inject javascript ([COLOR=#ff0000]red arrow[/COLOR]; click here to inject text/code)

Really, you can run any workflow. Usually actiona drives the workflow but in your case you launch the popup
by the command **actexec popup.ascr** which runs at end of cron job..

---

### Post by John Jason Jordan on 2020-01-28
> **ajgreeny said:**
> Unless things have changed when using cron which I'm not aware is the case, you must first export to your display the GUI application you want to use by adding the prefix of ***export DISPLAY=:0 &&*** prior to your cron command for the GUI part.  Without this no GUI application will start as far as I'm aware.
No poster, nor you, has mentioned this requirement so far so I wonder if this is the cause of your failure.

I just tried that. Now I get:

No protocol specified
Unable to init server: Could not connect: Connection refused
gxmessage: unable to initialize GTK

And I tried adding export XAUTHORITY=/home/jjj/.Xauthority as well, but same error message.

Here is the current incarnation of my script:

#!/bin/bash
export DISPLAY=:0
export XAUTHORITY=/home/jjj/.Xauthority
TS=`date`
rsync -avx --delete /home/jjj/ /media/jjj/Data/JJJ
#XAUTHORITY=/home/jjj/.Xauthority gxmessage -display :0 -name Home/jjj_backup -geometry 1300x200 -center -fg black -font "Junicode 22" $TS Home Backup Exit Status $?, Zero=Success #commented out since it didn't work
gxmessage -name Home/jjj_backup -geometry 1300x200 -center -fg black -font "Junicode 22" $TS Home Backup Exit Status $?, Zero=Success

Maybe someone can see something else in there that is causing the problem. 

I should add that to test with each new change I've been running the script from the command line with sudo, else I'd have to wait for 3am to see if a change made a difference. But if I run the script without sudo the message pops up as expected.

---

### Post by dragonfly41 on 2020-01-28
Here is a quickly cobbled together untested Actiona script (requires sudo apt install actiona).

Note that you need to change extension to ascr instead of txt.

---

### Post by John Jason Jordan on 2020-01-28
> **dragonfly41 said:**
> Here is a quickly cobbled together untested Actiona script (requires sudo apt install actiona).
Note that you need to change extension to ascr instead of txt.

OK, I installed actiona, changed the extension to .ascr, then tried to run it, but I got:
```
./popup.ascr: 2: ./popup.ascr: Syntax error: newline unexpected
```
I scanned through it, but I didn't see any newlines that didn't look like they belonged there.

Never mind, I figured it out, sort of. I had to run it as 'actiona -e popup.ascr,' not as ./popup.ascr. Unfortunately, after it popped up its window I was unable to read any of the text without a magnifying glass because my display is UHD, and apparently it is hard coded to expect FHD or something else. And after getting out my magnifying glass I couldn't figure out what to do with it. Eventually I found the forums, and read through all the questions that had been asked. Although I have to call my perusal of actiona scanty at best, it appears to me that it will suffer the same fate as the other tools that I have tried, that is, calling it from a root cron job will fail because root can't access my desktop to give me a popup or launch anything.

If I'm wrong about that, please clue me in!

---

### Post by dragonfly41 on 2020-01-28
There might be some loss due to me having to upload txt file (ascr extension was blocked). Possibly I'm using a different version of Actiona (3.9.2). I would just try the GUI. But actually I see that you have not used the command **actexec ./popup.ascr**

---

### Post by John Jason Jordan on 2020-01-28
@dragonfly,
We are cross-posting to each other. I just edited my original post.

---

### Post by dragonfly41 on 2020-01-28
I just don't understand why you need a magnifying glass!

In extremis your messagebox can be HTML code and make it as large as you need using <h tags.

But why not get rysync (or Grsync) call an Actiona script directly rather than going through cron?
Or even run rsync command inside Actiona?

[P.S.} Look at the Time Condition action in the GUI. This is equivalent to cron.

---

### Post by John Jason Jordan on 2020-01-28
> **dragonfly41 said:**
> I just don't understand why you need a magnifying glass!
In extremis your messagebox can be HTML code and make it as large as you need using <h tags.
But why not get rysync (or Grsync) call an Actiona script directly rather than going through cron?
Or even run rsync command inside Actiona?
[P.S.} Look at the Time Condition action in the GUI. This is equivalent to cron.

First, I discovered that installing actiona added a menu item under Accessories, so I used that to launch it instead of the popup.ascr script, et voilà! The window came up with readable text like all other programs. So now I have a fighting chance to figure it out. Except all the icons are 1mm, and lists of text items are scrunched together because the line spacing is set for a font half as big. But at least I can read most of the text now.

Unfortunately, it's hard to learn what the items do because I can't find a user manual. (Is there one somewhere?) I finally found the Time Condition action, and created one. It's sitting in the center window, but I don't know what to do with it. It may take me a week of trial and error to learn this program. It may be worth doing that, but let me ask one crucial question first: Can I make it run my rsync command *as root* at 3am every day, and at the end make a popup message on *my* desktop containing the rsync exit code, a popup that I will see when I sit down at the computer several hours later? (I leave my computer running 24/7 and never log out.)

If the answer is yes, I'll spend more effort on figuring it out. And in any event, thanks for bringing it to my attention.

---

### Post by HermanAB on 2020-01-29
Note that if your cron script runs before the GUI is up, then things won't work right - you cannot pop a message up on X if X isn't running yet.  That is why I suggested writing the output to a file and reading the file later when your GUI comes up.

---

### Post by dragonfly41 on 2020-01-29
> Unfortunately, it's hard to learn what the items do because I can't find a user manual.

I am hoist by my own petard. Having suggested using this automation tool I guess that I now have to show the roadmap.

The documents are a bit elusive and most of the community activity is in the French forum (the author is in France). I use google translate when I dive into French forum for tips. Do not overlook the flexibility of using Javascript in a Code objects. Or the use of Console logging.

[https://wiki.actiona.tools/doku.php?id=:en:start](https://wiki.actiona.tools/doku.php?id=:en:start)

[https://wiki.actiona.tools/doku.php?id=en:actions](https://wiki.actiona.tools/doku.php?id=en:actions)

[https://wiki.actiona.tools/doku.php?id=en:code](https://wiki.actiona.tools/doku.php?id=en:code)

[https://wiki.actiona.tools/doku.php?id=en:code:introduction](https://wiki.actiona.tools/doku.php?id=en:code:introduction)

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)


The Actiona GUI is only needed to develop and test each script. Thereafter the developed script can be run from command line

Let us stick with using cron.  

And instead of creating a popup message box let us use the Grsync GUI output.

Thus the cron command is **actexec -e myGrsyncJob.ascr**. This will run the Actiona script at the appropriate hour.

But how do we run Gsync in hands off mode?

Within Actiona we can run a Detached Command to launch Grsync (even though the user will not be present we can emulate "driving" the Grsync GUI).

[https://www.techrepublic.com/blog/linux-and-open-source/how-to-become-an-rsync-power-user-with-grsync/](https://www.techrepublic.com/blog/linux-and-open-source/how-to-become-an-rsync-power-user-with-grsync/)


With Grsync launched, go to Grsync preferences and tick on &#8220;Enable logging&#8221;. Hover over the preferences buttons to read the tooltips.

For example hovering over &#8220;Enable logging&#8221; we see that log file is saved in $HOME/.grsync folder.

You might choose the option &#8220;Overwrite logs&#8221; if you want a single log. Otherwise your logs might grow in size. Or the daily logs can be rotated.

Instead of having a popup message box when you arrive at your desktop it might be sufficient to leave Grsync open.  In which case tick the options:

Show sync output by default
Show error list  when finished

Command to launch Grsync is simply grsync

In Grsync session, extra options there is &#8220;Run as superuser&#8221;.

Now the actiona script must check that Grsync is in focus then select the session and hit 
the top key &#8220;Make a full run (go!)&#8221;.

For this we use the action .. Window > Window Condition to look for the grsync window title. 

If it is not present you have various options; terminate or wait for another go.

If it is present you might then call a procedure.

The procedure will

look for top button &#8220;Make a full run (go!)&#8221;

This is perhaps the trickiest action since the go button must be targetted. There are several options for targetting an object:

by image searching
by cursor coordinates

My approach would be to maximise Grsync window so that the position of the go button is fixed.

Find the exact position of the Grsync go button.
For this we need to have xdotool installed.

[https://askubuntu.com/questions/346913/show-realtime-mouse-cursor-coordinates-cursor-mod-overlay-also-copy-to-c/355443#355443](https://askubuntu.com/questions/346913/show-realtime-mouse-cursor-coordinates-cursor-mod-overlay-also-copy-to-c/355443#355443)

Then run ...

watch -ptn 0 "xdotool getmouselocation"

From this we see that the centre of the Go button is at position x:980 y:105 (on my small monitor). It will be different on your screen.

Copy this x:y position into a Click action.

Summary:
In the same way that Grsync GUI is a driver of rsync
Actiona can be the "hands off" driver of Grsync GUI.

Actiona script (not the GUI but myGrsyncJob.ascr) is run from cron at 3.00 am.
Actiona script runs Grsync session and auto clicks on go!.
Various exceptions can be accommodated such as opening log file. I would install glogg for that.

---

### Post by John Jason Jordan on 2020-01-29
> **HermanAB said:**
> Note that if your cron script runs before the GUI is up, then things won't work right - you cannot pop a message up on X if X isn't running yet.  That is why I suggested writing the output to a file and reading the file later when your GUI comes up.

You win.

 have given up on mail and .Xauthority and DISPLAY, as well as actiona. Mail is too much trouble, and getting a root cron job to pop up a message on my desktop may never work because of settings in my Xfce desktop environment. And I'm probably not smart enough to figure out actiona. At some point you have to pull the plug, and I have now officially given up on those approaches.

Instead I have just added the following line to the script:

echo "$TS Home Backup Done Exit Status $?" > /home/jjj/Software/Rsync_daily_log.txt #'date' is defined as TS earlier in the script, and $? is the rsync exit status..

This works, and I have created another cron job in my own user crontab to use gxmessage to pop up the results of that file on my desktop at 4am. I am the only user of this computer and I never log out or shut down, so it will be there when I sit down at the computer in the morning.

I probably should have done this from the beginning, but the efforts have been educational, so the experience has been useful, even if unsuccessful. Thanks to all who offered help. :)

---

### Post by sudodus on 2020-01-30
Congratulations and thanks for sharing your solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by John Jason Jordan on 2020-01-30
> **sudodus said:**
> Congratulations and thanks for sharing your solution :-)
Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

Not quite solved. 

The cron job in my crontab failed to pop up the message. The rsync scripts worked perfectly, and the Rsync_daily_log.txt file contains two lines with the successful results. But when I run the gxmessage command in the terminal it displays the popup, but with the following error message:

	dbind-WARNING **: 08:54:42.335: Couldn't register with
	accessibility bus: Did not receive a reply. Possible causes
	include: the remote application did not send a reply, the
	message bus security policy blocked the reply, the reply
	timeout expired, or the network connection was broken.

I am happy to ignore that warning, but apparently cron is not as forgiving.

I tried zenity and yad, which displayed the same error message, so they would probably fail the same as gxmesssage. Notify-send can't read the message from a file, so that won't work. The only message tool that works without the error message is xmessage, but that displays the message in a font that is about 1mm high - unreadable without a magnifying glass. That is because my display is UHD. If I can figure out how to change the default font size for X I might be able to fix this, but so far I haven't found out how to do that.

---

### Post by sudodus on 2020-01-30
I think that it is enough for** root's cron job** to write the message to a file.

Then another process should check for the message in that file, and I suggest that it is a process owned by you.

- It could be a program put in the 'autostart' directory of your desktop system.

- It could also be a line in your own user ID's crontab. I tested this method in Lubuntu 18.04.x LTS.

```

crontab -e

```

I added the following line (which writes a message every minute, you will modify this)
```

* * * * * asdf=$(/bin/cat /etc/lsb-release);DISPLAY=:0 /usr/bin/zenity --info  --text="$asdf"

```

- cat reads text from a file
- the text is put into the shell variable asdf
- the environment variable DISPLAY is set (to point to the desktop environment)
- zenity is displaying the text in an 'info' window

---

### Post by John Jason Jordan on 2020-01-30
@sudodus

I found a site that helped me get a decent font in xmessage: [https://tronche.com/wiki/Howto_specify_X_scalable_fonts_from_the_command_line]("https://tronche.com/wiki/Howto_specify_X_scalable_fonts_from_the_command_line")

So now my xmessage command is: xmessage -fn '-urw-*-*-r-*--50-0-0-0-p-*-*-*' -file /home/jjj/Software/Rsync_daily_log.txt . It works beautifully from the command line with no error messages. I put that into my own crontab like this: * * * * * xmessage ... etc. But cron is not executing the command every minute, there are no messages popping up. I also refreshed cron, even though the cron man page says that saving the crontab is all that is necessary.

My only problem now is cron. I'm ***that*** close!

---

### Post by Holger_Gehrke on 2020-01-30
cron gets started before the GUI so DISPLAY isn't set in its environment. Put DISPLAY=:0.0 before the command like so```

* * * * * DISPLAY=:0.0 xmessage -fn '-urw-*-*-r-*--50-0-0-0-p-*-*-*' -file /home/jjj/Software/Rsync_daily_log.txt
```
and it should work. BTW, cron sends any errors as mail. A simple 'mail' in the shell will allow you to read this (and it will tell you "Error: can't open display").

Holger

---

### Post by John Jason Jordan on 2020-01-30
> **Holger_Gehrke said:**
> cron gets started before the GUI so DISPLAY isn't set in its environment. Put DISPLAY=:0.0 before the command like so```

* * * * * DISPLAY=:0.0 xmessage -fn '-urw-*-*-r-*--50-0-0-0-p-*-*-*' -file /home/jjj/Software/Rsync_daily_log.txt
```
and it should work. BTW, cron sends any errors as mail. A simple 'mail' in the shell will allow you to read this (and it will tell you "Error: can't open display

OMG, it's working! That was the secret that I needed! A thousand thanks to all here!

---

### Post by TheFu on 2020-01-30
Doing GUI stuff from cron is a mistake, I wouldn't expect it to work forever.  But being lucky is better than being smart, so they say.
The *autostart* method at login would be my suggestion too.  Or just have the results show up as the message of the day whenever you open any terminal.

And be certain to clear the emails out or it is possible to fill a partition and crash the system.

---

### Post by John Jason Jordan on 2020-01-31
> **TheFu said:**
> Doing GUI stuff from cron is a mistake, I wouldn't expect it to work forever.  But being lucky is better than being smart, so they say.
The *autostart* method at login would be my suggestion too.  Or just have the results show up as the message of the day whenever you open any terminal.
And be certain to clear the emails out or it is possible to fill a partition and crash the system.

But I never log out or shut down, except when I have to install a new kernel and Update Manager requires a reboot. As for e-mails, I have no MTA installed, and I don't intend to do so. I see in /var/log/syslog muchos messages from cron bitching that it can't send mail. I wish I could stop it from trying, but if I do MAILTO="" in my backup scripts cron still tries to send mail, and still logs the error messages when it can't. But hey, /var/log/syslog is not exactly gripping, action packed literature, so I don't spend a lot of time reading it. :)

---

### Post by TheFu on 2020-02-01
Use **logwatch** to scan syslog and get notified of issues. 
If you use cron and don't want emails, don't allow any stdout or stderr messages.

---

