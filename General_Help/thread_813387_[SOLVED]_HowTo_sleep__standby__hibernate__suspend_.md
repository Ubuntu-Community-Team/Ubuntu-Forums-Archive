---
title: "[SOLVED] HowTo sleep / standby / hibernate / suspend from command line"
date: 2008-05-30
forum: General Help
---

### Post by aoakley on 2008-05-30
There are several threads which unsuccessfully seek a command line method to hibernate or suspend in Ubuntu, WITHOUT requiring root or sudo access. After a bit of digging, I've come up with the answer.

This is tested on Ubuntu 8.04 (Hardy) with a Dell Inspiron 1520 laptop. I would appreciate feedback from users of other systems.

To suspend-to-RAM (aka sleep):

```
pmi action suspend
```

To suspend-to-disk (aka hibernate):

```
pmi action hibernate
```

If you want to lock the Gnome session first (ie. require a password on resumption), then issue the following command before pmi:

```
gnome-screensaver-command --lock
```

For example, you can use these commands to create a button (launcher) on a Gnome panel (taskbar) that instantly locks the screen and goes into sleep mode:

Right-click panel, Add to panel, Custom application launcher, Add, Name: Sleep , Command: gnome-screensaver-command --lock ; pmi action suspend

---

### Post by fraia on 2008-06-01
Thanks-
This suspend/resume seems [-o< to work better than
 ```
sudo /etc/acpi/sleep.sh
```
on my Sony Vaio TZ170 (Hardy) - i got around the password by editing the sudoers file

A few things I noticed however: I honestly don't know how this 'pmi action' is implemented, but could it be skipping the resume sequence in /etc/acpi/resume.d/? 

My wireless won't auto-connect on resume (no big deal really) But it's also ignoring my hdd parameters script and so is spinning the drive up/down excessively again. I may poke around /etc/hdparam.conf later

you may want to keep an ear out for that one

---

### Post by motin on 2008-08-31
Thanks man! Now I can easily put my laptop to sleep after a certain amount of time:
```
echo 'pmi action suspend' | at now + 40 minutes
```

This way I can watch some Scrubs and go to bed without risking to fully drain the battery every night...

PS I tried to officially thank you for your post but can't find that medal Thank you-button?

---

### Post by cake_or_death on 2008-10-12
I tried this command on my Vaio, and it worked great... about three times.  Since then I get a black screen with flashing cursor.

---

### Post by Sam on 2008-10-12
> **motin said:**
> I tried to officially thank you for your post but can't find that medal Thank you-button?

The thank feature of each post is removed after 60 days ([source](http://ubuntuforums.org/showthread.php?t=702596)).

---

### Post by diegorodriguezv on 2008-11-05
I found out that
/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux 
works on my 8.04 Ubuntu.

---

### Post by Jesus-Ninja on 2009-05-12
Outstanding, it's taken me days to stumble across this having made other dismal attempts to do this from the command line or via scripts - brilliant! :)

---

### Post by _moo on 2009-05-17
I believe the proper solution is (assuming you are using gnome):

```
gnome-power-cmd suspend
```

or

```
gnome-power-cmd hibernate
```

This is equivalent to using the GUI.

---

### Post by hpeat on 2009-08-18
> **aoakley said:**
> There are several threads which unsuccessfully seek a command line method to hibernate or suspend in Ubuntu, WITHOUT requiring root or sudo access. After a bit of digging, I've come up with the answer.

This is tested on Ubuntu 8.04 (Hardy) with a Dell Inspiron 1520 laptop. I would appreciate feedback from users of other systems.

To suspend-to-RAM (aka sleep):

```
pmi action suspend
```

To suspend-to-disk (aka hibernate):

```
pmi action hibernate
```

If you want to lock the Gnome session first (ie. require a password on resumption), then issue the following command before pmi:

```
gnome-screensaver-command --lock
```

For example, you can use these commands to create a button (launcher) on a Gnome panel (taskbar) that instantly locks the screen and goes into sleep mode:

Right-click panel, Add to panel, Custom application launcher, Add, Name: Sleep , Command: gnome-screensaver-command --lock ; pmi action suspend

thx it works gr8 4 me.

---

### Post by akin1231 on 2009-08-27
That's a negative.  None of these actions work for me.  The button on the GUI for supend works really well but I need to run a script before any suspend action is invoked.  

I just need to figure out what that Suspend button does.  How would I figure this out?  Many thanks! 
Also if it's different, I need to run the same script if suspend is due to idle time

---

### Post by fermulator on 2009-08-28
> **akin1231 said:**
> That's a negative.  None of these actions work for me.  The button on the GUI for supend works really well but I need to run a script before any suspend action is invoked.  

I just need to figure out what that Suspend button does.  How would I figure this out?  Many thanks! 
Also if it's different, I need to run the same script if suspend is due to idle time

How do they behave? -- Could you please provide some command & response "quotes"?

---

### Post by Rebelli0us on 2009-11-07
I'm trying to create a keyboard shortcut but it doesn't work.

/usr/sbin/pm-suspend
returns "This utility may only be run by the root user." !!!

The built-in Suspend in Keyboard Shortcuts doesn't work either.


pmi action suspend
returns"The program 'pmi' is currently not installed.  You can install it by typing:
sudo apt-get install powermanagement-interface"



Pressing Ctrl+Alt+Delete brings up the Shutdown Dialog but it doesn't have focus or is behind the current window


Some fixing is needed here....

---

### Post by fermulator on 2009-11-07
Well, do
```
sudo apt-get install pmi
```

Then you can use
```
sudo pmi action suspend
```

As far as being able to bind that to a keyboard shortcut ... I believe it's expected that your keyboard shortcut couldn't auto suspend because it requires root access.  The workaround would be to bind it to "gksu pmi action suspend" possibly, but you'll still have to type your root password.

I'm not sure how, but I'm guessing the right course of action would be to figure out how the "suspend" button works in gnome-gui ... maybe tie into that somehow and invoke the command that it invokes...?

---

### Post by motin on 2009-11-09
In Karmic:

```
sudo apt-get install powermanagement-interface

```

Then run:

```
sudo visudo
```

And add this line, using your own username:

```
yourusername ALL=NOPASSWD: /usr/sbin/pmi
```

Save (Ctrl + X).

Now you should not have to enter a password for this command.

---

### Post by Rebelli0us on 2009-11-13
The "Suspend" command in Keyboard Shortcuts doesn't work. Why?

Also, why should a user have to type a password to suspend computer? That's bizarre.. machine is set to auto-suspend anyway..

---

### Post by AgenT on 2009-11-13
[B]
** SOLUTION NOT REQUIRING ROOT/SUDO **[/B]

Introducing... [SIZE=4][COLOR=DarkRed]**gnome-power-control**[/COLOR][/SIZE]
No sudo, no root, no fuss!

I found the solutions in this thread and elsewhere inadequate, because they just bypassed the problem by using sudo. I have solved this problem by writing a simple script.

**THE SCRIPT**
```

#!/bin/bash
#
# gnome-power-control
# Author: AgenT

case $1 in
suspend)
echo Suspending
    dbus-send --print-reply \
        --system \
        --dest=org.freedesktop.DeviceKit.Power \
        /org/freedesktop/DeviceKit/Power \
        org.freedesktop.DeviceKit.Power.Suspend
;;
hibernate)
echo Hibernating
    dbus-send --print-reply \
        --system \
        --dest=org.freedesktop.DeviceKit.Power \
        /org/freedesktop/DeviceKit/Power \
        org.freedesktop.DeviceKit.Power.Hibernate
;;
*)
echo Not supported command: '"'$1'"'
echo Usage: $0 '<suspend|hibernate>'
exit 1
;;
esac
```**SETUP**
1) Save the above as: gnome-power-control

2) Change file permissions to execute (right click on file -> properties -> permissions) 

3) optional: move this script into your ~/bin/ folder for easy access!

**USAGE**
To suspend: gnome-power-control suspend
To hibernate: gnome-power-control suspend

**BINDINGS**
Once in your ~/bin/ folder, you can bind other programs to use this! For example, create a Compiz shortcut to execute gnome-power-control suspend, or create a launcher on your toolbar to do the same thing!

**DOES NOT WORK?**
If this does not work for you, you either don't have DeviceKit (in Ubuntu 9.10) or if you do, then your suspend/hibernate is not working correctly.

---

### Post by Rebelli0us on 2009-11-14
> **AgenT said:**
> [B]
** SOLUTION NOT REQUIRING ROOT/SUDO **[/B]

Introducing... [SIZE=4][COLOR=DarkRed]**gnome-power-control**[/COLOR][/SIZE]
No sudo, no root, no fuss!

I found the solutions in this thread and elsewhere inadequate, because they just bypassed the problem by using sudo. I have solved this problem by writing a simple script.

**THE SCRIPT**
```

#!/bin/bash
#
# gnome-power-control
# Author: AgenT

case $1 in
suspend)
echo Suspending
    dbus-send --print-reply \
        --system \
        --dest=org.freedesktop.DeviceKit.Power \
        /org/freedesktop/DeviceKit/Power \
        org.freedesktop.DeviceKit.Power.Suspend
;;
hibernate)
echo Hibernating
    dbus-send --print-reply \
        --system \
        --dest=org.freedesktop.DeviceKit.Power \
        /org/freedesktop/DeviceKit/Power \
        org.freedesktop.DeviceKit.Power.Hibernate
;;
*)
echo Not supported command: '"'$1'"'
echo Usage: $0 '<suspend|hibernate>'
exit 1
;;
esac
```**SETUP**
1) Save the above as: gnome-power-control

2) Change file permissions to execute (right click on file -> properties -> permissions) 

3) optional: move this script into your ~/bin/ folder for easy access!

**USAGE**
To suspend: gnome-power-control suspend
To hibernate: gnome-power-control suspend

**BINDINGS**
Once in your ~/bin/ folder, you can bind other programs to use this! For example, create a Compiz shortcut to execute gnome-power-control suspend, or create a launcher on your toolbar to do the same thing!

**DOES NOT WORK?**
If this does not work for you, you either don't have DeviceKit (in Ubuntu 9.10) or if you do, then your suspend/hibernate is not working correctly.

Thank you.

Is there a straightforward way to directly create a new file in /bin folder? .. like in windows right click > new.

So I created new file as you described, in Desktop, then tried to drag it to /bin folder... "access denied", it's sickening.... I thought it was MY computer.

So, how do I invoke command "gnome-power-control suspend" and assign it to a Keyboard shortcut?

---

### Post by AgenT on 2009-11-14
> **Rebelli0us said:**
> Thank you.

Is there a straightforward way to directly create a new file in /bin folder? .. like in windows right click > new.

So I created new file as you described, in Desktop, then tried to drag it to /bin folder... "access denied", it's sickening.... I thought it was MY computer.

So, how do I invoke command "gnome-power-control suspend" and assign it to a Keyboard shortcut?
Not into /bin/ but into ~/bin/ which is short for /home/YOUR_USERNAME/bin/ 
~ is short for your home directory.

And it's not sickening that you cannot add into /bin on Linux. It's one of the reasons why there are no viruses, etc. in Linux, but there are a TON on windows. It's called common sense security. Yes it's your computer, and yes, if you want to, you can add a file into /bin but only as root user. Again, common security, which Windows has always lacked.

If you want more information, I suggest reading up on the [linux permission system]("http://meinit.nl/linux-permission-system-explained").

---

### Post by Rebelli0us on 2009-11-15
> **AgenT said:**
> Not into /bin/ but into ~/bin/ which is short for /home/YOUR_USERNAME/bin/ 
~ is short for your home directory.

And it's not sickening that you cannot add into /bin on Linux. It's one of the reasons why there are no viruses, etc. in Linux, but there are a TON on windows. It's called common sense security. Yes it's your computer, and yes, if you want to, you can add a file into /bin but only as root user. Again, common security, which Windows has always lacked.

If you want more information, I suggest reading up on the [linux permission system]("http://meinit.nl/linux-permission-system-explained").

Thanks again, I meant sickening in the sense that somebody with my experience cannot do simple things in Linux, even with your kind help. And "access denied" offers no help.

So I'm browsing, there is no BIN dir in  /home/YOUR_USERNAME/  ??

I did a search, there's a dozen BIN dirs, I thought BIN is like windows\system32

I also tried executing "gnome-power-control" from where it is (desktop) but nothing happens. I did the "permissions"  "allow execute". I just assume this is like a batch file, and once it works I can assign it a keyboard shortcut??

Help! Why is something simple so hard????

---

### Post by nothingspecial on 2009-11-15
Just make one. Although it`s not there by default, it`s in your path by default, even if it`s not there. 

Or it always used to be, using Hardy so things might have changed.

Edit -

Rereading that, it doesn`t sound very clear unless you understand paths. If a directory is in your path then you can execute any binary in that directory typing the name of the program. 

To see what I mean, try typing ```
ls /usr/bin/
```

One of the first programs you`ll see is the very commonly used apt-get. I`m guessing you type```
 sudo apt-get install blah blah blah
``` all the time.

If /usr/bin was not in your path you would have to type ```
sudo /usr/bin/apt-get install blah blah blah
``` because bash would not search /usr/bin to find it.

Other distros include ~/bin as a default directory, Ubuntu does not, but it does include ~/bin in your default path. So you can create ~/bin and bash will search it

To see which directories are in your path type ```
echo $PATH
```

Edit 2 -

I`m not sure that made it clearer, anyway, research your path if your interested

---

### Post by Rebelli0us on 2009-11-16
> **nothingspecial said:**
> Just make one. Although it`s not there by default, it`s in your path by default, even if it`s not there. 

Or it always used to be, using Hardy so things might have changed.

Edit -

Rereading that, it doesn`t sound very clear unless you understand paths. If a directory is in your path then you can execute any binary in that directory typing the name of the program. 

To see what I mean, try typing ```
ls /usr/bin/
```

One of the first programs you`ll see is the very commonly used apt-get. I`m guessing you type```
 sudo apt-get install blah blah blah
``` all the time.

If /usr/bin was not in your path you would have to type ```
sudo /usr/bin/apt-get install blah blah blah
``` because bash would not search /usr/bin to find it.

Other distros include ~/bin as a default directory, Ubuntu does not, but it does include ~/bin in your default path. So you can create ~/bin and bash will search it

To see which directories are in your path type ```
echo $PATH
```

Edit 2 -

I`m not sure that made it clearer, anyway, research your path if your interested



Thank you. If path works the same as in windows then I do understand it, that’s why I tried to drag the “batch” file into the BIN directory. But as I’ve mentioned, batch isn’t not running! Thanks for explaining anyway for the benefit of other new users, who I’m sure are googling on how to make Suspend work.

My original question above was about the "Suspend" command in Keyboard Shortcuts NOT working. It only blanks the screen momentarily. So I thought of finding the suspend command and assign a keyb shortcut to it. But as you’re witnessing that’s not working either.



//

---

### Post by victorfb on 2009-11-20
I know this thread is [solved] but I thought I could add some clarifications. I had the same problem/question about creating suspend and hibernate keyboard shortcuts.
The script works (thanks, AgenT!). The only thing is that ~/bin is not in your paths by default on ubuntu 9.10, so you can either create the script in one of your paths (you can find them with the command "echo $PATH" as AgenT mentionned) like /usr/bin. To do that, you'll need administrator rights so in a terminal type:
```
sudo gedit /usr/bin/gnome-power-control
```Then you copy-paste the script and save.
Then you still need the admin rights to add the execute permession so in a terminal type:
```
sudo chmod a+x /usr/bin/gnome-power-control
```Then the commands "gnome-power-control suspend" and "gnome-power-control hibernate" work, you can create keyboard shortcuts with them.
An other way would be to create the file in any directory and point there with you command. For instance, if you create it on your desktop the command will be "/home/YOURUSERNAME/Desktop/gnome-power-control suspend"
Cheers!

---

### Post by nothingspecial on 2009-11-20
> **victorfb said:**
> 
 The only thing is that ~/bin is not in your paths by default on ubuntu 9.10, 

I hate the way they keep changing things  :D

---

### Post by Rebelli0us on 2009-11-27
Thank you, it's working now... almost

For now, I'm running it from the desktop by calling the full path. It turns out the $PATH command is CASE SENSITIVE ... %@!^&* and the delimiter is : instead of ; ..lol

/usr/bin IS in path but ONLY some guy named "root" is allowed to do it, ... I figured out how to login as root, how do I make that the default in the login screen?

Under keyboard shortcuts, can I just put the line from the script?

dbus-send --print-reply \
        --system \
        --dest=org.freedesktop.DeviceKit.Power \
        /org/freedesktop/DeviceKit/Power \
        org.freedesktop.DeviceKit.Power.Suspend


All in one line, I assume the \ is a line break?


Last question and most important: When I suspend this way there's NO prompt for password when I wake the machine. Whereas when I suspend from the Shutdown dialog or the Sleep key I get the normal pw login. How does one enable the password prompt for this command?




//

---

### Post by Rebelli0us on 2009-11-27
Ok I tried it. If you just want a Suspend command, you don't need to call the batch file or script. Just create a new Keyboard Shortcut with this command in one line:

dbus-send --print-reply --system --dest=org.freedesktop.DeviceKit.Power /org/freedesktop/DeviceKit/Power org.freedesktop.DeviceKit.Power.Suspend



As I mentioned above, with this method, there is still NO prompt for password on Resume, that needs fixing.

The reason I'm here, is because the built-in “Suspend” command doesn't work, so that needs fixing too.

---

### Post by grandsatrap on 2009-11-29
Is this really solved??

I have pmi installed, but pmi action suspend does nothing. (none of the pmi commands do.)  The "sudo /etc/acpi/sleep.sh sleep" does.

However, it is well and good for me to force the computer to sleep, but how can I get it to do it on its own? After 30 minutes of doing nothing, the way my Windows XP does? 

I want my ubuntu server to sleep during the night (after some idle time) and then wakeup-on-lan when I try to use it over the internet (send a WOL packet first).

---

### Post by Rebelli0us on 2009-12-03
> **grandsatrap said:**
> Is this really solved??

I have pmi installed, but pmi action suspend does nothing. (none of the pmi commands do.)  The "sudo /etc/acpi/sleep.sh sleep" does.

However, it is well and good for me to force the computer to sleep, but how can I get it to do it on its own? After 30 minutes of doing nothing, the way my Windows XP does? 

I want my ubuntu server to sleep during the night (after some idle time) and then wakeup-on-lan when I try to use it over the internet (send a WOL packet first).

Auto-suspend works on my machine, screen timeout also... it's in the POwer options.

Have you tried the Suspend command on my last post above?

In windows I can wake up machines on my home network via magic packet, and also suspend them with utility from Sysinternals, but I haven't tried it in Linux cos LAN configuration seems more technical.

---

### Post by jayanramesh on 2009-12-05
> **aoakley said:**
> There are several threads which unsuccessfully seek a command line method to hibernate or suspend in Ubuntu, WITHOUT requiring root or sudo access. After a bit of digging, I've come up with the answer.

This is tested on Ubuntu 8.04 (Hardy) with a Dell Inspiron 1520 laptop. I would appreciate feedback from users of other systems.

To suspend-to-RAM (aka sleep):

```
pmi action suspend
```

To suspend-to-disk (aka hibernate):

```
pmi action hibernate
```

If you want to lock the Gnome session first (ie. require a password on resumption), then issue the following command before pmi:

```
gnome-screensaver-command --lock
```

For example, you can use these commands to create a button (launcher) on a Gnome panel (taskbar) that instantly locks the screen and goes into sleep mode:

Right-click panel, Add to panel, Custom application launcher, Add, Name: Sleep , Command: gnome-screensaver-command --lock ; pmi action suspend

Wonderful,thank you so much for your help

---

### Post by yavoh on 2009-12-22
These commands have worked the most reliably for me:
```

sudo s2ram
sudo s2disk
sudo s2both

```
Which are suspend-to-RAM (standby/suspend), suspend-to-disk (hibernate), and "hybrid", like the hybrid sleep feature of win7.

---

### Post by ehalls on 2010-01-03
> **aoakley said:**
> There are several threads which unsuccessfully seek a command line method to hibernate or suspend in Ubuntu, WITHOUT requiring root or sudo access. After a bit of digging, I've come up with the answer.

This is tested on Ubuntu 8.04 (Hardy) with a Dell Inspiron 1520 laptop. I would appreciate feedback from users of other systems.

To suspend-to-RAM (aka sleep):

```
pmi action suspend
```To suspend-to-disk (aka hibernate):

```
pmi action hibernate
```If you want to lock the Gnome session first (ie. require a password on resumption), then issue the following command before pmi:

```
gnome-screensaver-command --lock
```For example, you can use these commands to create a button (launcher) on a Gnome panel (taskbar) that instantly locks the screen and goes into sleep mode:

Right-click panel, Add to panel, Custom application launcher, Add, Name: Sleep , Command: gnome-screensaver-command --lock ; pmi action suspend

Great! I have been looking for this. Works on my gigabyte 912 tablet pc.

---

### Post by spiffman on 2010-01-07
I tried most of these, and got them to successfully put my desktop on hibernate, but then it IMMEDIATELY wakes up, i.e. ram writes to disk, computer powers down, a second goes by, then computer powers up and restores to the original state. 

Using ubuntu 9.10 amd64, still trying some other methods, but I haven't found any other posts with this problem... any ideas?

---

### Post by eipapp on 2010-01-17
Hey spiffman, I have the same problem and as yet, no solution. Just wanted u to know you're not alone with this issue. If you find anything that works, let me know.

eipapp

---

### Post by browneej on 2010-01-22
Don't know why this works if the problem is the nvidia driver, but I found [[COLOR="Blue"]_this_[/COLOR]]("http://www.xpmediacentre.com.au/community/mythtv-combined-front-backend/41202-mythbuntu-frontend-build-xbmc-mythtv-suspend-resume-remote.html") solution to the one-time-only suspend/hibernate:

> I have recently started having trouble keeping the thing asleep (ie it wakes up immediately after suspending). This seems to have solved it (on both Asrock and Zotac setup). If you are using legacy GRUB, add

Code:
usbcore.autosuspend=-1

to the end of the kernel line in /boot/grub/menu.lst. If you are using GRUB2, then it is a tad more complicated. You need to add it to the option GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, ie

Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"

and update GRUB:

Code:
$ sudo update-grub

Now it seems to work for me.  I get a white screen upon restore, but I hit enter and I get the lock/login screen.

---

### Post by SaintDanBert on 2010-02-01
> **aoakley said:**
> 
To suspend-to-RAM (aka sleep):
```
pmi action suspend
```

To suspend-to-disk (aka hibernate):
```
pmi action hibernate
```


On my Ubuntu Karmic (v9.10) system, I don't find [highlight] pmi [/highlight] anything.

A search using Synaptic found an **Intelligent Open Platform Management Interface (openipmi) **. Is this what I need to install?

Before I use SLEEP or HIBERNATE is there other configuration that I need? For example, does hibernate require a swap file or can I designate some other place to store that context? (I have 4GB ram that never swaps anything so I did not configure swap space.)

~~~ 0;-Dan

---

### Post by Exic on 2010-03-10
SaintDanBert: I installed the package "powermanagement-interface" which contains pmi and works very well.

---

### Post by Rebelli0us on 2010-04-27
Back in November, I was able to fix the NO prompt for password on Resume, on one pc. Now I need to do it for another machine, but I can't remember how I did it?! I checked the config editor and Suspend is checked... so I'm stumped again.

The script/command posted above in this thread works fine to suspend S3, BUT I get NO prompt for password on Resume, which is a serious problem.

---

### Post by Rebelli0us on 2010-04-27
This command works in terminal:

gnome-screensaver-command --lock ; pmi action suspend

but not in "keyboard shortcuts". The delimiter ; probably doesn't work. Is it possible to run 2 commands in "keyboard shortcuts"?

---

### Post by shahraj81 on 2010-07-19
Here is an easy and quick way to do suspend ubuntu from command line. (Tested with Ubuntu 10.04). It took me a while to figure it out:

[http://www.establishfacts.com/how-tos/suspendubuntufromcommand-line](http://www.establishfacts.com/how-tos/suspendubuntufromcommand-line)

Enjoy!

---

### Post by COKEDUDE on 2010-07-29
Thx for all of this good information.

---

### Post by chiefrocka on 2010-08-11
Ok I've been looking into this for a while. I see people installing various packages for suspending/hibernating. What I don't understand is that why can Gnome suspend if I don't already have those packages installed? This leads me to believe that I should be able to suspend Ubuntu without having to install these extra packages, since Gnome can do it.

I'm guessing the interface to suspend the OS is programmatic. In other words, I can only suspend from calling into some lib, not from command line. Is that true?

I'd like to look at the source of the power menu in ubuntu, but I have no idea what package that's in. Any pointers?

Also, are those packages recommended in this thread programs that call into the aforementioned programmatic interface (like 'pmi')?

---

### Post by marcw on 2010-09-26
In case someone else runs across this thread wondering how to use the command line to suspend (S3) in Lucid 10.04 without becoming root or using sudo, I found the answer here:

[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)

The short answer (for suspend) is this command (all one line):

```
 dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

---

### Post by dli8ilb on 2010-10-20
marcw, when i run that command, terminal says: > Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.UPower was not provided by any .service files

any ideas?  using 10.10

nevermind, i got it to work using HAL with:> dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0

---

### Post by Yoshizmo on 2010-12-22
Using Ubuntu 10.10 or 10.04 with default packages you can issue the command:
```
sudo pm-suspend
```

other options are:
pm-hibernate
pm-powersave
pm-suspend-hybrid

hope that helps.

---

### Post by Protocol84 on 2011-02-22
I am using pam-face-authentication to replace passwords for sudo and login. No matter what I do when I suspend it has to verify me 4 times while suspending and another 4 upon resume, I thought finding a way to suspend without needing root would alleviate the problem, but it is still present even though I have tried all the ways to do so in the forum.

Any thoughts?

---

### Post by Henk Poley on 2011-03-07
I suspect during suspend the power manager will send messages to the screensaver, X desktop manager (for example gdm), etc. to lock the screen. Normally if you lock the screen 4 times in a row (using different methods) you will only need to unlock it once. But your face detection screen lock apparently figures it needs to buffer all those locks and have you unlock each of them.

Try to figure out how you can get in such a situation outside of suspending. So, try to lock the screen by timeout, and then send a lock message from commandline over SSH (or by cron).

Then you'll have a testcase for the people of pam-face-authentication.

---

### Post by el_oscuro on 2011-03-21
> **Yoshizmo said:**
> Using Ubuntu 10.10 or 10.04 with default packages you can issue the command:
```
sudo pm-suspend
```

other options are:
pm-hibernate
pm-powersave
pm-suspend-hybrid

hope that helps.

You also need to install pm-utils before using these commands.  Otherwise works fine.

---

### Post by r_mano on 2011-03-22
...and if you want to run pm-suspend without entering any password (I use it for example with:

```
 
do-long-video-rendering.sh && sudo pm-suspend

```

...and go to sleep), you can add to the file /etc/sudoers (edit it using sudo visudo) the line:

```

your_user_name ALL=NOPASSWD: /usr/sbin/pm-suspend

```

---

### Post by giannosfor on 2011-05-01
> **motin said:**
> 
```
echo 'pmi action suspend' | at now + 40 minutes
```

How can actually suspend or hibernate in 40 minutes?
Not echo it.

---

### Post by SecretCode on 2011-05-03
The command shown **will **actually suspend in 40 minutes. _echo_ puts the quoted text into stdout, and _at_ reads the text piped from it - not the whole echo command, just its output.

Why not try it?

---

### Post by giannosfor on 2011-05-03
Thanks i feel very stupid,do you know how to cancel it after trigger?

---

### Post by SecretCode on 2011-05-04
Since it's more than 40 minutes since you posted, no :)

But seriously - a look at _man at_ suggests the command _atrm 1_ if 1 is the job number (you can check with _atq_).

You'll need _sudo_ if your user does not have rights to suspend (see a few posts back).

---

### Post by haudace on 2011-05-05
Thanks, I was looking for something like this. Hopefully, it still works with natty 11.04!:)

Edit: NVM, reading the log files I found my hard drive disk does not communicate well with natty. It does not power down when triggered in linux :(. Since I am loading linux from a USB, I just removed the internal HD and everything works fine now.

---

### Post by user2037 on 2011-10-25
Sadly none of these solutions work with 11.10. PMI produces "Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files"

---

### Post by landtuna on 2011-10-27
As someone mentioned above, this seems to work in Oneiric:

```
dbus-send --system --print-reply --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

---

### Post by aciddesir on 2011-11-16
> **user2037 said:**
> Sadly none of these solutions work with 11.10. PMI produces "Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files"

Seconded.  Also pm-utils commands are overriden if you use Jupiter at the same time.

---

### Post by petko10 on 2012-03-22
Guys you need to install the package "hal" . In short : 
1 Get powermanager-interface
2 Get hal
3 Type "pmi action suspend"

That worked for me on 11.10 .

---

### Post by Artif on 2012-04-30
> **marcw said:**
> [https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)
```
 dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

This was successfull on [COLOR=Blue]**L**[/COLOR]Ubuntu 12.04 Precise with OpenBox session. **Without sudo** and root privileges. LUbuntu is derivative with LXDE instead of heavy Unity, because this is the only declared distinction( [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu) ), the trick must be workable on Ubuntu and other official derivatives.

Usually in LUbuntu you also may use lxsession-logout, but it is a GUI solution (can not be used in autonomous script or else), and you can not use lxsession-logout on LUbuntu's Openbox session without some working on additional lxsession launch. But "dbus-send..." will do the job out of the box.

As posted at
[http://askubuntu.com/questions/93542/how-to-disable-shutdown-reboot-suspend-hibernate](http://askubuntu.com/questions/93542/how-to-disable-shutdown-reboot-suspend-hibernate)
you may find other targets:

[LIST]
[*]     org.freedesktop.consolekit.system.stop
[*]     org.freedesktop.consolekit.system.restart
[*]     org.freedesktop.upower.suspend
[*]     org.freedesktop.upower.hibernate
[/LIST]
 
You may use:
for reboot
```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart
```for shutdown 
```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```for hibernate
```
dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Hibernate
```

Suspend is described above:```
dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

This also do not need system modifications or root access.

P.S. 2All: Hey! Ordinary user do not have sudo access or root privileges!!! Editing of /etc/sudoers may lead to possible breaks in security system (remember possible vulnerability  of any software). Using of "sudo suspend-command" is an ugly workaround instead of real solution.

---

### Post by Rebelli0us on 2012-05-15
How do you send a SUSPEND command to another Linux machine on your network?

Something equivalent to Microsoft/Sysinternals PsTools psshutdown.exe utility.

---

### Post by HiImTye on 2012-05-15
would be easy if you just ssh'd into it

---

### Post by Rebelli0us on 2012-05-17
> **HiImTye said:**
> would be easy if you just ssh'd into it

I tried 

```
ssh user-name@192.168.1.102 sudo pm-suspend
```

but it didn't work. Any ideas how to suspend machines on the network?

---

### Post by Artif on 2012-05-28
> **Rebelli0us said:**
> I tried 

```
ssh user-name@192.168.1.102 sudo pm-suspend
```but it didn't work. Any ideas how to suspend machines on the network?

Did it ever worked directly on the machine? If not - try other ways to suspend.

I'm not shure you must not use double qoutes for command string, if there are internal field separators in the string:
ssh [EMAIL="user-name@host.name"]user-name@host.name[/EMAIL] "command argument argument"

---

### Post by Rebelli0us on 2012-05-28
> **Artif said:**
> Did it ever worked directly on the machine? If not - try other ways to suspend.

I'm not shure you must not use double qoutes for command string, if there are internal field separators in the string:
ssh [EMAIL="user-name@host.name"]user-name@host.name[/EMAIL] "command argument argument"

Yeah machines suspend just fine, I just want to be able to do it remotely. Do you have a command that works?

---

### Post by Artif on 2012-05-29
> **Rebelli0us said:**
> Yeah machines suspend just fine, I just want to be able to do it remotely. Do you have a command that works?

Yes I have it. This is exact duplicate of mentioned above DBus way command ( [http://ubuntuforums.org/showpost.php?p=11890267&postcount=57](http://ubuntuforums.org/showpost.php?p=11890267&postcount=57) ).
```
ssh [EMAIL="user-name@host.name"]user-name@host.name[/EMAIL] "dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend"

```

But you neeed to set up permissions. Into your file
"/usr/share/polkit-1/actions/org.freedesktop.upower.policy"
into section "defaults" you may insert
```
      <allow_any>yes</allow_any>

```

Ubuntu 12.04 Precise will suspend.

See:
*) [http://crunchbanglinux.org/forums/topic/17681/solved-suspend-not-working/](http://crunchbanglinux.org/forums/topic/17681/solved-suspend-not-working/) (Ubuntu based light weight distro)
*) [http://archive.linuxfromscratch.org/mail-archives/blfs-support/2011-February/068221.html](http://archive.linuxfromscratch.org/mail-archives/blfs-support/2011-February/068221.html) (from scratch...)

---

### Post by Rebelli0us on 2012-06-19
> **Artif said:**
> Yes I have it. This is exact duplicate of mentioned above DBus way command ( [http://ubuntuforums.org/showpost.php?p=11890267&postcount=57](http://ubuntuforums.org/showpost.php?p=11890267&postcount=57) ).
```
ssh [EMAIL="user-name@host.name"]user-name@host.name[/EMAIL] "dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend"

```

But you neeed to set up permissions. Into your file
"/usr/share/polkit-1/actions/org.freedesktop.upower.policy"
into section "defaults" you may insert
```
      <allow_any>yes</allow_any>

```

Ubuntu 12.04 Precise will suspend.

See:
*) [http://crunchbanglinux.org/forums/topic/17681/solved-suspend-not-working/](http://crunchbanglinux.org/forums/topic/17681/solved-suspend-not-working/) (Ubuntu based light weight distro)
*) [http://archive.linuxfromscratch.org/mail-archives/blfs-support/2011-February/068221.html](http://archive.linuxfromscratch.org/mail-archives/blfs-support/2011-February/068221.html) (from scratch...)

Thank you. I'm still trying to understand this.

Has to be installed on all machines?
```
sudo apt-get install policykit-1 upower acpi-support
```


There isn't a GUI for policy kit? Instead you edit manually?

```
sudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy
```

You set policy on receiving or sending machine? 

What if it's a Windows machine? For Windows machines on the network, Sysinternals\PsTools\psshutdown.exe works very well but it has to be sent by another windows machine, even a VM.

---

### Post by onex on 2012-08-27
> **aoakley said:**
> There are several threads which unsuccessfully seek a command line method to hibernate or suspend in Ubuntu, WITHOUT requiring root or sudo access. After a bit of digging, I've come up with the answer.

This is tested on Ubuntu 8.04 (Hardy) with a Dell Inspiron 1520 laptop. I would appreciate feedback from users of other systems.

To suspend-to-RAM (aka sleep):

```
pmi action suspend
```

To suspend-to-disk (aka hibernate):

```
pmi action hibernate
```

If you want to lock the Gnome session first (ie. require a password on resumption), then issue the following command before pmi:

```
gnome-screensaver-command --lock
```

For example, you can use these commands to create a button (launcher) on a Gnome panel (taskbar) that instantly locks the screen and goes into sleep mode:

Right-click panel, Add to panel, Custom application launcher, Add, Name: Sleep , Command: gnome-screensaver-command --lock ; pmi action suspend

Good work - you provided a piece of the puzzle for me, and it work's nicely!

I have this in my ~/.bashrc:

```
# Monitor off and sleep in $1 minutes
off () {
xset dpms force off && echo 'gnome-screensaver-command --lock; sudo pmi action suspend' | at now + $1 minutes
}
```

This switches off the monitor immediately and waits the specified number of minutes before sleeping the system. Great if you listen to stuff before sleeping! e.g. I'm listening to a podcast I know will finish in 47 minutes, so I just issue:

```
off 50
```

For this to work, I had to edit /etc/sudoers to enable sudo pmi without a password:

```
$USER ALL=NOPASSWD: /usr/sbin/pmi
```

Thanks again!

---

### Post by epikvision on 2012-09-21
> **aoakley said:**
> There are several threads which unsuccessfully seek a command line method to hibernate or suspend in Ubuntu, WITHOUT requiring root or sudo access. After a bit of digging, I've come up with the answer.

This is tested on Ubuntu 8.04 (Hardy) with a Dell Inspiron 1520 laptop. I would appreciate feedback from users of other systems.

To suspend-to-RAM (aka sleep):

```
pmi action suspend
```

To suspend-to-disk (aka hibernate):

```
pmi action hibernate
```

I tried the sleep command but I got the error message...
```
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Hal was not provided by any .service files

```
I would love to use this command, but it's not working.


> 
For example, you can use these commands to create a button (launcher) on a Gnome panel (taskbar) that instantly locks the screen and goes into sleep mode:

Right-click panel, Add to panel, Custom application launcher, Add, Name: Sleep , Command: gnome-screensaver-command --lock ; pmi action suspend

How do I do this on Ubuntu 12.04?

---

### Post by pqwoerituytrueiwoq on 2012-10-07
> I would love to use this command, but it's not working.
look at post #63
```
dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

---

