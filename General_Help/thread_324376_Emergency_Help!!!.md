---
title: "Emergency Help!!!"
date: 2006-12-23
forum: General Help
---

### Post by arthursc on 2006-12-23
I have just started ubuntu and I login but get returned to the login screen. Usename and pwd is correct but it apears that the desktop will not load?

Any ideas???

I can login to a terminal with my credentials from boot.

---

### Post by arthursc on 2006-12-23
> **arthursc said:**
> I have just started ubuntu and I login but get returned to the login screen. Usename and pwd is correct but it apears that the desktop will not load?

Any ideas???

I can login to a terminal with my credentials from boot.
Has anyone got any ideas??

---

### Post by iamhugeinjapan on 2006-12-23
This is a fresh install that wont login?

Can you login to Ubuntu graphically using the recovery kernel option in the Grub menu at boot time?

If it's a brand new install it might be worth reinstalling just in case something hiccupped the first time.

---

### Post by arthursc on 2006-12-23
> **iamhugeinjapan said:**
> This is a fresh install that wont login?

Can you login to Ubuntu graphically using the recovery kernel option in the Grub menu at boot time?

If it's a brand new install it might be worth reinstalling just in case something hiccupped the first time.
Tried Recovery mode still does the same. Not a new install. really do not want to re-install...can' too much data to lose.

---

### Post by Henry Rayker on 2006-12-23
Have you done anything recently? Perhaps installing Beryl or anything like that?

Try clicking the Options button on the bottom left of the login, select sessions and choose Gnome or KDE, whichever you had installed. Then enter your name and pass. See if that helps at all.

---

### Post by arthursc on 2006-12-23
> **Henry Rayker said:**
> Have you done anything recently? Perhaps installing Beryl or anything like that?

Try clicking the Options button on the bottom left of the login, select sessions and choose Gnome or KDE, whichever you had installed. Then enter your name and pass. See if that helps at all.
no installs. I can only do failsafe terminal

---

### Post by iamhugeinjapan on 2006-12-23
Your data is still recoverable using a live cd to copy it somewhere or burn to disc.

You could also write a cd or copy files around using the command line if you're confident enough.

---

### Post by finferflu on 2006-12-23
Since you can login from console, why don't you try installing a different Desktop Environment, such as KDE or IceWM?

If you are a beginner, I suggest you to switch to KDE, type:
```

sudo aptitude install kubuntu-desktop
```

Then try to login in the KDE session from the Sessions menu, and see if it works. At least you can get access to your desktop for now.

---

### Post by arthursc on 2006-12-23
> **finferflu said:**
> Since you can login from console, why don't you try installing a different Desktop Environment, such as KDE or IceWM?

If you are a beginner, I suggest you to switch to KDE, type:
```

sudo aptitude install kubuntu-desktop
```

Then try to login in the KDE session from the Sessions menu, and see if it works. At least you can get access to your desktop for now.
what about gnome?
I press escape at grub boot and when I select genric (recovery mode) do i lgin as my user id???

---

### Post by iamhugeinjapan on 2006-12-23
finferflu is recommending you install KDE because it will give you a different environment ,login manager and start up settings.  It will at least let you see if it's a problem with GNOME or the system itself. In the meantime you will hopefully have a usable desktop.

Depending on your Internet connection you may not want to install the whole Kubuntu system so lesser installs like

```
sudo aptitude install kde
```
or
```
sudo aptitude install kde-core 
```

may suffice.

---

### Post by arthursc on 2006-12-23
> **iamhugeinjapan said:**
> finferflu is recommending you install KDE because it will give you a different environment ,login manager and start up settings.  It will at least let you see if it's a problem with GNOME or the system itself. In the meantime you will hopefully have a usable desktop.

Depending on your Internet connection you may not want to install the whole Kubuntu system so lesser installs like

```
sudo aptitude install kde
```
or
```
sudo aptitude install kde-core 
```

may suffice.
ok. downloading 78mb of updates for kde.

Once this is done and i can login, what then to revert back to gnome?

---

### Post by iamhugeinjapan on 2006-12-23
If you want to and can sure.  As well as choosing GNOME in the sessions menu, you can switch everything back to the standard Ubuntu set up with 

```
sudo aptitude install ubuntu-desktop
```

---

### Post by Tiede on 2006-12-23
Hmm... Maybe a title other than "Emergency Help!!!" would get you more help... might I suggest something more explicit?
As for your problem, installing KDE is overdoing it, in my opinion.
Try this instead. When gdm starts (the login screen) select failsafe as your session. Then, try login in.
If it does, then the problem comes from your session or whatever you have in there: Beryl? Compiz? AIGLX? --for example, on my laptop, everything that would invoke xgl kills X.
Try removing your ~/.gnome2 folder and log back in again.

If it does not, then the problem is probably in your X11 configuration.
In such a case, type ALT+Ctrl+F1 to drop to a terminal. From there in, try
```
sudo dpkg-reconfigure xserver-common
```
If you cannot find the right driver for your card, try the vesa driver.
WARNING:The above step WILL change your /etc/X11/xorg.conf file, and therefore should be used cautiously.

---

### Post by arthursc on 2006-12-23
> **Tiede said:**
> Hmm... Maybe a title other than "Emergency Help!!!" would get you more help... might I suggest something more explicit?
As for your problem, installing KDE is overdoing it, in my opinion.
Try this instead. When gdm starts (the login screen) select failsafe as your session. Then, try login in.
If it does, then the problem comes from your session or whatever you have in there: Beryl? Compiz? AIGLX? --for example, on my laptop, everything that would invoke xgl kills X.
Try removing your ~/.gnome2 folder and log back in again.

If it does not, then the problem is probably in your X11 configuration.
In such a case, type ALT+Ctrl+F1 to drop to a terminal. From there in, try
```
sudo dpkg-reconfigure xserver-common
```
If you cannot find the right driver for your card, try the vesa driver.
WARNING:The above step WILL change your /etc/X11/xorg.conf file, and therefore should be used cautiously.
HI tiede.

Inlaws have aplace in orlando @ orange tree off the 27!

Anyhow.. I have got a term seesion and logged in with my user. what should I do now??

---

### Post by arthursc on 2006-12-23
Not getting any where.

I have booted to live cd but cannot see my home folder.

---

### Post by scrooge_74 on 2006-12-23
> **arthursc said:**
> I have just started ubuntu and I login but get returned to the login screen. Usename and pwd is correct but it apears that the desktop will not load?

Any ideas???

I can login to a terminal with my credentials from boot.

I  think you have probles with video card, did you try reconfiguring xorg?

sudo dpkg-reconfigure xserver-xorg

---

### Post by Tiede on 2006-12-24
sorry, i gave you the wrong package to reconfigure. Hopefully you did as scrooge_74 suggested. What is the result of your trials? Anything new?
Also, I should have asked that earlier. What exactly was the last major thing you did on the computer before this error started? This would help troubleshooting a lot since it would give us a better chance at pinpointing what exactly is cousing the error, instead of just having to push ahead on random ideas...

---

