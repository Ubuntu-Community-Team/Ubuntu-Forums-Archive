---
title: "&quot;open with&quot; application not associated for all files"
date: 2007-11-09
forum: General Help
---

### Post by explicitly ambiguous on 2007-11-09
The problem I'm experiencing is that the file associations in my system appear to have all been removed.  That is, when I look at any files 'properties' under the right click menu and go to the 'open with' tab there are no applications associated.

This happened while I was configuring gdesklets and it crashed, I then logged out with it not responding (grayed out).  When I logged back in I noticed that all files had lost their custom icons and investigated from there.

Any ideas as to what I should examine to to find a solution??


I thought this might be a nautilus problem so I tried stopping nautilus and restarting.  When this failed I did 'complete removal' & reinstall of nautilus and ubuntu-desktop via synaptic.  These have had no effect.

I've also tried 'sudo update-desktop-database' after reading the post #8 on [http://ubuntuforums.org/showthread.php?p=2161195](http://ubuntuforums.org/showthread.php?p=2161195) 

I'm at a complete loss as to what to do next, even just some more hints as to what to look for would be greatly appreciated...


I'm happy to post files or output of any commands that could be useful to help us solve this problem.


Thanks for taking a look,

Andy

---

### Post by TheExplorer on 2007-11-09
Try this:

[LIST]
[*]When at the login screen, press CTRL+ALT+F2.
[*]Log in using your admin account.
[*]Type *cd ~*
[*]Type *mv .gconf .gconf.old*
[*]Type *mv .gconfd .gconfd.old*
[*]Type *mv .gnome .gnome.old*
[*]Type *mv .gnome2 .gnome2.old*
[*]Type *mv .gnome2_private .gnome2_private.old*
[*]Type *mv .metacity .metacity.old*
[*]Type *mv .nautilus .nautilus.old*
[*]Type *mv .gtkrc-1.2-gnome2 .gtkrc-1.2-gnome.old*
[*]Switch back to the login screen by pressing CTRL+ALT+F7.
[*]Press CTRL+ALT+BACKSPACE. Don't worry, the login screen will come back in a few seconds.
[*]Log in.[/LIST]If it works then you can safely remove that '.old' dirs.
Thanks to [elreteipos]("http://ubuntuforums.org/showpost.php?p=2439771&postcount=8") for this workaround.

---

### Post by explicitly ambiguous on 2007-11-09
Thanks for the reply TheExplorer...   I'll give it a go tonight when I'm back at home. :)

---

### Post by explicitly ambiguous on 2007-11-09
hmm.... followed the instructions, but I failed to get it to work.   :(

---

### Post by explicitly ambiguous on 2007-11-10
Does anyone have any more ideas??    Or should I manually re-organise the associations? Or (shudder) re-install??  Perhaps someone has an idea as to how this could have happened in the first place -- so I can track down the broken files??

---

### Post by explicitly ambiguous on 2007-11-14
So I'm still sitting on the same problem...  moreover, I can't burn .iso files anymore from the right-click desktop menu.

???????:confused:????????

---

### Post by Kymus on 2007-11-17
I am having a [very similar]("http://ubuntuforums.org/showthread.php?p=3788970") problem myself

---

### Post by explicitly ambiguous on 2007-11-21
Perhaps someone knows what permissions the files TheExplorer mentioned should have?

At the moment they are as follows:

drwx------   6 andy andy 4.0K 2007-11-21 17:34 .gconf
drwx------   3 andy andy 4.0K 2007-11-21 17:36 .gconfd
drwxr-xr-x   4 andy andy 4.0K 2007-11-09 20:41 .gnome
drwx------  14 andy andy 4.0K 2007-11-20 15:49 .gnome2
drwx------   3 andy andy 4.0K 2007-11-09 20:40 .gnome2_private
-rw-r--r--   1 andy andy   86 2007-10-22 19:20 .gtkrc-1.2-gnome2
drwx------   3 andy andy 4.0K 2007-10-22 19:20 .metacity
drwxr-xr-x   4 andy andy 4.0K 2007-11-20 15:49 .nautilus

Is this normal?

Andrew

---

### Post by explicitly ambiguous on 2007-11-21
Kymus,

your solution was only to reboot??

---

