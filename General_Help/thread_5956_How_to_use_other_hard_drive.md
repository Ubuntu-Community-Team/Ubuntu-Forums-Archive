---
title: "How to use other hard drive?"
date: 2004-11-23
forum: General Help
---

### Post by novaburst on 2004-11-23
I just installed Ubuntu Warty. I have another hard drive that is a slave. Ubuntu was installed on the Primary hard drive and when I type df at the command prompt I only see the first hard drive.

I know the second hard drive is setup to be /dev/hdb1. It was setup up that way from a previous install of Slackware.
I chose the automatic partitioning from the Ubuntu install. On my Slack installation I had my /dev/hdb1 with a mount point of /home.

My question is, how do I mount this drive so I can use it?

Is there anyway to set the mount point to /home, since it is already on /dev/hda1?

---

### Post by wazoo42 on 2004-11-23
What filesystem did you use?  You should be able to:

mount -t *filesystemtype* /dev/hdb1 /temp

You can use what you like instead of /temp.  As far as a permanent solution, you need to add a line to your /etc/fstab.

---

### Post by novaburst on 2004-11-23
I used ext3.

Cool, I will try that, thank you very much!

---

