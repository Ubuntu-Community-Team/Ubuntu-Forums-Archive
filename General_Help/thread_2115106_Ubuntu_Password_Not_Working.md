---
title: "Ubuntu Password Not Working"
date: 2013-02-11
forum: General Help
---

### Post by basica on 2013-02-11
So, I just did a new install of ubuntu 12.10 on another computer I have here and my password is not working. I figured I must've mistyped it during install so I go to recovery mode and reset the password. I log back in, the password works initially but when I go to sudo something a second time it no longer accepts it. This process has occurred 3 times so far and I'm just about to do a reinstall but I wanted to check if this is a known error? I had a similar thing happen to me before but after the initial reset it worked.

Anyways, any help is appreciated.

---

### Post by TheFu on 2013-02-11
Every time I've ever not been able to login due to a password issue, it was my fault or a problem with the keyboard.  Either I'd mistyped it twice when it was set or I was typing a password too fast and the shift key would stick just a little too long on the following non-shifted character.  

As you can see from my signature, I've been typing passwords for a fairly long time.  However, I am not running 12.10.

---

### Post by omprakash paliwal on 2013-02-11
i am also having this kind of problem. i have account named heart-hacker... when i "sudo" something i works fine ( accepts password ) but when tried to su ( loging as root ) in terminal and providing the password it say " authentication failure" .. i don't know where is the problem... so i need help if u r familiar .....
:confused:

---

### Post by unheeding on 2013-02-12
> **omprakash paliwal said:**
> i am also having this kind of problem. i have account named heart-hacker... when i "sudo" something i works fine ( accepts password ) but when tried to su ( loging as root ) in terminal and providing the password it say " authentication failure" .. i don't know where is the problem... so i need help if u r familiar .....
:confused:

That's because the root account is disabled by default in Ubuntu.  It's asking for the root password when you "su" and there is no root password (at least, it isn't the same as your user password).  There are some steps to enable it, but you should be able to make do with sudo.

---

### Post by basica on 2013-02-12
> **TheFu said:**
> Every time I've ever not been able to login due to a password issue, it was my fault or a problem with the keyboard.  Either I'd mistyped it twice when it was set or I was typing a password too fast and the shift key would stick just a little too long on the following non-shifted character.  

As you can see from my signature, I've been typing passwords for a fairly long time.  However, I am not running 12.10.
Yeah, I checked that by using a password that is hard to mess up to test it (i.e. something like qwerty12345) but still no go. The fact that it happened three times, and each time worked initially when I logged in but stopped working after the first try suggests to me some kind of bug. The issue finally went away after running updates though so I'm cheering. Was getting really annoying.

---

### Post by TheFu on 2013-02-12
> **basica said:**
> Yeah, I checked that by using a password that is hard to mess up to test it (i.e. something like qwerty12345) but still no go. The fact that it happened three times, and each time worked initially when I logged in but stopped working after the first try suggests to me some kind of bug. The issue finally went away after running updates though so I'm cheering. Was getting really annoying.

Sounds like there were incompatible libraries loaded on your box somehow.  If you couldn't type in the password, exactly how did you run the updates on the system?

I'll add that reason to the very long list of reasons why any program may not work properly - out of sync libs.

---

### Post by basica on 2013-02-12
> **TheFu said:**
> Sounds like there were incompatible libraries loaded on your box somehow.  If you couldn't type in the password, exactly how did you run the updates on the system?

I'll add that reason to the very long list of reasons why any program may not work properly - out of sync libs.
Everytime I reset it, it would work the first attempt. So, I log in and then say go sudo vi /etc/samba/smb.conf and it would work. I then go to run sudo apt-get upgrade and the password won't work, the very same one that did work a moment prior. I would then restart, drop to root shell and reset the password. I did this several times. Ultimately, realizing that I only had one sudo before it stopped working I ran an update and then afterwards it was fine.

---

### Post by TheFu on 2013-02-12
> **basica said:**
> Everytime I reset it, it would work the first attempt. So, I log in and then say go sudo vi /etc/samba/smb.conf and it would work. I then go to run sudo apt-get upgrade and the password won't work, the very same one that did work a moment prior. I would then restart, drop to root shell and reset the password. I did this several times. Ultimately, realizing that I only had one sudo before it stopped working I ran an update and then afterwards it was fine.

Ah .... THAT explains it.  This was about sudo, not the login, correct?

I think sudo was recently updated, so depending on when you got those updates, the system libraries may have changed too.  I've not experienced this issue myself.  I only patch on weekends to avoid package updates in the middle of my patching process.

Any chance that you modified the /etc/sudoers file?  There is a special command for that - **visudo**.  Editing it directly is a really bad idea.

---

### Post by basica on 2013-02-12
> **TheFu said:**
> Ah .... THAT explains it.  This was about sudo, not the login, correct?

I think sudo was recently updated, so depending on when you got those updates, the system libraries may have changed too.  I've not experienced this issue myself.  I only patch on weekends to avoid package updates in the middle of my patching process.

Any chance that you modified the /etc/sudoers file?  There is a special command for that - **visudo**.  Editing it directly is a really bad idea.
Yeah, sudo only. I set it to login automatically. Thanks for explaining what may have been behind it btw; it's interesting how it all works together. I didn't touch the sudoers file, the issue occurred immediately after booting from the finished install. Anyways, if it's not one thing it's another hehe. This morning I was greeting with another issue as my mergelist file got corrupted as my internet dropped out. Thankfully figured that out too. Once again, thanks for the assistance.

---

