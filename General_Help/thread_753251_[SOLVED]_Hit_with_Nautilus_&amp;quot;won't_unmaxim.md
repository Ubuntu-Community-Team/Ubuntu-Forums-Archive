---
title: "[SOLVED] Hit with Nautilus &amp;quot;won't unmaximize&amp;quot; bug"
date: 2008-04-12
forum: General Help
---

### Post by transporter_ii on 2008-04-12
Ok, hit with what I think is a bug with Nautilus. I must have accidentally maximized the darn thing and then closed it, and now it is stuck maximized every time I open it, covering up the menu bars. It will not unmaximize, let me resize it, or minimize it in any way when it is running...and it causes strange screen behavior when I use alt-tab to get to other running programs (which I have to do because Nautilus sticks on the whole screen).

Exceptions:

1) Behavior stops if I turn off "always open in browser window" That's fine, but I don't like it like that as I end up with 14 different windows open to get to a subfolder.

2) If I start up Nautilus with "gksudo nautilus," the behavior goes away even if using  "always open in browser window."  (settings are tied to users?)

For the love of all things holy, if Nautilus "remembers" its last screen size, it MUST STORE THAT VALUE SOMEWHERE. I have searched google for hours to no avail. Why can't you just go in and edit that value somewhere?

Also, if it runs fine with gksudo, it must tie in settings somehow to a user. Is there a way to wipe out stored user settings and return to some sort of "default" state?

I have used Ubuntu for months now and loved it, but for some reason this bug irritates me to no end. If worse comes to worse, I'm going to format and reinstall...and I shouldn't have to do that just to get rid of a stored value located somewhere on the system.

All I can say is, the default setting for "Titlebar Action" (found in System\Windows Preferences), should default to "Minimize," because I'm pretty sure double-clicking the Titlebar was how I accidentally maximized Nautilus to begin with.



Transporter_ii

---

### Post by wdaniels on 2008-04-12
Sounds really strange.  But run gconf-editor and look under apps/nautilus/preferences.  You should see settings navigation_window_saved_geometry and navigation_window_saved_maximized.

---

### Post by transporter_ii on 2008-04-12
Just for testing, I created an account for my son and logged in under his name. Nautilus worked fine, so if anyone ever runs into this problem, it is tied to a user account.

Without creating myself a new account and moving all my files to it, is there a way to just set my account back to some type of "default" settings?

I guess moving to a new account is an option, but if I could just delete a file somewhere and get to the same point, that sounds easier. At least I don't think I have to reformat and start over!!! 

And by the way, this is a known bug. Go to google and type in "nautilus bug maximize unmaximize" and you will see numerous bug reports.



Thanks,

Transporter_ii

---

### Post by wdaniels on 2008-04-12
If you delete the nautilus settings in gconf-editor they should be re-created with default values.  Or you can rename/delete the hidden folder .gconf in your home directory, which should reset everything in gnome to default values the same as creating a new user.  But I expect if you just delete the navigation_window_saved_ settings like I said above, that ought to be enough.  Did you try it?

---

### Post by transporter_ii on 2008-04-12
I had some stuff going so I didn't want to log out, but going into gconf-editor didn't work with either changing the values or deleting the values and closing reopening Nautilus. And by the way, the key navigation_window_saved_maximized wasn't checked and it didn't seem to matter one way or the other.*

Renaming .gconf didn't work until I bit the bullet and just rebooted...but it fixed the problem after it logged back in and created its default settings.

I went in this time under System\Windows and changed the default action to "None," so I don't accidentally click a titlebar and maximize Nautilus again.

I'm pretty tolerant of bugs and don't mind work arounds at all, but I must say that is one of the the most irritating bugs I have ever ran into.

Anyway, thank you, thank you, thank you for a fix that turned out to be fairly simple.

Transporter_ii 


-=-=-=-=-

*And oddly, using gconf-editor was one of the first things I tried. I searched those preferences top to bottom and I didn't see either key you mentioned, but when I went back after you said to try that first, they were right there. Very strange, because I'm sure I would have seen it if they had been there.

---

### Post by ruicovelo on 2008-05-21
> **transporter_ii said:**
> 
I went in this time under System\Windows and changed the default action to "None," so I don't accidentally click a titlebar and maximize Nautilus again.


I got this problem too and I'm trying the solution here. But I don't think this happened because I maximized the windows. When you maximize a window, the title bar shouldn't disappear. And I don't recall maximizing anything anyway. This happened to me when I upgraded to Ubuntu 8.04.

EDIT:
I renamed the folder ~/.gconf/apps/nautilus and tried killall nautilus but that didn't help. Rebooting solved it. I forgot to try logging out.

---

