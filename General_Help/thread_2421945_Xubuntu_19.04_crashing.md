---
title: "Xubuntu 19.04 crashing"
date: 2019-06-29
forum: General Help
---

### Post by peyre on 2019-06-29
I'm running 19.04 64-bit on my desktop, but it's become unstable.  It crashes frequently, and I don't know what's causing it.  For a while I thought it was Firefox, but recently it's been crashing when Firefox hadn't even been opened.  I'll be in the middle of doing something, and the computer just stops responding.  Audacious continues playing music and the mouse moves, but nothing responds to mouse or keyboard.

The only consistent thing I've noticed has been happening this morning.  Samba seems to be crashing - I've been trying to move some ISOs from my wife's Win10 machine, but it never completes.  Sometimes it freezes when I right-click: it brings up the right-click menu and stops responding; more often it stops somewhere in the middle of the copy operation.  Good thing this box has a reset button 'cause it's gotten a lot of use today.

I opened Synaptic and reinstalled everything a search for **samba** brought up, then tried again with the same result.  Anyone have any suggestions?

_Computer details:_
Ibex 5015 Barebone System
Intel E2180 Pentium Dual Core 2.0GHz
256MB SSD
1TB drive for storage
4GB RAM

---

### Post by Autodave on 2019-06-29
Someone else will come along and ask you for error logs, but let me offer what I know.  Are you sure that it is not overheating?  Fans working and clean?  Maybe try running it with the case cover removed.

Since USB sticks, mouse, and keyboard all use the 5V live, are you sure that you don't have too many USB devices connected?  You could be drawing the 5V line too low either from the power supply being weak and/or failing.

---

### Post by peyre on 2019-06-29
It shouldn't be overheated.  I opened and dusted it out a few weeks ago, and the fan is running quietly and I can feel it blowing out warm-ish air in back.

The only USB devices I have attached right now are mouse & keyboard.  I also had a flash drive plugged in earlier, but that was it.  Half (2) of my rear USB ports have nothing plugged in.

---

### Post by kurt18947 on 2019-06-30
I've had similar symptoms but I think I know the cause. I think it was related to the video on Ryzen APUs. I've been running a few years old ATI/AMD video card because the video hardware in the Ryzen was not supported by Ubuntu. Recently I removed the ATI/AMD card and tried the onboard video. It did work but I had a couple incidents where the desktop video seemed frozen but the mouse pointer moved so it wasn't totally frozen. CTL-ALT-Delete didn't work, neither did CTRL-F1. I reinstalled the old video card and no more lockups. Have you made any changes to hardware or drivers?

---

### Post by peyre on 2019-06-30
The only change in hardware has been that I hooked up an old parallel Zip drive because the ATAPI one is starting to die.  That meant setting /etc/modules to load ppa and imm.

(Yes, this system is old enough to have a built-in parallel port.)
(And yes, I still use zip disks.  I'm always taking small files between home and work, and a physical disk in my work bag when I get home reminds me to retrieve them.  If I put them on flash drive I'd forget most of the time.)

---

### Post by peyre on 2019-06-30
Hm, I disconnected the parallel zip drive and rebooted, and it did the same thing copying from the ATAPI drive.  I've remmed out the imm line in /etc/modules, rebooted, and it still freezes during a copy operation.  Copy/move operations seem to be causing this thing to freeze.

Too bad there isn't an equivalent to sfc /scannow.

---

### Post by peyre on 2019-06-30
And now it crashed just opening my secondary hard drive in Thunar.  What gives?

---

### Post by chrispeddler on 2019-06-30
Have you tried reinstall your Zubuntu? Maybe a clean install might do. If so, and prob still exist, maybe you can try using the old but more stable version (18.04).

---

### Post by peyre on 2019-07-01
Ugh, I did that recently for a different issue I was having.  I could do it again, but I hesitate to go to all that trouble on a "see if this fixes it" kind of basis.  Reinstalling on my laptop isn't a big deal, but on my desktop it's a real production.

---

### Post by peyre on 2019-07-15
(Had to travel cross country so there was a delay moving on this one.)  So this past weekend I backed up my data and reinstalled Xubuntu from scratch, 18.04 LTS this time, and that seems to have resolved the issue.  I've been able to copy whole ISOs over the network without any trouble.  I must say I'm disappointed though, that I should have to resort to an entire wipe and reinstall for something like this.  It would be a big help if there were some equivalent to **sfc /scannow** in Ubuntu.

---

### Post by peyre on 2020-01-04
**Note: what I did in my post above did not fix this.**  The crashes continued.  I finally fixed this about a week ago.

Seems this wasn't a software issue as such - I had a device connected, an old ATAPI Zip drive, which was dying.  I pulled it out, and the lockups stopped, just like that.  So this was a hardware issue.

---

### Post by peyre on 2020-01-15
No sooner did I mark this solved but the crashes started to recur.  It's odd - the screen I'm in suddenly starts to get jumpy, then I look down and see my hard drive light is pegged, or close to it.  Whatever is running still kind of runs (video or audio plays in bits) but I'm unable to close any windows to help it shut down gracefully or **stop the application that's causing the slowdown**, even if I continuously click-click-click the X to try to close it.  Eventually I have to hit Reset, hold down the Power button, or pull the plug.  Then it starts normally again, but for how long I can only guess.

---

### Post by CelticWarrior on 2020-01-15
Something else is dying in your old system. Very likely it's the HDD.

---

### Post by peyre on 2020-01-15
Oh man!!  That thing has a good (though not exactly new) SSD, plus a 1TB HDD for storage.  I'd hate to have to replace either of them, but that's extra reason to make sure I have a good backup done.  What do you recommend I do to check them, boot with a Xubuntu DVD and fsck the drives?

---

### Post by CelticWarrior on 2020-01-15
You can use Disks to check the SMART values while running the OS. That alone should give an accurate drive health information.

---

### Post by peyre on 2020-01-15
Oh yes, of course!  Should've thought of that.  Thanks!

Any other pointers, if I can't seem to find anything with the disks?

---

### Post by peyre on 2020-01-16
Hm, so far (not) so good.  I ran an extended test on the SSD (the system disk) and everything came out OK.  In particular, Reallocated sector count reads 0.

Then again, as I understand it, SMART data is liable to give false negatives.

I'm running an extended test on the HDD now.

Edit: The HDD also checks out.  So, is there anything else you'd suggest I take a look at?

---

### Post by peyre on 2020-01-20
It seems to happen most often when I'm either surfing in Firefox, or navigating my file system in Thunar.  There's no prior indication of trouble; it just suddenly stops responding to mouse clicks.  Usually I'm able to move the mouse around, but I can't close anything.  Other times it just freezes up.  When I can move the mouse, it becomes jumpy.  And often it runs the hard drive hard, but sometimes the HD light is quiet.  In any case the only way out is to hit the Reset button or do a hard power-off.

---

### Post by CatKiller on 2020-01-20
That *symptom* - being able to move the cursor but not click on anything - is just because the window manager has got confused.

The underlying *cause* could be any number of things; electromigration in the processor or some other chip, swollen/failing capacitors on the motherboard, failing RAM, failing hard drive, failing power supply, intermittent connection, any of that kind of stuff. Data (charge, really) goes through a *lot* of parts before it gets where it needs to be, and any of them being wonky will cause issues. Fundamentally you're expecting one number but you get a different one, and then your system has no idea what to do next. 

All electronic components have a finite realistic lifespan. Some die quickly, some die slowly, but they all die in the end.

---

### Post by peyre on 2020-01-21
Ah, I was afraid of that.  I bought this machine back in 2009, so it's not surprising that it may be simply wearing out.  Might be time to start looking for a replacement.

---

### Post by peyre on 2020-01-30
I finally did it, switched my hard drives and video card over to a newer computer, and . . . the hanging issue is continuing.

So I've removed my video card (it is kind of old, but it was a good one for its time so I figured probably better than onboard Intel from 5 years ago).  We'll see if the hanging stops.

---

### Post by peyre on 2020-02-02
*[objectionable acronym]*  Still having trouble.

I thought my graphics card might have been the problem, since the disks return good SMART data, and when I pulled it out of my old computer to put in the new one, it did have quite a bit of dust in the fan and heatsink (not caked, but still kind of bad).  So I pulled the card out and started using the onboard Intel graphics.  Trouble with that is that I can't seem to use both monitors at once.  The BIOS shows an option for multi-display and it's enabled, but I think the signal won't reach - it's an analog monitor so an analog cable, connected to a VGA-DMI adapter to a DMI-HDMI adapter into the back of the computer.  Oh well, it was worth a try.

I still wanted both monitors, so I plugged in an old basic PCI-e graphics card I had sitting around.  Now I had both monitors again, but again I was experiencing intermittent freezing of the computer, just like before.  I'm running out of ideas here folks!  The only things I haven't changed out are the hard drives plus the mouse, keyboard, and monitors.  I don't know what else to do.

---

### Post by mastercore on 2020-02-09
I want to add my case in here since its related.
Just built a new computer and decided it was time to leave windows world. I only have 2-3 apps that do not exist on Linux so I thought I could just run them in a virtual machine in Linux.
I first loaded Ubuntu 18.04 but there were problems with display which got solved by loading Ubuntu 19.10. This is what I have running at the moment.

The machine specs are:
```
[COLOR=#000000][FONT=Arial]Gigabyte B450 Gaming X - motherboard[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]AMD RYZEN 7 1800X - chipset[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Crucial 32GB KIT(16GBX2) DDR4 2400 MT - RAM[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sapphire Radeon RX 5700 XT Nitro+ (8GB) - GPU[/FONT][/COLOR]
```

*inxi F *output is:
```
CPU~8 core AMD Ryzen 7 1800X Eight-Core (-MT-MCP-) speed/max~1868/3600 MHz Kernel~5.0.0-23-generic x86_64 Up~34 min Mem~1514.6/32174.4MB HDD~500.1GB(1.3% used) Procs~389 Client~Shell inxi~2.3.56
```

PROBLEM:
Just like @peyre said, I get spontaneous freezes of the OS. Often the mouse moves around, but no clicking and the system does not recognise the location of the mouse. i.e. mouseovers in the browser do not respond. Also no keyboard responce.
I tried to disconnect and reconnect the mouse and the keyboard (wirless units running off one pickup (logiteck MK700/MK710) but that makes no difference.
The only thing I can do at that point is to restart. (Luckily the system restarts super fast)[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=794216")

I have to look into what @autodave suggested. During the build I decided to wire up my old PSU which is only 550W. I have not tested heat in the box but I recon power will be frugal.
I will leave this post as is and hope my input helps the others (and me) to solve this problem.

I found an older but more powerful power supply that does not fit into my computer case, but one that I could jerry rig to test this thesis out.
I will try to remember to update this thread if I find the freezing problem changes...

---

### Post by peyre on 2020-02-12
Thanks for adding your situation, Mastercore.  FYI, I'm currently borrowing another graphics card, and so far I don't seem to be having hanging issues (unless I just jinxed it by saying so).

---

### Post by mastercore on 2020-02-12
This is day 2 of no crashes.
Seems like power was the cause
Today I installed a 750w PSU and all is well in the world

---

### Post by peyre on 2020-02-13
Well in my case I don't know what's doing it.  My computer just froze up again.  It seems to be happening less often with this borrowed card (though it's still happening!), but I don't know that's in fact the case - it might just seem that way.  I'm reaching my wits' end here...I've changed out the entire computer apart from hard drives and peripherals, yet the problem persists.

---

### Post by peyre on 2020-02-15
Another crash?  In the middle of a last-minute backup?  This is messed up.

I like (X)ubuntu, I really do.  But if my system is going to continue locking up on me at unpredictable times, I might have to think twice about this.  Seriously, I've replaced almost the whole system.  Windows 10 doesn't start mess with the mouse cursor and refuse to respond to mouse clicks or keyboard commands until I do a hard shutdown.  I've already lost data from this.  I never thought I'd say this about Ubuntu, but I just want it to *work* reliably.

---

### Post by peyre on 2020-02-23
Strange, I think it's been doing something different with this hard drive.  I thought it was crashing the OS and rebooting it, but now I've twice seen it log me out and bring me to the login screen.  I then have to reopen things.  Worse, it kills my backup jobs in progress.  Any suggestions, anyone?

---

### Post by peyre on 2020-02-23
Oh, and it's *also* been locking up as well.  I don't know what to do!

---

### Post by peyre on 2020-02-25
***Hang on a minute***, I think the backups might be the problem . . . it seems to happen *while I'm running one*, come to think of it.  I can't think why, though; it's just a shell script using rm, mv, and cp commands like 
```
rm -r -f /media/leon/BackupDrive/LeonOld
mv /media/leon/BackupDrive/Leon /media/leon/BackupDrive/LeonOld
cp -r -f ~/*.* /media/leon/BackupDrive/home/
cp -r -f /mnt/Storage/Data /media/leon/BackupDrive/Leon/Data
cp -r -f /mnt/Storage/Graphics /media/leon/BackupDrive/Leon
```
I've been hooking it up to the new computer's USB3 ports; I don't get it.

---

### Post by peyre on 2020-02-28
And now it just crashed on me again, shortly after startup and login . . . and I didn't even have a portable drive attached, much less backing up to it at the time.  What in the Sam Hill is going on?!?!

And now **AGAIN**, within a half hour of last time?  This is crazy.

And now three times in one evening?  And all I was doing was playing MP3s and editing a text file.  This is getting repetitive.

---

### Post by ronkey on 2020-02-29
> **chrispeddler said:**
> Have you tried reinstall your Zubuntu? Maybe a clean install might do. If so, and prob still exist, maybe you can try using the old but more stable version (18.04).

thanks its works[.]("https://instantpva.com/instagram-pva-accounts/")

---

### Post by peyre on 2020-03-05
I'm glad it worked for you ronkey.  I tried it myself without success.  I even went to the LTS and it's still crashing on me and also logging me off seemingly at random.  Just now it crashed on me twice in quick succession.  If this were my laptop I'd happily try reinstalling from scratch again, but doing that on my desktop is a big deal.  I have a *lot* of customizations on my desktop machine, making a reinstall from scratch a big deal and not something to try on a "well, maybe it'll work this time" basis.

Edit: today it's crashed on me twice *and* logged me off without warning once.

Edit: two more crashes.

And two more following lunch.  So my total for the day was 6 crashes and a spontaneous logoff.  With an operating system that prides itself on its stability.  Come on, *Windows 95* was more stable than this!

---

