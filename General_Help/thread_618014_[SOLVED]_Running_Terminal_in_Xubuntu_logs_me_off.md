---
title: "[SOLVED] Running Terminal in Xubuntu logs me off"
date: 2007-11-19
forum: General Help
---

### Post by nantax on 2007-11-19
I was fiddling with the settings for the desktop yesterday and set a resolution that is not supported by my monitor. I was advised to run sudo dpkg-reconfigure xserver-xorg and now I was able to login again.

I noticed this morning that when I try to run Applications -> Accessories -> Terminal, the screen turns black and Xubuntu will shutdown all application and return to the login screen. 

Can someone help me fix this problem? Thanks in advance.

---

### Post by p_quarles on 2007-11-20
That's a strange one, I have to admit. Does this happen with any programs other than the terminal?

Normally, my first advice would "run it from the terminal and post the error message." That doesn't seem to apply in this case. :D

So, let's see if you can run a terminal using a different method. I'm not familiar with Xfce, but in Gnome and KDE, you can bring up a command prompt by pressing alt-F2. If you are able to do that, type
```
xterm
```
Does the system crash, or does it bring up the terminal?

---

### Post by nantax on 2007-11-20
When I press Alt+F2 and run xterm, the program runs okay. Good replacement for the Terminal program that used to run under Application -> Accessories because the fonts is small and you can see the instruction from the web better.

I think that it's the only misbehaving program under the Applications menu. I can set preferences, open games, openoffice, pidgin and firefox. But when I try to run the Terminal application to type commands I read here in the forum, It would always log me out and put me back on the login screen. Is there a way to see what exactly happened when I run the Terminal application?

---

### Post by p_quarles on 2007-11-20
There should be. Like I said, I don't know Xfce, but you should be able to go to the menu editor to edit the launcher, which will allow you to find out what command it uses. 

Then, you can open xterm per my instructions, type the command for the default terminal, and you might be able to get some crash feedback before it logs you out.

---

### Post by nantax on 2007-11-20
I went to Applications -> Accessories -> Appfinder and the command that launches the terminal is xfce4-terminal.

I followed your instruction and opened xterm and then typed xfce4-terminal. I can't see anything after I press enter because the screen turns black and then it returns to the login screen.

Also the screen are all messed up at login. The splash screen is offscreen, I can't change the resolution to 1024x768 and I had to kill gdm run dpkg-reconfigure xserver-xorg again to fix it.

---

### Post by p_quarles on 2007-11-20
That's really weird. I'm kind of at a loss here, but you might give this a try:
```
sudo dpkg-reconfigure xfce4-terminal
```
If that doesn't work, I think these are the other options:
1) Wait for someone who knows more than I do to respond
2) Install and use a different terminal emulator. Personally, I think gnome-terminal and konsole are both quite nice, and more customizable than xterm. 
3) *As a last resort* you'll probably be able to fix this by backing up your data and reinstalling. Like I said: last resort.

---

### Post by nantax on 2007-11-20
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/xfce4-terminal/+question/7143](https://answers.launchpad.net/ubuntu/+source/xfce4-terminal/+question/7143) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thank you very much for your patience p_quarles. I searched for xfce4-terminal crash in google and it seems that the terminal window will crash if you have your desktop at 24bit color depth. Changing it to 16 fixes it.

---

### Post by p_quarles on 2007-11-20
Wow. That's one the strangest bugs I've seen. Anyway, glad you were able to repair things.

---

### Post by be4truth on 2007-11-27
I had the same problem on a brand new machine. The solution to set it to 16 bit is not a solution. I think this post isn't solved.

---

