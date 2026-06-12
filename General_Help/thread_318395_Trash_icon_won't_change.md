---
title: "Trash icon won't change"
date: 2006-12-13
forum: General Help
---

### Post by bg1256 on 2006-12-13
On Edgy, I can't get my trash icon to change, no matter which icon theme I use.  I seem to be stuck with the one shown in the attached photo.

I have no idea how to fix it.  Not a major problem, but if someone knows how, I'd greatly appreciate it.!

---

### Post by ciscosurfer on 2006-12-13
> **bg1256 said:**
> On Edgy, I can't get my trash icon to change, no matter which icon theme I use.  I seem to be stuck with the one shown in the attached photo.

I have no idea how to fix it.  Not a major problem, but if someone knows how, I'd greatly appreciate it.!After changing themes, have you tried logging out and then back in again?

---

### Post by bg1256 on 2006-12-13
I've tried that several times. This has been a problem since I installed Edgy when it first came out.

---

### Post by ciscosurfer on 2006-12-14
> **bg1256 said:**
> I've tried that several times. This has been a problem since I installed Edgy when it first came out.If it's an installed theme, check in **~/.icons**

If you're using the default, check in **/usr/share/icons**

And search out the offending trash icon. :-)

---

### Post by alphazero on 2006-12-16
I had the same problems. After searching, I found out that the trash icons names were changed for Edgy.

The new names for the trash are:

user-trash.png (new empty trash filename)
gnome-fs-trash-empty.png (old filename)

user-trash-full.png (new full trash filename)
gnome-fs-trash-full.png (old filename)

Your extension might be .svg instead of .png if you are using an iconset with scaleable graphics.

---

### Post by bg1256 on 2006-12-17
Alrighty, thanks for posting that. Only problem is, I'm not sure where to go with that or how to apply that information.

---

### Post by ayoli on 2006-12-17
find the icons theme you want to use in /usr/share/icons or ~/.icons and rename the trash icons from the oldname to the new name given by alphazero

---

### Post by bg1256 on 2006-12-17
Well, this is a noobish question, but here goes anyway.

I determined that the icon set I'm using (Snowish) is located in my .icons folder; however, I cannot figure out how to open that folder - since it doesn't appear in my home folder - and therefore, I can't rename the files.

Any ideas?

---

### Post by ayoli on 2006-12-17
> **bg1256 said:**
> Well, this is a noobish question, but here goes anyway.

I determined that the icon set I'm using (Snowish) is located in my .icons folder; however, I cannot figure out how to open that folder - since it doesn't appear in my home folder - and therefore, I can't rename the files.

Any ideas?

in nautilus hit ctrl+h to see hidden files/folders (with a leading dot)

---

### Post by bg1256 on 2006-12-17
Wonderful. Thanks for your help, everyone!

---

### Post by bg1256 on 2006-12-17
> **ayoli said:**
> find the icons theme you want to use in /usr/share/icons or ~/.icons and rename the trash icons from the oldname to the new name given by alphazero

Well, strangely enough, that didn't work...still stuck with the blue one.

---

### Post by bg1256 on 2006-12-18
Well, it seems I now have it figured out and configured properly.  The only thing I don't like is that it's awfully small in Edgy, while in Dapper, it's the normal size...

---

### Post by bebop_tango on 2007-02-11
It didn't work to simply rename the icon files. The home folder icon still "refuses" to change... some svg icons won't appear when changing to svg themes, like the ones which comes with the gnome-theme-extras package...

bg1256, what did you do to properly work these icons out...?

---

### Post by bg1256 on 2007-02-12
> **bebop_tango said:**
> It didn't work to simply rename the icon files. The home folder icon still "refuses" to change... some svg icons won't appear when changing to svg themes, like the ones which comes with the gnome-theme-extras package...

bg1256, what did you do to properly work these icons out...?

I did this:

> The new names for the trash are:

user-trash.png (new empty trash filename)
gnome-fs-trash-empty.png (old filename)

user-trash-full.png (new full trash filename)
gnome-fs-trash-full.png (old filename)

Your extension might be .svg instead of .png if you are using an iconset with scaleable graphics.

Also, you may simply need to explore the particular icon theme you are using...

And I never had a problem with the home folder icon not changing.  That would be a new one to me.

---

### Post by bebop_tango on 2007-02-12
I'm giving up... tried almost all combinations of renaming/linking the icons but nothing yet!

](*,) 

I've renamed the files, THEN created symbolic links with the original names, then I tried to symbolic link the original files naming the links with the user-trash* names... no good either way, not a single trash Icon NOT from the default themes installed will show up.

Why have the names changed, anyway...?

:confused:

---

### Post by g3k0 on 2007-02-12
are you using the gnome session or xgl or something?

---

### Post by ciscosurfer on 2007-02-12
A few things to try:[LIST=1]
[*]right-click the trash panel applet and remove it.
[*]switch to a new theme
[*]re-add the trash panel applet and see if that does it (log out and back in if necessary)[/LIST]

---

### Post by aktiwers on 2007-02-14
>  			 				The new names for the trash are:

user-trash.png (new empty trash filename)
gnome-fs-trash-empty.png (old filename)

user-trash-full.png (new full trash filename)
gnome-fs-trash-full.png (old filename)

Your extension might be .svg instead of .png if you are using an iconset with scaleable graphics.

This worked great for me! Thanks

To OP:
Did you remember to rename the files in the actual theme folder inside .icons?  I picked the 32x32 ones.

---

### Post by bg1256 on 2007-02-14
I'm the OP, and I have everything resolved.

Thanks!

---

### Post by rsambuca on 2007-02-14
Can you just recap exactly what you did?

---

### Post by bg1256 on 2007-02-14
> **rsambuca said:**
> Can you just recap exactly what you did?

Sure, no problem.

First off, you have to find the folder for the icon theme you are using, and it's in one of two places:
/usr/share/icons or ~/.icons.

You have to enter /usr/share/icons as root.  So, alt+f2, then 

```
sudo nautilus /usr/share/icons
```

Or, you open your home folder, ctrl+h and navigate into .icons.

Then you find the particular icon theme you are using.

Then, you find the trash icon.  It will be in a different place for each theme.  Searching might help you here :) 

The file(s) you will be looking for are:
gnome-fs-trash-empty.png (old filename) which neds to be changed to:
user-trash.png (new empty trash filename).

And gnome-fs-trash-full.png (old filename) needs to be changed to:
user-trash-full.png (new full trash filename)

Your extension might be .svg instead of .png if you are using an iconset with scaleable graphics. 

Some of the newer themes I've downloaded from gnome-look do not need to be altered, but if you are stuck with the blue trash can, then this should solve your problems!

---

