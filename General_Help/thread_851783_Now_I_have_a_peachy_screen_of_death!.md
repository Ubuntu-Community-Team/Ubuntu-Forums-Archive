---
title: "Now I have a peachy screen of death!"
date: 2008-07-07
forum: General Help
---

### Post by Alex J. on 2008-07-07
I've been having a lot of driver problems, usually it would give me a black screen before the login page, and I would go into the Grub recovery mode and change it back to the default driver. I thought that I fixed it, but after fooling with Compiz for a bit, I rebooted and got the normal login screen, but then it just gave me a blank peachy screen. It's not frozen or anything, and I'm guessing it's a driver problem again.

Trouble is, I can't figure out how to restore my Ubuntu to the default driver again from the Grub recovery this time. Is there any way to find out what the actually problem is and how to restore my Ubuntu again? 
I would feel so much better if I just could get into my ubuntu. **Any help?**

---

### Post by Cap'n Skyler on 2008-07-07
welcome to the forums!
and i have absolutely no help for you.LOL that is beyond the scope of my welcome message :P....and i have no idea as well.....:)
someone here should be along shortly to give a hand :guitar:

---

### Post by werries on 2008-07-07
well. first off, whats your system specifications
what driver did you install?
and what did you do in recovery before?

---

### Post by Alex J. on 2008-07-07
I have ATI Radeon Mobility X1200. I tried a bunch of things to get it working, but I think what finally got it working was installing it through Envyng. I'm *fairly* certain that I rebooted multiple times after installing the driver, I'm not entirely sure why it's acting up now. 
What I did before was go into Grub recovery mode and type in something like "dpkg-reconfigure xserver-xorg." I was stupid and didn't write it down, because I thought I had fixed it.

---

### Post by werries on 2008-07-08
im not actually sure how to solve this. i just wanted the info so that others could help out

---

### Post by crazyness003 on 2008-07-08
That sounds like a prob i had, but when i booted, the only thing that happened was compiz would not start up. Then when i tried to start it, it would give me a blank white screen...but i could still use and see my cursor only.
xgl was the culprit for me. i dunno how much help this is.
Ati uses soemthing like aiglx

see this post: [http://ubuntuforums.org/showthread.php?t=830812](http://ubuntuforums.org/showthread.php?t=830812)

---

### Post by Alex J. on 2008-07-12
I know that this post was a while ago, but I'm still having the blank screen problem and am unable to get into my Ubuntu. Of course, this makes me very, very sad :(

This person had a similar problem([http://ge.ubuntuforums.com/showthread.php?t=847860]("http://ge.ubuntuforums.com/showthread.php?t=847860")), and would make total sense since I ALSO was uninstalling sort of random evolution related things. How do you reinstall Gnome for Hardy Heron?

---

### Post by crazyness003 on 2008-07-12
use Alt+F2 to drop into the console?

If so, the closes tiv got to uninstalling and reinstalling gnome is 
```
sudo apt-get remove gdm 
```To remove The **G**nome **D**esktop **M**anager

then

```
sudo apt-get install gdm
```To install it.

I have not done this myself, i only pieced this info together from [http://ubuntuforums.org/showthread.php?t=832526&highlight=uninstall+gnome](http://ubuntuforums.org/showthread.php?t=832526&highlight=uninstall+gnome). I suggest you get another opinion. But then again, whats the worst that can happen?

---

### Post by Alex J. on 2008-07-12
Ermm...the first command definitely removed the GUI....

How do I get it back on? Not sure the second one did anything, it just goes to a command line prompt when I reboot now.

---

### Post by crazyness003 on 2008-07-12
> **Alex J. said:**
> Ermm...the first command definitely removed the GUI....

How do I get it back on? Not sure the second one did anything, it just goes to a command line prompt when I reboot now.

```
sudo /etc/init.d/gdm start
```
If gdm did install and didnt start up this code should bring it back.

Im gonna give the process a try now on a different partition. Gimme a sec.

---

### Post by Alex J. on 2008-07-12
Just did a fresh reinstall *sigh*. Hopefully the problem was me screwing around with uninstalling things, and I won't try that again. 
Thanks SO much though anyways.

---

### Post by crazyness003 on 2008-07-12
> **Alex J. said:**
> Just did a fresh reinstall *sigh*. Hopefully the problem was me screwing around with uninstalling things, and I won't try that again. 
Thanks SO much though anyways.

I just successfully uninstalled gdm then reinstalled but i used a slightly different approach.

Unfortunately it dosnt help you much since you did a fresh reinstall (which was gonna be my initial suggestion). Sorry

When i uninstalled gdm i had to stop x  and then install gdm using the above code. Then i had to restart x and everything was back to normal.

I might have overdone something but it worked for me.

whats important is they you solved your problem...you did solve the problem right?

---

### Post by Alex J. on 2008-07-12
Heh. Well, a reinstall did get my GUI back...now I just have to reinstall my wireless and ATI drivers. Upside is I'm becoming an expert at installing and configuring these drivers.
Anyway, your solution will probably come REALLY in handy in case this problem comes up again.

---

### Post by crazyness003 on 2008-07-12
> **Alex J. said:**
> Just did a fresh reinstall *sigh*. Hopefully the problem was me screwing around with uninstalling things, and I won't try that again. 
Thanks SO much though anyways.

I just successfully uninstalled gdm then reinstalled but i used a slightly different approach.

Unfortunately it dosnt help you much since you did a fresh reinstall (which was gonna be my initial suggestion). Sorry

When i uninstalled gdm i had to stop x  and then install gdm using the above code. Then i had to restart x and everything was back to normal.

I might have overdone something but it worked for me.

whats important is they you solved your problem...you did solve the problem right?

---

