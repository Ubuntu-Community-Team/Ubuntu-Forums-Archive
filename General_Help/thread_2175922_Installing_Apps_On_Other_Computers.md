---
title: "Installing Apps On Other Computers"
date: 2013-09-21
forum: General Help
---

### Post by llanitedave on 2013-09-21
I know this should be dirt-simple, but I think I need guidance anyway.  My wife and I have satellite internet, which is pretty bandwidth limited.  For both of us to keep up with all the regular updates and upgrades would push our bandwidth to unacceptably high levels.

I work away from home, and I can keep up with application downloads and updates just fine using the local motel internet.  What I want to do is install those apps and updates on my wife's machine when I'm home.  I know there's a way to do this other than having to install each time from source, but I'm having trouble finding a straightforward way to do it.  What would be ideal is to create a kind of local "software center" on a usb stick that I can use as an installation source.

She's on Ubuntu 12.04, but would like to upgrade.  I use both Ubuntu and Kubuntu 13.04.  I'd hope that wouldn't make a difference.

What's the best approach for this?

---

### Post by tgalati4 on 2013-09-21
There is no dirt-simple method, but reading these links might give you some insight into what might work in your situation.  Regardless, you would need to get both to the same Ubuntu level, otherwise the downloads you put on your machine won't match your wife's machine.  So, you want to get both to the same level.

[https://help.ubuntu.com/community/Rsyncmirror](https://help.ubuntu.com/community/Rsyncmirror)

[https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)

Your downloads are stored in /var/cache/apt/archives.  But these are only good for your machine and Ubuntu version.  You can simply copy some over and try installing them with *gdebi* once your machines are up to the same Ubuntu version.

```
gksudo gdebi-gtk
```

---

### Post by stinkeye on 2013-09-21
...also there is [**_[COLOR="#B22222"]Synaptic/PackageDownloadScript[/COLOR]_**]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")
Download on one computer, install in another.

---

### Post by llanitedave on 2013-09-22
Thanks to both of you.  This gives me something to get started with, at least.  It's not as simple as I'd hoped, but it looks doable.

---

### Post by stinkeye on 2013-09-22
> **llanitedave said:**
> Thanks to both of you.  This gives me something to get started with, at least.  It's not as simple as I'd hoped, but it looks doable.
The synaptic solution is fairly simple.
You can test at home first. Without a big download.

On the machine you wish to update, open synaptic and hit the reload button to check for updates.
Mark just one small update. 
Now instead of applying the update go to file>generate package download script.
Save the script to it's own folder on a usb drive.
All your doing is creating a bash script with wget lines to download the deb file for each marked upgrade.

Have a look at the generated script to check you only have one wget line.
eg
```
#!/bin/sh
wget -c http://ftp.iinet.net.au/pub/ubuntu/pool/main/a/apt/libapt-inst1.5_0.9.7.7ubuntu5_amd64.deb

```
The wget line points directly to the upgrade which means the two computers you use do not have to be the same release.

Follow the directions in the previous link and when you've done it once it will make sense.

---

