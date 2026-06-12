---
title: "New Video Card, Ubuntu is SLUGGISH"
date: 2007-09-28
forum: General Help
---

### Post by T3KN33K on 2007-09-28
So i just installed a new video card...  nothing fancy since I have only a PCI bus to work with, but all i wanted was something that had a video out port, and dual monitor support.  Anyways, after installing the new card, (Radeon 9250) I had to (after searching for an appropriate fix in Windows) use the dpkg-reconfigure xserver-xorg command to reconfigure for my new card.  I pretty much just followed most of the defaults, and upon restart, the GUI finally started.  But now everything is just... slow.  It feels like I'm running Vista on a computer with 256mb of ram.  Even typing right now is driving me insane, as there is a very noticeable lag between when i press the keyboard and when the character shows on screen. 

Now, using my onboard video before, Ubuntu was running like a top.  Is it possible that I did not correctly configure something?  Or does Ubuntu just not like my card?

Relevant specs are as follows:
2.8Ghz P4 with HT
1.25GB DDR2 RAM
ATI Radeon 9250 GFX Card


Thanks in advance for any help...

---

### Post by T3KN33K on 2007-09-28
bump

---

### Post by SeanTater on 2007-09-28
Try reconfiguring that again with default priority like so:

```
sudo dpkg-reconfigure --default-priority xserver-xorg
```

It should do more guessing on it's own, which in my case, was more correct than I was.

You should also consider whether the "ati" driver or the "fglrx" driver is best, as both should work for your card.

If you don't have fglrx, you might want to try it using this: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by tgalati4 on 2007-09-28
Perhaps your pci latency is upsetting your computer/human harmony.

Take a look at:

[http://www-128.ibm.com/developerworks/library/l-hw2.html](http://www-128.ibm.com/developerworks/library/l-hw2.html)

It that's too technical, then post the output of:

>lspci -vv

If you gotten this far, then install powertweak.

>sudo apt-get install powertweak

---

### Post by jocko on 2007-09-28
> **SeanTater said:**
> 
You should also consider whether the "ati" driver or the "fglrx" driver is best, as both should work for your card.

If you don't have fglrx, you might want to try it using this: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Correction: fglrx does NOT support anything below radeon 9500. Make sure you use the open source driver ("ati").

---

### Post by T3KN33K on 2007-09-28
> **tgalati4 said:**
> 
It that's too technical, then post the output of:

>lspci -vv

hmm.. might you mean "lspci -v", as the article suggests?

well, here's the relevant output from the latter:

```
03:01.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
        Subsystem: Diamond Multimedia Systems Unknown device 0161
        Flags: bus master, medium devsel, latency 64
        Memory at c0000000 (32-bit, prefetchable) [size=128M]
        Memory at dfbe0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
```

---

### Post by tgalati4 on 2007-09-29
Your latency is at 64.  For video cards it should be at 200 or higher.  Mine is set at max (248).  Try setting it to max latency, reboot and see if it's better.  With powertweak, you can make changes on the fly.

---

### Post by T3KN33K on 2007-09-29
this is probably a really stupid question...  but how the hell do I run powertweak??  Is there a GUI, or does it just run from the command line?

I just cant seem to run it.  from the alt-f2 Run command, it autofills powertweak to powertweakd, so presumably, that is the executable's name (...or whatever you call executables in linux).  But when I hit "Run", the window closes and nothing happens.  Same response in terminal with "sudo powertweakd"....  am I missing something?

---

### Post by tgalati4 on 2007-09-29
I found it under Applications-->Debian-->Apps-->System-->powertweak.  Try:

tgalati4@hpubuntu:/media$ whereis powertweak
powertweak: /etc/powertweak /usr/lib/powertweak /usr/share/powertweak


Since it's located in /usr/share, you can run it with:

>./usr/share/powertweak

It threw me at first as well.

---

### Post by T3KN33K on 2007-09-30
this is getting pretty strange...  My applications>debian folder is empty....  and my "whereis powertweak" gives me the identical output that you posted....  however I am still unable to start the damn thing :lolflag:...  I've also tried uninstalling and reinstalling, restarting....any other ideas??


**_EDIT:_** So, the answer to this comment lies very simply, here:```
sudo gpowertweak
```    :confused: :mad:

...will update soon as to whether or not maxing the PCI latency solves the problem

---

### Post by tgalati4 on 2007-09-30
There is an application that you can load in Synaptic that will give you the Debian utilities.  Maybe it can be found in "Add/Remove".  I don't remember it's name, but searching for Debian should turn it up.  

Thanks for the tip on gpowertweak.  I believe it's really a gnome front-end for the powertweak daemon--powertweakd.

---

