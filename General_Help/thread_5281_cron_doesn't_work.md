---
title: "cron doesn't work"
date: 2004-11-17
forum: General Help
---

### Post by |Syrius| on 2004-11-17
I executed "crontab -e" to add the following commands at a given time:

3 1 * * * amule

but it never runs amule by the cron.
amule runs normally by executting it in the command line but never by the cron.
I tried other commands in the crontab and none worked.
I've readed all the threads about cron and even tried to put PATH and SHELL as follows:
PATH=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games:/home/syrius
SHELL=/bin/bash
but it didn't work.
Any ideas?

---

### Post by sfw5000 on 2004-11-17
What do you get when you do ```
sudo crontab -l
```... it might be that the file your cron jobs are in is not the file being read by cron.

---

### Post by jwb on 2004-11-17
First, make sure cron is running. Do ps -A | grep cron from the command line. You should see something like "3525 ? 00:00:00 cron" if it is. If it isn't, you'll get nothing.

If it isn't running, do:

sudo /etc/init.d/cron start

This will get it running. To make sure it runs every time you start the machine, add a symlink in /etc/rc5.d and /etc/rc3.d to cron so that it will run in run level 3 and 5. If that doesn't make sense...... just post back here. Bonus points if you don't know, Google it, post back here with the answer, and we cheer your resourcefulness. :-)

OK, assuming you've got cron running-

crontab -e edits your user crontab. sudo crontab -e edits the root crontab. 

Decide which crontab you want it in, and edit it like you did before, only add the specific path to the program:

0 6 * * * /somepath/to/amule

I like to get a bit fancy and do

0 6 * * * /somepath/to/amule > /home/username/.amule_log

to see that it ran and get any output from the running..... some programs just run and there is no output (other than the task executing) so you may not see anything other than a changed time stamp.

See- I CAN post something other than smart-ass remarks.

Enough seriousness for November! Bring in the llamas!

---

### Post by |Syrius| on 2004-11-17
Well.... already have done all you have said.... but still no luck...
I tried to output to a file when run amule and he created the file but it's empty!!
i do have de cron daemon running... and here's the crontab -l output:

24 16 * * * /usr/local/bin/amule > /home/syrius/out.log

strange, isn't it?

EDIT: I run the crontab as a normal user and not as root.. but i think that doesn't matter... since amule runs as a normal user.

---

### Post by jwb on 2004-11-17
OK...... what is amule? Is it a CLI program? GUI program? When you run it from the command line, what happens?

---

### Post by |Syrius| on 2004-11-17
amule is a GUI P2P client... and that happen to all GUI apps
for instance... if i create an entry:

37 16 * * * echo "Hello World"

it does appear, but only if i do: cat /var/mail/syrius

---

### Post by Magneto on 2004-11-17
[QUOTE=|Syrius|]Well.... already have done all you have said.... but still no luck...
I tried to output to a file when run amule and he created the file but it's empty!!
i do have de cron daemon running... and here's the crontab -l output:

24 16 * * * /usr/local/bin/amule > /home/syrius/out.log

strange, isn't it?

EDIT: I run the crontab as a normal user and not as root.. but i think that doesn't matter... since amule runs as a normal user.[/QUOTE]
 run crontab as root and specify a user for amule

---

### Post by |Syrius| on 2004-11-17
i runned crontab as root like magneto said, but nothing happens.
I know that he does run the cron because i tell him to output to a file the amule's output  and he create the file but there's nothing in it

---

### Post by Magneto on 2004-11-17
[QUOTE=|Syrius|]i runned crontab as root like magneto said, but nothing happens.
I know that he does run the cron because i tell him to output to a file the amule's output  and he create the file but there's nothing in it[/QUOTE]
okay 
1.what directory is the amule executable located in? 
2.how do you normally run amule?

---

### Post by jwb on 2004-11-17
Maybe I'm being hard headed, and don't get something.

If you're running a GUI based program from the command line, all that will happen is the program launches, right? It does nothing until you interact with it from the GUI. Is that correct?

Are there parameters you pass to it when running from the command line? What is the GUI actually doing? (At the CLI level..... kinda like Gftp is really just a GUI for what happens on the CLI for ftp.)

I'm missing something here. What do you want the program to do after cron launches it?

---

### Post by |Syrius| on 2004-11-17
@magneto:
1.amule is in /usr/local/bin/
2.i run amule as a normal user and type "amule"

@jwb:

when i run amule it connects to the server automatically and starts downloading...
Think as gFTP knowing to start downloading from an ftp server as the program launches.

Thank you all for the patience!!

---

### Post by Magneto on 2004-11-17
i thought it was a daemon - i never used it i was thinking it was like giFTd

---

### Post by |Syrius| on 2004-11-17
no.. not really... what you mean is that cron cannot launch GUI apps??

EDIT: ok.. my bad... you're right.. cron doesn't run GUI apps.. it doesn't connect to the X Server... what i need is an cli app that "send" instructions to amule.
Thanks again for the patience!!!!

---

### Post by Magneto on 2004-11-17
run amuled then use the info at the bottom of this post to get it interactive - u can then do any amule stuff u want from the commandline and cron

you want to run amuled not amule


 Is there any way to start aMule with no graphical interface?

Yes. Since aMule 2.0.0-rc6, you can use aMule Deamon, which can be executed on the command line by typing amuled. To control it, use either aMuleWeb, aMuleCMD or any other such application for remotely controlling aMule.

Anyway, up to aMule 2.0.0-rc6, aMule was a monolithic application. This means that core and GUI were whole unsplittable block.

So, for those using an old aMule version or who refuse to use aMuled (aMule Daemon), there are still two walkarounds to run aMule on command line but they're not direct ways:

    * Through Xvfb
    * Through VNC 

Through Xvfb:
You should run Xvfb and then run aMule in it. Afterwards you can take control over aMule using aMuleCMD and ed2k in the same way as you would if you were accessing aMule remotely over telnet (see above).

Short example:
Run Xvfb:
Xvfb :1 -screen 0 640x480x16 &
Set display to use for amule:
export DISPLAY=:1
Then run aMule:
amule &
Note: After running export DISPLAY=:1, all graphical applications launched from that shell will be opened in Xvfb's display. To avoid this, you can run aMule with the following command, so that only aMule runs there:
DISPLAY=:1 amule &
INFO: See the Screen page to know more about the Screen command

Through VNC:
It's also possible to use vncserver instead of Xvfb to achieve something similar. Just install vncserver and execute vncserver :0 -geometry 1024x768 followed by export DISPLAY=:0. This will create a hidden X server, accessible only remotely using a VNC client. Once the X server is running, you will need a window manager to manage aMule window (well, it's not really needed, but it's useful if you want to be able to close aMule without simply killing it), I recommend FluxBox due to its low CPU and memory requirements. Just start it with fluxbox & and then run aMule with amule &. Now you can connect to the VNC server and see the aMule window.

Keep in mind that if aMule shows any dialog that requires user input (like the one showed the first time aMule is executed), it will get stuck there until someone connects to the VNC server and clicks ok in the dialog. Usually, this should only need to be done once (and this connection may be used to update the serverlist and set the preferences), from then on aMule will start without user interaction, showing only some informational messages at startup.

If you need help on this issue, search aMule's forums or join #amule IRC channel at irc.freenode.net and ask. 


[http://www.amule.org/wiki/index.php/FAQ_aMule](http://www.amule.org/wiki/index.php/FAQ_aMule)


[SIZE=5] And/Or you want this


 Can I manage aMule remotely through telnet in the same way I do with eDonkey?
Yes you can, but not exactly in the same way as you do with eDonkey. Just start a normal telnet (or ssh) session with the host computer (the one running aMule) and, once in, use amulecmd to take control over aMule. To start new downloads just use the ed2k command. Remember aMuleCMD must be configured.
Another aMule utility that might be of your interest is CAS (which's command is cas) which will show basic aMule statics.
Also, aMule WebServer might be what you are looking for if you can and don't mind using a web browser on the client computer. Have in mind that aMule WebBrowser must also be configured.[/SIZE]

---

### Post by |Syrius| on 2004-11-17
ok.. thanks... that's it.. i just thought cron would run GUI app's... but i'm just a newbie in linux matters.

---

