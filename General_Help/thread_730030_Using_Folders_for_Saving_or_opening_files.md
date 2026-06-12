---
title: "Using Folders for Saving or opening files"
date: 2008-03-20
forum: General Help
---

### Post by dcallman49 on 2008-03-20
I use Gutsy on my laptop Dell 1501, updated from Fesity, and have it networked at home with windows desktop with much more storage than my laptop.  Using places, I have permanently placed links to network drives and I can open files using nautilus just fine and copy files from local disks to network disks, just fine.  But with many applications, I am not able to save to a networked disk easily or to open a document on a networked drive.  I have been using Ubuntu for about a year and would like to know an easier way than copying to and from home folder and using nautilus for transferring to networked storage.

Thanks

David

---

### Post by ohzopants on 2008-03-20
*I assume you are using samba to access the windows shares.*

If you actually mount the shares, programs won't know that they are network files, so there shouldn't be a problem.  There are plenty of good howtos on this in the forums.

Be carefully about making samba shares mount automatically on a laptop though, since you will get some errors if/when you are not on your home network.

---

### Post by dcallman49 on 2008-03-20
Thanks, I will Mount them, I have been usung samba shares.  Since it is a laptop is there a way to make a script that I can run to mount drives when I am connected to the desired network.

Thanks a lot.

David:)

---

### Post by ohzopants on 2008-03-21
Yeah, and it's a pretty easy script too.  Just figure out the proper mount command for your shares and slap it in a script.  I'm no expert in scripting, so I won't propose one here since I don't want to be responsible in case it goes wrong.

There a roughly a gajillion tutorials on making bash scripts which are all better than what I could teach you.

You could also check out smb4k ([http://smb4k.berlios.de/](http://smb4k.berlios.de/)), which I believe is in the repos.  It's a pretty good gui for mounting samba shares, or at least it was last time I tried it.

---

### Post by dcallman49 on 2008-03-21
Thank you very much for your help.  I will try the Gui you recommended.  

Dave:KS

---

