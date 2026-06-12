---
title: "it wont come up"
date: 2007-12-24
forum: General Help
---

### Post by new2theu on 2007-12-24
I was on it lastnight and it ran great I was in windows and then went to restart in Ubuntu and it wont load gives error that the display has restarted 6 times in the last 90 seconds any help guys.

---

### Post by ~LoKe on 2007-12-24
Uh...please be more specific.

---

### Post by new2theu on 2007-12-24
what info do u need

---

### Post by ~LoKe on 2007-12-24
You need to be more specific about what you see when you try to boot.  What does the screen look like.  What did you do when you last used Ubuntu?

---

### Post by new2theu on 2007-12-24
i was surfing the net lastnight and all was okay when i shut it down. I did install a new mouse in windows. But when it tries to load ubuntu it starts out okay then it starts doing checks after the fifth one it starts trying to retry thats why i get the error message. Then the screen changes colors and says something is wrong it has restarted 6 times in the last 90 seconds.

---

### Post by ~LoKe on 2007-12-24
After it gives that error, what does the screen look like?  Is it black with white text, with a line at the bottom allowing you to type (or asking you to log in)?

---

### Post by new2theu on 2007-12-24
it is blue with a border around the whole screen and the only option i have is at the bottom of the screen it says okay. I did hit clt,alt,del to restart it again after a few when it didnt look like it was doing anything. It said stopping gnome display Im not sure if that helps.

---

### Post by ~LoKe on 2007-12-24
> **new2theu said:**
> it is blue with a border around the whole screen and the only option i have is at the bottom of the screen it says okay. I did hit clt,alt,del to restart it again after a few when it didnt look like it was doing anything. It said stopping gnome display Im not sure if that helps.

When you get to that screen, press ctrl+alt+F1.  It'll bring you to a black screen that prompts you for a user name and password.  Log in like you would normally.  After that you'll be able to type like you're in a terminal, type this in exactly!

> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by new2theu on 2007-12-24
It did as you said. So I typed in username and hit enter then it prompted me for my password but it wont let me type anything in there.

---

### Post by dlegend on 2007-12-24
> **new2theu said:**
> It did as you said. So I typed in username and hit enter then it prompted me for my password but it wont let me type anything in there.

The keys that you type for your password are invisible. Just try typing the password and hit enter once you've typed it.

---

### Post by new2theu on 2007-12-24
everything as you said but now it says
bruce@bruce-desktop:~$

---

### Post by dlegend on 2007-12-24
Did you type the command

> 
sudo dpkg-reconfigure -phigh xserver-xorg


as suggested by ~LoKe after logging in with your username/password? What does it say (if you did)? I can't help a lot as I'm not 100% sure on this but I'll try to help where I can until LoKe responds =)

---

### Post by ~LoKe on 2007-12-24
Yep.  Once you're at that line, type:
> sudo dpkg-reconfigure -phigh xserver-xorg
If that works alright (and it will), and only after that, type this:
> sudo /etc/init.d/gdm restart

All should be well.

---

