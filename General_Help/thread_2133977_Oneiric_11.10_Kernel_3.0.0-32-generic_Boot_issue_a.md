---
title: "Oneiric 11.10 Kernel 3.0.0-32-generic Boot issue and acting strange like a virus!"
date: 2013-04-09
forum: General Help
---

### Post by archangel2003 on 2013-04-09
This has been an on going issue.
 Most of the time when I boot up, it only goes to the purple screen with the dots after I put in the password going no further and I only have the mouse to move around and access to nothing.
 

 

 Sometimes it goes as far as the desk top picture showing up and nothing more, no icons and mouse pointer only.
 After several attempts to boot, (3 TO 10) it goes all the way through and boots all the way up like you would expect.
 However, even though it boots, the matrix background I have does not flow as it did when it was first installed.
 

 Now it does not go beyond the purple screen after the password.


 The only way I can boot now is to go to recovery mode and I am using it now to post this.


 Even though the desk top looks clunky with the huge icons, the matrix background is nolonger static and flows like it should, where as before it would not flow.

Also.

   
 The time delay once I choose Ubuntu over Windows, each step in the boot up process is unusually long as if there is a 30 second countdown to every step.

 

 When I first partitioned the hard drive and Ubuntu was installed, I would go from choosing Ubuntu over Windows, to typing the password, to up and running in 15 seconds or so, REAL FAST!

 

 Now it's 90 seconds minimum if it boots up to forever and I have to push the power button to kill it and start over again and again until it boots all the way up.

This is killing my Ubuntu joy!

This May my daughter is supposed to come out and she is Ubuntu wise, but until then I would love to get it fixed.

---

### Post by kuifje09 on 2013-04-09
I understand your system is dual bootable.   If you boot into windows thendoes it boot as usual.
I mean is it only related to ubuntu or a problem with the disk ....

The quickest check to do is force a fsck at boot.

as root type
```
touch /forcefsck
```

---

### Post by archangel2003 on 2013-04-09
> **kuifje09 said:**
> I understand your system is dual bootable.   If you boot into windows thendoes it boot as usual.
I mean is it only related to ubuntu or a problem with the disk ....

Windows is acting normal, and I never go on line with Windows, only work CADD with it.

> **kuifje09 said:**
> The quickest check to do is force a fsck at boot.

as root type
```
touch /forcefsck
```


I have no idea how to "force a fsck at boot".

---

### Post by kuifje09 on 2013-04-10
fsck is the way to check your disks integrity. There may be undetected errors sometimes.
Depending on when the last check was done automaticly it may not help.
However it does not harm when you force a check right now, to see if there is some problem with the disk wich is causing the slow boot and more...

when you do type as root     

touch /forcefsck

Then you will force the system to do a check at boot time.

---

### Post by kuifje09 on 2013-04-10
After the check is done, the system is up and running you can have a look at the loggings.  I think   /var/log/kern.log  and /var/log/syslog
could give messages about the disks.

The command [COLOR=#800000]    dmesg[/COLOR]      could show some messages too.

---

### Post by mörgæs on 2013-04-10
Please give a complete hardware description.

---

### Post by Impavidus on 2013-04-10
11.10 runs out of support this month, so moving on to the next version would be a good idea. Doing a clean install of 12.* may be the quick-and-dirty way out of your problem. Well, not really dirty, as it gives you a cleaner system than you have now, it's just not the neat way of solving problems.

---

### Post by archangel2003 on 2013-04-10
[FONT=arial][SIZE=2]**[[COLOR=#C61919][B]mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075")

Toshiba Satellite-P775
Intel Core i7
8 GIG ram
750 GIG HD
Ubuntu [/B][/SIZE][/FONT][FONT=arial][SIZE=2][B]Oneiric 11.10 
Kernel 3.0.0-32-generic

[/B][/SIZE][/FONT][**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721")

If I were to upgrade, I will have to wait unti my daughter comes out and helps me as I don't want to lose anything through my own inexperience.[FONT=arial][SIZE=2][B]

The thing [SIZE=2]I like about this system i[SIZE=2]s, well,[/SIZE] I surf the internet like a blind and clueless idiot as I [SIZE=2]never [/SIZE]had virus issues with Ubuntu[SIZE=2], only with [/SIZE][/SIZE][/B][/SIZE][/FONT][FONT=arial][SIZE=2]**[SIZE=2]Windows[/SIZE]**[/SIZE][/FONT][FONT=arial][SIZE=2][B].

The only thing I do for protection is not open an attachment[SIZE=2] not sent by a trusted source.[/SIZE]

A[SIZE=2]re there other issues I am unaware[SIZE=2], and [SIZE=2]s[/SIZE]hould be careful of?[/SIZE][/SIZE]
[/B][/SIZE][/FONT][FONT=arial][SIZE=2][/SIZE][/FONT]

---

### Post by Impavidus on 2013-04-10
Google tells me that computer has Intel graphics. There should be no graphics driver problems, that's something we can rule out.

I don't think you have a virus. Native Linux viruses aren't found in nature, cross-platform viruses and windows viruses-in-wine need a very specific way to get activated. Surfing alone won't won't infect you. Even clicking on attachments should be save. You'd have to explicitly enable them with root privileges to get your symptoms.

You can try fsck, as described before, and you can try logging in to your guest account. If that works the problem is in the user configuration, which is suggested by the fact that you do get to the login screen.

---

### Post by oldos2er on 2013-04-10
Viruses are not a big concern on Linux, however there are more important security issues Linux users need to be aware of. I'd start by reading [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

