---
title: "XAMPP on startup?"
date: 2005-07-30
forum: General Help
---

### Post by superultra on 2005-07-30
I am trying to get XAMPP (it calls itself LAMPP) to startup with the gnome login.  

I went to Sessions in preferences and added it the startup programs as:
/opt/lampp/lampp start 
It has an order of 50, but I'm not sure what that means.

It doesn't bootup though.  Gnome lists it as a program that is running, but I have to still go into the root terminal and start it myself with the very same command.  

Thanks for any help.

Oh yeah, I heart ubuntu.  It is awesome.

John

---

### Post by kassetra on 2005-08-01
[QUOTE=superultra]I am trying to get XAMPP (it calls itself LAMPP) to startup with the gnome login.  

I went to Sessions in preferences and added it the startup programs as:
/opt/lampp/lampp start 
It has an order of 50, but I'm not sure what that means.

It doesn't bootup though. Gnome lists it as a program that is running, but I have to still go into the root terminal and start it myself with the very same command. 

Thanks for any help.

Oh yeah, I heart ubuntu.  It is awesome.

John[/QUOTE]

Have you tried logging out of Gnome with XAMPP still running or at least open - and telling Gnome to save your session (that's what I did for BMP & GAIM)?  Or use the Auto-Save Session feature?  (Some programs do have issues with starting up automatically - Firefox is one I can name off the top of my head.)

---

### Post by superultra on 2005-08-01
I have, and it doesn't start XAMPP when I come back in again.

---

### Post by kassetra on 2005-08-03
[QUOTE=superultra]I have, and it doesn't start XAMPP when I come back in again.[/QUOTE]

This might be one of those "unloadable-upon-start" applications - but try this first:
When you have all of the applications open that you want to open automatically, open a terminal and type in:
```
gnome-session-save
``` Making sure to uncheck save session automatically or save session when you log out of gnome - so you don't change the session info.  Sometimes using this command works when the other options hadn't before.

---

### Post by superultra on 2005-08-06
[QUOTE=kassetra]This might be one of those "unloadable-upon-start" applications - but try this first:
When you have all of the applications open that you want to open automatically, open a terminal and type in:
```
gnome-session-save
``` Making sure to uncheck save session automatically or save session when you log out of gnome - so you don't change the session info.  Sometimes using this command works when the other options hadn't before.[/QUOTE]
 Thanks for the help, but these tips are sadly a no go. 

I'm a noob to Linux, but it seems like it would be an easy thing to add since it's just a command line operation.  ??

---

### Post by Ninjew on 2005-08-07
I'm loving Ubuntu as well, but was experiencing the same problem.  I'm also a Linux noob, so I feel your pain.

I went to the first place I should have looked for an answer, the LAMPP for Linux FAQ page, and sure enough, found the answer.  This is modified from information taken from [http://www.apachefriends.org/en/faq-xampp-linux.html#fsl](http://www.apachefriends.org/en/faq-xampp-linux.html#fsl) :

(I did these as root, but I don't know if that's necessary)


1.  change into the /etc/rc2.d directory

2.  type the following two commands in the terminal:

ln -s /opt/lampp/lampp S99lampp
ln -s /opt/lampp/lampp K01lampp


And it worked like a charm for me.  Now that I have an auto-login set up as well, I don't need to worry about anything on my Ubuntu server box.  If it goes wrong, I can just reset it and it will be all ready to go without any work.

This should work for you as well.

-Ninjew

---

### Post by Mum_Chamber on 2008-01-13
> **Ninjew said:**
> 
1.  change into the /etc/rc2.d directory

2.  type the following two commands in the terminal:

ln -s /opt/lampp/lampp S99lampp
ln -s /opt/lampp/lampp K01lampp

another old but charming comment. worked for me, too

---

### Post by Nepherte on 2008-01-13
Placing:
```
/opt/lampp/lampp start
```
in the session will not work because it needs sudo priviliges. So you have to link it in the /etc/rc.x directory as suggested.

---

