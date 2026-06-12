---
title: "Bug? Downloading files from browser - Save button greyed out unless a folder selected"
date: 2022-04-24
forum: General Help
---

### Post by trogdor422 on 2022-04-24
When I try to download something from Brave (also happens in Chromium and Firefox) the "Save" button is enabled at first, but if I go into a different directory, it is grayed out, unless I highlight a folder, then it lets me save, but not in the highlighted folder, but in the open folder... Which makes it impossible to save a file in a folder with no sub-folders.

Is this just me? Or can anyone verify this before I report a bug?

Thanks!

---

### Post by TheFu on 2022-04-24
Welcome to snap packages.  These packages have constraints to protect you - whether you want them or not. There's no way to locally override these protections. Only the snap-packaging team gets to choose and it sounds like for what you want, there's no way to override it anyway. 
So sorry.

Yes, please open a bug.  It will be closed - working as designed.  These issues have been pointed out since at least 2017 and there are many others with snaps.

---

### Post by trogdor422 on 2022-04-26
So this is different. I can eventually download, just getting there takes some doing. Brave is also not a snap (though Chromium and Firefox are). Thanks!

---

### Post by TheFu on 2022-04-26
> **trogdor422 said:**
> So this is different. I can eventually download, just getting there takes some doing. Brave is also not a snap (though Chromium and Firefox are). Thanks!

Maybe I don't understand.
File --> Save As ... comes right up for me. I'm using a non-snap version of FF v99.0 for that test.

In Chromium, I don't usually allow that program to save anything to local disk. It runs inside a sandbox environment with an overlay file system that doesn't allow any writes to hit real storage or be seen by any other processes.  So - I directly ran the program, outside a snap, without any protection .... the command is: ```
$ /snap/chromium/current/usr/lib/chromium-browser/chrome &
```
File --> Save As ... came right up, I forced it to /tmp/ and saved the page as html.  Worked perfect and fast.  That's with v100.0.4896.127.

I've never used Brave. Sorry.

I haven't used a browser to download files, like an ISO in years. Browsers are just too complex to be trusted.  **curl** or **wget** for me.  Plus, I can put those into a queue and drop the files where I like directly.  I did visit my favorite distro local mirror (a local university that mirrors the main 50 distros), found a small net-install iso file, right clicked, and the Save Link As ... option wasn't gray at all. This was in FF.

I must be missing something?

All I can guess is that the storage where you want to save the files isn't already mounted through an fstab config. Perhaps it is external storage?

Sorry, I'm not able to see the issue you are.  Could it be a DE thing?  I'm not using any DE - no Gnome, KDE, Mate, or any of the the others. I use just a great window manager, WM, fvwm. It is light, very fast, and extremely customizable. I'm not suggesting it for anyone else.  But some DEs will replace the built-in file dialogs with the DE file dialog, so it could be that? Maybe.

I'm just guessing now.

---

### Post by trogdor422 on 2022-05-02
It could be a Gnome thing... that's what I'm trying to track down...

In addition to the described problem, any time I open the file dialog in Brave the size and location seem to be all but random.

I don't live in a world where wget / curl are practical for me.

Thanks for your barinstorming!

---

### Post by TheFu on 2022-05-02
> **trogdor422 said:**
> It could be a Gnome thing... that's what I'm trying to track down...
When you run the programs, don't run them from the menu. Run them from a terminal so all the errors are spewed to that output.  GTK+ (gnome's toolkit libraries) spew junk all the time, most is really debugging data because their programmers are lazy.  There's a way to get much more details by setting an environment variable. I'd have to look it up - you can if you like.  If you do open a bug with Canonical or Gnome, including that would be helpful to the developers.

> **trogdor422 said:**
> In addition to the described problem, any time I open the file dialog in Brave the size and location seem to be all but random.  Does the file dialog appear to be the same as for other programs?  If so, then it is probably a shared library. If not, it is probably custom for that program only. I've never written a program that used a custom file dialog. It is just too easy to use one that already exists.  Plus, if my code was correct, I didn't have any control over that dialog besides the starting directory and what to filter (file extensions/directories-only ... ). The returned values, if multi-select was allowed, would be an array of memory that I'd have to manage. Not hard. In short, screwing it up would be extremely hard for any programmer with any experience.  I'd be more inclined to think there was file corruption on the hardware for either the directory or where the library was stored.  Did I miss the system log files?  How did those look? Any errors?

> **trogdor422 said:**
> I don't live in a world where wget / curl are practical for me.
Most people don't. ;)  Sigh.

> **trogdor422 said:**
> Thanks for your barinstorming!

Don't know if that spelling was Freudian, but definitely apt! Gave me a chuckle. Appreciated.

---

