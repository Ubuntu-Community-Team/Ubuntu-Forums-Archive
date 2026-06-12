---
title: "Computer semi shuts and displays a screen which I cant decipher"
date: 2013-06-01
forum: General Help
---

### Post by ravikanth1988 on 2013-06-01
Laptop: Linux X200 Tablet.
Dual boot - Windows 7 and Ubuntu 12.04
Problem:
In ubuntu the laptop shuts down and shows the following screen. I dont  know if it shows different screen everytime it shutsdown. I have attached one of the instances where this happened.[ATTACH=CONFIG]243411[/ATTACH]

This happens only occassionally - once in a week. When it happens it may happen many time.

In windows 7 this happens differently. The laptop just restarts. I dont know if this is because of the same problem.

---

### Post by ahallubuntu on 2013-06-01
If you have problems in both Windows and Ubuntu, it's probably a hardware problem.  Look at testing the RAM and the hard drive.

---

### Post by ravikanth1988 on 2013-06-01
Can you explain in plain english what is being displayed?

---

### Post by ahallubuntu on 2013-06-01
It's the contents of the kernel or system log.  You can see similar things yourself without crashing the machine: start Ubuntu, open a terminal, and type

```
dmesg
```

The fact that you see it as part of a crash seems to indicate some sort of hardware problem, especially because you have similar problems with Windows 7.

I can't quite read the last lines at the bottom, but they might indicate some clue to your problem.  Still, as I said, I would test the RAM and the hard drive at this point.  You can hold down the Shift key when you restart the machine and get a Grub menu and choose Memtest from there and let it run the full loop and see if you get any failures.

---

### Post by ravikanth1988 on 2013-06-02
With windows it just reboots. I get this message only when I use ubuntu. Do you think it could be a BIOS problem?

---

### Post by 3rdalbum on 2013-06-02
> **ravikanth1988 said:**
> With windows it just reboots. I get this message only when I use ubuntu. Do you think it could be a BIOS problem?

My money is on it being a problem with your RAM, or possibly with the cooling system on your CPU. After booting, the BIOS hands over control to the operating system, so it's not a BIOS problem.

The screen you are seeing is called an "Oops" (if you look carefully, you'll actually see the word "Oops") which indicates a kernel crash. On Windows, it's referred to as a "Blue Screen of Death", however by default Windows will not display the BSoD, it will just reboot whenever its kernel crashes.

---

### Post by ravikanth1988 on 2013-06-02
I have few more screen shots for diagnosis. The problem with taking it to service centre is that if it does not shut down at the centre I am back to square one. Is there way to pinpoint the problem? Thanks for the reply 3rdalbum :). The following are the shots:
[ATTACH=CONFIG]243457[/ATTACH][ATTACH=CONFIG]243458[/ATTACH]

The message displayed is different from what it was in the first post.

I have also observed that this shutdown is triggered by sudden jerks to the laptop - This may be imagination. 

Repeating the question: How do I exactly pin point the problem? If the laptop works fine at the service center I am back to square one.

---

### Post by ravikanth1988 on 2013-06-07
3rdalbum- should I just take it to a service centre?

---

