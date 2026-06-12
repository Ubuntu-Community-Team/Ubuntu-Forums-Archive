---
title: "Wallpaper slideshow?"
date: 2013-08-08
forum: General Help
---

### Post by c0lon on 2013-08-08
So I know that there are a ton of different tutorials already availabe on making a wallpaper slideshow. I've looked at them. But I messed up. I made the xml files correctly, or at least I think I did because I never got them up and running. I deleted some files that were already there and now when I try to change my wallpaper in System Settings > Appearance, there are only two options and they are both blank screens.

Any ideas? Thanks in advance

---

### Post by deadflowr on 2013-08-08
If you want a wallpaper slideshow, install wallch.(It's in the repos)

If you're going to try to make your own slideshow, it's always best to backup the existing files first.

I find the easiest way to figure things like this out is to make a copy of the wallpaper xml files and then clean out the existing information and replace it with my own. When you save your copy, rename it anything, as long as you give it the .xml extension and place in the gnome-background-properties folder.(or as it is with the slideshow /usr/backgrounds/contest/something.xml)
I have found though, that the most common mistake, and a good reason why wallpapers don't show up is because of a missing or misplaced symbol here or there.(< </ >).

If you didn't backup your files, or deleted your wallpapers, reinstalling them should bring it all back home.
The default wallpaper package is ubuntu-wallpapers.

I'd probaly have more on it for ya, but don't really know what you need or what exactly you did.

---

### Post by c0lon on 2013-08-14
Thanks. I was dumb and didn't back anything up and I didn't know which package to reinstall. Hopefully I cam get it to work now.

---

