---
title: "VMplayer only starts from &quot;sudo vmplayer&quot;"
date: 2007-02-20
forum: General Help
---

### Post by PaulFXH on 2007-02-20
I've been using vmplayer for about a week and I'm very impressed---easy install and works very well.
Up to now I've been discovering some exciting new feature every day.
However, today I had a bit of a set back and would appreciate some comments/advice.

I tried to run my existing (physical) Windows XP  in vmplayer (using this guide: [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Installation_On_Ubuntu_With_Vmware_player.html)](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Installation_On_Ubuntu_With_Vmware_player.html)).
However, I kept getting a file permission problems which prevented it working. So, I used "sudo vmplayer" and that got rid of the permission problems.

However, shortly after this, I found that vmplayer would not open at all due to a libpng problem which I was able to overcome by following the advice in another forum thread.
But, now vmplayer won't start at all UNLESS I type "sudo vmplayer" which means I can't use my icons.
Even now, before vmplayer launches, I get this error message:
[CODE(vmplayer:8802): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.][/CODE]
This doesn't stop anything but may be a clue as to why my vmplayer icons (or "vmplayer" in a terminal) don't work any more.
I have reinstalled vmplayer but this made no difference.
Has anybody had a similar problem and knows how to fix it?

---

### Post by A_arthur_N on 2007-03-23
I had the same problem.  I didn't find a solution to it but there is a way of running a sudo command in an icon, right click on it and change the launcher to:

gksudo vmplayer /location/filename.vmx

---

### Post by PaulFXH on 2007-03-23
Thanks A_arthur_N for that tip.
However, I did actually solve the problem by simply changing the permission on the ~/.vmware back from Root to me.
From what I can see, using Sudo to launch VMplayer caused this permission change to occurr.
The reason that I was forced to use Sudo to launch VMplayer related to the fact that I wasn't at that time a member of the Disk group which is the owner of the Windows partition in Ubuntu.
Best wishes
PaulO

---

