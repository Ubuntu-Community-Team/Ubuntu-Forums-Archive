---
title: "Boot up issues"
date: 2006-10-26
forum: General Help
---

### Post by bogey on 2006-10-26
I had a working dual boot system with Ubuntu 6.06 and Windows XP.

I was trying to install Slackware, reformatted the partition that I was installing Slackware on from ReiserFS to Ext3, and the installation failed.

My problem is that now when I try to boot into Ubuntu it fails and I end up at the boot prompt. I entered 'StartX' and Xfce started up but with errors (I have Gnome, KDE, and Xfce desktops loaded; Gnome is default).

I am sure the problem is due to me reformatting the partition from ReiserFS to Ext3. Any suggestions on how to fix my boot up problem?
Thx, Don

---

### Post by jazzgossen on 2006-10-26
Do you have XP and Ubuntu on their own partitions? If you've formatted any of those, you will of course need to reinstall.

Otherwise, what exactly happens when yout boot? What messages do you get? Are they the same when you boot Windows as when yuo boot Ubuntu?

---

### Post by bogey on 2006-10-26
XP is on sda, and I can still boot into and use Windows.
Ubuntu root is on sdb1, swap is on sdb2, home is on sdb6.
I was formatting sdb3 for Slack.

During a normal Ubuntu bootup, it starts out text based, then switches to color text based and then to the GUI login. Now it starts out text based (black and white) and stays that way until it goes to a boot prompt. No error messages.

---

### Post by jazzgossen on 2006-10-26
Without error messages, it's not easy to tell what's going wrong. Try to edit the boot entry in GRUB (press "e" in the GRUB menu) and remove "quiet splash" from the kernel line, if you have that there. Hopefully there will be more messages then. 

What do you mean by a boot prompt? I take it that you don't get to a login prompt at all?

---

### Post by bogey on 2006-10-26
Sorry, I meant login prompt. 

I am at work now, will edit GRUB when I get home tonight to and see if I am getting any error messages.

---

