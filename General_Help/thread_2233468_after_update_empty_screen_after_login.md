---
title: "after update empty screen after login"
date: 2014-07-08
forum: General Help
---

### Post by liz3 on 2014-07-08
I am running xubuntu 14.04 and after installing updates earlier and rebooting there is something wrong. Everything looks normal up to the login screen. Once I log in, I can see my desktop (the wallpaper) and the mouse pointer (which I can move) but nothing else (no icons, no toolbars). The keyboard shortcuts I have set up don't seem to do anything either (I can't open a terminal using cmd+t or any other program).

I used to have a similar problem after screen locking but in that case a reboot solved the problem (I found a more permanent solution by removing the new lockscreen and replacing it with to older uglier one). In this case, however, rebooting does not solve the problem. 
I have tried shutting down lightdm and restarting it but that doesn't seem to help. The computer is a work station with two monitors and I have tried rebooting with just one monitor (that used to cause a problem under 11.04 if I remember correctly). I have tried logging in as a different user and get the same problem only with a different wallpaper.

Any ideas what might be the problem? Or ideas how I could narrow down what causes the problem?

---

### Post by slooksterpsv on 2014-07-10
I'm wondering if it's a configuration issue. Have you tried creating another user and logging in? If not, you can do that from the a TTY (CTRL+ALT+F1-6, F7 is for whatever DE you're using, Xfce in this case).

You can create another user with useradd

You can also just try to dump your config files - **NOTE:** If you have specific application settings or that, they will be deleted in doing this.
If you really want to clear your config files type into a tty, the following:
```

rm -R ~/.config

```
Or you could just cd to it
```

cd ~/.config

```
and just remove the Xfce, gtk2, gtk3, etc. folders that Xubuntu uses.

---

### Post by liz3 on 2014-07-10
Hi,
I have tried that now and it does not change anything. The problem seems to be the same for all users with one exception: if I log in with root I can open programs using keyboard shortcuts!

I have tried deinstalling and reinstalling xfce, without luck.

I have tried installing unity, which starts fine but then I can't reach any program. For example, I can't open the terminal using keyboard shortcuts or using the application search. I thought it was an issue with either the xfce settings or xfce installation but it seems like something else is wrong as well...

I used this tutorial (I found it through an askubuntu answer):
[http://meandmyubuntulinux.blogspot.ca/2012/05/installing-oracle-11g-r2-express.html](http://meandmyubuntulinux.blogspot.ca/2012/05/installing-oracle-11g-r2-express.html)
to set up an oracle database, so my only guess is that I broke something during install/configuration?

---

### Post by Bucky Ball on 2014-07-10
I have changed the title of your thread to 'update' rather than 'upgrade'. Upgrade's are slightly different beasts.

Although the change is only reflected on the first post on the thread, it will be reflected in any searches or on the 'New Posts' list. ;)

Try this:

```
sudo rm ~/.Xauthority
sudo rm ~/.ICEauthority
```

Reboot.

---

### Post by slooksterpsv on 2014-07-10
Ahhh that that little d vs gr makes a big difference. I was thinking you went from 13.10 to 14.04, if it was just updates then what Bucky Ball posted should work.

---

### Post by bumpycat on 2014-11-16
I'm having the same problem as the original poster, after upgrading distribution from 12.04 to 14.04. I've re-installed everything I can think of. After a little bit of reading, it looks like the greeter isn't starting a session. I've removed all of:
~/.cache
~/.config
~/.ICEauthority
~/.Xauthority

Is there a specific set of packages I can reinstall to rebuild the whole lightdm/greeter/session stack?

---

### Post by matt_symes on 2014-11-16
Hi

> **bumpycat said:**
> I'm having the same problem as the original poster, after upgrading distribution from 12.04 to 14.04. I've re-installed everything I can think of. After a little bit of reading, it looks like the greeter isn't starting a session. I've removed all of:
~/.cache
~/.config
~/.ICEauthority
~/.Xauthority

Is there a specific set of packages I can reinstall to rebuild the whole lightdm/greeter/session stack?

I am also having issues with lightdm when coming out of suspend. If I resume to the login screen and login, I get no useable desktop. 

Looking at the lightdm logs it seems to be starting 2 greeter sessions on VT7 and VT8 although the interactive greeter session is actually on VT8. 

There is then a warning "VT_WAITACTIVE 7 interrupted system call" and both x sessions it has started are closed down leading to no desktop.

I can move to VT1 and start lightdm manually and get to a useable desktop. I'm really doubtful that lightdm should be using 2 virtual terminals.

Have you checked the lightdm logs in /var/log/lightdm to check it is a lightdm issue before you reinstall it ?

If you have not, it may be worth doing that first.

I'll post what you need to purge and reinstall when I have checked myself

Kind regards

---

### Post by bumpycat on 2014-11-16
That sounds a lot like my situation - like you, I can start X (xfce4) from tty1 and it then looks pretty normal, but for some reason the normal process doesn't work. I'm not too familiar with the chain of lightdm-greeter-session, so I was assuming lightdm is the problem.

The lightdm logs aren't showing any errors, and there is only an entry for VT7. lightdm is also doing everything in debug mode now - I don't know how that's happened.

---

### Post by matt_symes on 2014-11-17
Hi

> **bumpycat said:**
> That sounds a lot like my situation - like you, I can start X (xfce4) from tty1 and it then looks pretty normal, but for some reason the normal process doesn't work. I'm not too familiar with the chain of lightdm-greeter-session, so I was assuming lightdm is the problem.

The lightdm logs aren't showing any errors, and there is only an entry for VT7. lightdm is also doing everything in debug mode now - I don't know how that's happened.

I think your situation my be slightly different from mine but the cause may be the same.

In my case it seems that lightdm thinks I have a multiseat setup, that I don't have, and that is why I have 2 VTs.

As i workaround, I have set up my system to resume to the desktop and not to the lightdm login screen while I in investigate the problem. You may want to try this as, with my setup, it always resumes successfully to the desktop.

This workaround is a bit of a security risk but better than the previous situation.

I'll post back to this thread if I make progress on the problem.

Post back if the workaround works for you or not.

Kind regards

---

### Post by bumpycat on 2014-11-18
That's a really good workaround - my system is a media server so it stays logged in all the time.

Unfortunately, the update has also broken my sound drivers and flash player, so I have further problems :P I'll give it a few more attempts and then I think it's time to reinstall.

---

