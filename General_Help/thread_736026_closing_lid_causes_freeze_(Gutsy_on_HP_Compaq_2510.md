---
title: "closing lid causes freeze (Gutsy on HP Compaq 2510p)"
date: 2008-03-26
forum: General Help
---

### Post by Ace_NoOne on 2008-03-26
Hello,

When closing the lid on my [HP Compaq 2510p]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-306995-3355633.html"), the touchpad button lights up (indicating that the touchpad is disabled) and the machine goes to sleep (suspend? hibernate?).
 Most of the time I can't wake it up anymore afterwards. 

This happens although I have disabled any such behavior (System > Preferences > Power Management > On AC/Battery Power > When laptop lid is closed: Blank screen).

After reading several posts here, it seems that I'm not to the only one with this problem, but I couldn't find a solution.

This is a very annoying issue, so I'd be immensely grateful for any help!


(Apart from this issue, Ubuntu *Just Works* on this machine though - only the SD card reader and some unimportant special buttons seem unsupported.)

---

### Post by cmnorton on 2008-03-26
Look through your logs (/var/log), and look at the output of dmesg. Is there BIOS setting that covers power behavior?

---

### Post by Ace_NoOne on 2008-03-26
Thanks for the quick response!

I've been looking through some of the logs, but I'm not at all sure what I'm looking for (still pretty much a Linux newbie).
Same with the *dmesg* output (see [http://pastebin.com/m734814fe](http://pastebin.com/m734814fe)).

I hadn't thought of checking the BIOS - will do that later (can't reboot right now).

---

### Post by cmnorton on 2008-03-27
This is one of those wierd problems. This is an HP, and they're pretty supportive of Linux. I'd start bugging them from the hardware point of view. You can also submit a question or bug at Ubuntu Launchpad. That never hurts.

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by Ace_NoOne on 2008-03-28
> **cmnorton said:**
> This is an HP, and they're pretty supportive of Linux.
Great! I wasn't aware of that.

> **cmnorton said:**
> I'd start bugging them from the hardware point of view.
I'll see what I can do. (Expected reaction: "What is this 'Linux' you speak of? Why should we care?" - i.e. I'm skeptical, despite your assertion above... )

> **cmnorton said:**
> You can also submit a question or bug at Ubuntu Launchpad. That never hurts.
For that I'd need more specifics - i.e. figure out what really causes this.


PS: No relevant settings in the BIOS, it seems.

---

### Post by makzimuz on 2008-05-01
Hi there,

A couple of my colegues and i have been having the same problem. Our linux guru at work has been able te solve this problem.
This is how you can sove it:

-open a terminal window
- at the prompt enter the following:
sudo echo 1 > /proc/acpi/video/C099/DOS
and all your problemens should be over. it works like a charm for me.

BUT! This is not persistent if you do a reboot of your system the setting is gone. To overcome this you can add this line:
echo 1 > /proc/acpi/video/C099/DOS
to the file /etc/rc.local
Then the setting is applied every time you boot your machine.

I don´t know exactly what the setting does. It has something to do with letting the video card handle power management is stead of the OS.

I hope it helps.

---

### Post by Ace_NoOne on 2008-05-01
> **makzimuz said:**
> sudo echo 1 > /proc/acpi/video/C099/DOS
[...]
I don´t know exactly what the setting does. It has something to do with letting the video card handle power management is stead of the OS.
Thanks for sharing, makzimuz!

However, since this is overriding a system setting, I'd rather have someone confirm this isn't harmful before giving it a try.

---

### Post by Ace_NoOne on 2008-05-05
So I've tried it after all - and it doesn't work, unfortunately.
After the first two times I could "revive" the machine, but the third time it locked up again.

---

