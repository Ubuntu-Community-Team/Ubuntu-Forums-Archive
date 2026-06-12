---
title: "Multiple users help"
date: 2007-02-22
forum: General Help
---

### Post by Anonii on 2007-02-22
How are you gentlemen?

First of all I use Feisty, but I dont think that that is the source of my problems.

Sooo, I have two users. Me, and my sister. I want my user to have full access over my sisters stuff, and my sister to have none over mine (This is easily managed in specific folders, by editing the permissions in them, but isn't there  a faster way to do to all her Home directory?).

Also, I want my sister to be able to access my VirtualBox's virtual drives. I changed her VirtualBox's directories to mine, and loaded my operating system, too. But there will be nothing on the available OS list. 

And my last problem, which is KDE related: When I'm switching between users and sessions, everything is working alright. The problem is when I try to close one, and stay only on the other one. In GNOME I'd just logout from that user, and I'd be able to use the other, just like that. But when I'm logging out in KDE, I will get a white screen in which I can type but not execute commands, and there it stays. I can only get past this by rebooting.

Thank you.

---

### Post by Sqwishy on 2007-02-22
> **Anonii said:**
> How are you gentlemen? My neck hurts, I had a bad sleepy time :( 

> **Anonii said:**
> ...but isn't there  a faster way to do to all her Home directory?). Yep you can open a terminal and type 'cd /home' to change to the home directory, then type chown or chmod or whatever the command is (type man <command> to see what it does) to make it so that you can control her folders and use the recursive switch (i think) to apply it to all sub folders, ex. chwhatever -r /home/sistershomefolder

> **Anonii said:**
> And my last problem, which is KDE related Solution: use gnome :D

---

### Post by Anonii on 2007-02-22
> **Sqwishy said:**
> My neck hurts, I had a bad sleepy time :( 

 Yep you can open a terminal and type 'cd /home' to change to the home directory, then type chown or chmod or whatever the command is (type man <command> to see what it does) to make it so that you can control her folders and use the recursive switch (i think) to apply it to all sub folders, ex. chwhatever -r /home/sistershomefolder

 Solution: use gnome :D

Ok the home directory permissions problem is solved. Now the KDE problem remains, and the Virtual Box one.

[No, I wont switch to GNOME, at least yet. I'm gonna totally switch to KDE when 4 hits, and I want to get used to it (I've been a hardcore GNOME fan the last 2 years.). And well, Amarok and K3B are so sweet.)

---

### Post by Sqwishy on 2007-02-22
Goodie your permissions are happyfull!! but i've never used Virtual Box and I don't use KDE so I can't help you there.

---

### Post by Anonii on 2007-02-22
> **Sqwishy said:**
> Goodie your permissions are happyfull!! but i've never used Virtual Box and I don't use KDE so I can't help you there.

Okay, thanks...

[By the way, I didnt fix the permission problem with your solution (I tried too, but it gave me the ownership of the home directory, which wasnt what I wanted.), because I was lazy and bored to RTFM. Instead, I opened Konqueror (the KDE file browser) with root permission (couldnt remember the command *kdesu* before; similar to gksudo in GNOME), and changed the permissions from the GUI (I changed it so that everyone can read/write from it.). But well, I'm sure that I could have fixed it with your way, too.]

---

### Post by Anonii on 2007-02-25
I also noticed another problem, which I will post here to avoid making a new thread, and in case someone can still answer my other questions.
I noticed that the **shutdown **command, wont shutdown but instead it will reboot my PC.
For example: **sudo shutdown -h now** , will instantly reboot... If I use the shutdown KDE button it will shutdown correctly, tho.

Any ideas?

(Answers to my previous problems are more than welcome, too.)

---

