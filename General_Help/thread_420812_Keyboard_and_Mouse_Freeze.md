---
title: "Keyboard and Mouse Freeze"
date: 2007-04-24
forum: General Help
---

### Post by LinkRJH on 2007-04-24
Hello,

This would be my third post regarding this issue without any help as of yet. I've installed Feisty and cannot use my computer for any significant amount of time before my keyboard, mouse, or both freeze. It seems to be one then the other and dependent upon how much I use them as to what will go first. I'll be surprised if I can finish typing this post before I lose my keyboard again.

Without the ability to use a mouse or keyboard, I have to do a hard power down with my computer with is potentially damaging to my hardware making Ubuntu a less and less friendly choice - as it may destroy my computer.

The mouse and keyboard are both USB, and based on what I have gathered from other sites I've read regarding these types of issues, this is the information you would need to assist me:

```
linkrjh@gigahertzog:~$ lsusb
Bus 002 Device 003: ID 413c:2005 Dell Computer Corp. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
linkrjh@gigahertzog:~$
```

I am glad I haaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa aaaaa

---

### Post by Pete051 on 2007-04-24
I'm having the same problem, Logitech itouch cordless mouse and keyboard on an xp2500 system. everything is fine then for no reason I can figure out both mouse and keyboard go dead leaving the reset button as the only solution :(

---

### Post by LinkRJH on 2007-04-26
> **Pete051 said:**
> I'm having the same problem, Logitech itouch cordless mouse and keyboard on an xp2500 system. everything is fine then for no reason I can figure out both mouse and keyboard go dead leaving the reset button as the only solution :(

And yet no response as to how to fix this.  It's disappointing.

---

### Post by mills on 2007-04-26
i had a kind of similar problem and recently solved it by adding the noapic nolapic line to grub

this link will show you how if want to give it a try 

[http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)

hope it does the job

---

### Post by extre on 2007-04-26
I also have the same problem, my mouse just freezes. Sometimes it works for 10 seconds and sometimes for hours. I´m using a LX710 Bluetooth mouse.

Have tried some workarounds without any luck. 
Any suggestions?

---

### Post by titus1950 on 2007-04-26
> **extre said:**
> I also have the same problem, my mouse just freezes. Sometimes it works for 10 seconds and sometimes for hours. I´m using a LX710 Bluetooth mouse.

Have tried some workarounds without any luck. 
Any suggestions?

Disable "USB legacy support" on your Bios,....  so far is the only fix,for me.

---

### Post by titus1950 on 2007-04-26
> **LinkRJH said:**
> Hello,

This would be my third post regarding this issue without any help as of yet. I've installed Feisty and cannot use my computer for any significant amount of time before my keyboard, mouse, or both freeze. It seems to be one then the other and dependent upon how much I use them as to what will go first. I'll be surprised if I can finish typing this post before I lose my keyboard again.

Without the ability to use a mouse or keyboard, I have to do a hard power down with my computer with is potentially damaging to my hardware making Ubuntu a less and less friendly choice - as it may destroy my computer.

The mouse and keyboard are both USB, and based on what I have gathered from other sites I've read regarding these types of issues, this is the information you would need to assist me:

```
linkrjh@gigahertzog:~$ lsusb
Bus 002 Device 003: ID 413c:2005 Dell Computer Corp. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
linkrjh@gigahertzog:~$
```

I am glad I haaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa aaaaa





Disable "USB legacy support" on your Bios,.... so far is the only fix,for me.

---

### Post by magnus07 on 2007-04-27
LinkRJH, did the suggestion work for you?
After asking, please provide feedbacks :-)

---

### Post by magnus07 on 2007-04-27
some more here: [http://ubuntuforums.org/showthread.php?p=2546905#post2546905](http://ubuntuforums.org/showthread.php?p=2546905#post2546905)

---

