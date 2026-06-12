---
title: "Random Freezes 12.04 and 12.10 after clicks."
date: 2012-10-26
forum: General Help
---

### Post by gregbrown on 2012-10-26
Hello :-)

I have been trying Linux on/off for years now, but until Ubuntu 12.04 I was unable to get a system functioning fully. I installed 12.04 and was pleased when I was presented with a fully functional system. BUT ... soon after installation I started experiencing random freezes that most often require turning the system off to recover. (The mouse and frequently the keyboard are unresponsive.) Occasionally I got a msg indicating an internal problem reported by the display logs which I dutifully reported. This became so frustrating that I upgraded to 12.10.

The system continues to freeze after clicks of the mouse.  This morning I clicked Dash Home and it froze after displaying the icon text, but not the icons.

I'd like very much to use Ubuntu exclusively, but it is unstable here. Anyone have a fix?

I tried to put the lshw output here, but the reviewer thinks it has too many images. It has one.  I'll try to attach it. Now it complains that it is an invalid file. Grrrr... Zip attached.

---

### Post by davejm73 on 2012-11-12
Hi

I have the exact same issue with no answers, please let me know if you found a solution

thanks

---

### Post by Gilles2 on 2012-11-17
Hi
I had a similar problem with the mouse freezing and found the solution in another place.
What worked for me:
Go the terminal (ctrl+alt+t)
sudo rmmode psmouse
sudo modprobe psmouse

I hope it will help you.

---

### Post by hubertofliege on 2012-11-28
I have a similar problem. 

OS: 12.10 32 bit
Laptop: Asus B53J 
Processor: Intel I5
Graphics card: ATK, I think. 

System freezes every time I use it.

Symptoms:

- Sometimes I can move the mouse, sometimes I can't.
- It happens randomly, even while browsing the internet.
- It can be a few hours after I start it up, or sooner.
- It happens invariably if I try to load music to a music player through Rhythm Box

I'm posted this same info in a similar thread:

[http://ubuntuforums.org/showthread.php?p=12378267#post12378267](http://ubuntuforums.org/showthread.php?p=12378267#post12378267)

Can someone explain what those commands do before I try them?

---

### Post by hubertofliege on 2013-01-01
Has anyone come across a trouble shooting guide for this?  I'm looking all over, and I am out of ideas.

---

