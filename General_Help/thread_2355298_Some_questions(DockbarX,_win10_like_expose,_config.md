---
title: "Some questions(DockbarX, win10 like expose, config folders, disable trackpad)"
date: 2017-03-11
forum: General Help
---

### Post by llysender on 2017-03-11
First of all thank you very much in advance for any and all responses to this thread.



[LIST]
[*]Regarding DockbarX, is it posible to to get previews working on Xubuntu?
[*]Also is there any win10 like expose program that has both window selection/search and vurtual destop manipulation on a single page?
[*]In the home folder is it posible to nest all the config folders under 1 folder?
[*]Lastly is it posible to disable trackpad when a usb mouse is plugged in and reenable it when it is plugged out?
[/LIST]

---

### Post by vanadium on 2017-03-12
It is sometimes better to ask one specific question in one thread, but here we go

> 
    Regarding DockbarX, is it posible to to get previews working on Xubuntu?

Yes, but only when you use compiz as your window manager. See [https://github.com/M7S/dockbarx](https://github.com/M7S/dockbarx). In the settings of xfce, you can readily change the window manager in use (Compiz mist be installed for you to be able to choose it, of course).
> 
    Also is there any win10 like expose program that has both window selection/search and vurtual destop manipulation on a single page?

Gnome shell has this as its central feature. However, xfce has xfdashboard, which mimics this functionality.
> 
    In the home folder is it posible to nest all the config folders under 1 folder?

Of course, but then you will also need to reconfigure each application to look into the new location for its config.
> 
    Lastly is it posible to disable trackpad when a usb mouse is plugged in and reenable it when it is plugged out?

Of course, but not easily through a graphical user interface. It would be rather easy to define a hotkey that runs a command that turns the trackpad off. More difficult would be to have that command triggered automatically upon insertion of a usb mouse. Thus, to answer your question, yes, again, it is possible. Under linux, very much is actually possible, but sometimes it may require quite some technical skills to actually implement it.

---

