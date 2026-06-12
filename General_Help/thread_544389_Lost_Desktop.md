---
title: "Lost Desktop"
date: 2007-09-06
forum: General Help
---

### Post by cssutto on 2007-09-06
On one of my laptops, the desktop is gone.

The boot goes as it should until I am asked for the user name and password.

I enter those and instead of getting the desktop, i get a blank screen the proper tan color.

The mouse will move the cursor but that is it.

How do I recover the desktop without reinstalling?

---

### Post by thelocust on 2007-09-06
At the startup screen you should select safemode for you session.

---

### Post by ljmagyar on 2007-09-06
erm.... how does one do that exactly?

---

### Post by thelocust on 2007-09-06
Sorry Failsafe mode (sorry still getting rid of my windows jargon) When you boot up your computer and it goes to your login screen there should be a session option, choose failsafe and tell us what happens.

---

### Post by ljmagyar on 2007-09-06
in my case... nothing... absolutely the same thing.  nice mouse on a brown screen.

i had edited my /etc/network/interfaces file and remarked-out the loopback stuff... i think this is what caused my problem... but i do not know how to recover from my error

---

### Post by cssutto on 2007-09-07
My desktop came back on its own this morning and I have no idea why.

However, there is no failsafe or safe mode in linux.

You do have the option on boot to choose recovery mode, but that gives you a command line system.

It certainly does not give you a desktop.

However, if one knows the proper commands one can repair about any error with the recovery mode.

One can either use recovery mode to copy backup files or most frequently to fix xorg.conf when you screw up your screen resolution.

Apt-get and all of that stuff is available.

Please give advice on those things which you are knowledgable.

CSSJr

---

### Post by ljmagyar on 2007-09-07
ok.. so when i go int failsafe / gnome, the system takes forever-10 minutes or sr, but eventually i get a desktop.  when i try to edit the /etc/network/interfaces file, the text editor tries to start, but fails and self-terminates.

i have tried using a live CD, but i can not browse to the hda to edit the file.  when i sudo su mount /dev/hda i get an error can't find /dev/hda in /etc/(something... sorry its gone from my h-RAM) some config file that doesnt exist

---

### Post by sumguy231 on 2007-09-07
> i had edited my /etc/network/interfaces file and remarked-out the loopback stuff
Definitely don't do that again. 

It sounds like you might have an easier time dropping to the terminal and editing /etc/network/interfaces. Hit Ctrl+Alt+F1 (Press Ctrl+Alt+F7 to get back to the desktop or login screen) and log in. When you get there, type:
```
sudo nano /etc/network/interfaces
```
Uncomment the loopback line, and press Ctrl+X to save. Type 'exit' at the terminal and press Ctrl+Alt+F7 to get back to graphics.

---

### Post by ljmagyar on 2007-09-07
> **sumguy231 said:**
> Definitely don't do that again. 

yah.. <slaps forehead>... what a dipstick!

> 
It sounds like you might have an easier time dropping to the terminal and editing /etc/network/interfaces. Hit Ctrl+Alt+F1 (Press Ctrl+Alt+F7 to get back to the desktop or login screen) and log in. When you get there, type:
```
sudo nano /etc/network/interfaces
```
Uncomment the loopback line, and press Ctrl+X to save. Type 'exit' at the terminal and press Ctrl+Alt+F7 to get back to graphics.
well, after some persistence i was able to get the hda mapped and i edited the interfaces file... all is good.

thanks for your help!

---

### Post by Resonance378 on 2008-04-07
> **cssutto said:**
> On one of my laptops, the desktop is gone.

The boot goes as it should until I am asked for the user name and password.

I enter those and instead of getting the desktop, i get a blank screen the proper tan color.

The mouse will move the cursor but that is it.

How do I recover the desktop without reinstalling?

As of today (post restart after updates for Hardy Heron 8.04) I'm experiencing this exact issue.
I have no idea what the cause of this is or how to attempt to recover from it.

I realize this is an old post but this is my exact problem currently and the only one like it I've found posted in the board search/history.

---

### Post by Resonance378 on 2008-04-07
The original post was from 2007 - the latest post to this issue is from today - same exact issue, months apart screams of bug or a way to hose an update.

Anyone have any thoughts.  My original post should be the last on page 1.

Tan desktop post login to desktop environment.  Nothing else.

---

### Post by scradock on 2008-04-19
Same problem here, with up-to-date Hardy. I tried to switch from fglrx driver installed by EnvyNG to the (same) driver installed from the ubuntu repo and got into xorg-hell. Eventually I can start up and get the log-in screen (looking normal), but logging in gets me the tan screen with no gnome panels, no desktop icons and no access to programs - except that a start-up program (aMSN) duly pops up and logs itself in as if everything was normal.

I found I could recover my normal desktop by choosing "Failsafe GNOME" for my session option. Everything works as expected - networking, wireless, Compiz, Googleearth,.... - but next time I start X I'm back to the tan screen.

If I choose GNOME as my session option it asks me if I want to make that my default; it doesn't ask me that if I choose "Failsafe GNOME". How can I make the "Failsafe GNOME" settings my default?

Alternatively, how can I fix my start-up script (Xclient script) to do whatever it used to do? For that matter, what IS my Xclient script (so-called in login-in session option list)?

Help, anyone?

---

