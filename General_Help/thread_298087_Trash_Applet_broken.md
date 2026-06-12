---
title: "Trash Applet broken"
date: 2006-11-12
forum: General Help
---

### Post by Chris Slattery on 2006-11-12
I'm using Edgy and my trash applet has stopped working. Whenever I delete a file it doesn't appear in the trash, but it does appear in my ~/.Trash folder. When I delete them from there, they just reappear, so I can't delete files! Can anyone tell me how to redirect the trash applet to my ~/.Trash folder. I've tried reinstalling, but that didn't work.

---

### Post by Chris Slattery on 2006-11-12
Can anyone please help me with this? I can't delete any files off my computer!

---

### Post by kinematic on 2006-11-12
have you tried "sudo dpkg-reconfigure gnome-applets"
and you can delete files without the trashcan.....open nautilus and go to configure(i'm using the dutch locale so i'm not sure if that is what it's called but it's the second at the top left),behaviour,offer delete command that bypasses the trashcan.

---

### Post by Chris Slattery on 2006-11-12
> **kinematic said:**
> have you tried "sudo dpkg-reconfigure gnome-applets"
and you can delete files without the trashcan.....open nautilus and go to configure(i'm using the dutch locale so i'm not sure if that is what it's called but it's the second at the top left),behaviour,offer delete command that bypasses the trashcan.

The "sudo dpkg-reconfigure gnome-applets" didn't work, but thanks for the delete option, so that I can actually delete files now!:-D
I'd still like the trash applet to work, though...

---

### Post by kinematic on 2006-11-12
just to be sure ;) 
you did "sudo dpkg-reconfigure gnome-applets" without the quotes in a terminal....

---

### Post by Chris Slattery on 2006-11-12
> **kinematic said:**
> just to be sure ;) 
you did "sudo dpkg-reconfigure gnome-applets" without the quotes in a terminal....

Yes. It brought up a message about some CPU applet (which I didn't install) and it did something. I noticed it did restore the trash icon to its normal position, but it didn't fix my problem.

---

### Post by Chris Slattery on 2006-11-18
I've had no further help from anyone and this problem is still annoying me. I've searched the computer for any configuration files for the trash applet that could yield some way to change the path it uses, but have found nothing. This is very irritating; can no-one help me out?

---

### Post by robolange on 2006-11-19
I just decided to investigate why my Trash can hasn't been working. I found this post and noted that my ~/.Trash folder is full of old deleted stuff. One person can be written off as a fluke, but 2 people having the exact same problem... I bet there are a lot more people seeing this bug.

I am running 6.10, but I don't recall whether the Trash can worked even in 6.06.

---

### Post by robolange on 2006-11-19
I found a confirmed bug report for Ubuntu documenting this behavior:

[https://launchpad.net/distros/ubuntu/+source/gnome-applets/+bug/34247](https://launchpad.net/distros/ubuntu/+source/gnome-applets/+bug/34247)

and another forum thread:

[http://www.ubuntuforums.org/showthread.php?p=811629](http://www.ubuntuforums.org/showthread.php?p=811629)

It seems that this bug is caused when you insert a removable device and delete something from it. Rather than just deleting the item from the device like one would expect, someone had the brillant idea of creating a .Trash-username folder in the root of the removable device's filesystem and moving the deleted item there. As this bug documents, for some reason the Nautilus Trash bin can get confused and only look in the removable device's trash folder, rather than in your main trash folder.

In my case, my Nautilus Trash is now linked to the .Trash-rlange folder on my LS-120 floppy disk. If I delete things from the floppy, then Trash icon changes and the Trash can works correctly. However, if I delete things from my home directory, they go in the ~/.Trash folder but the Trash icon doesn't change and the Trash folder doesn't show them.

This stems from another bug:

[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/12893](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/12893)

This bug was filed against the whole practice of putting trash folders on removable devices. The general consensus is that items on removable devices should just be deleted, like they are under every other operating system. Unfortunately, there seems to be some hand-wringing about scenarios in which a desperate user wants to recover a lost file, so the fix seems to be held up and they might try to think up a yet-more-complicated (and therefore buggy) solution. Hopefully common sense will prevail and someone will just implement a simple fix that gets rid of trash folders on removable devices and makes Nautilus Trash look only in ~/.Trash.

And hopefully, it won't take another 6 months to get this fix. So far I have not found any method of letting users afflicted with this bug fix their Trash can. The only useful thing I can do is follow the advice earlier in the thread and enable the Delete command in Nautilus to bypass the Trash, or just use the command line to delete things.

I recommend we move this discussion over to the forums thread I mentioned in this post. That thread is much older and people there may know more about this problem.

---

### Post by Chris Slattery on 2006-11-19
> **robolange said:**
> I found a confirmed bug report for Ubuntu documenting this behavior:

[https://launchpad.net/distros/ubuntu/+source/gnome-applets/+bug/34247](https://launchpad.net/distros/ubuntu/+source/gnome-applets/+bug/34247)

and another forum thread:

[http://www.ubuntuforums.org/showthread.php?p=811629](http://www.ubuntuforums.org/showthread.php?p=811629)

It seems that this bug is caused when you insert a removable device and delete something from it. Rather than just deleting the item from the device like one would expect, someone had the brillant idea of creating a .Trash-username folder in the root of the removable device's filesystem and moving the deleted item there. As this bug documents, for some reason the Nautilus Trash bin can get confused and only look in the removable device's trash folder, rather than in your main trash folder.

In my case, my Nautilus Trash is now linked to the .Trash-rlange folder on my LS-120 floppy disk. If I delete things from the floppy, then Trash icon changes and the Trash can works correctly. However, if I delete things from my home directory, they go in the ~/.Trash folder but the Trash icon doesn't change and the Trash folder doesn't show them.

This stems from another bug:

[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/12893](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/12893)

This bug was filed against the whole practice of putting trash folders on removable devices. The general consensus is that items on removable devices should just be deleted, like they are under every other operating system. Unfortunately, there seems to be some hand-wringing about scenarios in which a desperate user wants to recover a lost file, so the fix seems to be held up and they might try to think up a yet-more-complicated (and therefore buggy) solution. Hopefully common sense will prevail and someone will just implement a simple fix that gets rid of trash folders on removable devices and makes Nautilus Trash look only in ~/.Trash.

And hopefully, it won't take another 6 months to get this fix. So far I have not found any method of letting users afflicted with this bug fix their Trash can. The only useful thing I can do is follow the advice earlier in the thread and enable the Delete command in Nautilus to bypass the Trash, or just use the command line to delete things.

I recommend we move this discussion over to the forums thread I mentioned in this post. That thread is much older and people there may know more about this problem.

Thanks for the info robolange. Good to see that this has been recognised as a bug and that there is some closure to this. I propose posting the temporary solution of enabling the delete file function somewhere, so that others with this problem will have some way of deleting files from their computer.

---

