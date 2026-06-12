---
title: "Serious problems with installation"
date: 2017-02-25
forum: General Help
---

### Post by joaopeterson on 2017-02-25
Hi,

I'm trying to install Ubuntu on my machine but I made a disaster. First, I tried to install through unetbootin, but then I realized that I forgot to resize my disc to get free space(....), ok, got back to windows, tried to resize the C directory. It wasn't possible, something to do with not movable stuff, tried to do it with a software called "EaseUS" (saw it on a forum), it should resize my disk rebooting my pc. Something happened and it didn't work, also my windows 10 didn't boot anymore. Then, tried to reset my windows(I was already desperate) and it didn't work. Finally, I tried to just overwrite Windows and install Ubuntu, but I got an error and now my machine don't even boot(any OS), it got stuck on "verifying DMI Pool Data... Update Success".

I know I was completely stupid, but I'm really desperate, please help me.

Joao Peterson

---

### Post by speartip on 2017-02-25
First off, you need to tell us how you wish to proceed.
If you're happy to wipe your disk & install Ubuntu, that should be do-able.
If you wish to save Windows, then if you have the Windows Disk, you could boot into that & try repairing your system.
Choice is yours really.

---

### Post by joaopeterson on 2017-02-25
Now I'm in a situation that I don't even care hahaha

But since I don't have the windows cd, guess I'll stay with ubuntu(no problem with that).

I can still boot Ubuntu through unetbootin, so I think that burning a Ubuntu cd/usb stick there and booting through it should work (?)

---

### Post by yancek on 2017-02-25
Do you have Ubuntu on a flash drive now which you are booting to try to install it?  Or did you do a 'frugal' install and when you boot the computer you see the 'unetbootin' option on the boot menu?  In either case, if you are able to boot Ubuntu to a Desktop, open a terminal and run this command and post the output here:  sudo fdisk -l(Lower Case Letter L in the command)  This will be a starting point.

---

### Post by joaopeterson on 2017-02-25
Actually, I was wrong, I can't even boot with unetbootin, it used to appear alongside Windows 10, I'm not booting from a cd/flashdrive

---

### Post by speartip on 2017-02-25
If you have Ubuntu installed on a flash drive, you need to get your computer to boot from that drive, otherwise it goes straight to your hard drive and fails. When your computer is first turned on you will need to press the appropriate key to reveal your boot menu. On mine it's the esc button but it could be one of the f  keys or the delete button. When your boot menu appears, choose your flash drive to boot from, and try out ubuntu from there.

---

### Post by joaopeterson on 2017-02-25
Unfortunately I don't have either a flash drive nor a cd with Ubuntu, but I'll get one

---

### Post by speartip on 2017-02-25
In you 1st post you said you used unetbootin. How did you use it if not installing ubuntu to a usb stick?

---

### Post by joaopeterson on 2017-02-25
It is possible to use the hard drive and when you reboot it'll appear "windows" and "unetbootin", choosing "unetbootin" is like choosing "try Ubuntu", you have to finish the install process

---

### Post by mörgæs on 2017-02-26
Which kind of hardware are we talking about and which version(s) of Ubuntu?

---

### Post by RobGoss on 2017-02-26
I't been a while since I've used Windows and ISO files were not available at that time, nowadays you have the option to download a **ISO** file for your Windows operating system in case it's needed as long as you have a registered licensed copy you should be good to go

**Windows ISO download**
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)

If you want to try to repair your Windows system you can download that** ISO** and burn it to ether a **USB** or **DVD, **it's your choice

Once you've done that and successfully repaired your Windows system you can then try installing **Ubuntu,** of course you will be Dual booting and this may be a bit more complicated considering what you've been threw already, I'm sure you'll need to read up on how to accomplish this with the help from the forum and staff

In the mean time this may help you get started which ever way you decide to go

How-to install Ubuntu 16.04
[https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Dual booting Windows & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


Best of luck

---

### Post by joaopeterson on 2017-02-27
Well, my pc is really old, it's a dual core 2.2Ghz, 2gb memory, 80gb hd. That's what I remember.

Edit: I was trying to install version 16.04 LTS

---

### Post by joaopeterson on 2017-02-27
Wow, I didn't know ISOs were available for windows. Thanks

I'm waiting a friend return from a trip in order to burn the cd for me... But you guys are awesome

---

### Post by RobGoss on 2017-02-27
> **joaopeterson said:**
> Well, my pc is really old, it's a dual core 2.2Ghz, 2gb memory, 80gb hd. That's what I remember.

Edit: I was trying to install version 16.04 LTS

What version of Windows did you have installed on this machine?

You should probably try installing a lightweight version like Lubuntu it should do well on this machine because it uses less resources

---

### Post by RobGoss on 2017-02-27
One thing about Linux is when trying to install any distribution you sometimes run in to issues, don't let that discourages you because sometimes it's the most simplest thing

---

### Post by mörgæs on 2017-02-27
> **joaopeterson said:**
> Well, my pc is really old, it's a dual core 2.2Ghz, 2gb memory, 80gb hd. That's what I remember.

Edit: I was trying to install version 16.04 LTS

Then I think you should try X/Lubuntu or Mate in stead of Ubuntu. 16.04.2 is a good choice (not .0 nor .1)

---

### Post by joaopeterson on 2017-02-27
In two days my friend will be able to burn the cd for me. I'll try to solve the problem(if it is solvable) with the cd and keep using linux, if it doesn't work, I'll just buy a machine with it installed

---

### Post by mörgæs on 2017-02-28
Good, please keep us posted.

If you want a CD then only the [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") is available. All other ISOs need a DVD.
Installing from a USB stick is normally a safer approach.

---

### Post by joaopeterson on 2017-03-02
Problem solved!!!!

I burned a DVD with the ISO and installed rewriting windows(like "delete everything, I just want to start from square one")

I'm posting this using my pc, which runs Ubuntu now. Thank you all very much

---

### Post by RobGoss on 2017-03-02
That's great glad you got it all worked out

---

