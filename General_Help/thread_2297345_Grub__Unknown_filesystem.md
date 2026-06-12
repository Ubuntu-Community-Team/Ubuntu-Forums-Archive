---
title: "Grub : Unknown filesystem"
date: 2015-10-02
forum: General Help
---

### Post by manish19 on 2015-10-02
[COLOR=#111111][FONT=Ubuntu]I had installed Ubuntu 14.04 on a Windows 7 Computer. It worked perfectly for almost a year. I was playing around with Ubuntu settings ( a cardinal sin, I know !) and in specific I was trying to change the username of my Computer. So I made very minor changes to the files etc/group , etc/hosts , etc/users. Those changes involved replacing the name manohar (original username) with Manish (new username). I did the mistake of not replacing each and every instance of manohar. When I restarted the computer I was shocked to realise that I was unable that the username stayed manohar and more importantly I was unable to login with my old password. Note : Windows 7 was working perfectly. So, I went to advanced recovery mode and went to root mode. And now here is the wierd part, I was able to login to root using username "Manish" and my old password. Originally, the root was read-only due to which I was unable to make any changes to the files. I changed it to read/write mode by executing **mount -o remount,rw /** . Then, I replaced the instances of "Manish" with "manohar" (actually I am not sure if I changed it everywhere). I restarted the computer and instead got greeted by a Grub error of unknown filesystem. I checked the available partitions using ls command. Sadly, for all partitions I got unknown filesystem. Now, I am unable to access both Ubuntu and Windows.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What do I do? I preferably want a solution which recovers my Ubuntu account as it had some useful documents. I don't value the Windows 7 as much.[/FONT][/COLOR]
[CENTER][/CENTER]

---

### Post by oldfred on 2015-10-02
Duplicate thread. Closed
See this:
[http://ubuntuforums.org/showthread.php?t=2297346](http://ubuntuforums.org/showthread.php?t=2297346)

I am assuming since only a minute apart that forum hiccuped, which it sometimes does.

---

