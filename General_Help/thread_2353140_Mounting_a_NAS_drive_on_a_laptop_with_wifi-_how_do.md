---
title: "Mounting a NAS drive on a laptop with wifi- how do I get it to not slow down startup"
date: 2017-02-19
forum: General Help
---

### Post by ravalox on 2017-02-19
So I have a laptop that by nature relies on wi-fi connectivity, I also have a NAS on my network.  I set it up in fstab and when I start up my machine I can connect to it in Ubuntu/Kubuntu/Xubuntu- once the machine is started that works just fine, however if I take this out of fstab the machine boots MUCH faster because it's not waiting on the mount in fstab to timeout.  How can I get the best of both worlds?  I know I could write a shell script but then I'd have to go tamper with it whenever the IP address of my nas changes which I'd like to avoid- this seems like a problem linux has likely solved.  I'd like it not to mount on startup as it has no network access until the desktop loads the connection information- but then mount it when it's connected; sparing me a slow start.

---

### Post by papibe on 2017-02-19
Hi ravalox.

I'd recommend taking a look at [autofs]("https://help.ubuntu.com/community/Autofs").

You would avoid the fstab entry, and thus a faster boot. Also, you won't actually mount the NAS share until you actually access the directory, like with a 'cd' command, or clicking on the directory from the file manager.

IMHO that would solve most of your current inconveniences.

You can go even further and configure autofs to use a script before mounting the remote directory, which would be specially useful when you are not at home.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Morbius1 on 2017-02-19
Another option is to not have it automount in fstab at all.

For a given generic fstab entry:
```
//server/share /mountpoint cifs username=xxx,password=yyy,uid=1000 0 0
```
Change it to this:
```
//server/share /mountpoint cifs username=xxx,password=yyy,uid=1000,user,noauto 0 0
```
The noauto will make it so it doesn't automount at boot and user will make it mountable without being root.

You've got a couple of options at this point:

[1] If you set the mountpoint to be under /media or your home directory the fact that it's in fstab will force the creation of an icon in the file manager - [COLOR=#0000cd]that is actionable[/COLOR]. Click on it and it will look to fstab to find out how and your share will mount. Right click it to unmount.

[2] Or ... You can create a startup application entry that's pretty simple:
```
mount /mountpoint
```
That too will will force it to go to fstab to find out how.

In both cases the share doesn't mount at boot but after login/

[COLOR=#0000cd]**EDIT**[/COLOR]: Actually, option [1] is sorta kinda like a poor man's version of AutoFS - with one exception. AutoFS can unmount by itself after a user specified duration of inactivity whereas my method will not.

---

### Post by ravalox on 2017-02-19
I tried autofs- I couldn't get it to work; I followed the guides and it just won't work.

auto.master entry:

+auto.master
/path/to/folder /etc/auto.nfs


auto.nfs entry:
Mediashare <ip.address>:/volume1/Mediashare

Even made the auto.nfs permissions mirror the auto.net and auto.smb files tthat come with autofs- no joy.  I did the noauto fstab entry and it solves the boot problem however the things I read suggest I would prefer autofs; if only it would work.

---

