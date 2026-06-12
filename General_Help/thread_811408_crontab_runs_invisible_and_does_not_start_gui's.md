---
title: "crontab runs invisible and does not start gui's"
date: 2008-05-29
forum: General Help
---

### Post by EdwardTheThird on 2008-05-29
Hi,

I have made a script 'task.sh', which adds a line to a logfile each time it's executed.  In that script, i want to start firefox.  When i manually execute the script, all works fine.

When I execute it with crontab, a line is still added to the log file, however, firefox does not start anymore.  No terminal window appears either, so the script really runs 'invisible'.

How can i fix this, i've been searching internet and trying a lot...

thanks for any hints

---

### Post by bingoUV on 2008-05-29
Check what display you are running by the following command. Most probably it is :0.0.
```

echo $DISPLAY

```

Your cron does not know which display it is to open firefox in. You need to tell it that. Suppose the display you obtained above was :0.0. In your task.sh, add the following before firefox
```

export DISPLAY=:0.0

```

Replace :0.0 by display if it is not :0.0

---

### Post by kpkeerthi on 2008-05-29
[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)
[http://ubuntuforums.org/showthread.php?t=105250](http://ubuntuforums.org/showthread.php?t=105250)

---

### Post by EdwardTheThird on 2008-05-29
BingoUV,
this is what my script looks like now:


```
#!/bin/sh
export DISPLAY=:0.0
clear
echo "starting task..."
sleep 2
export DISPLAY=:0.0 
firefox
sleep 2
echo `date`
sleep 2
date >>/home/edward/scripts/tasklog.log
```

echo $DISPLAY shows indeed ":0.0"

Still script runs invisible... :(

I'm checking out the links now that kpkeerthi gave...

---

### Post by EdwardTheThird on 2008-05-29
Hi,

the links are very usefull, however still no success...

I tried 
```
echo $DISPLAY
```
-> returns :0.0

Then I run ```
crontab -e
```
and have this line:
```
#m h dom mon dow command
* * * * * export DISPLAY=:0.0 && firefox
```

But still not working...
Getting out of ideas here :confused:

---

### Post by kpkeerthi on 2008-05-29
You should specify absolution path of the program in crontab. change firefox to /usr/bin/firefox.

To get full path run
```
which <program-name>
```

Eg:
```
which firefox
```

Also, you may want to change the * * * * * cron to something meaningful instead of all stars.

---

### Post by kpkeerthi on 2008-05-29
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by EdwardTheThird on 2008-05-29
i've tried several times with both the full path (/usr/bin/firefox)  and just firefox.  It did not make any difference, it just never pops up.  Also, the 5 stars should run it every minute, but changing to 
```
03 11 * * * export DISPLAY=:0.0 && /usr/bin/firefox
```
still doesn't work

This should just work, no??

---

### Post by kpkeerthi on 2008-05-29
I didn't realize you had 5 stars. That should work. Not sure why it doen't for you. I have some GUI apps started using crons and work fine.

May be try restarting the cron daemon after changing the crontab.

```
sudo /etc/init.d/cron<press-tab-key> restart
```

---

### Post by EdwardTheThird on 2008-05-29
already restarted the deamon too...
But last week I changed something in my 'security' settings to allow to connect with vnc viewer... I'm beginning to wonder it has something to do with this...
I'm gonna check out what I changed exactly in order to get the vnc viewer to work, because i forgot by now ...

Also, if i start firefox in TTY1 I get warnings (but maybe that's normal that it does not work in tty1):
```
export DISPLAY=:0.0 && firefox
```

->output:
```
Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified

(firefox-bin: 29868): Gtk-Warning **: cannot open display:
user@mypc:~$ export DISPLAY=:0.0 && firefox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
(firefox-bin: 29868): Gtk-Warning **: cannot open display:
```

---

### Post by kpkeerthi on 2008-05-29
> **EdwardTheThird said:**
> Also, if i start firefox in TTY1 I get warnings (but maybe that's normal that it does not work in tty1):
```
export DISPLAY=:0.0 && firefox
```

->output:
```
Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified

(firefox-bin: 29868): Gtk-Warning **: cannot open display:
user@mypc:~$ export DISPLAY=:0.0 && firefox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
(firefox-bin: 29868): Gtk-Warning **: cannot open display:
```

Yes. It won't work as there is no 'X' in a TTY console.

---

### Post by kpkeerthi on 2008-05-29
And, remember to use **full path** of the program in crontab. This is important.

---

### Post by bingoUV on 2008-05-29
> **kpkeerthi said:**
> Yes. It won't work as there is no 'X' in a TTY console.

It has always worked for me from a TTY console. After setting DISPLAY variable, who cares whether there is X there or not?

Edward, try running this from within X once, and then running your command from TTY. If it works, we could work a somewhat more secure alternative
```

xhost +

```

Then we could troubleshoot your cron job further.

---

### Post by EdwardTheThird on 2008-05-29
bingoUV:
great!

I executed xhost +
Firefox starts correctly now from crontab...! (finally :) )

Don't get the reason for it yet: there is only 1 machine, so it should have access to it's own display ..?

---

### Post by bingoUV on 2008-05-29
OK. xhost + is a bit insecure as it asks the X server to allow incoming connections from anywhere. You should do a xhost - , and then try one of the following to see whether they work. Whichever solution works, put it in ~/.xsession file.
```

xhost +localhost
xhost +<username>

```

Reason : There could be other users logged on a different DISPLAY on the same machine. It is probably to protect you against them that they are not allowed access to your X server. But I am not sure.

---

### Post by EdwardTheThird on 2008-06-10
Hi BingoUV,

when the PC restarts, and I am not logged in yet, the job does not start.  Do you (or someone else) know how I can avoid this?

regards

---

### Post by EdwardTheThird on 2008-06-11
> **EdwardTheThird said:**
> Hi BingoUV,

when the PC restarts, and I am not logged in yet, the job does not start.  Do you (or someone else) know how I can avoid this?

regards

correction:
the job starts (i added some logging), but firefox does not want to start, probably because no valid display is available because no-one is logged in...
How can i start a GUI application (firefox) when noone is logged in yet, for instance after the pc has restarted.  This should be possible no?

greets

---

### Post by bingoUV on 2008-06-11
Firefox is an X application. It needs an X display to connect to. So, it is not possible.

Even if it were possible, what can you do with it? You will never see the window. You will never be able to type into it or click on it. It might as well be not running. Except that now this Firefox will eat memory and CPU cycles for effectively not running.

You can automatically create another X display which automatically starts Firefox. But then you cannot say no one is logged in.

---

### Post by EdwardTheThird on 2008-06-11
> **bingoUV said:**
> Firefox is an X application. It needs an X display to connect to. So, it is not possible.

Even if it were possible, what can you do with it? You will never see the window. You will never be able to type into it or click on it. It might as well be not running. Except that now this Firefox will eat memory and CPU cycles for effectively not running.

You can automatically create another X display which automatically starts Firefox. But then you cannot say no one is logged in.


I don't actually need to see anything.  I have setup a certain page into my 'home' page, so when firefox is started, it visits a certain page on the internet.
Is it possible to automatically start a session with an X display active whenever the PC starts?  If this were possible, it would work anyway.

---

### Post by bingoUV on 2008-06-11
Now we are talking. I don't understand what you gain by firefox visiting some page on the internet when you cannot even see it, but it does not matter : 
1. Configure vnc server : 
```

mkdir ~/.vnc
gedit ~/.vnc/xstartup

```

Fill the following into the file ~/.vnc/xstartup
```

#could run a window manager or desktop environment here, but since you are not 
#going to see this ever, why waste even more memory and CPU cycles by starting 
#window manager. By uncommenting the next line, it will run gnome desktop
#gnome-session &
firefox &

```

Give execute permissions to ~/.vnc/xstartup.

2. Run it manually for the first time. It will ask password to authenticate the client. Give any password.
```

vncserver :99

```

3. Add it to /etc/rc.local so that it always runs on bootup. Add the following line to /etc/rc.local
```

sudo -u <your username> vncserver :99

```

The good thing about all these steps is, you would not even know/care if it does not work. Enjoy.


PS: Sorry, if you want to test it,
```

vncviewer :99

```
Give the password that you set in step 2 above.

---

