---
title: "Ubuntu 14.04 LTS menu and laucher missing"
date: 2015-05-25
forum: General Help
---

### Post by chris382 on 2015-05-25
After a restart my computer booted up with the menu and side bar with apps or launcher missing. What can i do to fix this issue? I also can't open up terminal with ctrl  alt t . this all happened after installing virtual box

---

### Post by Bashing-om on 2015-05-25
chris382; Hello;

What options do you get when you right click on the desktop ?

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-25
Thanks for the reply. When i right click it gives me these options.. New folder, New document, Organize Desktop by Name, Keep Aligned, and change Desktop Backgroud.
I searched for this issue online and the only solutions i get tell me to do ctrl alt f1 but when i do that it gives me a black screen. I cannot believe this happened to me and i want things to go back to normal because now i really can't use this computer. I don't understand why this happened but before the reboot i was trying to download virtual box.. i really don't even know to be honest but there's gotta be a way to fix this.

---

### Post by v3.xx on 2015-05-25
I wonder if you could get lucky.  Reset Unity:
```
setsid unity
```
Can't get to terminal?  Go to console (tty):
Ctrl + Alt + F1
To go to GUI from console:
Ctrl + Alt + F7


Whats up Bashing :)

---

### Post by chris382 on 2015-05-25
Doing Ctrl Alt F1 gives me a black screen. Thanks.

---

### Post by Bashing-om on 2015-05-25
@chris382; Well;

What happens when you choose "change Desktop Backgroud" ?

@v3.xx; Great to read you too ! Let's see what it takes to get this done.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]it's fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-25
When i go to change desktop background it goes into my settings and from there i can change the way my background looks or go to All settings.

---

### Post by chris382 on 2015-05-25
I've noticed that when i click on the behavior tab it says below that some settings have been overriden by an external program. When i restore it does nothing.

---

### Post by v3.xx on 2015-05-25
That should of took you to a login prompt.  Try ..
Ctrl + Alt + F2
Still no good?  May have to go to recovery mode at boot and use low resolution mode.

Also run
```
sudo apt-get -f install
```
See if that spits out any errors that may help us.

Note:
Sudo is not used in recovery mode, you already have superuser status when in recovery mode.

---

### Post by chris382 on 2015-05-25
Ctrl alt F2 just gave me a black screen too. I don't have access to any terminal.

---

### Post by chris382 on 2015-05-25
How would i go to recovery mode and use low resolution mode?

---

### Post by chris382 on 2015-05-25
Now when i try to log in it gives me a black screen and i cant even get to my desktop..
I'm completely done with ubuntu if i can't solve this issue. Unbelievable that i've run into so many issues after upgrading from windows! Now i really can't use my computer. 
I mean come on now ... i should've just stayed with windows.

---

### Post by v3.xx on 2015-05-25
> i should've just stayed with windows. 
Your choice, linux is not windows.

Myself, its been 5 or 6 years since I have had any serious downtime.  I was a newb back then :)

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by chris382 on 2015-05-25
Thanks for the help.

---

### Post by v3.xx on 2015-05-25
Ain't seen nothing yet.

Wait till Bashing kicks in :D

---

### Post by Bashing-om on 2015-05-25
chris382; Welp;

It is fixable, just a matter of finding out what is broke where .

Let's try this:
Boot to the login screen, at this screen key combo ctl+alt+F1 yields a console interface, log in here with your username and password (there is no response to the screen when password is entered. enter your password blindly and hit the enter key)
In this terminal execute terminal command:
```

sudo service lightdm start

```

What does the system report ?
Does the Desktop start ?

If the display does not start the report will give us a hint of where the failure is.


But, if you are not going to use it; there is no point in fixing it.


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-26
No it's just that i'm really really frustrated about it and when i try to do the ctrl alt f1 it just takes me to a black screen. I then entered my password and it still is stuck at a black screen. I was able to get to the desktop before but not im not able to and when i login it takes me to a black screen also. This is fixable i just need to calm down and try everything you tell me. 
The display isn't starting when i enter my password blindy, thankyou Bashing-om. It stays black. I'd like to get back to linux and it is better than windows it's just i'm a noob to ubuntu.

---

### Post by chris382 on 2015-05-26
When booting in safe mode its gives me nine options.. resume, clean, dpkg, failsafex, fcsk, grub, network, root, and system-memory. What exactly would i do from here? Thanks.

---

### Post by Bashing-om on 2015-05-26
chris382; Hey;

That's the spirit ! It is fixable, just find the fault.

This is looking more and more like a graphics driver issue. Are you running a proprietary graphics driver ? That driver is not under ubuntu's control - is built against the installed kernel, when the kernel is updated that driver gets broke.

Let's get a terminal interface via other means;
Try:
Boot to the grub menu, with the normal kernel selected press the 'e' key for edit mode -> boot parameters screen;
In the boot parameter screen arrow down to the line starting with 'linux' and arrow across to "quiet splash" replace these terms with the term "text" with out the quotes - ; key combo ctl+x to continue the boot process to TTY1.

Log in here with user name and password.

If you can get to this point we do trouble shooting in respect to the GUI;
IF you can not, we do trouble shooting in respect to grub ( GRand Unified Bootloader).

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]to restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-26
UPDATE. When i boot into recovery mode and continue to resume its takes me to my login screen and when i log in instead of giving me a black screen it just returns me back to the login.

---

### Post by chris382 on 2015-05-26
I'm not sure if i am running a proprietary graphics driver. I probably should know that but i'm a complete noob. Sorry. I'm a little lost Bashing.. Pressing the "C" key while booting takes me to the grub command line. I don't see anything to do with the kernel? Maybe i'm doing something wrong. Thankyou Bashing-Om.

---

### Post by Bashing-om on 2015-05-26
chris382; Hey, Hey .....

Making good progress.

Ok You can get to a terminal, and now looks as if it is a authorization issue.
By the way - it is 'e' for edit and 'c' for command line at the grub menu .

Let's examine authorizations:
boot to terminal:
Now what results:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
Where your output should be similar:
> 
sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Feb  4 15:15 .Xauthority

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 2282 May 26 12:20 .ICEauthority

sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 May 24 17:34 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 29 sysop sysop  4096 May 26 12:20 sysop
sysop@1404mini:~$
 where I am "sysop", where you see "sysop" ; in your outputs should be "you" .

When this is over and done with, we look at the graphics driver.

[INDENT][INDENT]access, access, who has access
[/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-26
When trying any of those commands both on grub command line and root shell prompt i get no file or directory. Am i doing anything wrong? Sorry that i'm such a noob.. and thankyou for staying in there for me.

---

### Post by chris382 on 2015-05-26
I also have a flash drive that i booted linux off of before when i had windows and i erased windows installing ubuntu. Maybe i could boot from the flash drive and reinstall ubuntu 14.04 or will that work? if so.. how?

---

### Post by chris382 on 2015-05-26
I've also noticed that when i boot in safemode and resume it and when i log in the screen turns black for a seconds and then goes back to normal and just takes me back to the login like as if it were a glitch or something..
When i do a regular boot without safemode and the resume i log in but the screen goes black but i hear the sounds of being at the login so im assuming that it is just going taking me back to the login but its a blackscreen so i can't see what is going on.

---

### Post by Bashing-om on 2015-05-26
chris382; Wellll ..

Let's get on a common page. My post #19 refers.

Boot to this TTY1 terminal; and we continue.
Merely because I prefer a direct boot to a terminal.

Once you are terminal we can then look at things.
And another, HEY. Being new is not a sin, not knowing is not a sin. We were all new at one time and we do understand the learning curve.

[INDENT][INDENT]we work to that end.[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-05-26
Once tty is reached, maybe a test desktop (flashback) would be of help.  May make trouble shooting and installing drivers a lot easier.  Just a thought

---

### Post by jon91 on 2015-05-26
Hi,

I am watching this post with great interest as I have an almost identical situation.

14.04 LTS 32bit, updated via Software Updater - and Launcher and Menu gone after a reboot!!!!

I am a newbie to Linux and Ubuntu, and also wary of using commands in the Terminal incase I seriously screw something up.
However - I have executed the terminal commands that I have seen so far in this and similar posts - and feel that I am slowly getting somewhere (and learning).

Jon

---

### Post by Bashing-om on 2015-05-26
jon91; Hello;

If your situation is identical, feel free then to tag along and add to the thread.

Learning, and checking commands: The system has a 'manual' installed. You can (and should) consult the manual about any command you are unsure about.
For instance you often see the 'ls' command to 'list' info about a file ( all things in linux are files !).
To consult the manual is terminal command:
```

man ls

```
Often the 'info' command will give better information. - 'info' in many cases is replacing 'man' .
```

info ls

```
As you learn, feel free to open a thread on any particular question you have .

And now back to your regularly scheduled program. Activating the GUI:

Can you boot to terminal ?
What in your case results in this terminal from executing terminal command:
```

sudo service lightdm start

```
this assumes that you are 
a) running upstart as the init system (14.04 LTS 32bit, ; you are)
b) unity is your Desktop Manager

else you are in the wrong thread.

[INDENT][INDENT]it is all a process in learning
[/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-26
> **Bashing-om said:**
> chris382; Hey;

That's the spirit ! It is fixable, just find the fault.

This is looking more and more like a graphics driver issue. Are you running a proprietary graphics driver ? That driver is not under ubuntu's control - is built against the installed kernel, when the kernel is updated that driver gets broke.

Let's get a terminal interface via other means;
Try:
Boot to the grub menu, with the normal kernel selected press the 'e' key for edit mode -> boot parameters screen;
In the boot parameter screen arrow down to the line starting with 'linux' and arrow across to "quiet splash" replace these terms with the term "text" with out the quotes - ; key combo ctl+x to continue the boot process to TTY1.

Log in here with user name and password.

If you can get to this point we do trouble shooting in respect to the GUI;
IF you can not, we do trouble shooting in respect to grub ( GRand Unified Bootloader).
[INDENT][INDENT]fault isolation[INDENT][INDENT][INDENT]to restoration
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Sorry could you be more specific? I boot into the grub menu by accessing recovery mode correct? I don't know how to get to the grub menu that you want me to go into with the normal kernel selected..

---

### Post by Bashing-om on 2015-05-26
chris382l Ho Kay;

> 
Sorry could you be more specific? [color=red]I boot into the grub menu by accessing recovery mode[/color] correct? I don't know how to get to the grub menu that you want me to go into with the normal kernel selected..

Nope not correct to get the grub menu.
My bad in "assuming" you were aware. My apologies for my failure.

OK, get to the grub menu :
Legacy MBR system; Boot the system and as soon as the bios screen clears depress and hold the right-shift- key -> grub .
UEFI system; as soon as the firmware screen clears repeatedly depress and release the escape key -> grub .

Once at the grub menu, with the normal ubuntu kernel selected press the 'e' key for edit mode . -> boot parameters screen;
In the parameters screen arrow down to the line starting with linux - similar to "linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " ; Arrow across to the terms "quiet splash" and replace these with the term 'text' - without the quotes;
key combo ctl+x to continue the boot process to TTY1.
   

Advise when you have achieved to this stage.

[INDENT][INDENT]the 1st time is never easy
[/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-26
No need for an apology. Thanks for the reply. Still i am confused on what to do :( I'm assuming that there's two options to get into the grub menu, correct? I can get their either with Legacy MBR system and UEFI system. Right? Pressing and holding the right shift key after the bios screen clears doesn't do anything but i could be doing it wrong. 
Also assuming the firmware screen is where it loads up the ubuntu logo ? I've repeatedly pressed and released the escape key here but it just makes the ubuntu logo blink a lot. 
I should be doing the apologies here. Thank you for your time and I apologize for my misunderstanding. Is there maybe a video i could watch that would guide me to to get where you want me to be in the grub menu?

---

### Post by chris382 on 2015-05-26
> **chris382 said:**
> When booting in safe mode its gives me nine options.. resume, clean, dpkg, failsafex, fcsk, grub, network, root, and system-memory. What exactly would i do from here? Thanks.

I believe that i was at the grub menu here. Correct? It lists those options right? I'm a little confused.

---

### Post by Bashing-om on 2015-05-26
chris382; shucks;

One of those methods should work to get the grub menu to display.
There is but a short window of opportunity for grub to recognize that the key is depressed.
In the case of the legacy boot method, actually any key will divert to the grub menu.

In the case of UEFI, there is but a 3 second window when grub begins to boot into for grub to recognize that the escape key is pressing.


[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT]try try again ( sky diving excepted)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-26
I have access to a terminal when pressing ctrl alt f3 and i can login to shell. says tty at the top. Can we do any commands to get my computer working again? Thanks! I don't care much about losing data but i just need a computer that will work and run.

---

### Post by Bashing-om on 2015-05-26
chris382; Yeah,

That too is doable from the F3 console:
Even though I "think" what we have here is a graphics driver issue; let's do a quick check and make sure "you" are authorized to access your desktop.
In that F3 Console, what returns from the terminal commands:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
similar to mine ?
> 
sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Feb  4 15:15 .Xauthority

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 2282 May 26 12:20 .ICEauthority

sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 May 24 17:34 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 29 sysop sysop  4096 May 26 20:51 sysop
sysop@1404mini:~$
 Where I am 'sysop' in your output you should see where is sysop your username.

If the above is a positive result, we next look at graphics:
I do need to see these outputs.
What have we for hardware ?
```

lspci -vnn | grep VGA -A 12

```

And what is the driver doing ?
```

sudo lshw -C display

```

As we consider the probability of (RE-)installing the graphics driver.

[INDENT][INDENT][INDENT]in that process of fault isolation
[/INDENT][/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-27
Okay this is getting better. All the commands work and match the output of yours which are similar. After trying lots of other things online and seeing people with the similar problem online i did what someone said that would solve the issue which was executing the command sudo apt-get install --reinstall ubunutu desktop and after doing so it lists the following packages will be removed psmisc:1386 virtualbox-4.3:386 and i feel that the package virtual box has something to do with it and maybe not so much my graphics driver but i could be very wrong since i'm a noob and i don't know but none of this ever happened and only happened after installing virtual box and restarting. Anyways After executing the command lscpi -vnn | grep VGA -A 12 i get VGA compatible controller [0300]: Intel Corporation ValleyView Gen7 [8086:0f31] (rev 0e) (prog-if 00 [VGA controller])
Flags: bus master, fast devsel , latency 0, IRQ 255
SATA controller [0106] : Intel Corporation ValleyView 6-Port SATA AHCI Controller [8086:0f23] (rev 0e) (prog-if 01 [ACHI 1.0]
Is that what you were looking for? If not i can type more for the output of that command. Thanks.

When executing sudo lshw -C display i get description: VGA compatible controller
Product: ValleyView Gen7
Vendor: Intel Cooperation
bus info:pci@0000:00:02:.0
version: 0e
width:32 bits
capabilities: pm msi vga_controller bus_master cap_list
configuration: latency=0
I can also type more but i don't know what you are looking for in this command.

---

### Post by chris382 on 2015-05-27
I feel that we are getting closer here to fix this.

---

### Post by chris382 on 2015-05-27
Thanks Bashin-Om! It's fixed and after running the command sudo apt-get install --reinstall ubuntu-desktop and connecting my computer to internet to download the new packages it removed virtual box and re installed everything so now my launcher and menu came back to normal. SOLVED! We did it!

---

### Post by chris382 on 2015-05-27
> **jon91 said:**
> Hi,

I am watching this post with great interest as I have an almost identical situation.

14.04 LTS 32bit, updated via Software Updater - and Launcher and Menu gone after a reboot!!!!

I am a newbie to Linux and Ubuntu, and also wary of using commands in the Terminal incase I seriously screw something up.
However - I have executed the terminal commands that I have seen so far in this and similar posts - and feel that I am slowly getting somewhere (and learning).

Jon

Jon try this! Boot into recovery mode and resume in the menu and then when at the login do ctrl alt f3 and login in the terminal
apt-get update
sudo apt-get install --reinstall ubuntu-desktop
It will say memory will be freed just enter "Y"
Let it download packages and remove anything. 
That's it. It worked for me. Let me know if it worked for you.

---

### Post by Bashing-om on 2015-05-27
chris382; Hey;

Nawww. you did all the work;

There is yet this to check:
> 
configuration: latency=0

where this line should show a graphics driver in use; as in my output:
```

sysop@1404mini:~$ sudo lshw -C display
[sudo] password for sysop: 
  *-display:0             
       description: VGA compatible controller
       product: RV515 [Radeon X1300/X1550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       [color=blue]configuration: driver=radeon[/color] latency=0
       resources: irq:16 memory:e0000000-efffffff memory:fd4f0000-fd4fffff ioport:4c00(size=256) memory:fd400000-fd41ffff

```
Where I am running ATI for my graphics set, and have the opensource driver "radeon" in use.

As yours is an Intel graphics set, it should "just work" . Let's see where we go from here.

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-27
configuration: driver=i915 latency=0
There you go.

---

### Post by Bashing-om on 2015-05-27
chris382; Hey hey ;

Yepper, looks to be finer than a frog's hair .
Yep all over with except a final shouting Hooray !

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and we look forward
[INDENT][INDENT][INDENT]to our next adventure
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jon91 on 2015-05-27
Hi Bashing-om and Chris,

Chris wrote:
[COLOR=#000000]Jon try this! Boot into recovery mode and resume in the menu and then when at the login do ctrl alt f3 and login in the terminal[/COLOR]
[COLOR=#000000]apt-get update[/COLOR]
[COLOR=#000000]sudo apt-get install --reinstall ubuntu-desktop[/COLOR]
[COLOR=#000000]It will say memory will be freed just enter "Y"[/COLOR]
[COLOR=#000000]Let it download packages and remove anything. [/COLOR]
[COLOR=#000000]That's it. It worked for me. Let me know if it worked for you.



Do I actually have to be in 'recovery mode' to do this?
Or can I just be in a terminal after booting up? (There is only one user account on this machine).

Many thanks,

Jon (Newbie to Linux and Ubuntu)[/COLOR]

---

### Post by RobGoss on 2015-05-27
Hello Chris I had the same problem after installing [COLOR=#000000]VirtualBox you can read this thread[/COLOR]
 [http://ubuntuforums.org/showthread.php?t=2279936](http://ubuntuforums.org/showthread.php?t=2279936)

My mistake was I downloaded VB from their website and for some reason it removed my terminal, sidebar and software center, so I was helpless and could not even remove it from the command line. I'm not sure how you can fix it all I can do is tell you how I did. I had a clone of my OS and simply placed my Clonezilla USB in my machine and restored it. Once the restore was done everything was just fine.

It is recommend to only install software from the Ubuntu software center because at least we know it's safe for us to install. I hope you get it working my friend I love Ubuntu to just give up so we learn as we go. Best of luck.

---

### Post by Bashing-om on 2015-05-27
jon91; Hey ;

> **jon91 said:**
> Hi Bashing-om and Chris,

Chris wrote:
[COLOR=#000000]Jon try this! Boot into recovery mode and resume in the menu and then when at the login do ctrl alt f3 and login in the terminal[/COLOR]
[COLOR=#000000]apt-get update[/COLOR]
[COLOR=#000000]sudo apt-get install --reinstall ubuntu-desktop[/COLOR]
[COLOR=#000000]It will say memory will be freed just enter "Y"[/COLOR]
[COLOR=#000000]Let it download packages and remove anything. [/COLOR]
[COLOR=#000000]That's it. It worked for me. Let me know if it worked for you.



Do I actually have to be in 'recovery mode' to do this?
Or can I just be in a terminal after booting up? (There is only one user account on this machine).

Many thanks,

Jon (Newbie to Linux and Ubuntu)[/COLOR]

Any terminal will do, this ^ is but one way to gain an interface .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by chris382 on 2015-05-27
> **Bashing-om said:**
> chris382; Hey hey ;

Yepper, looks to be finer than a frog's hair .
Yep all over with except a final shouting Hooray !

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[INDENT][INDENT]and we look forward[INDENT][INDENT][INDENT]to our next adventure
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Our next adventure Bashing-Om? Well I'll be moving now because some kids in my neighborhood started making trouble and were up to no good and I got in one little fight and my mom got scared
She said 'You're movin' with your auntie and uncle in Bel Air' 
So i guess our adventure continues when i move back to with my mom which is where i have my computer.

---

### Post by chris382 on 2015-05-27
> **robert159 said:**
> Hello Chris I had the same problem after installing [COLOR=#000000]VirtualBox you can read this thread[/COLOR]
 [http://ubuntuforums.org/showthread.php?t=2279936](http://ubuntuforums.org/showthread.php?t=2279936)

My mistake was I downloaded VB from their website and for some reason it removed my terminal, sidebar and software center, so I was helpless and could not even remove it from the command line. I'm not sure how you can fix it all I can do is tell you how I did. I had a clone of my OS and simply placed my Clonezilla USB in my machine and restored it. Once the restore was done everything was just fine.

It is recommend to only install software from the Ubuntu software center because at least we know it's safe for us to install. I hope you get it working my friend I love Ubuntu to just give up so we learn as we go. Best of luck.

Hello Robert! I replied to your thread with a solution as it seems to be almost exactly similar.

---

### Post by jon91 on 2015-05-28
Hi,

I tried this - it didn't work for me.....

now i'll try:
sudo lshw -C display
and see what the video driver is doing....

Jon

---

### Post by jon91 on 2015-05-28
Hi All,

Here is my output form the video hardware:

*-display
   description: VGA Compatible controller
   product: Core Processor Integrated Graphics Controller
   Vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 12
   width: 64 bits
   clock: 33Mhz
   Capabilities: msi pm vga_controller bus_master cap_list rom
   Configuration: driver=i915 latency=0
   resources: irq:46 memory:fac00000-faffffff memory:e0000000-efffffff import: f080(size=8)


(the last line might actually be f086(size=8) at the end - can't read my own handwriting.......)


Any suggestions?????

Many thanks,

Jon

---

### Post by Bashing-om on 2015-05-28
jon91; Welp ...

The Intel graphics set is active, and the driver for Intel is loaded.

Off-hand I know of nothing to add.

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

