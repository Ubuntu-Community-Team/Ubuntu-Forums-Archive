---
title: "Tiny problem with Beryl"
date: 2006-10-31
forum: General Help
---

### Post by Mohammed Abbas on 2006-10-31
Hey guys , 
I've a small problem here , I think it's small !
I've successfully installed XGL and all work fine. However , only window decoration works , I can't change the look of the inner window or the taskbar . They still look old !
_[[URL=http://imageshack.us][IMG]http://img528.imageshack.us/img528/336/xglwi9.png[/IMG]]("http://img528.imageshack.us/my.php?image=xglwi9.png")[/URL]_
When I go edit window options from system , It displays this message ;
> Cannot start the preferences application for your window manager

Window manager "beryl" has not registered a configuration toolWhat's wrong then ?

---

### Post by MadTxn on 2006-10-31
I don't think that's an option.

---

### Post by skymt on 2006-10-31
You need to run gnome-settings-daemon on login. I don't know how you're logging in, but assuming you use something close to the default, you should be able to just add gnome-settings-daemon to your Sessions control panel.

---

### Post by Perfect Storm on 2006-10-31
I had the same problem, untill I install the diffrent GTK2 engines which are not installed by default.

---

### Post by Mohammed Abbas on 2006-10-31
> **skymt said:**
> You need to run gnome-settings-daemon on login. I don't know how you're logging in, but assuming you use something close to the default, you should be able to just add gnome-settings-daemon to your Sessions control panel.

Thanks ! this way worked fine .
edit : since I close the terminal window , changes diappear .. how could I make this parmenentaly ?

Regards,
Mohammed Abbas

---

### Post by Mohammed Abbas on 2006-10-31
> **Artificial Intelligence said:**
> I had the same problem, untill I install the diffrent GTK2 engines which are not installed by default.

how to install the GTK2 engine ?

Regards,
Mohammed Abbas

---

### Post by d3v1ant_0n3 on 2006-10-31
Have a look [ HERE](http://www.gnome-look.org/index.php?xcontentmode=100&PHPSESSID=048ac05bb4845d8f128a2893e6e29eb6) for GTK themes...you can install them by drop and dragging the downloaded files into Ubuntu's theme manager (I think it's in system>Preferences, but I won't swear to it since I'm in KDE). You can then apply the different themes by clicking on the 'controls' tab and selecting the newly installed theme.

Hope that helps.

---

### Post by skymt on 2006-10-31
> **Mohammed Abbas said:**
> edit : since I close the terminal window , changes diappear .. how could I make this parmenentaly ?

To make it stays open when you close the terminal window, run it like this:```
nohup gnome-settings-daemon &
```You probably want to run it on login. How you do this depends on how you set up Beryl, but if you still go through gnome-session, you can just add it (just as "gnome-settings-daemon", don't bother with the nohup stuff) in System > Preferences > Sessions > Startup Programs.

EDIT: If you log in through a script, just add "gnome-settings-daemon &" at the top.

---

### Post by Mohammed Abbas on 2006-10-31
> **skymt said:**
> To make it stays open when you close the terminal window, run it like this:```
nohup gnome-settings-daemon &
```You probably want to run it on login. How you do this depends on how you set up Beryl, but if you still go through gnome-session, you can just add it (just as "gnome-settings-daemon", don't bother with the nohup stuff) in System > Preferences > Sessions > Startup Programs.

EDIT: If you log in through a script, just add "gnome-settings-daemon &" at the top.

All fine now !
Thanks a bunch .:)

---

