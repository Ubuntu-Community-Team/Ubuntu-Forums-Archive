---
title: "Bootup/logout issues related?"
date: 2008-06-12
forum: General Help
---

### Post by editrix on 2008-06-12
Like a lot of people, I've been having problems with Hardy and am loath to make changes at the system level without knowing the consequences first. I'm also wondering if the following two issues are related.

When booting up, I have no visual feedback whatsoever until the login screen, and I'd like to see what modules are loading, as I used to in Dapper. Editing grub didn't help. I've installed startupmanager but I have no idea what to do with it.

Then, when I log out, I'm getting the Gnome logout screen rather than KDE's (I installed Gnome first, then the KDE & am using kdm). In Control Centre's Login Manager, it's telling me I'm not using a boot manager, although the drop-down menu says I can use grub. I have no idea if changing this will help or hurt, and I'd like some advice, please.

---

### Post by cmnorton on 2008-06-12
> **editrix said:**
> ... Then, when I log out, I'm getting the Gnome logout screen rather than KDE's (I installed Gnome first, then the KDE & am using kdm). ...

I ran into this. I believe my visiting the Login Manager under Advanced System Settings, you'll find a way to set up the screens properly, and that should fix your exit screen.

---

### Post by editrix on 2008-06-12
Thanks for the quick reply.

> **cmnorton said:**
> I ran into this. I believe my visiting the Login Manager under Advanced System Settings, you'll find a way to set up the screens properly, and that should fix your exit screen.

I don't see any "Advanced System Settings" so I'm probably looking in the wrong place. I'm using KDE's Control Centre. Are you referring to Gnome? Can I change KDE's settings in Gnome?

---

### Post by cmnorton on 2008-06-13
System settings is on the "K" menu (sorry don't know the official name).

When that comes up, there will be two tabs. The right-hand tab is advanced. You should find the login manager there at the top. Sorry that I wrote the other response and did not use commas. That was at a KDE desktop system; I'm on Ubuntu now.

---

### Post by editrix on 2008-06-14
> **cmnorton said:**
> System settings is on the "K" menu (sorry don't know the official name).

When that comes up, there will be two tabs. The right-hand tab is advanced. You should find the login manager there at the top.

Thanks for this. What I found is the screenshot attached. But I looked at all the tabs and don't see anything about visual feedback (I realize it's probably not the correct term) or which logout screen to display. 

 > Sorry that I wrote the other response and did not use commas. 

Your commas were fine. :-)

---

### Post by angry_johnnie on 2008-06-14
Maybe logging into GNOME.
then look for

**System > Administration > Services**

and disable gdm

As for the visual feedback during boot, you may, using startupmanager, choose **show text during boot**, or use some usplash theme.

It should be pretty much the same as going to /boot/grub/menu.lst and deleting the part that says **quiet splash** from the kernel line.

---

### Post by editrix on 2008-06-14
> **angry_johnnie said:**
> Maybe logging into GNOME.
then look for

**System > Administration > Services**

and disable gdm

You're right, it was ticked. Unfortunately, unticking didn't help.:(

> As for the visual feedback during boot, you may, using startupmanager, choose **show text during boot**, or use some usplash theme.

It should be pretty much the same as going to /boot/grub/menu.lst and deleting the part that says **quiet splash** from the kernel line.

From what I can tell, startupmanager is correctly configured--but it didn't help either. I rebooted and still no feedback. What scares me is I'm coming up to the time I'll have to do the fsck and I won't see anything on the screen that will allow me to do it.

Hmmm ... tried to load starupmanager yet again and got this:

```
Grub Legacy detected
Usplash detected
Splashy not detected
/usr/share/startupmanager/gtk_frontend.py:193: GtkWarning: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
  self.main_window.show()
```

Which might be related to my unticking gdm in Gnome?

---

### Post by editrix on 2008-06-14
> **angry_johnnie said:**
> Maybe logging into GNOME. then look for
**System > Administration > Services**
and disable gdm

You're right, it was ticked. Unfortunately, unticking didn't help.:(

> As for the visual feedback during boot, you may, using startupmanager, choose **show text during boot**, or use some usplash theme.

It should be pretty much the same as going to /boot/grub/menu.lst and deleting the part that says **quiet splash** from the kernel line.

From what I can tell, startupmanager is correctly configured--but it didn't help either. I rebooted and still no feedback. What scares me is I'm coming up to the time I'll have to do the fsck and I won't see anything on the screen that will allow me to do it.

Hmmm ... tried to load starupmanager yet again and got this:

```
Grub Legacy detected
Usplash detected
Splashy not detected
/usr/share/startupmanager/gtk_frontend.py:193: GtkWarning: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
  self.main_window.show()
``` but no startupmanager.

Which might be related to my unticking gdm in Gnome?

Whoops! It just showed up--three minutes later. What it says is in the attachment.

BTW, I'm also getting the Gnome wheel instead of the KDE watch. I'll bet that's a related issue, too.

EDIT: Aargh! Now I can't close startupmanager! When I killed it, the terminal didn't reset--it thinks startupmanager is still running.

---

### Post by angry_johnnie on 2008-06-15
I got the same gtk error message when launching startupmanager from kde, but not when I launched it from gnome, so I'm guessing the problem lies there... although it launched quite alright, on this computer, despite the error message.

You could try launching it from gnome.  It should work fine.

You've ticked both the 'show boot splash' and 'show text during boot' options in startupmanager.  It can be done, but if you're still not seeing anything, then there may be something wrong with your current usplash theme.  Why don't you select a different one, from the appearance tab?  Or, just untick the 'show boot splash' option.

Did you try it the other way?  Removing **quiet splash** from the kernel line in /boot/grub/menu.lst should do it.

You could also go to the 'advanced' tab, and reset everything to defaults.

That should, at least, take care of your non-graphical, non-verbose, boot.

As for GDM sitting there when you log out, it just makes no sense, and I've no clue, so you may just consider this a big fat **bump** to your thread. :-)

Hopefully, some of the really really smart members of this forum will figure it out.

Good luck.

---

### Post by editrix on 2008-06-15
> **angry_johnnie said:**
> 

You've ticked both the 'show boot splash' and 'show text during boot' options in startupmanager.  It can be done, but if you're still not seeing anything, then there may be something wrong with your current usplash theme.  Why don't you select a different one, from the appearance tab?  Or, just untick the 'show boot splash' option.

Thanks for pointing this out, because in actual fact I never ticked anything--that is, I loaded the program but didn't actually use it. I did notice that it says my screen is 640 x whatever, but it isn't, it's 1024x768. But my usplash.conf file has the correct resolution.

> Did you try it the other way?  Removing **quiet splash** from the kernel line in /boot/grub/menu.lst should do it.

Haven't tried much at all, because I'm afraid of breaking it worse. I'm actually more comfortable with this "other way" as you can see what a text file is doing :-)

> You could also go to the 'advanced' tab, and reset everything to defaults.

As I said, I never reset anything. This is a little scary--where did it get this info?

> As for GDM sitting there when you log out, it just makes no sense, and I've no clue, so you may just consider this a big fat **bump** to your thread. :-)


Understand, I'm not 100% sure it is GDM. It just doesn't look Kubuntu-ish. It's not blue, for one thing. Just did a Google image search for > kubuntu hardy "log out" menu which is no fun on dialup, and didn't see anything that looks like what I have.

> Good luck.

Thanks. I need it :-)

---

