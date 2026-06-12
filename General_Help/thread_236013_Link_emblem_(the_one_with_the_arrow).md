---
title: "Link emblem (the one with the arrow)"
date: 2006-08-14
forum: General Help
---

### Post by kadane|R| on 2006-08-14
Hi..

My question is simple. How do I get rid off the link emplem that apears automaticaly when you create a link on you'r desktop?

Using Ubuntu 6.06

---

### Post by BitTorrentBuddha on 2006-08-14
There is none for me, how are you making a link, using the ln command? Symbolic links make it look all messed up.

---

### Post by BitTorrentBuddha on 2006-08-14
You could make a hardlink using the ln command: ```
ln /path/to/file ~/Desktop/
```

---

### Post by kadane|R| on 2006-08-14
Symbolic links appear with the arrow, hard link comlains about not being able to work with directories. 
Basically what I wanted is to make shortcuts on the desktop to some dirs in my /home. In the end I used the launcher option (typng nautilus /the/name/of/thedir) and it worked. 

I know it's an ugly solution but it works, desk free of arrows... 
By the way I think that in the end it's all the same when you create the link or the launcher.



Another question. Is there a way to move the text that is below the icons to the side or above?

---

### Post by aeiah on 2006-08-14
i use the same method to get rid of link arrows for desktop icons. i also delete the text and just use a 'space' so i have no text under the icons.

to have text at the side (and possibly the top although im not too sure about that) you have to browse your way to the desktop options in the gconf-editor. i cant direct you there right now because im at work on an xp box, but you'll probably be able to do a forum search for having text at the side of icons *nod*

---

### Post by kadane|R| on 2006-08-16
I googled and searched on the forum and found nothing.
Also found nothing in gconf-editor.

So the question still exists, how do I change the text below the desktop icons to the side.

...and thanks for the replies.

---

### Post by Ramses de Norre on 2006-08-16
```
gconf-editor /apps/nautilus/icon_view
```
Check "labels_besides_icons".

---

### Post by kadane|R| on 2006-08-22
Sorry for the delay..

This option works only for nautlus icons, it didn't change my desktop icons.

---

### Post by ilovenicotine on 2008-02-02
> **kadane|R| said:**
> Hi..

My question is simple. How do I get rid of the link emblem that appears automatically when you create a link on your desktop?

Back to the original question:

I've looked high and low and found the answer no where.  So I figured it out myself!

Depending on what theme you're using, the link icon is different but always named the same.  The secret is to delete it...(or move it like I did.)

Start in /usr/share/icons/
and find the theme you're using: Human, Tangerine, etc.
navigate to /usr/share/icons/[theme_name]/

you'll see 16X16, 22X22, 24X24, 32X32, scalable, etc.

in each one of those there is a folder called "emblems" which holds the link emblem icon and others.

the one you're interested in is "emblem-symbolic-link.png" or if you're in scalable "emblem-symbolic-link.svg"

I renamed all of them to something like "emblem-symbolic-link.png.bak" and restarted my computer.

Now the weird part is I was using Human icon theme but for some reason I had to rename the ones in Tangerine.  The icons are also in the gnome folder, it's confusing, so I just renamed them all.

To find all of the link images on your system go to /usr/share/icons/ and type:
find . -iname "emblem-symbolic-link.*"

To rename them, cd into each [size]/emblems directory and type:

sudo mv emblem-symbolic-link.png emblem-symbolic-link.png.bak

don't forget the sudo!

The best part of all of this: not only do you not see them anymore but the space that they take up above icons is gone too, so all of my icon rows are the same distance apart, exactly what you would expect if we "turned off" this feature!



> **kadane|R| said:**
> Basically what I wanted is to make shortcuts on the desktop to some dirs in my /home. In the end I used the launcher option (typng nautilus /the/name/of/thedir) and it worked.

That's works very well for the desktop but not so good for folders.  My biggest dislike with that method in my home folder is that it opens links in a new window.  It's also doesn't allow you to browse into from a file chooser like GIMP's "open" dialog.  Also when you ls the directory it's in it shows up as File:: or something.

---

