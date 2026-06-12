---
title: "Disk Management"
date: 2007-12-10
forum: General Help
---

### Post by sicofante on 2007-12-10
Hi,

I just installed Disk Management from Add/Remove... and I've got a nice icon under the System Tools menu. The software is supposed to allow the user to do some things, among them ***[Usermount lets users] mount, unmount, and format filesystems.*** That's exactly why I installed this app.

If I launch Disk Management I just get a dialog box saying:  [B]"There are no filesystems which you are allowed to mount or unmount.
Contact your administrator."[/B] Of course there are filesystems and disks (three, no less) in my system, so the key is that I am not allowed to do anything with them, yet I'm the only person using this computer, hence its only administrator... :confused:

Here would go my usual rant about Ubuntu usability, lack of design, disrespect for the newbies, etc., etc., etc. but today I just want to ask how do I get past that useless dialog box and do something useful with my new app?

Thanks for any help.

---

### Post by LaRoza on 2007-12-10
It sounds like you have to run it as root.

```

gksudo usermount

```

---

### Post by sicofante on 2007-12-10
OK. Now how do I run as root a menu entry? I don't want to use the terminal.

---

### Post by pietjanjaap on 2007-12-10
make the same icon, but put "gksudo" or "sudo" before the start command.

---

### Post by sicofante on 2007-12-10
I didn't make any icon (how would I?). I just installed Disk Management from Add/Remove... How do I change the installed menu entry to do what you suggest?

EDIT: Nevermind. I just found the Main Menu entry in Administration which allowed me to edit the conflicting menu entry. I added gksudo to the command a it finally ran. The software is so terrible I uninstalled it immediately. I finally had to go to the terminal and manually edit the fstab file. A BIG MINUS for Ubuntu. Not being able to manage disks graphically is simply unacceptable. (I had tried PySDM before and it's very poor as well.)

---

### Post by LaRoza on 2007-12-11
> **sicofante said:**
> I didn't make any icon (how would I?). I just installed Disk Management from Add/Remove... How do I change the installed menu entry to do what you suggest?

EDIT: Nevermind. I just found the Main Menu entry in Administration which allowed me to edit the conflicting menu entry. I added gksudo to the command a it finally ran. The software is so terrible I uninstalled it immediately. I finally had to go to the terminal and manually edit the fstab file. A BIG MINUS for Ubuntu. Not being able to manage disks graphically is simply unacceptable. (I had tried PySDM before and it's very poor as well.)

Well, it is better than a GUI in my opinion. It also sounds like you are not used to editing text files. Once you get used to it, you will find the Windows registry infuriating, and wonder why Windows does it that way.

If the software is "so terrible", make it better. You didn't spend much time using it, so I doubt you had enough time to judge it (I never used it).

Don't blame the software and Linux, it does exactly what it is supposed to do.

---

### Post by sicofante on 2007-12-11
> **LaRoza said:**
> Well, it is better than a GUI in my opinion. It also sounds like you are not used to editing text files. Once you get used to it, you will find the Windows registry infuriating, and wonder why Windows does it that way.
Don't be too fast assuming things. I've been editing files with vi for some 20 years now. I used IRIX well before Windows 95 was a success. That doesn't mean I find it the right way of working IN A DESKTOP OS. As a matter of fact, I find it's the worst way and according to the success of other GUI based operating systems, I'm not alone...

>  If the software is "so terrible", make it better. You didn't spend much time using it, so I doubt you had enough time to judge it (I never used it).
I appreciate the fact that any open source is susceptible to be changed. But that doesn't change the fact that a particular application is terrible. There's no time to spend with Disk Management (try it yourself and you'll see what I mean). It'll just read the fstab file and issue mount or umount commands. 

> Don't blame the software and Linux, it does exactly what it is supposed to do.I do blame Ubuntu (I didn't say "Linux" anyway) and the software. I've arrived to Ubuntu after all the hype about it being easy to use and so far this is pure sarcasm in certain areas. Administration is one of those areas.

---

