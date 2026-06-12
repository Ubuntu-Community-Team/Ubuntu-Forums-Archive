---
title: "ubuntu will not shut down"
date: 2007-11-25
forum: General Help
---

### Post by raveyd on 2007-11-25
I am dual booting Win XP and Ubuntu gutsy gibbon. When I shut down Ubuntu, my computer always restarts automatically...the only way I can shut it down properly is to let it restart into Win XP then shutdown. 

Any ideas how to solve this so that I can just shut down from Ubuntu?

---

### Post by 3ntity on 2007-11-25
> **raveyd said:**
> I am dual booting Win XP and Ubuntu gutsy gibbon. When I shut down Ubuntu, my computer always restarts automatically...the only way I can shut it down properly is to let it restart into Win XP then shutdown. 

Any ideas how to solve this so that I can just shut down from Ubuntu?Try opening a terminal and typing:
```
sudo halt
```
then your password.
This should shutdown your computer. Alternatively, you can try 
```
sudo shutdown -h now
```

If this doesn't help, and your pc reboots anyhow, you can hit 'c' when Grub shows up, which will give you a command line. Here,  you can simply type 'halt' and your pc should shut down. This should prevent you from having to load WinXP [which is ultimately what we want, right ;)].

Sounds like one bizarre problem tho ;)

---

### Post by raveyd on 2007-11-29
Thanks for the reply. I tried all these things. The only one that worked was using halt in the GRUB command line. 

Any other ideas what may be going on?
I don't really wany my computer to restart every time I try to shut it down.

---

### Post by raveyd on 2007-12-03
I've still got the problem that Ubuntu will not shut down:confused: and it's getting quite annoying having to go to Grub command line to shutdown. 

I've been doing some searching on the subject, and I am wondering if something may be wrong in the scripts in init.d, which is causing my computer to reboot when it goes into run level 0 or otherwise to go into run level 6 instead of run level 0. 

What can I look for to check this idea and to understand what is going on?

---

### Post by reincarnut on 2007-12-03
hi folks, a li'l help this way too, please?

my gutsy gibbon refuses (randomly) to log off or shut down. and no, mine is NOT dual-boot. clean linux-only machine.

i normally shut down using the menu --> system --> quit--> shut down

a. if the system shuts down correctly i see the usual status bar thingy going left to right and everything finally powers off and i have a clean shut down.

b. when it doesn't shut down, the screen goes blank after a while like it is beginning to shut down and stops. my power led remains on. after a li'l while i end up having to force the power off.

this happens (again randomly) when i log off. sometimes the logging off brings me back to the users login and sometimes it hangs.

is there something i can do to make it 'a' always without having to type anything? 

additional info: my system is updated realtime, so i am given to understand that all my patches and updates are current.

i am not a very 'advanced user', so please be gentle :-)

---

### Post by raveyd on 2007-12-07
Does anybody have any idea what I can do to make my computer shut down instead of always rebooting? I am running out of patience and about to distro-hop.......

---

### Post by metalheart on 2007-12-07
Open System -> Settings -> Power Management. Navigate to General. There is a selection for 'When I press Power Button'. Select **Turn Off**. Does pressing your computers power button turn the computer off?

---

### Post by Ansuer on 2007-12-07
I too am having shutdown/reboot issues with Gusty.  My laptop shows the progress bar run down and shows the eth's have stopped, then it just hangs.  Happens on both reboot and shutdown from ubuntu.

Strange thing is, the last two times I got "updates" it was able to reboot fine that once, then it's back to the reboot or shutdown hang.  My laptop has the latest bios and firmware.

---

### Post by raveyd on 2007-12-07
Tried changing the power button setting and that didn't work.

Any other ideas?

---

### Post by other guy on 2007-12-09
Bump for having the same issue.):P

The only alternative for me. Is to force it to power down while the machine is POSTing after a restart. By holding the power button in. Not very fun.

Nothing else works. That particular machine also has XP and it shuts down just fine under that.

---

### Post by Sef on 2007-12-09
Have you gone into your BIOS and checked the power management settings?

---

### Post by GraeSquirrel on 2007-12-09
I loaded fiesty fawn and everything was great.  Decided to take theupgrade to gibbon. When gibbon came up it had the same problem your having.  Not knowing beans (coffee?) about the system yet I opted to remove Ubuntu completely then reload fawn.  Works great now.  Guess I will upgrade when I have ubuntu time under my belt.

---

### Post by other guy on 2007-12-09
> **Sef said:**
> Have you gone into your BIOS and checked the power management settings?

I have the BIOS set up to my liking. Since it powers off fine under Windows. I assume it is a issue of some type with the Linux. If there was an issue in MS. My first thought would be hitting BIOS to correct it.

The machine powered off just fine sometime last week. It is near enough a stock install. That i am thinking an update may of caused this. The user has not many needs past mail and surfing.

I ran across this thread on a search. Figured I would hop in and give a question bump. So we all can benefit.

---

### Post by reincarnut on 2007-12-10
another bump. my problem still continues... and randomly at that. sometimes it shuts down and sometimes it doesn't. its like playing the lottery... i always have to hope that i get lucky :-)

c'mon isn't there something we could do? where have all the coffee grinders gone? help us poor newbies...i'm kinda sure there is some setting that we could tweak, there always seems to be!

there is.



isn't there?


hello?


he...llo...?

---

### Post by Joeb454 on 2007-12-10
just curious, what happens if you run ```
sudo shutdown -P 0
```

That'll tell your pc (or laptop) to shutdown completely, power off, and it'll do it as soon as you hit enter from typing your password for sudo

---

### Post by other guy on 2007-12-10
> **Joeb454 said:**
> just curious, what happens if you run ```
sudo shutdown -P 0
```That'll tell your pc (or laptop) to shutdown completely, power off, and it'll do it as soon as you hit enter from typing your password for sudo


I just tired it. My wifes machine still dos not power off correctly. It does power off in XP as it should. I even brewed a fresh pot of 7.10 _64 on it. To try and correct the issue. No joy..

---

### Post by philinux on 2007-12-10
Install and run 

startup-manager from synaptic it manages shutdown settings as well.

It's fully configurable

---

### Post by angryfirelord on 2007-12-10
Ahh yes, ACPI issues....

Anyway, if the above suggestions do not work, open up your menu.lst file:
```
gksudo gedit /boot/grub/menu.lst
```
Go down to the line that says "kernel." Add the following next it (after everything else on that line)
```
acpi=force
```
Save and exit. Reboot the machine, then try to shut it down again.

Now if that fails, then go back to your file, remove the acpi=force comment and add this to the kernel line:
```
acpi=off noapic
```
Do the same. Reboot the machine and try to shut down.

If that still fails, then remove that comment from the kernel line. I'll have to do some more searching.

---

### Post by other guy on 2007-12-10
There are numerous entries where is shows the word kernel. Not being totally helpless... But not all that knowing. Where would I inject that statement? There is much more, for ease of reading. I trunicated it. I am assuming this is where you are referring to:

```

## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d96220e4-e268-4a40-bfed-e6be655329b7 ro quiet splash **[COLOR=Red]acpi=force[/COLOR]**
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d96220e4-e268-4a40-bfed-e6be655329b7 ro single **[COLOR=Red]acpi=force[/COLOR]**
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```Is this how it should look in the file?

---

### Post by reincarnut on 2007-12-10
hi folks. i seemed to have done something that seems to be working fine now - log out and shut down are working without problems, so far so good. tested it a few times too. i dunno if it makes sense, but this is what i did:

system --> administration --> login window --> general tab

i changed the 'default session' to 'run xclient script'. 
[IMG]http://files.myopera.com/reincarnut/ubuntu/Screenshot-Login%20Window%20Preferences.jpg[/IMG]

(it had been earlier changed to 'gnome'. and yes, i had done it myself for some reason i don't remember :oops: )

lo and behold, things became normal. or so it seems. hope this might help someone out here... but don't ask me why or how it works. me no speek geek.

until next time!

---

### Post by angryfirelord on 2007-12-10
> **other guy said:**
> There are numerous entries where is shows the word kernel. Not being totally helpless... But not all that knowing. Where would I inject that statement? There is much more, for ease of reading. I trunicated it. I am assuming this is where you are referring to:

```

## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d96220e4-e268-4a40-bfed-e6be655329b7 ro quiet splash **[COLOR=Red]acpi=force[/COLOR]**
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d96220e4-e268-4a40-bfed-e6be655329b7 ro single **[COLOR=Red]acpi=force[/COLOR]**
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```Is this how it should look in the file?
Yes, that's exactly where they go, sorry for not making that clear. Although you don't need to put one on recovery mode since that's not the option you normally boot with.

Just try those two possible solutions I mentioned above and report back on what happens.

---

### Post by other guy on 2007-12-10
It's ok. :D A user has to think on his or her fingers.

I tried what the op did and my option was set to the one he suggested that worked in his case. In addition I did what you suggested. No go on any task I set for it.

I did do one thing. I depressed the power button and the machine did cycle a full power down(set in BIOS as a workaround for now.) While not an optimal solution it does work.  I would however like to find how to get this going. I am not fond of such a trivial issue effecting an install. I do however like a good puzzle.

I just find it odd. That Ubuntu will not go full shutdown even forcing it in the terminal, but XP will. My first real issue so far using Ubuntu that a simple switch or edit does not seem to fix.

Thank you anyone who is taking the time to assist me or others who may encounter this type of issue. I apologize to the op for butting in on your thread. I felt it was better to keep all related issues in one thread and make it easier for others later on. If they do a search and find this like I have.

---

### Post by reincarnut on 2007-12-11
> **reincarnut said:**
> hi folks. i seemed to have done something that seems to be working fine now - log out and shut down are working without problems, so far so good. tested it a few times too. i dunno if it makes sense, but this is what i did:

system --> administration --> login window --> general tab

i changed the 'default session' to 'run xclient script'. 

(it had been earlier changed to 'gnome'. and yes, i had done it myself for some reason i don't remember :oops: )

lo and behold, things became normal. or so it seems. hope this might help someone out here... but don't ask me why or how it works. me no speek geek.

until next time!

sorry, false alarm! my hylobatida has a mind of its own. it still doesn't log off.
hopefully evolution will help me out... eventually.:-?

---

### Post by Tea, anyone? on 2007-12-12
I've got a problem with this too.I've tried acpi=force both with and without pci=noacpi in both the kernel line and in open space, all with the same result. After the ubuntu splashscreen, descriptive text comes up:

Reading files needed to boot...
(Re)generating splash steps for: sed: can't read /etc/inittab: no such file or directory
Preparing restricted drivers....
Setting the system clock.
Starting basic networking....
Starting kernel event manager
Loading hardware drivers...

and it holds on loading the hardware drivers for some minutes before proceeding through some more stuff. When the desktop loads, everything is slow and sometimes there is a problem with the gnome panel.

acpi=off noapic has no effect on shutdown, but at least it doesn't affect startup either...

My kernel bit looks like:

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=86e07f63-6bd9-4364-a64b-ae7e08f575b4 ro quiet splash acpi=force
initrd /boot/initrd.img-2.6.22-14-generic
quiet

Computer is a Toshiba Satellite Pro 4300

Thanks in advance.

---

### Post by Het Irv on 2007-12-12
Have you checked the network manager.  I replaced mine with Wicd and it fixed the shutdown issue.  Somehow Network Manger was hanging on shutdown.

---

### Post by Tea, anyone? on 2007-12-12
No,  I've replaced network manager with wicd, but still the laptop won't shut down completely.  Same as before, the hard disc spins down and everything goes quiet, but the ubuntu splashscreen stays up after the orange br has fully disappeared.

Wicd is a better tool than network manager though.  Thanks for that pointer.

---

### Post by badccg on 2007-12-12
> **other guy said:**
> Bump for having the same issue.):P

The only alternative for me. Is to force it to power down while the machine is POSTing after a restart. By holding the power button in. Not very fun.

Nothing else works. That particular machine also has XP and it shuts down just fine under that.



hi,

I haven't seen anyone ask this yet.  Is your BIOS up-to-date to allow the OS to shutdown the hardware?


my 2 cents,
CC

---

### Post by Tea, anyone? on 2007-12-12
Yes, the computer shuts down fine under XP, and even in Ubuntu when I'm using acpi=force.  Trouble is the system is unuseable when I've included that.

---

### Post by other guy on 2007-12-12
> **badccg said:**
> hi,

I haven't seen anyone ask this yet.  Is your BIOS up-to-date to allow the OS to shutdown the hardware?


my 2 cents,
CC

Under XP the OS shuts down properly. I set the BIOS to allow power button shutdown as  temp fix. Not elegant, but holding the button in for 4 seconds. At least allows me to not have to do it after BIOS cycles. Sabayon  *does not *shut down correctly also..

It is a band new board and I updated it to the latest on the manufacturers page. Actually I tried a few variants to see if that was the issue prior to my first post.

---

### Post by Raventiger on 2007-12-12
I'm also having this issue. I only have ubuntu 7.10 on my laptop and it refuses to shutdown at all. I've tried adding the options to the kernel in grub but that didn't work. The bios seems only accessable from a custom program that came with it's windows xp professional image so I can't change any option in there. I am also unsure of how to update the bios or indeed what version the bios currently is.

Any help would be warmly appreciated.

---

### Post by other guy on 2007-12-13
The BIOS is lower than Windows or any OS. It stands for **B**asic** I**nput **O**utput **S**ystem. So you should be able to get to it with some keystroke. As it boots.

It can be the Delete,Insert or F#keys. 


If the machine shuts down correctly in the Microsoft kernel. I would assume it is not the BIOS in this case. Even though it cannot be ruled out.

I did boot an older kernel of another distro, not based off Debian.

I went in the CLi and did the shutdown -h now.. 
Still it restarted and not powered off. With what I have done so far. I set the power key on the workstation keyboard to use that. It passes the shutdown and such. Still it restarts. Even though  I can clearly read power down.


This is a tough one to send a bug tracker on. Since it is not just Ubuntu. I can replicate it, but it might be so localized. That any fixes are or will be tough, unless you're BKAC. My *nix skills are growing everyday, but not yet enough to where i can do BOFH type stuff. Windows yes. *nix no.

---

### Post by danwood76 on 2007-12-13
Out of interest if you boot into the recovery console and do a 'shutdown -P now' does it shutdown?

regards,
Danny

---

### Post by other guy on 2007-12-13
Myself, I have considered that and done it. Nothing happening with productive results. (refer to post 19,22 & 21.)

---

### Post by danwood76 on 2007-12-13
if you boot off the live cd does it shutdown?

I think there are some acpi/hardware problems that are not allowing the shutdown.
I have gutsy running on 4 different computers of various ages and never had these probloems.

---

### Post by other guy on 2007-12-13
I have never encountered this issue using Ubuntu on any hardware I asked it to run on. Matter of fact any kernel I asked hardware to run. Usually  I can correct it.

I have tried other Live distros. Gentoo based,Slack based and RPM based. All give poopies for me. This is why I haven't considered a bug tracker. It is a hardware issue and my weapon of choice is Ubuntu. it is not this distro's fault as I see it.

Though I would like to solve this puzzle. It works great under MS kernels. 
:-({|=

---

### Post by Lostincyberspace on 2007-12-13
Have you tried reinstalling? I know it is kind of extreme but it fixes a lot of problems.

---

### Post by other guy on 2007-12-13
> **Lostincyberspace said:**
> Have you tried reinstalling? I know it is kind of extreme but it fixes a lot of problems.


I have tried going back as far as my U collection will let me; 6.10. So it is a yes to your querry. I even tried other distros as a fix. Total no go for shutdown.. Even terminal shutdown with switches.

It is honestly an interesting issue to me. Not fun, but I will follow though.

---

### Post by Lostincyberspace on 2007-12-13
Have you tried updating your bios?

---

### Post by other guy on 2007-12-13
> **Lostincyberspace said:**
> Have you tried updating your bios?

Please refer to post #29. :KS

---

### Post by danwood76 on 2007-12-13
you could try recompiling the latest kernel with various acpi options, although this may just waste a lot of your time if it doesnt work.

---

### Post by other guy on 2007-12-13
I thought about going full Gentoo on it. Until I can get it knowingly going or at least a fix. I an not willing to take the time to gamble with a full compile with a Sempron LE-1100.

Keep in mind every bit of help I get is very much desired. New ground is best traveled with friends. This is something I have never encountered before.

---

### Post by Lostincyberspace on 2007-12-13
> **Lostincyberspace said:**
> Have you tried updating your bios?
In that case have you tried reverting the bios?

---

### Post by kvonb on 2007-12-13
-

---

### Post by other guy on 2007-12-13
Not an inkling of less of wires here.  I got a Linux based router and it is CAT6 lines, from all the machines. The distance  I need to cover is not worth the headache of wireless.

(My sneaker net is only like a 2 second latency.)

I only have workstations here, no portables.

---

### Post by raveyd on 2007-12-13
Thanks for all the responses - I've been trying all the suggested things and nothing worked. i've temporarily reverted to PClinuxOS. That powers down with no problems. Strange.

---

### Post by angryfirelord on 2007-12-13
> **raveyd said:**
> Thanks for all the responses - I've been trying all the suggested things and nothing worked. i've temporarily reverted to PClinuxOS. That powers down with no problems. Strange.
Ok, try this. Install the 2.6.22 kernel from the repositories and try shutting down with that.

---

### Post by Tea, anyone? on 2007-12-14
I've got 2.6.22-14 generic, but it doesn't do any good for me.  Would you recommend trying different kernels?

---

### Post by digitaria on 2007-12-20
> **Tea, anyone? said:**
> the hard disc spins down and everything goes quiet, but the ubuntu splashscreen stays up after the orange br has fully disappeared.


I seem to have the same issue.

I've been running 7.10 fine for a few weeks with this exception.  I have tried acpi=force, with and without pci=noacpi - and it makes no difference.  Haven't tried placing that directive in "open space" - I'll try that when I get home.

On system halt, you can hear the hard disks stop, but the splash screen remains, with the orange bar cleared as above.  Not only has this hardware shut down happily under Windoze, but it has shut down successfully under Mandrake 10.1.  So I don't think the BIOS is relevant here.

Hardware - Pentium III 500, 384mB RAM, MoBo A-Trend 6220M.  It's the only fly in my Ubuntu ointment. :(

TIA for any suggestions.

---

### Post by kvonb on 2007-12-29
-

.

---

### Post by l3th0x on 2008-01-06
Hi,

Try to hibernate, and several  messages (you have to wait a minute),  will tell you that it fail to set xfermode, then a "system halted" message will appear, and finally a "please power me down manually" will appear too, the press the power button, it will shut down.

I know that this is not a solution. but it is something.

Best Regards.

---

### Post by myke on 2008-01-07
BUMP BUMP BUMP

I'm also in the group having this problem.   I've tried a multitude of suggestions to fix the problem from folks on this board as well as the kubuntu forums.   I also downloaded a possible bug fix from the bug listings but it didn't work either.

I DEFINITELY think this is a BIG BUG.  And not just from Gutsy.   I clean installed Gutsy right after it first came out and have only started having this problem with some recent normal updates over the past 2 weeks or so.  Up until then and all the way back to Breezy, I've never had shutdown/restart problems.  

Now ... EVERY shutdown or restart goes thru the splash screen then blanks out causing me to have to hard shut down via the power button.    And yes, my bios is up to date and winxp shuts down fine.

I think this is simply a bug. Lots have reported the same problem in this thread and others as well as on the Kubuntu forums. 

For everyone I've read, it seems to not just have started with a Gutsy upgrade or install but after one of the periodic package updates.   

Just don't know which one caused the problem.

This needs to be reported as a serious nagging bug.   I'd do it myself but I don't know how and probably wouldn't explain it technically enough anyway.

---

### Post by kvonb on 2008-01-08
-

---

### Post by myke on 2008-01-08
> **kvonb said:**
> Try this: when you get the "black screen" wait a few seconds then press ctrl-alt-backspace to kill the x-server.

That worked for me, as it then went into reboot mode and I could power off during the system reset phase, saving me from disk-check errors each time.

The problem (as I later found out) was that something I installed (from the repos!!!) deleted everything in my shutdown folder (/etc/rc0.d).

Is yours empty too?

I agree there seems to be a LOT of obvious and major bugs in Kubuntu 7.10, it's a shame as I took this release as an opportunity to switch to Kubuntu from standard Ubuntu! 

Typical :rolleyes:.

Yes, it is quite the shame that this release is so buggy as it is the MOST buggy of the releases I've seen since Breezy.   I love Kubuntu, though, as I think KDE is simply a better desktop environment than Gnome (please don't flame me Gnome lovers).  I mean, you can't even move your toolbar icons around in the Gnome environment.   Of course, I use KDE but mix it with some quite fine GTK/Gnome based programs such as Synaptic and SoundJuicer.    

I'll have to look when I get home from work today to see if that shutdown folder is empty.  If it is, how do I get whatever is supposed to be there back??   What files are supposed to be there???   Could I boot up the live cd and copy that folder to my portable hard drive and use that or would it break something since there have been updates since then??

Maybe your idea will fix my problem.   All of the various other solutions I've seen posted on the boards have usually helped either shutdown or restart work more often but never both and never either one consistently.  

ANY MORE IDEAS PEOPLE???   Can someone file a bug on this if it isn't already there??  I don't know how.  I'll do it if someone will tell me how.  Clearly with so many folks experiencing the EXACT same issue, it's a bug and was not caused by the initial install/upgrade of Gutsy but by something updated along the way.

---

### Post by kvonb on 2008-01-08
-

---

### Post by Allan_Jones on 2008-01-09
Over the last few days I've installed Ubuntu 7.10 and Xubuntu 7.10 on an old laptop. My experience matches some of these here.With both Ububtu 7.10 and Xubuntu 7.10 the computer takes a long time to shut down. The screen goes blank reasonably quickly, but it takes about 2 minutes 30 seconds for the backlight to go offe.

Recently with Xubuntu 7.10, shutting down has launched the log-in page.

This is the first time I've put Linux on a machine. This shut-down problem is driving me back to Windows XP.

Allan

---

### Post by chris.simpson on 2008-01-12
I see I'm not alone with this problem. It's a nuisance but, since the hard disk spins down, there shouldn't be any lasting damage from having to manually power off each time. My /etc/rc0.d/ directory isn't empty, and it appears that the various other solutions suggested here haven't helped others, so I don't expect them to help me since my symptoms are identical to those most frequently reported (orange bar goes down to nothing, but ubuntu logo stays on screen). Any further ideas from those with more skill than me?

---

### Post by jerrylamos on 2008-01-12
This sounds like 
[https://bugs.launchpad.net/ubuntu/+bug/119308](https://bugs.launchpad.net/ubuntu/+bug/119308)
The fix posted there has worked for a number of us:

In applications, accessories, terminal do sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1
do sudo gedit /boot/grub/menu.lst (where the l is a lower case L). Find the first line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Restart, then try "Shutdown".   It should. Mine did.
Usual cautions apply when changing system files.....backup the file being changed, ...

Cheers, Jerry

---

### Post by mjezell on 2008-01-13
I've been having the same shutdown problem many have described in this thread.  Went to the above bug link and read through it and found a situation that I had done on my computer.  Because my system is a desktop, I assumed that I did not need the "Power Manager" running.  But from the bug post I found where another user who also disabled "System --> Preferences --> Sessions --> Power Manager" went back and enabled it, solving his problem.  I did the same and have not had it happen since.  Hope this helps someone.

---

### Post by Tea, anyone? on 2008-01-18
Hooray!  Hurrah! and Huzzars!  Thank you jerrylamos, that did just the job.  My venerable Toshiba Satellite Pro 4300 now shuts down completelywhen I ask it to.

To confirm what I did-

I first added apm power_off=1 to /etc/modules

Then added apm=power_off to /boot/grub/menu.lst (already had acpi=off)

I already had a few extra things in menu.lst fromprevious attempts to get this working - my system now works, so I'm leaving them all in.  In case it helpsanyone, here is what I've got:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=86e07f63-6bd9-4364-a64b-ae7e08f575b4 ro quiet splash noacpi acpi=off apm=on noapic apm=power_off
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

Hope this helps someone else.  I'm trying to think of anything else I might have done in the weks that this has been annoying me.  I'll post again if I do think of anyhting that might be relevant.

---

### Post by Nibes on 2008-01-21
Hello. I am kindda newbie to Ubuntu. I run it along with windows xp. And I have the same problem. after i click on quit, everthing goes ok until it freezes after the progress bar runs down. 
At first I thought "oops I messed things up while installing and uninstalling packages from synaptic manager" I did installed kubuntu Xubuntu and Ubuntu all in the same machine... just messing around. "Ok" I thought all my fault. "best thing to do: re-install ubuntu again!"
I did that "the re-install" after that ubuntu shutdowns properlly. hurray!! 
Then I noticed my nvidia card wasn't working and I decided to install the drivers to have all those cool stuff ubuntu does and xp doesn't. But then I got an akward "out of range" message everytime ubuntu starts up. no problems with the shutdown. I managed to bypass the login screen and the "out of range" ins't a problem anymore. but then the shutdown problem startd all over again. It isn't cool to shutdown the machine using the power button. 
So may the shutdown problem be related with nvidia drivers??

---

### Post by danwood76 on 2008-01-21
Yes it does sound like an nvidia driver (+ compiz?) issue from certain people, but obviously its different with each setup.
It sounds as if turning the apm (power management) off fixes the issue.

Ive not yet installed a system running an nvidia card so I cant really speak from expeiance but I have never had these issues with ati/intel cards/chipsets.

regards,
Danny

---

### Post by Nibes on 2008-01-22
Well, I did the operations above and I got this

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8c67c2c0-d1a3-4ee1-ba95-5ffd6d855f64 ro quiet splash locale=pt_PT acpi=off apm=power_off
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

after that i restart and the in the new session i did a shutdown but i bumped on the same problem. 

I will wait for more solutions to solve this problem. or a new update with this fixed. Meanwhile I will keep shuting down in the old way, really old way. pushing the button. 
I think I will paint it red. :)

---

### Post by danwood76 on 2008-01-22
If you disable the nvidia driver by editing the /etc/xorg.conf to use the vesa driver instead of nvidia do you get the same issue.

Im trying to work out if you are indeed having a problem caused by the nvidia driver or if it is unrelated.

regards,
Danny

---

### Post by Nibes on 2008-01-22
I started the sistem in recovery mode. I typed the root password and I got a command line. then I  did this " : sudo dpkg-reconfigure xserver-xorg" to acess a configuration menu  where I choose to use vesa driver instead of nvidia. "reboot"
Everything started, 
Then I order the shutdown and ubuntu 7.10 did shut down,

Now I wonder how can I get those cool 3D effects on? shall I try to reconfigure the xserver-xorg again but now with the nvidia driver... Will I get that "out of range" message again? fears of freedom. I will try. 
thank you Danny.

---

### Post by Nibes on 2008-01-23
hello again. 

Does Nvidia driver mess up the shut-down in ubuntu? yes it does.

how to solve the problem and keep the desktop effects on? I don't know. 

Is there a way to add a shut-down line in the "grub menu" so every time I want to shut-down I will restart the system and then I can choose the shut-down option instead of pushing the button?

---

### Post by danwood76 on 2008-01-23
Best thing to do is file a bug report with the nvidia team.
Then possibly give up on compiz unless you want the shutdown problem.

they will hopefully fix the issue with a later driver release.

regards,
Danny

---

### Post by Nibes on 2008-01-24
Hello again. finally it's fixed. Simple re-install of network manager did it. 
regards nibes

---

### Post by wildsnail on 2008-01-26
I have also had problems with shutting down kubuntu-gutsy-x86 since using envy to update my ati driver on my laptop. The solution from jerrylamos in post #57 seems to have sorted it for me - cheers,mate:KS

---

### Post by Diranda on 2008-01-28
Hello all,

I am having the same problem on my Toshiba Satellite laptop. I don't have an Nvidia graphics card, but I have had issues with Network Manager in the past with older versions of Ubuntu.

I can live without Compiz, so am going to take that off and see if the problem goes away.  I am also going to check and see if Nvidia drivers have been installed on this box and remove them if they are.  

For now, what I will try is to log out and drop to the login screen, and shutdown from there.

I love this new version of Ubuntu, but this shutdown problem bugs me.

Cheers,
Diranda:KS

---

