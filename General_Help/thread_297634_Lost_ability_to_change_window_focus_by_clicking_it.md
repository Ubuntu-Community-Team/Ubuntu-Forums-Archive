---
title: "Lost ability to change window focus by clicking its contents"
date: 2006-11-11
forum: General Help
---

### Post by glave on 2006-11-11
I'm not sure what has happened, but now I can only change focus of my windows when I click on the title bar. If I click on the title, it brings that window to the front focus, but if I click on the contents of the window, the window position stays the same in Z order, and does not come to the front.

Is this a setting somewhere or a bug?

---

### Post by glave on 2006-11-11
Gah this is driving me nuts! Anyone have an idea??

---

### Post by fragos on 2006-11-12
System-> Preference-> Windows will let you change focus base on cursor position.  That may be a place to start.  Applications-> System Tools-> Configuration Editor may also be of help.  There are some parameters that you can't access with Gnome and they will be here.  Since I don't know how you got yourself into to this mess its hard to find a solution.

---

### Post by straxus on 2006-11-16
This has happened to one of my boxes as well, after upgrading to Edgy.  In addition, Yakuake no longer responds to it's hot keys.

---

### Post by jhaitas on 2006-11-17
i have had the same problem for a while... perhaps we should report this as a bug... when a window receives focus via software the z-order does not change... VERY ANNOYING

---

### Post by straxus on 2006-11-18
Do the rest of you who have this problem also have an issue with hotkeys?  Alt-Fkey, printscreen, and others aren't working here even though they are setup correctly in Preferences -> Keyboard Shortcuts.  Oddly, my media keys work fine.  I was just wondering if this was a seperate issue or not.

---

### Post by glave on 2006-11-19
I haven't had any problems with hotkeys, except trying to get min windows+e key to bring up a browser. I never could get that to work...

That's absolutely the only thing I've tinkered with on any kind of keyboard or windows settings at all. Still having this crazy problem though... :(

---

### Post by glave on 2006-11-19
Not a fix, but this did fix things for me (so far).

I was just tinkering around and I installed xgl and beryl, and viola, everything is back to normal again. 

Something up with gnome??

---

### Post by glave on 2006-11-21
Scratch that thought, I just rebooted and I'm back to being unable to change focus by clicking again, and this time I'm in XGL and using Beryl.

:(

---

### Post by klj on 2006-11-21
I had that problem in Dapper after trying out Beryl and deleting it again. In "Preferences/Sessions", I had an entry setting my keybord to the wrong keymap... no idea why Beryl would do such a thing.

I removed that, and windows focus worked again.. dont ask me why... might be a coincidence, but I had tried a lot of stuff before that without luck.

Another thing You might try is to add "metacity --replace" (or just try it in a terminal). I did that too after having deleted Beryl, because it had removed all windows around applications, and made it impossible to move them. Not sure if this helped the focus-thingie, though.

---

### Post by glave on 2006-11-22
My keyboard setting is on 'unknown' currently, so I've set it to Logitech Internet (mine's Internet Pro if there is a difference).

We'll see how it goes over the next few days, although currently it was working again just fine.

---

### Post by fragos on 2006-11-22
The keyboards are the same except that the pro version has more special function keys.

---

### Post by glave on 2006-11-23
Well, having that set still caused the problem. Been working great all night, but after watching some tv I come back to the computer and its not working again.

I did discover that restarting the xserver seemed to kick it back into gear just fine though..... ?

---

### Post by jedbro on 2006-11-30
Did anyone figure this out?

The only fix I've seen is
1) Reseting my Keyboard to default and then setting it to my real keyboard (Dell multimedia usb)
Then..

2) I have to run "metacity --replace".

This sucks though because I have to do this every time I re-boot :(

*Edit*

Forgot to mention I too was running beryl before (not anymore). 
I've since disabled beryl, beryl-manager and emerald from my session startup list, but still doesn't work unless I do the above.

---

### Post by glave on 2006-12-08
Well with some various other bugs I've had, I switched to kde and everything magically went away. I'm guessing whatever the issue, it must be a gnome thing.

---

### Post by strabes on 2006-12-08
> **glave said:**
> I'm not sure what has happened, but now I can only change focus of my windows when I click on the title bar. If I click on the title, it brings that window to the front focus, but if I click on the contents of the window, the window position stays the same in Z order, and does not come to the front.

Is this a setting somewhere or a bug?

Are you using beryl by chance? If so, those options are in the Choices tab of the General Options plugin of beryl-settings.

---

### Post by solderhead on 2006-12-10
I have had the same problem with losing the ability to change window focus.  I have been using KDE exclusively, and I have also run into the problem where I can not change window focus withouit clicking the title bar.

I think that the problem came along with the Adept Updater's automatic updates.  I remember seeing some KDE and X stuff being updated around the time that these problems came along.

---

