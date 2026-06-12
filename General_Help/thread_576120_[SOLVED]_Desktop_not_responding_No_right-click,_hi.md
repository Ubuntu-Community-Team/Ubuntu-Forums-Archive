---
title: "[SOLVED] Desktop not responding? No right-click, highlight, etc."
date: 2007-10-14
forum: General Help
---

### Post by rainwalker on 2007-10-14
I don't know when it started, except that it was earlier today, but my desktop (the desktop itself) isn't responsive. Right-clicking doesn't do anything, I can't click and hold to highlight anything, and (I just thought it was weird) my wallpaper appears as soon as I log in (before the splash screen, which i don't think is normal).
I'm on Feisty, and I run Beryl by default but it doesn't change if I switch to Metacity/Compiz Fusion.

Any suggestions?

---

### Post by aysiu on 2007-10-14
Can you create a new test user and see if the test user experiences the same problem?

This can help you determine whether the problem is with a system-wide program/configuration file or with a user-specific configuration file.

---

### Post by rainwalker on 2007-10-14
Ah! Great idea, I'll try that now...

---

### Post by rainwalker on 2007-10-14
Okay, it doesn't happen with the other user, so I know it's my fault...

---

### Post by aysiu on 2007-10-14
Hm. Now the question is... which config file is messing things up?

So even on Metacity it doesn't work? Is it possible that Nautilus (which usually manages the desktop) isn't running?

Try Alt-F2 ```
nautilus
``` and see if that makes the desktop right-clickable.

---

### Post by rainwalker on 2007-10-14
Nope, it just opens a file browser window

Also, I can still middle-click on my desktop to initiate the rotate cube and scroll on it to change workspaces (things I have to have the mouse on the desktop to do). I don't know if that's important, but I thought I'd tell you anyway

---

### Post by aysiu on 2007-10-14
And you're sticking to Metacity for now (no Beryl or Compiz)?

You might want to try renaming each of these config folders one at a time and then see if it makes a difference (unfortunately, it's time consuming, but you may have to log out and log back in again):
/home/*username*/.gconf
/home/*username*/.gconfd
/home/*username*/.gnome
/home/*username*/.gnome2
/home/*username*/.metacity
/home/*username*/.nautilus

---

### Post by rainwalker on 2007-10-14
Augh, finally, the forums were taking forever to load...


What am I supposed to rename them to?

---

### Post by aysiu on 2007-10-14
> **rainwalker said:**
> Augh, finally, the forums were taking forever to load...


What am I supposed to rename them to?
Anything, as long as you know how to rename them back. For example, you could rename ~/.gconf to be ~/.gconf.old or ~/.gconf.backup

---

### Post by rainwalker on 2007-10-14
-sigh-
Alright, I'll go do that
See you in 20 minutes...

---

### Post by rainwalker on 2007-10-14
Just another tidbit before I go, I first noticed this when my PSP wouldn't appear on the desktop when mounted

---

### Post by rainwalker on 2007-10-14
Okay, so I renamed /home/username/.gconf to .gconf-old and this is what happened:
- Everything loaded after the splash screen
- All of my theme settings reverted back to the default ones, except Emerald is being used instead of Metacity, and the font settings are back to the defaults (ew)
- I CAN right-click and highlight now!

What should I do now?

---

### Post by rainwalker on 2007-10-14
Oh CRAP.
I just realized, I renamed that file without making a backup! That means I have to go back and reset eveything, doesn't it?

Wait, couldn't I just run 
```
sudo mv /home/username/.gconf-old /home/username/.gconf
```

---

### Post by strabes on 2007-10-14
Why can't you just delete ~/.gconf and rename ~/.gconf-old to ~/.gconf, all using nautilus? If you wanted to move the folder using the CLI you wouldn't need to use sudo and you'd need to add the -r (recursive) flag. So the command would be:```
mv -r  ~/.gconf-old ~/.gconf
```

---

### Post by rainwalker on 2007-10-14
I could, but that's once I figure out what's actually wrong with my .gconf file.

---

### Post by rainwalker on 2007-10-14
Ooh...I just realized, I was poking around in gconf-editor the other day...I bet I messed something up

---

### Post by rainwalker on 2007-10-14
Okay, so I need to compare the two .gconf's and find what's different.
I went in and looked at their contents, and all I can figure out is that my original .gconf has more folders than the current one...
Is there a command I can use to compare them to find the differences?

---

### Post by rainwalker on 2007-10-15
Aha! Fixed!
The only thing is, I don't know how!

I renamed .gconf-old to .gconf and changed that other .gconf to .gconf-new, and when I logged back in, everything works!

---

### Post by avik on 2007-10-15
> **rainwalker said:**
> Okay, so I need to compare the two .gconf's and find what's different.
I went in and looked at their contents, and all I can figure out is that my original .gconf has more folders than the current one...
Is there a command I can use to compare them to find the differences?

I know you fixed your problems, but for future reference, the command to compare multiple files is:

```

diff [OPTIONS] FILES

```

In your case, you would now do:

```

diff .gconf .gconf-new

```

---

### Post by rainwalker on 2007-10-15
Alright, thank you very much :)

---

### Post by ben2talk on 2008-03-31
If it's any help, I recently went through this process with a slightly different approach.

.gconf holds many settings, and I didn't want to lose them - and it's a lot of hassle to keep checking. I started by opening nautilus, navigating to .gconfig and dragging it onto the shortcut panel, I then renamed it AA.gconfig and restarted.

On restart, all my hours of setting up inside the AA.gconfig folder were also accompanied with the settings files from many programs. Most of the program folders I could simply restore by opening the .config in a new window - the APP folder holds most junk - and I copied HALF of the folders first (Half - split is faster than doing it one by one). Log out and in and repeat - each time copying another half (if no problem). Doing this in alphabetical order, so you know which half caused the problem... It took me four logins to get back to my original settings (fortunately I had already opened up the advanced desktop effects settings and exported it as a text file called 'Wobbly.profile'.

After making the .gconfig file a backup, the login was consistently fast - just a few sedonds to read and display the panels... and the weirdest part is that I DIDN"T FIND A PROBLEM. I ended up copying ALL the settings back, and have a fast login with all my settings intact!

Thanks for pointing me to the .gconfig

Surely this is one reason that a gnome only installation is probably a little dangerous, because when the failsafe login fails, KDE seems to be a reliable backup...

Thanks guys, I'm happy again. Now, where's the menu for making a nice image of my partition and restoring the image backup I made last week.... I remember loving Vista for having this! I'd prefer to love Ubuntu for it...

---

