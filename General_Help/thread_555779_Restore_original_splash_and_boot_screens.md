---
title: "Restore original splash and boot screens?"
date: 2007-09-20
forum: General Help
---

### Post by ticopelp on 2007-09-20
When I was first experimenting with Ubuntu on my laptop, I ended up installing both kubuntu-desktop and xubuntu-desktop, because I wanted to see which I liked best. Well, now my bootup sequence is a mess... the boot splash says Kubuntu, the login splash says Xubuntu, and I'm using regular old Ubuntu!

Is there any way to reset everything to the Ubuntu "default" without completely reinstalling the OS? 

Thanks.

---

### Post by por100pre1 on 2007-09-20
Not sure about it, but try this:

```
sudo dpkg-reconfigure usplash-theme-ubuntu
```

Let me know if this works or not. :-k

EDIT:You can change the gdm theme with this:

```
gksu /usr/sbin/gdmsetup
```

and session splash screen with this:

```
gnome-splashscreen-manager
```

---

### Post by Tripletaco on 2007-10-17
So, did it work Ticopelp?  I have a very similar problem.  I was going to start a new thread, but you might appreciate a little help still and I know I need some.

Here's what happened to me.  I originally had Ubuntu 7.04.  I thought I would try setting it up so I could play around with Kubuntu also.  I think this would be having basically dual sessions.  Pardon my terminolgies.  I'm trying to learn.  Mine ended up all convoluted like yours.  Then I thought I would overwrite it all with Ubuntu 7.10 (I think tribe 4).  Well it's still a mix between Kubuntu and Ubuntu.  I would like one or the other.  I got back to the Ubuntu splash screen, but still have the Kubuntu Login.  My Desktop looks like Gnome again.  I think I can switch the desktops between Gnome and KDE by changing the session.  

I would like some help getting this partition back to pure Ubuntu.  by the way. I have a dual boot, Windows XP and Ubuntu.

---

### Post by Tripletaco on 2007-10-17
OK, I decided to try your method Por100pre1.  I got an error with the second command. I Thought I was going to be able to paste that error message here.  But it won't paste and its not on my screen anymore.  It said something about my GDM not being correct.  That I was using the wrong display manager.  I must be using the KDE display manager.  how do I fix that?

The third command came up with the result:  bash: gnome-splashscreen-manager: command not found.

---

### Post by por100pre1 on 2007-10-17
Try [this]("http://www.getdeb.net/app.php?name=usplash-switcher") for boot splash.

For login screen (if using KDE):

```
kcontrol
```

Got to **System Adminstration> KDM Theme Manager**. Be sure to click **Administrator Mode**.

---

### Post by pakux on 2008-01-17
```
sudo dpkg-reconfigure usplash-theme-ubuntu
```


\\:D/ Great!!!  That worked perfectly for me. I had the same kind of mess caused by a candid trial of xubuntu.

Thanks for both the question and the answer.

---

