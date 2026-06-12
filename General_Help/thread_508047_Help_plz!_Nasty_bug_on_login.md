---
title: "Help plz! Nasty bug on login"
date: 2007-07-23
forum: General Help
---

### Post by Pablopcv on 2007-07-23
Hello. I have a nasty bug in my UbuntuEdgy OS. When I try type my user name in the login screen, it restarts automatically. This bug started after I changed the gnome default iconset and tried to open the login window manager. (root terminal crashed when I did that)

The problems showed up when I tried to open the terminal (terminal didn't boot, the same with file explorer). The whole thing was so buggy that I decided to restart my pc and I cant login to my session now.

I'm not very experienced in this and I dont know how to fix this. I dont know what exactly caused this bug or whats happening (I guess that server X is the problem but I dont really kniow).

I know...sorry for my spelling hehe

hope you can help and thanks in advance
pcv

PD: I cant make a bug report cuz I cant login my account. I'm in M$ right now :mad:

---

### Post by lisati on 2007-07-23
First of all, welcome to the team.

Secondly, relax, there's bound to be someone in Ubuntu-land who is able to help without the need to make a bug report.

---

### Post by defishguy on 2007-07-23
This has happened to me.  You can log on by changing the session to "gnome failsafe".  Remember to change the session before hitting enter after your password.  Once logged on open System -> Preferences -> Themes and delete the icon theme that is causing the problem.

Good luck.

---

### Post by Pablopcv on 2007-07-23
hi fish guy and thanks for the reply... yeah that was the first thing that I tried but it restarts when I type any character on the text box. I tried to run recovery modes and its the same thing... The only thing that I can do is enter the root terminal without graphics...

thanks 
pcv

---

### Post by Pablopcv on 2007-07-24
well, I can now login by skipping the losgin screen but it dont makes any difference at all. The gdm still very buggy. When I try to open anything it crashes immediately. I cant even send a bug report because the keyring manager crashes too and im unable to make a wireless connection... 


thanks for the attention 
pcv

---

### Post by Crafty Kisses on 2007-07-24
> **Pablopcv said:**
> well, I can now login by skipping the losgin screen but it dont makes any difference at all. The gdm still very buggy. When I try to open anything it crashes immediately. I cant even send a bug report because the keyring manager crashes too and im unable to make a wireless connection... 


thanks for the attention 
pcv

You might want to post the following output:
```
glxinfo
```

---

### Post by Pablopcv on 2007-07-24
hi Codename, I appreciate your attention. When I request "glxinfo" it replays this:

```
 Error: Unable to open display (null) 
```

I cant use that comand with graphics on because I cant use terminal  :confused:

I dont konw the real cause of the bug

---

### Post by Pablopcv on 2007-07-24
there is a way to know what is causing this problem?

---

### Post by Crafty Kisses on 2007-07-26
> **Pablopcv said:**
> hi Codename, I appreciate your attention. When I request "glxinfo" it replays this:

```
 Error: Unable to open display (null) 
```

I cant use that comand with graphics on because I cant use terminal  :confused:

I dont konw the real cause of the bug

You need to reconfigure your X server it sounds like, you might want to try this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Hope this helps.

---

