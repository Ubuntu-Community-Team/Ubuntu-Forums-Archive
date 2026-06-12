---
title: "Desperately need to backup to host or CD!"
date: 2013-01-13
forum: General Help
---

### Post by Franknj229 on 2013-01-13
My host computer is very unstable and I need to back up files from my Ubuntu guest.  I once had a share folder that I successfully transfered files to from the guest to the host, but that isn't working anymore, and I can't get the guest to recognize my CD/DVD burner. (To clarify, the reason I would be willing to transfer files to an unstable host is because I can then transfer the files to an external hard drive.  It's the only way I know how to do that.  If there is an easier way, cut out the middle-man, I would love to give it a try)

I have googled these issues and tried every suggestion I found, but nothing seems to relate to my systems.  (ie., "click this" - Well, I don't have that.  Or, "type this" -Error message)

I am very weak when it comes to Linux, so please be detailed if possible.  If something seems obvious to you, it doesn't to me.

Thank you for your help,

Frank

---

### Post by SeijiSensei on 2013-01-13
I suggest simply exporting the virtual machine itself.  If you're using VirtualBox, select a VM from the main VirtualBox screen and pick File > Export Appliance.  You'll need as much disk space for the image as you allocated when you created the machine.  Then when you get things straightened out you can re-import the VM.

---

### Post by Franknj229 on 2013-01-13
Thanks for the suggestion.  I exported the VM to my external hard drive.  I just want to verify a couple things before I move on.

1) I originally gave the VM a 60GB hard drive, but the exported file is only 11GB. Did you mean the file would be literally the exact size I originally alocated? Or does the 11GB simply indicate how much I have stored currently?  In other words, is this ok?

2) When I inport the file back into VirtualBox later, it will contain all my files, photos, bookmarks, etc.?

Thanks again!

---

### Post by btindie on 2013-01-13
Have you tried googling for "[Ubuntu virtual box guest additions]("https://forums.virtualbox.org/viewtopic.php?f=1&t=51459")" as it comes up with some results that may help. It may be worth while uninstalling the existing guest additions and then reinstalling it.

The other option is to use ssh which will allow remote access to the guest from the host, which I presume would be windows? To do so, install the ssh server on your guest. You can then use something like WinSCP to access the remote filesystem and copy them directly to your USB hard disk.

If this is something you wanted to do on a regular basis you could look at using rsync over ssh instead.

---

### Post by SeijiSensei on 2013-01-14
> **Franknj229 said:**
> 1) I originally gave the VM a 60GB hard drive, but the exported file is only 11GB. Did you mean the file would be literally the exact size I originally alocated? Or does the 11GB simply indicate how much I have stored currently?  In other words, is this ok?

I think you should be fine. I believe that the VM disk is sized dynamically, with the 60GB being a ceiling.  You might want to do a little research on the [VirtualBox site](http://www.virtualbox.org) just to make sure.

> 2) When I inport the file back into VirtualBox later, it will contain all my files, photos, bookmarks, etc.?

It is an exact image of the virtual machine.  If the files, etc., were stored on the VM's virtual disk, they will be there when you reinstall.

---

