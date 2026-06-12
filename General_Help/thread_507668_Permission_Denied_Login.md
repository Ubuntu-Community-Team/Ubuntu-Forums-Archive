---
title: "Permission Denied Login"
date: 2007-07-23
forum: General Help
---

### Post by eluser on 2007-07-23
Having a problem. When booting up Ubuntu it doesn't starts in a terminal like mode (pardon my terminology, I'm not super familiar with linux) instead of the normal login mode, I try to log in as "administrator" (there is no root account, this is the only one) and this fills the lines

bash: /dev/null: Permission denied

I've read some of the other topics related to this, but the closest to my problem suggested logging in as root and changing the permissions of the /dev/null directory. Problem is, there's no root account for me, just administrator. 

The permission denied issues started before i restarted. I was logged in and everything locked up, couldn't access anything. Last changes I can remember making is changing the permissions of the contents of "bin" (or possibly "sbin") from 755 to 777. I didn't figure this had anything to do with it since it's a different directory and I was adding permissions, not removing them. Then the system shut down and, like said, I can't log in. 

Is there any way to change the permissions of the /dev/null directory or another walk-around to get Ubuntu up and running again?

Oh, I'm also running this as a virtual machine on fedora if that makes any difference.

---

### Post by apjone on 2007-07-23
reboot. At grub screen press  ESCAPE and choose single user login (recovery mode). This should boot up and log you in as root.

Yes there is a root account, you just have probably not set a password on it. Unless of course you removed root.

---

### Post by eluser on 2007-07-23
EDIT: Successfully changed permissions on that folder, and had to end up changing the permissions on the contents of usr/bin folder too (which did make a difference after all) and I can get in now. Thanks!

---

