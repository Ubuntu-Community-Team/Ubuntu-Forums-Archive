---
title: "Question: Nautilus-action / gnome-open"
date: 2006-12-02
forum: General Help
---

### Post by yopnono on 2006-12-02
Need help on this. I would like to know if someone else have this issue.

I have a nautilus action (open as sudo) and this use gnome-open to open files/folder.

But quite often it fails to open. All I get is "starting administration..." then nothing, even if I try 10 times.

If I then check the processes there is a lot of (gksudo gnome-open file_name)

Then I tried to update nautilus-action to latest, same.
Then I replaced the gnome-open with the version 2.17. And so far it have worked. 

Using Dapper.

---

### Post by justice_4_you on 2007-05-23
> **yopnono said:**
> Need help on this. I would like to know if someone else have this issue.

I have a nautilus action (open as sudo) and this use gnome-open to open files/folder.

But quite often it fails to open. All I get is "starting administration..." then nothing, even if I try 10 times.

If I then check the processes there is a lot of (gksudo gnome-open file_name)

Then I tried to update nautilus-action to latest, same.
Then I replaced the gnome-open with the version 2.17. And so far it have worked. 

Using Dapper.

i have the same issue in feisty...i've read that someone solved it with a new libgnome2-0 pkg  so i downloaded a fresh one and installed it but nothing happened.
plz give me an answer!

---

### Post by yopnono on 2007-05-23
> **justice_4_you said:**
> i have the same issue in feisty...i've read that someone solved it with a new libgnome2-0 pkg  so i downloaded a fresh one and installed it but nothing happened.
plz give me an answer!

I don't use the gnome-open anymore I use instead ```
gksu nautilus %M
``` for open folders, and ```
gksu gedit %M
``` to edit files for the nautilus-action

---

### Post by justice_4_you on 2007-05-24
i already use nautilus to open directory, but i can't just use gedit to open file cause i should specify a different program for every filetype and it's really boring!

gnome-open would just open the specified file with the default app for it's filetype! it's surely better, or at least it would be if it worked :P!

---

### Post by yopnono on 2007-05-26
> **justice_4_you said:**
> i already use nautilus to open directory, but i can't just use gedit to open file cause i should specify a different program for every filetype and it's really boring!

gnome-open would just open the specified file with the default app for it's filetype! it's surely better, or at least it would be if it worked :P!

Add info to the bug:
[https://bugs.launchpad.net/bugs/75524](https://bugs.launchpad.net/bugs/75524)

---

### Post by 12345 on 2007-05-26
this bug with "gnome-open" is existing since age and still not got fixed :/
so here is the fix for opening folders AND files with gksudo:

> Path: bash -c
Parameters: if [ -d '%M' ]; then gksudo nautilus '%M'; else gksudo gnome-open '%M'; fi

optional: Conditions > Appears if selection contains [x] Both
# that will open folder or file as root and not only file.

---

### Post by justice_4_you on 2007-05-27
thx 12345, i'll try that out immediately after destroying my windows vista partion (i'm sick of its incompatibility!)

---

