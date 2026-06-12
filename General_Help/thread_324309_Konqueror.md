---
title: "Konqueror"
date: 2006-12-23
forum: General Help
---

### Post by drito on 2006-12-23
Suddenly, Konqueror opens all folders in separate windows. ***Open folders in separate windows*** disabled via Configure Konqueror.

---

### Post by cheesygit182 on 2007-07-14
I understand this is an old thread, and bumping isn't really necessary, but as this thread is in google's top ten when I search for {"Open folders in separate windows" konqueror} I thought I'd add a solution.

I have had the same problem for a long while now, that is; even when the "Open folders in separate windows" checkbox is unselected in konqueror, all folders open in new instances of konqueror. 
I spent ages googling to no avail, and asked several so-called "linux experts" at a certain site... I had everyone stumped.
You see, what was strange was that when I ran konqueror as root, it worked as it should. It was only from my login account that I was having problems.
I assumed I could solve it by copying the root account's settings for konqueror to my account, as so:
/root/.kde/share/config/konquerorrc     --->    /home/cheesygit182/.kde/share/config/konquerorrc
but that did nothing.

I put up with it for a while, every now and then racking through the konqueror settings, to find nothing.
Then, I stumbled across the "File Associations" section of the settings, with options such as "Show file in embedded viewer" or "Show file in separate viewer".
I thought I was on to something, so I changed the option for the "inode" group to "Show file in embedded viewer", and the same for the "Embedding" tab of the "Directory" options withing the "inode" group.
It worked! Goodness knows what changed it in the first place, it seemed to happen without me doing anything.
Anyway, for anybody who has the same problem - change the "File Associations" options for directories.

Hope this helps somebody!

~Andrew

---

