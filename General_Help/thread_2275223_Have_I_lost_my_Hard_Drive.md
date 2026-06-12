---
title: "Have I lost my Hard Drive?"
date: 2015-04-24
forum: General Help
---

### Post by nu2this2 on 2015-04-24
As has been seen in my recent two threads I have been attempting to install an update of Ubuntu. Firstly, I was able to install 10.10 from a live CD and that went well however I found  that there was no way that I could do an update. Then I tried to install 14.04.02 and that attempt worked when using the "Try Ubuntu" on the live CD but failed when I Tried to install it on my HD. A message appeared Stating that perhaps I should clean the DVD and use a compact disc laser lens cleaner. I inserted the lens cleaner disc in the CD drive but nothing happened. Had to shut down by using the on/off button. I put back the live CD and tried again. This time I chose erase HD and install. During that installation, during the copying files phase, after about 80% thru the process the computer would freeze up, the mouse became unresponsive and the only way to shut down was to use the on/off button. I tried again and all I have now is a blinking cursor in the upper left corner.

Might I have ruined the HD?

---

### Post by oldos2er on 2015-04-24
Could you please list your hardware specs?

---

### Post by pmi2 on 2015-04-25
> **nu2this2 said:**
> ...Might I have ruined the HD?Based on what you wrote previously, probably not.  It passed a disk check earlier, correct (?)

On the other hand, since the laptop is older, so is the optical drive, and there is a good chance it is not reading your installation media completely.  This is fairly common with older DVD drives, as they get old, they start to fail on some DVDs.

If you still suspect the hard drive is bad, (and if you can verify that the DVD drive is working, using a different media than your install disk), then there are various ways of testing it using programs that boot from a CD or DVD.

---

### Post by nu2this2 on 2015-04-25
Thank you for the input.

 Looks like the HD is operational but I'm still having problems. Was able to burn the iso for Version 14.04.2LTS. During the retrieving files phase of the install, the process seemed to come to a standstill at file 10 of 49. I waited and waited for progress but nothing happened. I clicked the "skip" button and immediately saw information appear in a previously blank area regarding the installation process. There were numerous notations such as Source ID 9653 was not found when attempting to remove it, Queue failed to flush, and various kernels also failing to flush.

The progress is advancing however at a very slow rate. This has been going on now for about 45 min or so. Since there are only 10 files remaining I think I will just wait it out. As an aside, What is the "skip" button do?

Thank you,

---

### Post by nu2this2 on 2015-04-25
Well something happened. Message appeared.
Installer crashed. Were sorry; the installer crashed. after closing the window you can file a bug report etc etc. Don't really know what to do next.

Update; Just saw this on the screen. "The problem cannot be reported. This is not an official Ubuntu package. Please remove any third party package and try again.
I'm really confused now, and I don't have a clue as to how to follow this instruction. This really a bummer!!

---

### Post by dragonfly41 on 2015-04-25
You have not answered the earlier question ..

> Could you please list your hardware specs?

If you look in your PC/laptop BIOS can you boot from USB?

If yes, I would create a LiveUSB (on some other PC perhaps using unetbootin).

This is sometimes more reliable than old DVD for live Ubuntu.

---

### Post by nu2this2 on 2015-04-25
Thank you,
I have checked the BIOS and do have the option to boot from a USB storage stick.
I'm not familiar   with unetbootin what is it?

---

### Post by dragonfly41 on 2015-04-25
unetbootin is a small app you can download to run on either Windows, Linux or Mac to burn a LiveUSB.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by dino99 on 2015-04-25
easy ways to do installation without 'burning'
[http://ubuntuforums.org/showthread.php?t=2275300&p=13272156#post13272156](http://ubuntuforums.org/showthread.php?t=2275300&p=13272156#post13272156)

---

### Post by buzzingrobot on 2015-04-25
Dunno if your DVD burning tool allows adjusting the speed, but, if it does, try setting at the lowest level.

Cancelling an in-progress install seems like a way to get a bad install, a bit of a throw of the dice, as does skipping something.  It's possible, of course, that the mirror was very slow.  At the beginning of the install process you'll see options to download updates and some proprietary packages during the install.  Those can be left unchecked if bandwidth or slow mirrors are issues.  Updates can be done (and should be) after a successful install, and the proprietary codecs, etc. acquired by installing the ubuntu-restricted-extras package.

---

### Post by nu2this2 on 2015-04-25
Hello again,

Much to my surprise 14.04.2 is installed on my HD but because it is very slow and sluggish I can't really use it. I downloaded, burned and verified this version from the official Ubuntu website so I am confused as to why the message this is not an official Ubuntu package.

---

### Post by Bashing-om on 2015-04-25
nu2this2; 3rd time:

What are your hardware specs ?
Takes some hosses now-a-days to run the top of the line ubuntu edition.
Might try a lighter sister ? Say (L)ubuntu ? If old hardware here is the issue.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT][INDENT]if you do not say
[INDENT][INDENT][INDENT][INDENT]we can not say
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by buzzingrobot on 2015-04-25
Without knowing your hardware specs, suggestions are impossible. Inadequate RAM, inadequate video card and/or inappropriate driver, faulty install, swap misconfiguration, etc., might be at play.

---

### Post by nu2this2 on 2015-04-25
Sorry but I don't really know how to find out what the specs are.

---

### Post by buzzingrobot on 2015-04-25
No problem.  Click on the cog icon at the far right of the top panel.  In the menu that drops down, click on "System Settings". Within Settings, click on "Details". That will display some basic information about your hardware.

---

### Post by nu2this2 on 2015-04-25
Great!! Thank you.

Memory 1.4
Processor Mobile AMD Sempron(tm) Processor 3300+
Graphics Gallium 0.4 on ATI RS480
OS type 32-bit
Disc 77.1 GB

---

### Post by Bashing-om on 2015-04-25
nu2this2; Hey hey ...

Now we are cooking with Crisco .

OK; this:
> 
Processor Mobile AMD Sempron(tm) Processor 3300+

says you do not have the horse power to run ubuntu --- My Wife's old graphics station had that same same processor .. ran 10.04 great .. 12.04 .. way to laggy ..
I did install (L)ubuntu, and it did perform admirably.

[INDENT][INDENT][INDENT]so, Who ya gonna call
[/INDENT][/INDENT][/INDENT]

---

### Post by buzzingrobot on 2015-04-25
Have to agree with Bashing-om, unfortunately.Google says that's hardware from 10-11 years ago. Ubuntu Unity isn't going to perform adequately on it. 

Take a look at Lubuntu ([http://lubuntu.net/](http://lubuntu.net/)), an Ubuntu derivation that's intended to have fewer resource demands. Burn an install image to a USB stick and test it in live mode. (Or a DVD, but live mode off a DVD is pretty slow.)

I suspect the video chip may be the real limiting factor, though.  I've no idea if an adequate driver, open source or proprietary, is available for it.  AMD/ATI did drop support for a considerable number of older chips a while back.

---

### Post by nu2this2 on 2015-04-25
Thanks to both you guys.

Well darn. I do have 10.10 on a live CD and was able to install it on my laptop. I took it off though when I tried to view a you tube vid and got a message saying I needed to update my browser, I couldn't find a way to update firefox so that's when I started looking for a later version of Ubuntu. Is there a way to update it?

---

### Post by Bashing-om on 2015-04-25
nu2this2; Welp;;

Short answer is no .. not on that hardware.
Do a clean fresh install of lubuntu and be happy .
And as buzzingrobot notes, you must run the open source graphics driver .. AMD dropped support for that graphics card.

[INDENT][INDENT]not so much that the bear talks so well
[INDENT][INDENT][INDENT]but that the bear talks at all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-25
;)Gotcha,

I'll do that. Thanks so very much for the help. I'll give it a shot and hopefully will be able to post** Problem solved!**;)

---

### Post by mörgæs on 2015-04-26
In addition you should use the solved flag (in Thread Tools) for this and the other threads.

---

### Post by jimmy-frydkaer on 2015-04-26
If your computer is an older model the computer does not have a lot of resources and you need to make the install according to that fact.

Insert your Ubuntu disk in the optical drive and let the computer boot up on the live cd/dvd

when you see the Ubuntu logo, and a square field at the bottom of your screen in the midst you press the ESC key on your keyboard.

The screen will change and now you hit the F6 key and find a point saying "nomodeset" - Mark that and hit the space key. A mark will show that you've picked that mode. 

Hit the ESC key again and then hit the Enter key.

Your install should now go all the way.

DO NOT MARK "Download updates while installing" AND DO NOT MARK "Third party packages"

Updates and third party software is not good while installing Ubuntu on computers with limited resources. You can install those when the install is up and running.

---

### Post by nu2this2 on 2015-04-26
Hello again,
Thanks to jimmy-f. Tried that, didn't work. Never saw a square field at the bottom of the screen.

For some reason I cannot complete the installation. The wifi connects and then suddenly disconnects.

---

### Post by jimmy-frydkaer on 2015-04-26
Just hit the ESC key at the very first screen you see

---

### Post by mörgæs on 2015-04-26
[http://ubuntuforums.org/showthread.php?t=2275135&p=13271559&viewfull=1#post13271559](http://ubuntuforums.org/showthread.php?t=2275135&p=13271559&viewfull=1#post13271559)

---

### Post by nu2this2 on 2015-04-26
Hello,
Was finally able to install but with many glitches, for some reason the wifi connection keeps disconnecting, have message of incomplete language support. All activity seems very slow and lagging. Really don't know what's happening.

Also, wifi doesn't appear as though it even sees my network.

---

### Post by Bashing-om on 2015-04-26
nu2this2; Hey, Hey ...

Do you have access to a wired internet connection ?

With the machine connected wired, one can complete the install/updates and then install the drivers for WIFI .

[INDENT][INDENT]where there is a will
[INDENT][INDENT][INDENT][INDENT]there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-26
Hi there,

I could connect an Ethernet cable to the modem. I don't know why this is happening. The wifi is working perfectly on both my desktop and my wife' laptop. I have never had this happen before. 

I'll give it a try when I get back from lunch. 

I want to say I really appreciate the effort you folks are going to in trying to help me;);)

---

### Post by nu2this2 on 2015-04-27
Hello,

I was able to hardwire the laptop thru an Ethernet cable, during the process the question was asked do I wish to connect to a wireless network. Since I was already connected to a modem I assumed that I was connected, so answered no and proceeded with the installation. Once completed a restart was required. The restart could not be done with the mouse. Had to do a hard stop. Then error messages showed up, I/O error, dev sro, sector 320380, SQUASHFS error,read_data_failed to read block OX9593b82 etc. etc.

I shut down the laptop and restarted. The program began but said "Incomplete language support" go to settings-lang support. I then connected to my wireless network but was disconnected over and over again. This happened before  when I tried to install this version. I have other versions  and even though they are slow, sluggish or freeze up, I am ale to access the internet and not be disconnected ever!

I'm beginning to think that I'm not going to be able to install any version of Ubuntu.
What do you folks think?

---

### Post by pmi2 on 2015-04-27
Using wi-fi may require downloading drivers that may have been skipped when you answered "no" to the q. above, or some other extra steps.

If you started the installation process using a hard-wired Ethernet connection, then I think it would be best to complete the installation that way also.  Then reboot, login, and let the OS download any automatic updates, reboot again, login again, make sure you can access the Internet using a browser etc.  

If everything works correctly using a hardwired cable connection, only then try wi-fi.  (my 2 c worth)

---

### Post by Bashing-om on 2015-04-27
nu2this2; Welp;

Nope, I am a firm believer of (l)ubuntu for older hardware . I have seen the proof many times.

So, what release/version did you try and install ?
lubuntu desktop standard install ?
this:
> 
I/O error, dev sro, sector 320380, SQUASHFS error,read_data_failed ......

make me question the integrity of that install medium.

Before we do any thing else, verify that burn:
standard install liveDVD:
Boot the liveDVD and as soon as the bios screen clears depress and hold the right -shift- key -> language screen; escape key to accept the default -> boot options screen.
Choose the " check disk for defects" option .. takes a while to run and complete ->
what results ?
If that test is good, then we run a check on the installed file system
if that check is good then
we connect to a wired connection and complete the install .

[INDENT][INDENT]that is just what I think
[/INDENT][/INDENT]

---

### Post by pmi2 on 2015-04-27
> **Bashing-om said:**
> ...Before we do any thing else, verify that burn...From the earlier posts, I think the CD/DVD drive on this older machine may not be working 100%.  

If so, even a perfect DVD will not install reliably.  This is based on my experience with older hardware, including a couple older DVD drives which I own, and which work fine for playing media, but not for installation or live CD use.  The symptoms are very similar to mine.  This would not be a Ubuntu v. something-else issue, no OS would install correctly except by accident under those conditions.

There was a suggestion to boot from USB stick, but it got buried someplace above.  I would go with that at this point.

+1 on the older hardware, and, the thread about bringing older hardware back to life (linked somewhere above) was very helpful to me personally.  Thanks to that, I was able to get some of my collection of antiques up and running various versions of Ubuntu and Linux Mint.

However, old DVD drives may not be worth saving, not like other older components.  

You have to think of rotating drives and media as a wear-out item.  A 20-year-old car may be worth saving, but 20-year-old brakes and wheel bearings - not so much  ;)

---

### Post by buzzingrobot on 2015-04-27
You're attempting to install with a DVD, right?  The /dev/sr0 refers to the CD/DVD drive and "SQUASHFS" is the compressed file system used in the live mode install images. The I/O error, failed to read block.., etc., might indicate a bad burn or a faulty image, or a bad/dirty DVD.

---

### Post by nu2this2 on 2015-04-27
> **Bashing-om said:**
> nu2this2; Welp;

Nope, I am a firm believer of (l)ubuntu for older hardware . I have seen the proof many times.

So, what release/version did you try and install ?
lubuntu desktop standard install ?
this:

make me question the integrity of that install medium.

Before we do any thing else, verify that burn:
standard install liveDVD:
Boot the liveDVD and as soon as the bios screen clears depress and hold the right -shift- key -> language screen; escape key to accept the default -> boot options screen.
Choose the " check disk for defects" option .. takes a while to run and complete ->
what results ?
If that test is good, then we run a check on the installed file system
if that check is good then
we connect to a wired connection and complete the install .

[INDENT][INDENT]that is just what I think
[/INDENT][/INDENT]

Ran the check and no errors were found
The version I downloaded is-----------Lubuntu- 15.04- desktop-386.iso

---

### Post by Bashing-om on 2015-04-27
nu2this2; Well then;

I get my feet wet with 15.04 - I have not yet installed it and have not 'seen' it.
On a wired internet connection, boot lubuntu - reset in bios to boot the hard drive as 1st boot priority .
Boot to a terminal and execute:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
post these outputs, and we see where we go from here .

[INDENT][INDENT]forward, backward or sideways
[INDENT][INDENT][INDENT]we will "getter done"
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-27
> **Bashing-om said:**
> nu2this2; Well then;

I get my feet wet with 15.04 - I have not yet installed it and have not 'seen' it.
On a wired internet connection, boot lubuntu - reset in bios to boot the hard drive as 1st boot priority .
Boot to a terminal and execute:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
post these outputs, and we see where we go from here .

[INDENT][INDENT]forward, backward or sideways
[INDENT][INDENT][INDENT]we will "getter done"
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

How do I boot to a terminal, Thanks.

---

### Post by Bashing-om on 2015-04-27
nu2this2; Hey;

Let's do this the sure way - there are others; Boot to a terminal from grub's boot menu;

Boot to grub, and press the 'e' key for edit mode -> boot options screen;
Arrow down and across to the terms "quiet splash" in the line similar "linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff" and replace these terms with the term 'text' with out the quotes;
key combo ctl+x to continue the boot process to TTY1.
Log in here with user name and password - there will be no response to the screen when password is entered, enter the password blindly and hit the enter key.
Now enter the terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```


[INDENT][INDENT]simple is better
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-27
Sorry for the ignorance but I don't know how to boot to Grub. Please explain what to do.

Thanks

---

### Post by Bashing-om on 2015-04-27
nu2this2; My Apologies ..

I had not considered your new to ubuntu and that a single install 'buntu will not display the grub menu .
So back up on tic -> grub boot menu.

Boot the lubuntu  install and as soon as the bios screen clears, depress and hold the right -shift- key .
lubuntu's boot menu should now present it's self.

[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-28
Hello, 
Sorry, didn't work. The screen went to the language page and began counting down seconds. Never got to Grub boot menu.

---

### Post by Bashing-om on 2015-04-28
nu2this2; Yak ...

No sorry about it ... we are just struggling through, trying to get you a working lubuntu install.
This:
> 
The screen went to the language page 

indicates to me that you were booting the liveDVD rather than the install.

Let's back up and regroup; Have you not to this time been able to boot to the desk top in that liveDVD ?
Have you been able to complete the install to your hard drive ? ( easily checked from booting the liveDVD and check and see what is installed. )

We need to be on the same page and communicating from a common reference point ,,, Either booting the liveDVD OR booting the install. One or the other, they are mutually  exclusive.
The 1st step is to boot that liveDVD; verifying what works and where there might be a problem. Then install.
In that install there is a procedure I follow to make it happen in such a way to know what is going on. ( I have done this a few times on old hardware) .

All a matter of establishing that reference point, so we can look out
[INDENT][INDENT][INDENT]see what needs to be done

[INDENT][INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-28
Bashing- Om,

Thank you for your patience and continuing help I really appreciate it. Gonna have to wait a bit before going forward though. Been informed I have some honey doooose to do for wifey. Gotta keep'er happy. Be back when I can.

---

### Post by nu2this2 on 2015-04-28
I'm back at it.
After rereading your instructions, I can report this. With the liveDVD in the optical drive I booted up.After depressing and holding  the rt. shift key after the bios cleared, the language screen appeared. I then pressed the esc key . The screen then offered the following options.
1. Try Lubuntu without installing.
2. Install lubuntu.
3. Check disc for defects. I have done this and no errors were found.
4. Test memory.
5. Boot from first hard disk.

Those were the only options.

Lunbutu is on my hard drive as I have previously posted however with many errors.

---

### Post by Bashing-om on 2015-04-28
nu2this2; Good deal;

We are assured the install medium is good and valid.

So next is to see that status of the installed operating system.
my post #38 refers .. but in small steps .

Reset in bios such that the hard drive has 1st boot priority;
Boot the system
Now as soon as the bios screen clears depress and hold the right -shift- key
Do you now see the grub boot menu screen ?

Yes ? -> we want to now edit the boot parameters:
press the 'e' key for edit mode -> boot parameters screen;
in this screen arrow down  to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " arrow across to "quiet splash" replace these terms with the term 'text' - without the quotes ;
key combo ctl+x to continue the boot process to TTY1 .
Can you log into the system here with your username and pass word ?

You get to this point then next is to update/upgrade the system.
and we then address:
> 
Lunbutu is on my hard drive as I have previously posted however with many errors.


[INDENT][INDENT]even with small steps
[INDENT][INDENT][INDENT]even the longest journey can end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-28
Do I do this with  the dvd in the drive?

---

### Post by nu2this2 on 2015-04-28
I,m not sure if I am at the grub menu. At the top of the screen is GNU GRUB ver 2.02 beta2 -22 ubuntu1

At the bottom of the screen are various sentences such as Minimum Emacs  like screen editing is supported etc. At the bottom screen it mentions  CTRL-c F2 for a command line. AmI at the right place?

---

### Post by Bashing-om on 2015-04-28
nu2this2; Yepper;

You are at the right place .. in the menu is something like:
*ubuntu on /dev/sda1  -- or some such

with this option selected ( arrow keys to move from one choice to another )
depress the 'e' key .

Now the screen changes to that of the boot parameters screen .
Make the edit and let us know what results .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-28
Well unfortunately  I don't see anything like that, what's more  my arrow keys are not functional. Just to be clear my DVD is not in the drive. Also, the only choices given me are Press ctrl-x or F10 to boot, ctrl-c or F-2 for a command- line or ESC to discard edits and return to the Grub menu.

---

### Post by Bashing-om on 2015-04-28
nu2this2; Humm ... 

sounds to me like you are at that "grub boot parameters" screen .
And yes the DVD removed from the DVD drive is correct.

Be aware I have not seen 15.04 to this time .. I do know that the boot sequence is changed and that systemd is now available and is the default in (u)buntu, not sure if that change applies also to (l)ubuntu .

The line that is similar to this " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " where the vmlinuz- and UUID= will be differnt  ; is not seen ?

[INDENT][INDENT]sometimes, I do not know
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-28
Yes, The line is:
Linux / boot/linuz-3.19.0.15-generic root=UUTD=53104504-bea4-42b-8515-1676b8914275.

---

### Post by Bashing-om on 2015-04-28
nu2this2; Humm ..

Not at all as I had expected to see ..
systemd the starter process ?.. sure is different from what I expected.
Let's try this:
at the end of that line " Linux / boot/linuz-3.19.0.15-generic root=UUTD=53104504-bea4-42b-8515-1676b8914275 " add the term 'single', again with out the quotes.
key combo ctl+x to continue the boot process ..

What results ?

[INDENT][INDENT]some times I do wonder
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-28
I can't do that because I have no cursor. It looks like I can only do the keyboard commands. as posted before.

---

### Post by Bashing-om on 2015-04-28
nu2this2; yuk !

No cursor ... OK

Back into bios .. see if you can find the option "plug and play" make sure it is enabled .
Perhaps also see about the "USB" setting .. change it to or from "legacy" .
save your changes and see now what results when you boot the hard drive install .

[INDENT][INDENT]trials, troubles and tribulations
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-28
Thanks Bashing,
Man-O Man your workin' the late shift out there in Arkansas! I'm out here in California and its getting to be dinner time. I'm going to sign off for now but will continue in the A.M. with your suggestions.

Thanks once more!!

---

### Post by nu2this2 on 2015-04-29
Hello,
I think I am in the area I'm supposed to be. I see  grub> with a cursor and I am able to type. Is that O.K.?

---

### Post by Bashing-om on 2015-04-29
nu2this2; Only a Maybe.

We might be able to work it from that grub > prompt.

We can sure try.
Let's see if the system boots from there - just to get an idea if the system is stable;
From that grub > prompt:
we do a manual boot.
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```
where we tell grub (GRand Unified Bootloader) where it's files are and we tell the kernel where it's files are -> 'boot' tells the kernel to "do it " .

Can you boot manually, and what do you boot to ?

[INDENT][INDENT]an adventure in learning
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-29
> **Bashing-om said:**
> nu2this2; Only a Maybe.

We might be able to work it from that grub > prompt.

We can sure try.
Let's see if the system boots from there - just to get an idea if the system is stable;
From that grub > prompt:
we do a manual boot.
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```
where we tell grub (GRand Unified Bootloader) where it's files are and we tell the kernel where it's files are -> 'boot' tells the kernel to "do it " .

Can you boot manually, and what do you boot to ?

[INDENT][INDENT]an adventure in learning
[/INDENT][/INDENT]

Do I type each line one at a time and press enter? I've never done this before.

---

### Post by Bashing-om on 2015-04-29
nu2this2; Yep;

You have the right of it .. one command per line ,, enter key at the end of each line to execute.

No shame in not knowing ...

Not a one of us who do have a bit of knowledge was born with it.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-29
In the first line of the commands,

hdO, Is that an O as in numeral zero or an alphabetical O. My keyboard doesn't  have that symbol.

---

### Post by Bashing-om on 2015-04-29
nu2this2; Yeah ...

The '0' it be a zero as in the number . the letter 'o' looks that <- way .
If the number pad numerals do not work, try on the keyboard the upper row .. on an ascii keyboard that is.

[INDENT][INDENT]we be stepping up
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-29
Darn I wish I could show you a screen shot of my screen probably would explain a lot. But I get "Can't find command".  My keyboard doesn't have a number pad only the upper row numbers.

I have tried to use those numbers as well as upper case "O" without success.

When I first used the grub menu the cursor appeared like this. Grub> c_.
 Notice the lower case c"." I typed your command as you posted after the cursor.
I then went through the iterations of trying the various ways to type the O with no success.

Then since your commands did not with a "c", I tried typing the command Without the "c" and this message showed up.
 error: missing ')' symbol .
grub>_      Appeared.

---

### Post by Bashing-om on 2015-04-29
nu2this2; could be -

That I am blowing smoke, I have yet to see what 15.04 looks like, and with systemd it is a whole new ball game in the booting arena.

How about this as a thought, download the .iso of release 14.04 of lubuntu .. and we start this install all over from scratch.
That is something I am familiar with, and more up my alley .

hard to hit the target
[INDENT][INDENT][INDENT]shooting in the dark
[/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-29
O.K.------------I'll do that. I think that's small enough to put on a CD isn't it ?

---

### Post by Bashing-om on 2015-04-29
nu2this2; unfortunately ;

NO, will not fit on a CD, best I recall it is 6 bytes to big.
Got to have a DVD or USB ...

IF you must use a CD .. then we are looking at a 'minimal' install .. workie great, last long time -> but there is a very steep learning curve/knowledge base to make it happen to get to a working desktop of your choosing && install the applications that you must choose to install. 

That happens to be what I do .. and I am very happy with my system. Up front, even with the extent of my knowledge it had it moments and difficulties to overcome. Now, all that said, if you are into a real learning experience in many many areas then I am willing to go there with you. But this is not for the faint hearted.

[INDENT][INDENT]standard desktop install
[INDENT][INDENT][INDENT]keeps it simple
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-29
O.K.

I found a DVD-R and will burn it now.

---

### Post by nu2this2 on 2015-04-29
O.K. got it burned and verified. Where do we venture from here.

---

### Post by Bashing-om on 2015-04-29
nu2this2; K

As this install has been problematic; let's do this in small stages.
1) verify the .iso that you downloaded :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

2) Burn at a slow rate:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

3) verify the burn:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

4) Boot the liveDVD and make sure that you have a wired internet connection and all devices do function as ecpected

5) Install to hard drive:
"erase disk and install ubunu" and in the initial install screen are check boxes for "install third party software" and do simultaneous "updates" while installing . Do not check these boxes . The install will go much smoother and faster - we control these after the install is completed.
identify keyboard, geographical area, username and password - pass word tattooed on eyelids - and let the install wizard take care of everything.

Done with the initial install ... 
Then we do the light house work

[INDENT][INDENT]all there should be to it
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-29
Hi there,
O.K. I have burned the disk and the hash sum check matched. So hopefully we can continue however, company just arrived so I will have to continue tomorrow if you are available.

---

### Post by Bashing-om on 2015-04-29
nu2this2; Yep;

Lord willing
Winds do not exceed
ISP holds all together
My box continues
I do wake up tomorrow

[INDENT][INDENT]I will meet here
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-30
Bad news. The installation failed! The failing step was "load installer components from CD".

Then I did an integrity checked that failed. This surprised me in as much as it had matching hash tabs from my previous sum check.

The last message----------"Your CD ROM or this file may have been corrupted". Is there a way to know the MDSum of this particular disk?

I am trying to find out how to burn at a slower speed------------so far, no luck.

Perhaps as one person said maybe the drive is old and no good?

---

### Post by Bashing-om on 2015-04-30
nu2this2; Hello:

Yes, there is:
> 
Is there a way to know the MDSum of this particular disk


The instructions - only a bit of a hassle - are included :
[code]
https://help.ubuntu.com/community/HowToMD5SUM
"Check the CD -> You can check the integrity of the CD without rebooting as follows."

What is the operating  system you are downloading and burning the CD from ? Perhaps I can provide the better instruction.

Got to have that firm foundation.

[INDENT][INDENT]it can be done
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-30
Hi,
The OS is win7 professional.

---

### Post by Bashing-om on 2015-04-30
nu2this2

see if these help:
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

[INDENT][INDENT]I do know it can be done
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-04-30
Hi again,

Thank you for the two links. Yes I had read them before. Re: dvd on windows, I don't have the options as described. What I can do however is left click the file and select Burn disk. Unfortunately I have no control over the burn speed. the instructions say Right-click on an **_ISO i_mage **. When I call up my download folder the type is listed as disk image file. Is this the same as an iso image?  

Also, the description of my version is: lubuntu 14.04.1 - alternate- i386. Is that the version I should have downloaded?

 This is the MD5sum----- a7c153f1101fb8a181ccda01a448ffd1 from ubuntus' website page and my DVD matches That.

This I very confusing. Do you think I might have a faulty CD/DVD drive?

---

### Post by Bashing-om on 2015-04-30
nu2this2; Making progres;

Yeah confirmed the md5sum is correct per:
[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS)

I have not seen Windows in years, so can not advise specifically, it does seem reasonable that " disk image file " is the .iso file.
The burn speed in 'buntu's brasereo burner is an option under 'properties' ; perhaps Windows is similar.

The alternate install is different from that of the desktop 'standard install' .. but should work for us . Particularly if you do have the less ram. Ram is the limiting factor here.
See:
[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO) 

I have not seen this 'alternate' so I do not know  what the installer looks like exactly . We will struggle through that.

For now all I can suggest is to burn the .iso ( as an image, not as data) and see what we have to work with once booted.

[INDENT][INDENT]all in that process
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-04-30
nu2this2; continuation;

Is this familiar ?
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

As to the state of the CD drive... I do not know how one would verify the CD drive other than see if it works with known good CDs, 
Once burned, does the ubuntu install CD boot up on this Windows 7 machine > Then it should boot on this machine we are trying to install onto . Maybe turn up a disk cleaner disk .. Can not hurt to try it and see.

[INDENT][INDENT]we do have to have the hardware
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-01
Good morning (for me anyway),

Well I found another application that burned a new DVD and voila, it seemed to work. Booted up as per your instructions. Of course I couldn't keep you updated because I was hard wired to my modem. Long story short the computer has been stuck at " Retrieving file 142 of 881 (19%). I had to disconnect the Ethernet to return on line. The laptop is still running and I ask, where to from here?

---

### Post by Bashing-om on 2015-05-01
nu2this2; Humm ...

Honestly, I do not know .. With a valid install medium, should go smooth ..

Tell ya what, think it is past time to look at the ram situation, make sure we have the ram to support lubuntu,

Abort the installation and ->
Boot up the liveDVD to "try ubuntu" ( does that option exist in this 'alternate install' ??) mode, and post back the output of terminal command:
```

free -m

```

Making sure we are not running out of ram. This should be as simple as falling out of bed wide awake .


[INDENT][INDENT]find the reason why not
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-01
No,

That option does not appear.

Install Ubuntu
Check for defects
test memory
Boot from HD
Rescue a broken system

Those are the only choices.

---

### Post by Bashing-om on 2015-05-01
nu2this2; Well that blows ->

That idea of "try ubuntu" from the boot menu.

How bout this an an alternative:
choose " install ubuntu"
and does the key combo ctl+alt+F4 yield a console interface ?

Maybe I should burn a DVD of the alternative install, so I know, and we are on the same page.

As I really want to get that nagging thought of insufficient ram out of the way.
Also look and make sure that the processor is 'PAE' enabled.
```

grep -w lm /proc/cpuinfo

``` as maybe we also have to "force" PAE.

No holding breath too much

[INDENT][INDENT]we cross bridges as we come to them
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-01
From a previous post of the specs.


 Memory 1.4GB
 Processor Mobile AMD Sempron(tm) Processor 3300+
 Graphics Gallium 0.4 on ATI RS480
 OS type 32-bit
 Disc 77.1 GB

---

### Post by Bashing-om on 2015-05-01
nu2this2; Yeah , ... Great .

Sorry I forgot about the prior posting of system specs, several irons in different fires.

Ram is not an issue !
Getting us to a terminal to see what we can do is .
Anyone ? else booted the 'alternative' installer, know a way to get a terminal ?

[INDENT][INDENT]gotta be a way, it's 'buntu
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-01
I think I might be able to burn at a slower speed, have to sort it out though. Is being hard wired to the Internet required when trying to install?

The reason for the question is that during the installation(that failed) there were numerous questions asked for which I didn't know the answers. Since I was hard wired to my modem, I was disconnected from the router so couldn't go wireless to ask for direction.

Thanks

---

### Post by Bashing-om on 2015-05-01
nu2this2; Well;

Yes and/or nooo .. depends
IF you have WIFI during the install process, then yes one can install via WIFI ....
But, but, but .. the drivers available in the live-install are not the same as those in the actual install and consequently one MAY not have drivers for WIFI initially once installd . Then one has to have a wired connection to install the WIFI driver ( with a high degree of probability said driver is available).

Alternately, one CAN install with no internet connection, and hope for the best when the installed system is updated - dependencies resolved - to what is current.  There is a high degree of a successful update when connected to a wired connection afterward. Will not hurt to try as all one looses in a fresh install attempt is a bit of time - say about 30 minutes. Then remember to disable the DVD as the   system update source .

[INDENT][INDENT]it is a possibility
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-01
O.K.

I was just now able to burn a new Livedvd at 2x. That is considerably slower than before. So I will try to install without internet and then try to update with a hard connection. Maybe I'll get lucky;)

---

### Post by Bashing-om on 2015-05-01
nu2this2; Hokay !

Remember, once installed and wired internet connection confirmed, then the very next thing is to disable the DVD in the sources.list .

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-01
Configuring the network:  Is asking which is the primary net work interface
1. etho: Marvell technology group PCI-E Fast Ethernet Controller.-----------OR
2. wlan0: Ralink corp PCI  (Wireless).

Since I'm trying a no internet install, how do I answer the ?

---

### Post by Bashing-om on 2015-05-01
nu2this2; Yuk;

Sorry to say, I have no idea; and worse
I know of no one - who has experience with the alternate install - to ask.

All I know to do at this point is for me to burn the .iso to disk and see what I see when I try and install it .
Not this night, but in my AM .

[INDENT][INDENT]best I can do
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-01
Bashing,

Thank you so much for all the help and assistance. I really do appreciate the time you have expended in trying  to solve this problem. I am going to sleep on this. For now----------who knows what might happen


BTW Love the sense of humor in your posts ;) ;)

---

### Post by Bashing-om on 2015-05-01
nu2this2; OK;

We tackle this with a fresh perspective after rest.
> 
BTW Love the sense of humor in your posts


Defiance in the face of adversity !

[INDENT][INDENT]we do not let little things whoop us
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-05-02
nu2this2; My afternoon:

I am back and prepared to proceed. My morning chores took a bit longer , and preparing/updating the environment I will work in took a bit longer than I had anticipated.
Downloading the 14.04 lubuntu alternate .iso file now .

I will be back when I know more.

[INDENT][INDENT]let's see, what can we do
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-05-02
nu2this2; Hey ;

I have a alternate .iso on hand and ready to install ..

Did you note the advisory in the download page NOT to use 14.04.2 that there is a bug ? I did not pursue the reason of the bug, following instruction I did down load release 14.04.1 .

Going off line at this time .. powering down, pulling my network cable and booting up .. see what results with an attempt to install lubuntu 14.04.1 without the network capability .

There is no substitute for the direct experience ->
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-05-02
nu2this2; OK !

I have your answer. Yepper can do with no networking .
> 
Configuring the network: Is asking which is the primary net work interface
1. etho: Marvell technology group PCI-E Fast Ethernet Controller.-----------OR
2. wlan0: Ralink corp PCI (Wireless).

choose option 1 - the wired connection .
Next is a screen that advises how unhappy the installer is and a request for help.
In this screen choose " do not configure the network at this time" .
continue.
Now continue with the install .

I think we can,
[INDENT][INDENT]I think we can
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-02
Hello Mr. Bashing, (AKA Little engine that could)

Thank you for your perseverance, appreciate the trouble you are going through to help me! I have just now discovered that I misspoke, (like a politician?) when I said I verified the disc. Yes, I must have verified a successful burn, but **not **a matching md5sum check! I don't know why but try as many times as I can I can't seem to get the sums to check. I have used three different checkers, Winmd5free, Md5checker and winmd5sum and all agree and state the sums don't match. 

I am at a total loss as to what the answer is. :confused:

---

### Post by Bashing-om on 2015-05-02
nu2this2; Well ........

I do not use Windows, so can not directly advise in how to verify the burn-image-to-disk .
This much I did learn about verifying the disk when booted and "check disk for defects". If I do not have an internet connection my box crashes !
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

As you are burning the .iso on Windows , it rules out a bad CD drive on the problematic machine as a cause of a bad write. Hey; you are burning the .iso as an image NOT as data, yes  ?

As the .iso md5sum is valid, there must be a failure in the write process, somewhere. One thing for sure, that install medium must be good else nothing else will be !

[INDENT]until that disk's md5sum is verified
[INDENT][INDENT][INDENT][INDENT]we are dead in the water
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-02
So it looks like you have to be connected to the internet in order to install correct? 

As a clarification, I am downloading the Ubuntu file and **then** checking the md5sum with the checker but not burning at this time. I have made way to many DVD
coasters. That's why I check the sum now before burning.

When I am burning the iso it is as an image and not as data file. This is being done on my desk top not the problematic laptop.

---

### Post by Bashing-om on 2015-05-02
nu2this2;

Yep, the install can be done without the internet connection.

But, I really do not know why it is required in this case to do so, as the wired connection is available ??

Hey .. this is a wired connection, yes ? I vaguely recall how difficult of a time I had way back in my dial-up connection era installing (k)ubuntu 9.04 ! Here in my area 'high speed' connections are readily available, I have not had to cope with other in ages. I hope that is not a bridge we will also have to cross.

-----------------------

I just have no idea why the liveDVD is not valid;
Have you checked the md5sum of the disk this way ?
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

[INDENT]still;
[INDENT][INDENT][INDENT]dead in  the water
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-02
Gotta  go,

Momma wants some BBQ Ribs for din din.

---

### Post by nu2this2 on 2015-05-03
Hello Again,

Just for the fun of it I downloaded  Lubuntu 15.04 on my wives laptop and much to my surprise it resulted in a successful and matching md5sum download. I'm thinking I have a problem with my desktop machine. The install was going fine when all of a sudden I lost my connection to the internet. This had happened before  with this version and I was never able to complete the install. I then duplicated this procedure but this time burned and installed Ubuntu 14.04.2. With the exception of one aspect that refused to complete,it installed successfully and seems to be working at the moment. I am able to go on line, use you tube, do searches etc. I haven't familiarized my self with any of the features of this O.S. at the moment and will have to look at some tutorials to learn the ins and outs of it.

I can't really understand what the issue is with the Lubuntu version or why it is impossible to DL on my desktop. At least I do have something on my old laptop that functions.

---

### Post by Bashing-om on 2015-05-03
nu2this2; That my friend is great news !

Fault isolation by sparing off the hardware, works .

OK, as you now have an lubuntu install . Get this install updated, then see what issues may still exist:
From the desktop, key combo ctl+alt+t will yield a terminal interface;
execute terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

I guess I best go back at look the bug advisory for installing 14.04.2; see if there is any relevance.

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS](https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS)
> 

Alternate Install
Alternate ISOs are for low-RAM PCs. Computers with less than 400 MB of RAM are considered low-RAM computers. You can find more information about Alternative Install.

Note: There is an issue with 14.04.2 alternate install, please use the 14.04.1 version here and then update.


I have not found any amplifying info:
[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

Let's work with what we have, see what there is that might need fixing !

[INDENT][INDENT]we are having fun now
[/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-03
Thank you,

I didn't know how to do that, believed that updates would have to be done, and your help will make it easier for me to do.

Right now I am looking at this tutorial, hoping to glean some information: [https://www.youtube.com/watch?v=oabgv5Q9mIg](https://www.youtube.com/watch?v=oabgv5Q9mIg) Thanks again for all your help. I'm sure looking forward to your coming to my rescue again in the future.

---

### Post by Bashing-om on 2015-05-03
nu2this2; Good deal ..

As this little matter of the original quest is now concluded;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

That reference tutorial looks to be directed at the flag ship release (U)buntu'; using a different Desktop Environment than (L)ubuntu; not much relevance.
You will find many great sources for instruction in using 'buntu; however be aware that ubuntu is an ever evolving operating system and moves fast. Many tutorials may be outdated. You will soon learn what does apply. - where I use 'ubuntu' as the generic term for all the distributions, a very large sisterhood. Your emphasis will be on learning the (L)ubuntu environment ( where the only difference is the Desktop and the installed default application) . The kernel is the kernel is the kernel, no matter the distribution or release of linux that you have booted.

And Yes, we are here to help you on your way. I will be more than glad to assist further in any way I can.

It's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT]

---

### Post by nu2this2 on 2015-05-03
Hello Bashing-Om,

I have marked the thread as solved ;).

Just for clarification purposes, I am up and running with Ubuntu 14.04.2, not Lubuntu. That version (Lubuntu) never did load properly for me. Even with matching hash sums I was disconnected from the internet.

---

### Post by Bashing-om on 2015-05-03
nu2this2; Still, Great !

You 'may' find ubuntu a bit sluggish  but with a Gig and a half should do nicely.

I like this for a starting reference :
[http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty)

[INDENT][INDENT]let the adventure begin
[/INDENT][/INDENT]

---

