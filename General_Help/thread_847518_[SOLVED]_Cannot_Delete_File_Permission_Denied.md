---
title: "[SOLVED] Cannot Delete File: Permission Denied"
date: 2008-07-02
forum: General Help
---

### Post by VexVishnu on 2008-07-02
After uninstalling Wolfenstein I attempted to remove two hidden folders,
tcetest (which was for the True Combat: Elite mod) and .etwolf. I cannot delete either one of them. I can't change the permissions on them when I right click and "sudo rm -rf *filename*" doesn't remove it either.

I was having trouble with Wolfenstein. Every time I would join a game the screen would go black and the program would close. So I decided I would take everything from Wolfenstein off my comp so that I could reinstall it completely fresh.

First off I want to figure out how to delete these files, but do these files even matter?

---

### Post by Elfy on 2008-07-02
Are you including the . in the filename - which makes it hidden

You could do it with gksudo nautilus as well, bear in mind that they won't show in your normal trash as they will be root's

---

### Post by VexVishnu on 2008-07-02
I did include the . in the filename.
What exactly is gksudo nautilus? I'm still fairly new to Ubuntu.

---

### Post by Elfy on 2008-07-02
nautilus is the file manager 

gksudo opens it as root - use it instead of sudo when running a gui

be careful you could cause damage to the file system when logged in as root

---

### Post by fooman on 2008-07-02
> **VexVishnu said:**
> I did include the . in the filename.
What exactly is gksudo nautilus? I'm still fairly new to Ubuntu.

it will open nautilus as root.  which should give you permission to do pretty much whatever you want....so be very careful.

---

### Post by Elfy on 2008-07-02
All that said it's usually the other way round - can't delete from nautilus so use the terminal, it would appear that it's likely to be the path which is wrong.

---

### Post by VexVishnu on 2008-07-03
Thanks That Worked!

---

### Post by Elfy on 2008-07-03
You're welcome - can you mark thread solved

---

### Post by Scoats on 2008-12-10
Thanks everyone. Those suggestions helped me too.

---

### Post by aalian on 2009-02-06
THANKS TO ALL
 really helped me A LOT!

---

