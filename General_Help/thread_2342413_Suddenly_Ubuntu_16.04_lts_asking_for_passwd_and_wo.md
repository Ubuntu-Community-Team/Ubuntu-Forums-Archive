---
title: "Suddenly Ubuntu 16.04 lts asking for passwd and wont let me in"
date: 2016-11-06
forum: General Help
---

### Post by teprac on 2016-11-06
Hi, I've had  Ubuntu 16.04 lts on my computer for a few months. And this morning for the first time it would not auto login. It's asking for my password and when  I enter it it just goes back to the screen asking for the password. 

I'm stuck and cannot login.

Any suggestions?

---

### Post by asgard2 on 2016-11-06
can you login over the tty terminal (CTRL+F1) ?

---

### Post by teprac on 2016-11-06
When I get tot he screen where i can login with my usr or guest it wont let me in choosing either option

where would i try the [COLOR=#000000]terminal (CTRL+F1) ?[/COLOR]

---

### Post by asgard2 on 2016-11-06
There are 6 tty terminals, you can reach them over the shortcut "CTRL+ALT+F1" up to F6, CTRL+ALT+F7 is your gui.
If it is a problem with your login manager, you can still login at these terminals.

@[**[COLOR=#000000]Impavidus[/COLOR]**]("https://ubuntuforums.org/member.php?u=1417721")
oha thx, now it is correct #-o

---

### Post by Impavidus on 2016-11-06
It's ctrl-alt-F1 up to ctrl-alt-F6, with ctrl-alt-F7 to get back to the GUI.

---

### Post by teprac on 2016-11-06
so i did ctrl-alt-F1 and now i'm at a black screen with: ~$

not sure what command to enter here ?

> **Impavidus said:**
> It's ctrl-alt-F1 up to ctrl-alt-F6, with ctrl-alt-F7 to get back to the GUI.

---

### Post by oldrocker99 on 2016-11-06
CTRL-F1 **should** give you a login prompt, and you enter your password after entering your user name.

---

### Post by teprac on 2016-11-06
ok so i managed to get back in after following this thread...

Can't login to Ubuntu 16.04 after upgrade
[http://askubuntu.com/questions/759871/cant-login-to-ubuntu-16-04-after-upgrade](http://askubuntu.com/questions/759871/cant-login-to-ubuntu-16-04-after-upgrade)


and i ran this command:


sudo apt-get purge nvidia*

---

### Post by teprac on 2016-11-06
So assuming the purging nvidia command is the problem, is there something i can do to make sure the nvidia drivers are the correct drivers and are up to date ?

---

### Post by teprac on 2016-11-06
Ok, so i ran the purge nvidia command and now I can login.

When I went to open a browser the system crashed.

I rebooted and ran these commands from the command line to up nvidia drivers:
sudo apt-get install nvidia-current

I then rebooted the system and now I cannot login, so I'm back to where I started.



So where do I go from here?

---

