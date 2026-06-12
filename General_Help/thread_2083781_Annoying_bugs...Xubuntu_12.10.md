---
title: "Annoying bugs...Xubuntu 12.10"
date: 2012-11-13
forum: General Help
---

### Post by kiasta on 2012-11-13
These bugs are always present upon a fresh install. I've re-installed 4 times already and they are there every install.

First is my USB drive has 2 icons on the desktop, 1 of them goes away when I either remove the USB drive or uncheck removable drives in the desktop settings. While the other icon stays there no matter what, and I cannot remove it nor unmount it.

Second bug has to do with the default archive manager (Archive Manager). Every time I select the extract here option in the context menu it crashes, I would post the crash log but I do not know where to find the logs and the crash report is not exactly copy/paste friendly... Xarchiver seems to work just fine, though, so until it's fixed I just remove Archive Manager entirely.

So as for the first bug I will elaborate. It happens when I reboot the computer with the USB drive in the port. If I reboot the computer without the USB drive in the port there are no mounted icons and it works as it should when I insert it into the USB port. This is annoying because I do not have a working cd-drive so I use this USB drive for my OS installations and backups. So I usually always have it plugged in.

Mounted Devices:
[http://i.imgur.com/VaYNr.png](http://i.imgur.com/VaYNr.png)

Archive Manager Crash:
[http://i.imgur.com/ux3lL.png](http://i.imgur.com/ux3lL.png)
[http://i.imgur.com/occfn.png](http://i.imgur.com/occfn.png)
[http://i.imgur.com/ZwPw6.png](http://i.imgur.com/ZwPw6.png)

The rest of the line of code that was cropped just says archive .session files

Anyways, not sure if these are considered bugs related to Ubuntu or XFCE nor do I know where else to post this. Move if needed.

Any ideas how to fix that icon/mount bug?


*EDIT* I didn't realize I set this thread to kubuntu, could a mod change it to xubuntu? Not sure why I put Kubuntu in the title either, sorry for the confusion.

---

### Post by Toz on 2012-11-13
Both are known bugs:

Duplicate icons on desktop: [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375")

Archive manager crash: [https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1038336]("https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1038336").

---

### Post by kiasta on 2012-11-14
> **Toz said:**
> Both are known bugs:

Duplicate icons on desktop: [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375")

Archive manager crash: [https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1038336]("https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1038336").

I'll be keeping an eye out for when a fix is discovered. Thanks Toz.

---

### Post by Toz on 2012-11-14
There are some workarounds listed in the comments if you wanted to try them until the fixes are made available.

---

### Post by LewisTM on 2012-11-14
_Desktop_: Until it's fixed, just press F5 on the desktop. Duplicates gone!

_Archive_: Make sure **squeeze** is installed then remove file-roller ('Archive manager'). Thunar will use Squeeze instead for extracting.
I happen to like file-roller so here is a command to make Thunar use squeeze for extracting even if file-roller is present:
```
cd /usr/lib/x86_64-linux-gnu/thunar-archive-plugin
sudo mv file-roller.tap file-roller.tap.bak
sudo ln -s squeeze.tap file-roller.tap
```
Cheers!

---

### Post by pkadeel on 2012-11-14
File-Roller bug is apparently fixed and Thunar users can fix it manually via command line.
I just applied that fix on my Xubuntu and it seems fixed.

Link is present in Toz post.

---

### Post by kiasta on 2012-11-14
> **Toz said:**
> There are some workarounds listed in the comments if you wanted to try them until the fixes are made available.

Yeah, I've been working on the mounting issue, apparently the thunar proposed package is not working for me. I'll try the other fix, but this is a production machine so I am not sure if I want to do that or not. I develop php applications and I'd rather just wait for the ubuntu team(or whomever is in charge of fixing bugs) to fix the issue.

I've already made a post about it on there, with a screenshot attached. As for the Archive Manager, I've not yet had the chance to look into it.

Thanks again Toz :)

---

### Post by kiasta on 2012-11-14
> **LewisTM said:**
> _Desktop_: Until it's fixed, just press F5 on the desktop. Duplicates gone!

_Archive_: Make sure **squeeze** is installed then remove file-roller ('Archive manager'). Thunar will use Squeeze instead for extracting.
I happen to like file-roller so here is a command to make Thunar use squeeze for extracting even if file-roller is present:
```
cd /usr/lib/x86_64-linux-gnu/thunar-archive-plugin
sudo mv file-roller.tap file-roller.tap.bak
sudo ln -s squeeze.tap file-roller.tap
```
Cheers!

I don't have Squeeze installed and have uninstalled Archive Manager, perhaps I'll re-install it and get it fixed; though, I rather like Xarchiver. Besides, I'm currently working on a proposed version of thunar so I really just want to work on one bug at a time. I appreciate your help, though.

---

### Post by LewisTM on 2012-11-14
> **kiasta said:**
> I don't have Squeeze installed and have uninstalled Archive Manager, perhaps I'll re-install it and get it fixed; though, I rather like Xarchiver. Besides, I'm currently working on a proposed version of thunar so I really just want to work on one bug at a time. I appreciate your help, though.
If you install Xarchiver, the thunar-archive-plugin will use it for your operations. The install routine adds file /usr/lib/thunar-archive-plugin/xarchiver.tap

---

### Post by kiasta on 2012-11-14
> **LewisTM said:**
> If you install Xarchiver, the thunar-archive-plugin will use it for your operations. The install routine adds file /usr/lib/thunar-archive-plugin/xarchiver.tap

I've already installed Xarchiver. Like I said in my OP: "Xarchiver works just fine". My immediate concern, however, is the mounting bug; it's rather annoying. I was just bringing the bugs to the attention of the community, and perhaps some help with each. I assumed both of these issues were problems with configuration files and easily fixed. Since they are official bugs, I'll just wait until official fixes are released. I am on a production computer and I do not want to apply quick fixes or workarounds, if this was a personal computer that would be a different story.

Thanks, though, for your help :)

*EDIT* I was just informed that was the wrong bug for the icon bug, here is the correct link: [Bug #1072137]("http://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1072137") It has yet to be resolved.

---

### Post by Elfy on 2012-11-15
Fix for the desktop was released today (might need to enable proposed to see it, I'm not sure) but I don't see desktop drives twice now nor duplicates in thunar.

---

