---
title: "Windows install not found when I boot to the XP CD."
date: 2007-01-08
forum: General Help
---

### Post by Punctuation M on 2007-01-08
I've a question in regards to my PC.

I have a 80GB hard drive with four partitions on it, two belong to Windows and the other two belong to Linux (Extension 3 and Swap). Problem is when I boot to the Windows XP CD, it does not find the Windows XP install so I am unable to log onto the recovery console to set the Master Boot Record to Windows default. At the moment GRUB (Linux) has taken over the MBR but I would like to delete the Linux partitions, but if I do, I would get nothing but GRUB error messages. So, how can I set the MBR back to Windows default if I am unable to log onto the recovery console?

I realise this is a windows issue but to be honest, I've tried some of the windows help sites and chat rooms and they're saying things like "Well, first if you tell us what GRUB means, we can try and help you fix it" or "Why would you install linux if you know nothing about it", and even "We don't support linux, it's a tool for hackers". Now, I installed it because I am interested in it; and would rather install it on my laptop, then delete the linux partitions on my PC (have it running windows only for the family). I would really like some help because the people who deal with windows issues don't quite understand how GRUB takes over the MBR and they keep saying log onto the CD and type FIXMBR at the C:\> prompt; but how the hell am I suppose to do that when I can't log onto the recovery console, all I get when I boot to the CD is the install options, and even if I try to install the XP it says <No drives found> or something similiar.

Help please?

---

### Post by oracle5 on 2007-01-08
I really can't think of an easy way to do it if fixmbr doesn't work. I can think of an elaborate way like deleting the ubuntu partition, resizing the windows partition to take up all but about 300mb. Then on that 300mb install Damn Small Linux and set grub up to boot windows first after 1 second or something short like that. Then you would lose minimal disk space and it would be almost back to normal. That probably doesn't help but its the best I could come up with.

oracle5

---

### Post by Punctuation M on 2007-01-09
Well, I appreciate that information, but why has this occured? do you know? Why isn't the XP CD finding the drive? When I load the Fedora or Kubuntu, it sees the drive, but I tryed 6 XP and two Vista disks, and it can't find the drive. Man, Windows is driving me crazy; sending error reports all day, dahm joint charges an arm and a leg for the OS and it crashes ten times as much as Linux. They need to throw another cake at Bill I think, to snap out of it and hire people who can do the job, correctly.

There's nothing more I would like to do then to have Kubuntu or something similiar on the PC, but unfortunatly, the family don't quite know the OS nor do they know how to navigate. I told them that I could show them, but they would rather run the Windows because they say it's more user friendly - and I've to respect that because it is there computer. 

Does anyone know why the Windows XP CD is not seeing the hard drive installed? Come on people, you guys deal with linux, you have to know what I'm talking about?

Don't just read the post and think I've solved it, because I need your help.

There has to be a geek someone in this forum who knows computers back to front who has seen this problem.

Any help would be greatly appreciated.

---

