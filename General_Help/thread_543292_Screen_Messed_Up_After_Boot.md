---
title: "Screen Messed Up After Boot"
date: 2007-09-04
forum: General Help
---

### Post by jyank on 2007-09-04
EDIT: I've figured this out, feel like an idiot

I went back into recovery mode and reconfigured x again but instead of using nv I switched to vesa and and lower resolution and it worked.  I guess since it was a fresh install it didn't know what NV was.

Hello,

I decided to re-install Ubuntu (7.04) to try and mess with somethings, but I'm having an issue after booting up.  I  think I know the issue, but correcting it is what I don't know.

When I boot into Ubuntu everything goes fine, I see usplash and the logo, but I believe the problem is when X starts, it boots me to the login screen, but it looks like this:

[[IMG]http://img212.imageshack.us/img212/8443/0904072204ik2.jpg[/IMG]](http://imageshack.us)


I had the same thing happen when I tried to install, but I rebooted and hit F4 and changed the resolution to something lower since I figured the correct drivers were not installed during installation, and that worked fine, I got everything installed.

I assume now that its the same issue, however, I can't seem to fix it.  I can boot into a command line by booting via recovery mode.  I have also tried just logging in at the screen and I can succesfully, but when I try to switch to a commandline, the screen stays messed up.

I have searched the forums and have tried

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

```

I went through all the settings and set everything up correctly, with NV as the driver and all the supported resolutions, but yet the same thing still happens.

Not really sure what else to try, any help is appreciated.

Thanks

---

