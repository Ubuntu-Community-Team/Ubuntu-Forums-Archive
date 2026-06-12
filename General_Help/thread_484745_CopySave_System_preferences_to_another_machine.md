---
title: "Copy/Save System preferences to another machine"
date: 2007-06-26
forum: General Help
---

### Post by Moustacha on 2007-06-26
Is there anyway of doing this, like how WXP has the "Files and Settings Transfer" so copy your my documents and settings to a new machine, is there a method (manual or automatic) of doing this for Ubuntu? ie copy user x from machine a to user x on machine b including their preferences and data.

---

### Post by kidders on 2007-06-27
Hi there,

In most circumstances, copying settings around is trivial on Linux machines, since (by convention) they're all stored in users' home directories, along with their personal files. On a well-designed Linux OS, running well-written applications, nothing belonging to any user should exist anywhere else.

Conventionally (again), application settings are stored in files/directories with names that start with '.'. You can make a list of yours with **ls -ad ~/.[^.]*** or similar.

If I wanted to copy my files & settings from one OS to another, I would probably just tarball my entire home directory & copy it to the destination. Once it's unpacked, I'd expect to have to rewrite file & directory ownership for the entire directory, to match my UID on the new OS, with something along the lines of **sudo chown -R username:groupname ~username**.

While in theory it couldn't be any more straightforward, there are a few wrinkles to watch out for...[LIST]
[*]Some settings directories (eg ~/.thumbnails, ~/.Trash, ~/.wine) can be extremely large, so you might want to delete any that aren't particularly useful, before copying.
[*]Occasionally, badly-written applications may store user preferences outside the home directory.
[*]Again, on occasion, badly-written applications may get upset where the versions installed on the source & destination OSs are different, *and* the settings they store aren't properly intercompatible.
[*]It's at least conceivable (although it shouldn't happen) that some files in a user's home directory are owned by someone else. This can lead to unpredictable behaviour on both the source & destination machines.
[*]It's also possible that certain application preferences may not take effect on the new OS, if it's missing a dependency of some sort ... eg a user-specific application plugin that depends on a system library that isn't installed on the new OS.[/LIST]These are all rare gotchas, but I thought I might as well be thorough, and try to think of as many as I could. In principle, even copying settings between different distros should be perfectly straightforward.

As one final comment, I thought I'd mention something I tend to do, more often than not ... mostly because I don't necessarily want to copy *absolutely all* my application settings between two operating systems. Imagine...```

cd ~
for i in $(ls -ad .[^.]*); do mv $i dot$i; done
tar cf dotfiles.tar dot.*

```On the destination machine, I can then pick & choose which settings to actually install (ie by removing the word "dot" from the file/directory name), whenever it happens to suit me.

I hope something in here helps!

---

### Post by Moustacha on 2007-06-27
Thanks for the very thorough response. I tried copying settings before on Fedora, but it didn't work =\ Hopefully Ubuntu will. Maybe in a later Ubuntu they'll have a "files and settings" transfer type program for ubuntu->ubuntu

---

