---
title: "Totally lost here?"
date: 2007-04-04
forum: General Help
---

### Post by westmatrix on 2007-04-04
I installed this Ubuntu, and was able to login, now I forgot the password and even the username!!!
Anyways I read and searched through this forum on how to get or reset the password, but I am unable to boot in recovery and all this fancy stuff.

What keys do I press to get into recovery mode?
How do I reset all passwords?

Cheers
West

---

### Post by amohanty on 2007-04-04
When you see the grub menu press ESC to drop into the recovery console. If you see something like 'grub booting default in 3...2...' press ESC to get to the grub menu.

You will hava a command prompt. There type the following:
**cat /etc/passwd | grep 1000**
The first word before the colon is your username (use something you can remember the next time :) )

Then type:
**passwd the_username_you_just_saw**

enter new password twice. Then press **Ctrl-D** and you should be good to go.

HTH
AM

---

### Post by westmatrix on 2007-04-04
Ok this is just stupid, I read this [http://ubuntuforums.org/showthread.php?t=133102]("http://ubuntuforums.org/showthread.php?t=133102") and now it works.

But what about security?
This is not the safest way to be able to reset a password?

---

### Post by westmatrix on 2007-04-04
Thanks  amohanty, I just got it.
	 

> **amohanty said:**
> When you see the grub menu press ESC to drop into the recovery console. If you see something like 'grub booting default in 3...2...' press ESC to get to the grub menu.

You will hava a command prompt. There type the following:
**cat /etc/passwd | grep 1000**
The first word before the colon is your username (use something you can remember the next time :) )

Then type:
**passwd the_username_you_just_saw**

enter new password twice. Then press **Ctrl-D** and you should be good to go.

HTH
AM

---

### Post by westmatrix on 2007-04-04
Sorry  amohanty, how do I get this server edition to bring up a GUI?

---

### Post by amohanty on 2007-04-04
> But what about security?
This is not the safest way to be able to reset a password?

Technically  in a production setup, you are not supposed to have physical access to the machine. Security has limits :) I once heard that the most secure box, would be something in a locked lead concrete box at the bottom of the marianas. Of course ots completely unusable. Also if somebody has physical access to your machine, you have more to worry about than just passwords.

In the server edition, you would have to install ubuntu-desktop - **sudo apt-get install ubunt-desktop** (you can get by with much less, but its more complicated and quite unneccesary)

Keep in mind that this will install a ton of stuff and boot up in GUI mode the next time. 

ANy reason why you setup the server edition?

AM

---

### Post by westmatrix on 2007-04-04
I have ordered the desktop edition; BUT
I downloaded a server edition thinking it would be better than the desktop edition.

I am sick and tired of windows and it's constant issues and problems 8 years is enough.
I am willing to learn how Ubuntu works and get out of this MS monopoly.

I have been having issues with windows since date of install day 1; 8 years ago.

I will have to wait for my desktop version to come to do the GUI install then.

---

### Post by amohanty on 2007-04-04
you can download the regular edition - it is the desktop edition.

AM

---

