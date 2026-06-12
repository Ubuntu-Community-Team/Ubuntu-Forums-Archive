---
title: "Unison file permissions error"
date: 2006-12-06
forum: General Help
---

### Post by Thumper322 on 2006-12-06
Hello all...

I set up Unison (**unison-gtk**) to synchronize my flash drive and a folder in my home directory. Whenever I run Unison, it copies files perfectly from the flash drive to my home directory--but refuses to copy files from my computer to the flash drive (it complains about a file permissions error).

What do I do?

Thanks for any help...

---

### Post by SyvanX on 2006-12-06
Are you able to write anything to the flash drive while you're in Ubuntu, or is it a unison specific problem?

Also, are you manually mounting the flash drive or is it mounting automatically?

---

### Post by madcow72 on 2006-12-06
Sounds like your flash drive is root permissions only.  You should be able to set permission by editing fstab.  A quick fix could also be to run unison-gtk as root by pressing Alt+F2 then: ```
kdesu unison-gtk
``` and then change permissions with chmod afterward...although I know this isn't elegant.

---

### Post by madcow72 on 2006-12-06
Sorry...this posted 2x so I removed the 2nd.

---

### Post by Thumper322 on 2006-12-06
> **madcow72 said:**
> Sorry...this posted 2x so I removed the 2nd.

I have full write permissions to the drive, which is mounted automatically. It's working out of the box.

Trouble is, running Unison--whether as me or as root with **gksudo** (I'm running GNOME)--inevitably results in this error.

And no, the flash drive isn't locked.

This makes no sense... I can write to it, but a program running *as root* can't? :???:

---

### Post by madcow72 on 2006-12-06
What about when you're not using Unison?  Can you drag and drop files onto the drive manually?  This might say if it's a permissions error or Unison specific.

---

### Post by Thumper322 on 2006-12-06
> **madcow72 said:**
> What about when you're not using Unison?  Can you drag and drop files onto the drive manually?  This might say if it's a permissions error or Unison specific.

> **Thumper322 said:**
> I have full write permissions to the drive, which is mounted automatically. It's working out of the box.

And, as I said, Unison doesn't even work when running *as root*. ](*,)

---

### Post by SyvanX on 2006-12-06
Is unison telling you what file the permissions are failing on?

Also, a couple of random thoughts, is the drive fat32, and are you using the --owner option to preserve ownership of the files?  I was thinking since fat32 doesn't observe unix permissions that might be a problem.

---

### Post by Thumper322 on 2006-12-06
> **SyvanX said:**
> Is unison telling you what file the permissions are failing on?

Also, a couple of random thoughts, is the drive fat32, and are you using the --owner option to preserve ownership of the files?  I was thinking since fat32 doesn't observe unix permissions that might be a problem.

I'm using the GUI, so I didn't set an --owner option. Yes, the drive is FAT32. And it squawks about (IIRC, not on my laptop right now) "Unable to set permissions for /media/Flash/Doc/.#docname.random-numbers to" and then a string of letters and dashes. (Something like drx-w--x--w, I think.)

---

### Post by SyvanX on 2006-12-06
> **Thumper322 said:**
> "Unable to set permissions for /media/Flash/Doc/.#docname.random-numbers to" and then a string of letters and dashes. (Something like drx-w--x--w, I think.)

That makes it look like a unison error for sure. Something *is* being written by unison to the flash drive.

I think the *.#docname.random-numbers* are how unison treats the files until they are finished copying, when they are finalized they get their normal name.  

When you get back to your laptop, check in the preferences to see if there is an option set like "Synchronize Owner" or "Preserve Owner", when I get to my laptop, I'll try to replicate your error.

---

### Post by Thumper322 on 2006-12-07
> **SyvanX said:**
> That makes it look like a unison error for sure. Something *is* being written by unison to the flash drive.

I think the *.#docname.random-numbers* are how unison treats the files until they are finished copying, when they are finalized they get their normal name.  

When you get back to your laptop, check in the preferences to see if there is an option set like "Synchronize Owner" or "Preserve Owner", when I get to my laptop, I'll try to replicate your error.

Where are the preferences?

Running **unison -perms 0** works, but I like having a GUI...

---

### Post by SyvanX on 2006-12-07
I'm sorry, I don't have any experience with using the GUI.  There aren't any preferences, and I couldn't find any way to set options via the GUI.  

I'm glad that the command line works, that means the GUI just needs some tweaking.

You can set options for the GUI the same way you set them for the command line, try running 
```
unison-gtk -perms 0
```

If it works, you can modify the menu for the Unison-GTK entry to include it so it runs that way every time.

---

### Post by Thumper322 on 2006-12-07
> **SyvanX said:**
> I'm sorry, I don't have any experience with using the GUI.  There aren't any preferences, and I couldn't find any way to set options via the GUI.  

I'm glad that the command line works, that means the GUI just needs some tweaking.

You can set options for the GUI the same way you set them for the command line, try running 
```
unison-gtk -perms 0
```

If it works, you can modify the menu for the Unison-GTK entry to include it so it runs that way every time.

Sounds good...

I don't suppose I could make a ".unisonrc" type of file for this?

---

### Post by SyvanX on 2006-12-07
Alright, I think this should work for you. :) 

You can add options to your profile.  Edit the profile file
```

nano ~/.unison/default.prf  # Substitute your profile name for *default*
```

Then add the following line below the roots listed in the file.

> perms=0

That should preserve the setting for your root without forcing Unison-gtk to always use perms=0.

---

### Post by Thumper322 on 2006-12-08
> **SyvanX said:**
> Alright, I think this should work for you. :) 

You can add options to your profile.  Edit the profile file
```

nano ~/.unison/default.prf  # Substitute your profile name for *default*
```

Then add the following line below the roots listed in the file.



That should preserve the setting for your root without forcing Unison-gtk to always use perms=0.

Bingo! This is perfect. Thanks! :-D

---

