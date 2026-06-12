---
title: "Like to Try Gnome Desktop - Using Unity"
date: 2014-08-07
forum: General Help
---

### Post by anon_private on 2014-08-07
Hi,

I am running ubuntu 12.04.2 from a pendrive.

I would like to try the Gnome desktop environment.

I can't see it in the software centre.

sudo apt-get install gnome. Did not function.

Advice please.

If I prefer Unity, how would I revert?

Thanks

---

### Post by Rev2010 on 2014-08-07
I believe this is how I installed Gnome but I can't recall for sure: [http://askubuntu.com/questions/337015/gnome-desktop-environment](http://askubuntu.com/questions/337015/gnome-desktop-environment)

Keep in mind you'll need to logout and then login using new Gnome option. To revert back to Unity simply logout again and login by chosing the Ubuntu option. If that doesn't work just Google how to install Gnome in 12.04, there are many writeups on it. I think one other is the gnome session fallback.


Rev.

---

### Post by grahammechanical on 2014-08-07
We need to be clear about a few things. There is the Gnome 3 desktop environment (DE) and Ubuntu is built upon it. So, Ubuntu already has Gnome but it uses the Unity user interface instead of the Gnome organization choice of Gnome 3 shell. It is the Gnome 3 shell or just gnome shell that you should look for in the Ubuntu Software Centre.

You should also understand that gnome session fallback is not the same as gnome 3 shell. As you are running from a live session you may need to enable some repositories such as universe and multiverse to get software centre showing the same applications that it does when it is install onto a hard disk.

Regards.

---

### Post by anon_private on 2014-08-07
> **Rev2010 said:**
> I believe this is how I installed Gnome but I can't recall for sure: [http://askubuntu.com/questions/337015/gnome-desktop-environment](http://askubuntu.com/questions/337015/gnome-desktop-environment)

Keep in mind you'll need to logout and then login using new Gnome option. To revert back to Unity simply logout again and login by chosing the Ubuntu option. If that doesn't work just Google how to install Gnome in 12.04, there are many writeups on it. I think one other is the gnome session fallback.


Rev.

Thank you, I will try the code.

Regarding logging in.

When I use the live DVD there is no login.

I don't think that I have a username or password.

Advice please.

Best wishes.

A

---

### Post by ibjsb4 on 2014-08-08
> **anon_private said:**
> Hi,

I am running ubuntu 12.04.2 from a pendrive.

I would like to try the Gnome desktop environment.

I can't see it in the software centre.

sudo apt-get install gnome. Did not function.

Advice please.

If I prefer Unity, how would I revert?

Thanks

You can try gnome fallback session.
```
sudo apt-get install gnome-panel
```
At the login screen, click on the icon and choose your desktop.

Ubuntu Gnome is different, there is a download iso for it.

---

