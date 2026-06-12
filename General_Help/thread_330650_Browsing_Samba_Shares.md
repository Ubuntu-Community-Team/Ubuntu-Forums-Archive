---
title: "Browsing Samba Shares"
date: 2007-01-03
forum: General Help
---

### Post by Buck2348 on 2007-01-03
There is a bug in Edgy that makes it difficult to browse samba shares.  The workgroup and the remote computers show up with a generic text file icon, and clicking on that produces the following error:  "Couldn't display "smb:///mshome".  The location is not a folder."  Repeatedly clicking on the icon or on "Reload" eventually allows me to get into the shared folders.  The bug is documented on[ Launchpad.]("https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277")  I tried several ways to apply the fix without success.  I tried both patching the package and using a later version with the patch already applied.  I got into dependency hell and even when I finally apparently got the package gnome-vfs2 installed it didn't fix the problem.  Can anyone tell me how to apply the patch they have and fix this problem?

Thanks,
Buck

---

### Post by wpshooter on 2007-01-03
Well, I see that I am not the only person that has noticed this.  I noticed this a while back and I think I reported it at the time.  I finally just gave up on trying to get this to work on a consistent basis.

Is it possible that if I have installed ALL available updates as shown in Update Manager (which I normally do when they are available), that this will NOW work consistently ?

Thanks.

---

### Post by Buck2348 on 2007-01-03
> **wpshooter said:**
> 
Is it possible that if I have installed ALL available updates as shown in Update Manager (which I normally do when they are available), that this will NOW work consistently ?

Thanks.
I don't think updates will fix it until Launchpad shows "Fix Released" for Edgy.  I don't know anything about the process for fixing bugs, but it seems to me that since it's fixed in gnome-vfs2 they could release an update fixing it in Edgy.  Some posts on the Launchpad page say they have applied the patch and it works in Edgy.

A workaround is to mount the shares--that gives faster access to them than samba does when it's working right.  There's a how-to [here.]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")  A little more than halfway down the page, "How to mount network folders on boot-up."

Buck

---

### Post by tagra123 on 2007-01-03
> **Buck2348 said:**
> I don't think updates will fix it until Launchpad shows "Fix Released" for Edgy.  I don't know anything about the process for fixing bugs, but it seems to me that since it's fixed in gnome-vfs2 they could release an update fixing it in Edgy.  Some posts on the Launchpad page say they have applied the patch and it works in Edgy.

A workaround is to mount the shares--that gives faster access to them than samba does when it's working right.  There's a how-to [here.]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")  A little more than halfway down the page, "How to mount network folders on boot-up."

Buck

Its not the same problem, but I had a similar problem. I've pointed to this on several samba/nautilus posts. This bugged me since Jun 2006. Finally found a workable solution. I like Ubuntu but some of the "lack of planning, documentation or whatever it is?"

Surely a real techy or developer of Ubuntu could clear these sorts of thing up fo us.  Anyway I got it to work in dapper and am posting in every post that asked the question.

[http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18](http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18)

---

