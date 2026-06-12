---
title: "Unable to boot - minimal BASH-like grub"
date: 2012-11-04
forum: General Help
---

### Post by Endlesskiss on 2012-11-04
I've been running Ubuntu quantal (12.10) x86 with wubi for about 1 week. everything went smooth and slowly but surely I started neglecting my previous Windows 7 installation.

I still went to Windows 7 for Guitar Pro & iTunes sometimes...

one day Windows 7 wanted to run a chkdsk so I interrupted it and went back to my Ubuntu.

Yesterday, Windows 7 decided to fight back to get it's lost dignity and started a 'Windows repair tool', it happened all night long and when I woke up it showed me the famous "Send\Don't Send" window.

Now when I try to boot into Ubuntu I get the "minimal BASH-like" grub and I can't do anything...

about WIndows 7... when I try to boot (safe & normal mode) I get a black screen just before the logon screen...

I was searching the net for a solution and I found 'boot-repair', followed the instructions nicely and got this: [http://paste.ubuntu.com/1332180/](http://paste.ubuntu.com/1332180/)

nothing's fixed right now... I'm running Ubuntu via the 'Try Ubuntu' feature from the Live CD... I'm backing up important stuff but I really don't wanna lose my Windows stuff (both Ubuntu and W7 are on the same partition).


what am I supposed to do next?

Sincerely,
Adam.

---

### Post by bcbc on 2012-11-04
This explains what's going on with the Wubi install and how to fix it (if chkdsk recovered the entire root.disk): [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

I'm not sure what's happened to Windows. That's not typical.

Boot repair doesn't do much for wubi installs. It needlessly replaces the windows bootloader and in your case resets the boot flag on the same partition. I don't think it causes any issues, but IMO it's best to avoid making unnecessary system changes.

If you're using Ubuntu more than windows it's best to move to a traditional dual boot. If you fix your Wubi root.disk you can migrate it: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

