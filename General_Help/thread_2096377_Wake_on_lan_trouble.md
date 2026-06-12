---
title: "Wake on lan trouble"
date: 2012-12-19
forum: General Help
---

### Post by rucker222 on 2012-12-19
Hi guys,

I'm having real trouble getting wake on lan to work properly on my 64bit desktop machine at home using kde, the motherboard is an asus striker II extreme.

I've installed ethtool, added the below command to /etc/rc.local

```
ethtool -s eth0 wol g
```Enabled WOL in the bios, forwarded a port on my router to that machine and then put the machine to sleep.

So far so good...

The problem I'm having is after modifying rc.local the machine does not go to sleep again in the same way it used to.  Before modifying rc.local if I put it to sleep, I could hit a key on the keyboard and it would wake up and go strait to an unlock screen but now it starts up back at the bios logo screen 'Republic of Gamers' or what ever it is and gives the options of del for setup and tab for bios post message or something along those lines.

It does not matter what I do to the machine locally,  I could sit their all night bashing away at the keyboard but nothing happens. 

Even if I hold the power button to shut the machine down and then power it back up again it only gets to this point in the boot up and then sits there.  I have to literally unplug the power from the back of the machine and leave it off for a few seconds before I can get it to boot up again properly.

When I issue the wake on lan command from my laptop the desktop pc does fire up.  Unfortunately though it freezes at that same screen exactly as it does when I hit the keyboard. 
I did once get the machine to start up completely from sleep after issuing the wake on lan command a second time once it have fired up and got the the republic of gamers screen.

It seams almost like the computer after being put to sleep ignores anything other than the magic packets sent to it once it gets to that screen and ignores anything else.

I don't even understand why I am all the way back at the screen after waking the computer up anyway rather than at the unlock screen I used to get .

If anyone can help me to get this working properly i would really appreciate it.

Cheers.
Lee

---

### Post by tgalati4 on 2012-12-19
Sleep and Resume (whether local via the power switch or WOL) has always been troublesome in Linux.  There are so many variations of hardware and the ACPI power specification has many variations and implementations.

I would check all of the relevant logs in /var/log.  Then I would locate the sleep and resume scripts and print them out.  They are typically located in /etc/acpi.

It's possible there is a timing issue, so a couple of "sleep 2" commands might help.  

Does sleep work with the keyboard sleep button and resume work with the power button reliably?  First verify that sleep/resume is bullet-proof locally.

Also, send an email to ASUS with your issues.  It may be as simple as a BIOS patch and future BIOS upgrade.

---

### Post by rucker222 on 2012-12-22
> **tgalati4 said:**
> Sleep and Resume (whether local via the power switch or WOL) has always been troublesome in Linux.  There are so many variations of hardware and the ACPI power specification has many variations and implementations.

I would check all of the relevant logs in /var/log.  Then I would locate the sleep and resume scripts and print them out.  They are typically located in /etc/acpi.

It's possible there is a timing issue, so a couple of "sleep 2" commands might help.  

Does sleep work with the keyboard sleep button and resume work with the power button reliably?  First verify that sleep/resume is bullet-proof locally.
  
Also, send an email to ASUS with your issues.  It may be as simple as a BIOS patch and future BIOS upgrade.

Hey tgalati4

Thanks for the reply!  I need to do some more testing but it looks like things are working now.  

I didnt even think to check if the bois had an update available until you mentioned it.
I believe that was one of my problems as now it starts back at the unlock screen like it is supposed to.  That along with the fact that somehow while enabling WOL I must have changed my boot device priority.  It turns out the machine was freezing because it was trying to boot from my external HDD.  

No wonder it didn't want to start up! 

Thanks again!!!!

---

