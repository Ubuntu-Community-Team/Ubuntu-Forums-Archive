---
title: "ububtu 16.04 won't boot, stuck in purple loading screen"
date: 2017-01-14
forum: General Help
---

### Post by nantia on 2017-01-14
Hello, I yesterday shutdown my laptop after a while of keeping it on.
Today my laptop won't boot.i manually shut it down and on again but It is just stuck in the purple ubuntu loading screen.

I think I maybe know the problem.Yesterday I changed the device name of my laptop from nantia-someNumbers to nantia-laptop.
Since than I tried to to some sudo-things and It gave me an error which I googled and found out that I had to go to the etc folder and change in some files the old device name to the new (nantia-laptop) manually.
I tried to do that but I didn't had the write permissions and because of lack of time I just shutdown the laptop and was going to fix that today.

I am not sure if that is the reason why my laptop won't boot.but except that I only installed an official  Google drive syncer so it can't have made the problem....

Please help!!

---

### Post by ik-0 on 2017-01-14
Changing the host name shouldn't affect booting.  If it's stuck on the purple screen, try pressing esc or tab to see the boot process.  You can also edit the boot line in grub by pressing "e" and removing the "quiet splash" part.  Based on where it's getting stuck, you'll need to do some troubleshooting.
You can easily boot the system using a live CD and then mount the drive using a terminal to modify the configuration

List available devices and partitions
$ lsblk
Mount the drive
$ sudo mkdir /media/disk1
$ sudo mount /dev/sda1 /media/disk1
$ cd /media/disk1

The modify files as you see fit.

---

### Post by nantia on 2017-01-14
Hello and thanks!

I did what you said (deleted the quiet splash and saw boot) and it ended at a screen with the words "ubuntu 16.04 lots nantia laptop tty1, nantia laptop login"
I can't write or do anything here.

Doest this tell us anything  about the problem?

---

### Post by ik-0 on 2017-01-14
Not at all - it seems to boot and freeze.  Try using a boot CD and Mount the drive as I described to change back any files you edited.

---

### Post by nantia on 2017-01-15
Thank you very much!
I did not edit any file as I said in my first post.
But if I don't find a solution a will just delete ubuntu and reinstall it again...(this is what I have learnt so far to do ..)

---

### Post by santosh83 on 2017-01-15
> **nantia said:**
> Hello and thanks!

I did what you said (deleted the quiet splash and saw boot) and it ended at a screen with the words "ubuntu 16.04 lots nantia laptop tty1, nantia laptop login"
I can't write or do anything here.

Doest this tell us anything  about the problem?

From your description it appears that the boot process gets completed successfully and you get as far as the tty login prompt, but you can't type anything right? Did you try changing to another tty to see if anything happens? The shortcuts for that are CTRL+ALT+F1 to CTRL+ALT+F7. The last one is for the graphical screen of the login manager and X. Does anything happen? What happens when you press CTRL+ALT+DELETE?

---

### Post by nantia on 2017-01-15
Hello.
Yes that is right I can't type anything here.
With the F1 to F6 combinations I can write login and password. (But wtf am I supposed to write for login.?I only have my password..)
At F7 I can't write anything neither.
With ctrl+alt+delete it seems like the laptop reboots and it gets me again to the purple ubuntu loading screen...

---

### Post by santosh83 on 2017-01-15
What you describe is normal then. At the login prompt you first need to give your user account name and then the password for it. You would've created at least one account when you installed Ubuntu, as a part of the installation process. So type whatever name you gave during the signup process (the actual user name and not the full name), and then when login prompts you, type the password. Also looks like your system is booting to the text terminal instead of the graphical login screen. All desktop installs of Ubuntu and its variants go straight to the graphical login screen (CRTL+ALT+F7) where you login to your desktop. Only the server install defaults to the text terminal. You say you don't get anything when you go to CTRL+ALT+F7, which suggests that either you didn't install X and a graphical desktop environment or X isn't starting for you, for some reason.

Either way need more details to say anything more.

---

