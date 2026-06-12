---
title: "Lightdm returns to login"
date: 2013-12-16
forum: General Help
---

### Post by Tristan_Williams on 2013-12-16
I have a Dell Vostro 220. I have installed Ubuntu Minimal from the mini.iso on this website: [https://help.ubuntu.com/community/Installation/MinimalCD#A32-bit_PC_.28x86.29](https://help.ubuntu.com/community/Installation/MinimalCD#A32-bit_PC_.28x86.29)

It has been installed and maintained for over 2 months, and has not given me any problems until now.

I have Xfce4 installed and the 3.11.0-14-lowlatency kernel installed.

Today, I installed LightDM, because my mother and siblings do not know how to log in and start XFCE from the command line.
It installed with no problems.
The contents of /etc/X11/default-display-manager are the following:
```

/usr/sbin/lightdm

```

After installing and configuring so that lightdm would start on boot, I did one last update/upgrade, and rebooted.

After booting, lightdm showed up, and showed everyones profiles just like i expected.

When I go to log in, I type my password and after pressing ENTER, it starts to load Xfce4...

But then it just returns to the login screen...

I can login to tty1 with no problem.

And before you say it, yes, I tried to delete ~/.Xauthority... But it wasn't there so no problem...

SO.... Where did I go wrong?



Edit:

It is only two users that have this issue. The Administrator, and the Guest Account.

It strikes me as odd that those two accounts are the only ones that were created by Ubuntu.
The other three accounts were created by me, personally. So I think it is just an issue with system created accounts.

Also, I ran the following command:
```

ls -al ~/.Xauthority

```
and got the following output:
```

ls: cannot access /home/tristan401/.Xauthority: No such file or directory

```

And I ran the same command for ~/.ICEauthority, and got the following output:
```

-rw------- 1 tristan401 root 3014 Dec 16 20:57 /hone/tristan401/.ICEauthority

```

So obviously something is going on with the system-created accounts...

---

### Post by Tristan_Williams on 2013-12-18
For anyone who sees this thread in the future, I found no solution. 

I discovered that all of the display managers (gdm, lightdm, xdm, lxdm) had the same problem.

I simply uninstalled it, and now I am back to logging in with the command line.

I did find a way to autostart my DE, but that happens after you log in through command line.


To do this, edit your users ~/.bashrc file, and add the following line to the bottom:

```

# Uncomment the line corresponding to your desktop environment
#sudo startxfce4        #for Xfce4
#sudo startx        #for unity

```

Now your desktop environment will start upon login of this user.
If you want this for ALL users, add that line to the end of /etc/bash.bashrc

(I couldn't find the commands to start kde, lxde, or gnome... sorry about that)

---

