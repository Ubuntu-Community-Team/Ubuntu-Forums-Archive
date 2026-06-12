---
title: "Newbie - how do I mount a USB stick and install a driver from Terminal (no Launcher)"
date: 2015-05-26
forum: General Help
---

### Post by jon91 on 2015-05-26
Hi,

I am new to Ubuntu, and learning as I am going along.

After installing new updates via 'Software Updater' and a re-boot - I have no launcher / menu.
14.04.2 LTS 32bit

I have followed a few threads and executed a few commands on the terminal.

I have now downloaded a new driver for my video card (via another computer), and have it on a USB stick as a .deb file.

How do I:
Mount the USB stick?
Install the new .deb driver that is on the USB stick?

Many thanks to those who have helped me so far - I would be lost without your help.... 
(I've spent 5 late nights trying to get to the bottom of this....)

Jon

---

### Post by Bashing-om on 2015-05-26
jon91; Hey;

Following your thought process that there might be a fault in the driver.
> 
After installing new updates via 'Software Updater' and a re-boot - I have no launcher / menu.
14.04.2 LTS 32bit

Often happens that an update in the kernel breaks the proprietary driver.

1st one should examine the log file and see what the system reports:
```

less /var/log/Xorg.0.log

```
('q' to Quit out of 'less' )
Then look at what hardware is installed:
```

lspci | grep VGA
lspci -vnn | grep VGA -A 12 ##might get the more relevant info

```

Then see what driver if any is loaded:
```

sudo lshw -C display

```

Take a look and see what the ubuntu community (software repository ) has for a driver:
```

ubuntu-drivers devices
sudo ubuntu-drivers list

```

OK. now you do decide to install a proprietary driver from the repository.
Gui way is from the Software Center -> "Additional Drivers" utility and install the recommended driver.
from terminal:
```

sudo ubuntu-drivers autoinstall

```

If it is determined that the driver is not at fault, we next  look for a fault in the X window system. But that is a horse of another color. We might have to go there.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by jon91 on 2015-05-29
Hi Bashing-om,

Many thaanks for your reply....

In answer to the stuff I should be looking at

log file is 3 pages long
(how do I copy it to another drive - and then plug it into this netbook - so I can post it to this thread???
I can access Terminal and desktop, but no launcher or menu.....
Laptop with Ubuntu has Ubuntu on SSD, and original windows on HDD - so if I can access the HDD in Ubunto - I can paste a file there - then re-boot to windows to log on to the forum.....
It's slow - but I had to do it previously.....)

---

### Post by jon91 on 2015-05-29
continued


lspci grep VGA (can't do vertical line on this netbook), gives:
00.02.0 VGA compatible controller: Intel Coropration Core Processor Integrated Graphics Controller (rev12)

lspci grep VGA -A 12   gives:
00.02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev12) (prog-if 00 [VGA controller])
 Subsystem: Wistron Corp. Device [17c0:10d9]
 Flags: bus master, fast devsel, latency 0, IRQ 46
 Memory at fac00000 (64-bit, non prefetchable) [size=4M]
 Memory at e0000000 (64-bit, prefetchable) [size=256M]
 I/O ports at f080 [size=8]
 Expansion ROM at <unassigned> [disabled]
 Capabilities: <access denied>
 Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
 Subsystem: Wistron Corp. Device [17c0:10d2]
 Flags: bus master, fast devsel, latency 0, IRQ 47

---

### Post by Bashing-om on 2015-05-29
jon91; Hey, Hey;;

We have a tool :
> 
log file is 3 pages long
(how do I copy it to another drive - and then plug it into this netbook - so I can post it to this thread???


Install and use this means of transferring info:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install pastebinit
pastebinit /var/log/Xorg.0.log

```
The pastebinit tool will run the request and the result will be a URL back in your terminal; pass that complete URL back to the thread.

We read the file and I do expect to be able to rule out the graphics driver as the culprit here.

Then we see where we go after reading the log.

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]1 step at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jon91 on 2015-05-29
at terminal typed in
ubuntu-drivers devices

(waited 20 secs for the terminal blinking cursor to come back... then typed:)

sudo ubuntu-drivers list

waited a while (about 20 secs) - then cam back with the cursor for the next command (nothing listed to the terminal)

then typed in
sudo ubuntu-drivers autoinstall

after a little while (10 secs) - came back with

No drivers found for automatic installation.



Doesn't look like i'm having much success.........

The sad thing is - that apart from no launcher or menu - I think everything else is running well.......

Any ideas Bashing-om????
I have no idea what to do next....... However - many thanks for all your help so far, I could never have got this far without help!!!!!

Jon

---

### Post by jon91 on 2015-05-29
Hiya Bashing-om!!!

Many thanks for all your help so far!!!!

I loaded the commands to the terminal - but misread pastebinit as pasteit - so have installed 'pasteit'!!!!

AFterwards - I realised my mistake when I saw the final command!!!!

So I then installed pastebinit, and ran it.

Here is the URL:
paste.ubuntu.com/11440168/

WOW!!!!
I had no idea that SO MUCH could be done in terminal!!!!!!

Jon

---

### Post by jon91 on 2015-05-29
As you say Bashing-om:

Fault isolation: 1 step at a time.

I repair old Jaguars for 'fun' - and with the 1970 and 1980's V12 engines - it's one step of diagnosis - so you can eliminate something because you know it works correctly.... Eventually you narrow down to the culprit by logical deduction.

Thanks for all your help - you really have been a great help to me (and no doubt many others!!!!!!

Jon

---

### Post by Bashing-om on 2015-05-29
jon91; YeaH ;

> 
WOW!!!!
I had no idea that SO MUCH could be done in terminal!!!!!!

When you drive your Jaguar to church on Sunday, that is one way .. But on Saturday night ?
Now that is the terminal !

OK, I see no fault from the Xorg file.
Intel has great support in 'buntu, and Intel "just works" What is provided is the best that Intel can do ! There is no other driver that can replace the best there is .

So, ya want to play with this and use it as a learning experience, or try some shot gun approaches which may reach resolution, but will not tell us why ?

That "learning experience" - on both our parts, may take a bit of time to investigate what is not going on for the GUI display .

Me. I warn you, 
[INDENT][INDENT][INDENT]I always want to know the why
[/INDENT][/INDENT][/INDENT]

---

### Post by jon91 on 2015-05-29
Hi Bashing-om!!!!!

I would like to get to the root of this problem - IF you are interested in delving????

(When I boot off the HDD into Windows - I am reminded of the old rubbish OS!!!! Linux is SO much more elegant!! (In operation - i'm not interested in the pretty wallpaper/desktop!!)).

What ideas do you have next????

Jon

---

### Post by Bashing-om on 2015-05-29
jon91; Ho Kay;

Preliminary stuff; see what it is for sure we are working with:
Boot to the login screen and here rather than trying to login to the GUI do a key combo ctl+alt+ F1.
Login here with username and password - there is no response to the screen when the password is entered, Enter the password blindly and hit the enter key.
This gets us a console, and X is running.
In this interface execute and post the results of terminal commands:
```

lsb_release -a
echo $DESKTOP_SESSION
echo $XDG_CURRENT_DESKTOP
cat /usr/share/xsessions/ubuntu.desktop

```

Then we shift to manual, and see what the system reports when we try and start the desktop from 'terminal' .
------------------------
> 
(When I boot off the HDD into Windows - I am reminded of the old rubbish OS!!!! Linux is SO much more elegant!! [color=blue](In operation - i'm not interested in the pretty wallpaper/desktop!![/color])).

My system is akin to a "street rod" Built up with no hang ons - no power steering, no air conditioner or any of that such - and a 4 barrel carb. - It does have the bucket seats .
It is fast, light and flexible. If I want a fancy GUI (display) I have to choose to start it . 
But, like a lot of things, if ya build it you got to have a good idea of what you are doing. The result of efforts are pleasing.

[INDENT][INDENT]I never said it was going to be easy
[/INDENT][/INDENT]

---

### Post by jon91 on 2015-05-30
Hi Bashing-om,

Thanks for your help and assistance

lsb_release -a gives
Distributor ID: Ubuntu
Description: Ubuntu 14.04.2 LTS
Release:   14.04
Codemane:   trusty


cat /usr/share/xsessions/ubuntu.desktop   gives:
[Desktop Entry]
Name:Ubuntu
Comment:This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=unity
Icon=
Type=Application
X-LightDM-DesktopName=Unity
X-Ubuntu-Gettext-Domain=gnome-session-3.0

That's what I have so far.

Jon

---

### Post by Bashing-om on 2015-05-30
jon91; Yeah ;

That do say we are dealing with unity on release 14.04 and I see no other Desktop Environment (DE) here.

OK, let's see what results when we try and set the DE back to defaults:
From the F1 console interface:
1st make sure "you" have access to the /hom directory.
```

ls -al /home
ls -al /home/jon/

```
where 'jon' is to be "your"username.
My result for reference:
> 
sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 May 28 12:54 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 29[color=blue] sysop sysop  4096 May 30 13:14 sysop[/color]
sysop@1404mini:~$

sysop@1404mini:~$ ls -al /home/sysop
total 4632
drwxr-xr-x 29 sysop sysop    4096 May 30 13:14 .
drwxr-xr-x  4 root  root     4096 May 19  2013 ..
drwx------  2 sysop sysop    4096 Sep 13  2014 #133454 • Fedora Project Pastebin_files
-rw-r-----  1 sysop sysop   11389 Sep 13  2014 #133454 • Fedora Project Pastebin.html
drwx------  2 sysop sysop    4096 May  7  2014 .aptitude
-rw-------  1 sysop sysop   40626 May 29 21:59 .bash_history
-rw-r--r--  1 sysop sysop     309 Jul  8  2013 .bash_logout
-rw-r--r--  1 sysop sysop     220 May 19  2013 .bash_logout~
-rw-r--r--  1 sysop sysop     220 Jul  8  2013 .bash_logout-orig
<snip>
-rw-------  1 [color=blue]sysop sysop     326 May 30 13:14 .ICEauthority[/color]
<snip>
-rw-------  1 [color=blue]sysop sysop     209 Feb  4 15:15 .Xauthority[/color]
<snip>
 Where i am 'sysop' .

Now, it comes back that "you" do have the rights to access /home then :
```

sudo apt-get install dconf-tools
export DISPLAY=:0
dconf reset -f /org/compiz/

```
We could do more here to reset the DE, but, let's see what happens with this simple reset of 'compiz'. If the system screams and hollers, I do want to see the entire output and in context.
Please use "code tags" in the transfer of the results - maintains the formatting and promotes readability :
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Reboot now and let's see if the Desktop is restored in all it's glory.


[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jon91 on 2015-05-30
Hi Bashing-om,

Firstly - a big THANK YOU!!!!

in answer to your terminal commsnds:

drwxr=xr=x    4 root root  4096  Feb 27  16:38 .
drwxr=xr=x  22 root root  4096  May 21  23:19. .
drwxr=xr=x   3 root root  4096  Feb 27  16:38 .encryptfs
drwx------     30 j      j     12288  May 30 22:31 j

more to follow........

---

### Post by Bashing-om on 2015-05-30
jon91; Yuk !

> 
drwxr=xr=x 3 root root 4096 Feb 27 16:38 [color=red].encryptfs[/color]


I know nothing of encrypted file systems, and I may go to floundering on you.

But, will struggle and see what results.

[INDENT][INDENT]when I do not know
[INDENT][INDENT][INDENT][INDENT]I say so
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jon91 on 2015-05-30
Hi Again Bashing-om,

on listing what's under my login: 'j'

There's atleast 4 times as much as you have!!!!!

2 especially are massive - and appeared about or ONLY after the first troubles with no Launcher / Menu

drwxrwxr-x 2 j   j    1065357312  May 3  17:36  73dqrKtBv-

drwxrwxr-x 2 j   j    1065021440  May 4  03:18  G1e pGS8cP

-rw------ 4 j   j   110819685   May 3  12:25   tmp.5KR0dubT (continues about 50 characyers long!!!! .Q6Usg


most of the others are folders I recognize or things that look sensible.

However - if you need a full list to see it all for yourself - what should I do???

Many thanks.

Jon

---

### Post by jon91 on 2015-05-30
Hi,

encryptfs is only because I want my files safe from prying eyes. 
I do some part time consultancy for some investment funds (covers my rent)  - and I would look rediculous if somebody got hold of confidential assesments that I made for them - analysing companies or other funds.....

Ubuntu asked me if I wanted an encrypted SSD - so I chose 'hell yes!!!'

Jon

---

### Post by Bashing-om on 2015-05-30
jon91; Hey;

Of interest is from my reference outputs that are marked in blue. That 'YOU', 'j', are the owner and are grouped to the directory/files. 

As this may be a l O n G thread, with several replies. I do so want that you learn how to use code tags to relay info:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
It sure helps when formatting is retained and things are kept in context.

If required for large outputs, welp, you learn about 'redirection' to a file  in the terminal. Appending that file to your post.
Large files we can use the pastbinit tool.

We remain at the 1st step; to establish that "YOU" have ownership and permissions to access /home .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by jon91 on 2015-05-30
OMG Bashing-om!!!!

YOU did it!!!

I have a full and normal desktop!!!!!!

Thank you SO much!!!!!

Next - I will log onto Ubuntuforums.org with the laptop - and then I can cut and paste the results (with the formatting you have requested) to the thread.

Probably there are lots of things on my machine that are screwed up or just plain 'wrong'.

I do have Ubuntu Tweak and BitBleach.

Many thanks once again.

Jon

---

### Post by Bashing-om on 2015-05-30
jon91; He he ...

Well, I might be inclined to take credit, but nope, I have done nothing to make this happen, many times ubuntu is "self healing" .

You have the demonstrated need of an encrypted file system so that remains ! DO not forget what that decrption key is ! If you loose the means to access your system there is no recovery !

As to other issues. open as many thread as needed to address any given situation . One issue to the thread; like dead men - one to a box .

As too:
> 
I do have Ubuntu Tweak and BitBleach.

exercise extreme care and caution, as often unforeseen side effects can and do occur . * nothing you can do with them that can not be done better in terminal, once you know what you are doing )

If you now have your desktop restored in all it's radiant beauty then
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and we just
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

