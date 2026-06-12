---
title: "saving email attachments to windows shared folder"
date: 2007-01-13
forum: General Help
---

### Post by michael.fries on 2007-01-13
I have a windows shared folder on an XP box.  It was pretty east to access it within Ubuntu, and I now have a pretty little icon on my desktop.  When using an application like open office, when I select "save as", and then select "Browse for other folders" within the provided pop up window this shared drive appears as a choice, and it is easy to save to it.

However, when using Thunderbird and trying to save an attachment, even though an almost identical pop up window appears, this shared drive is not provided on the list when I "Browse for other folders" .  

How can I get this shared file on the list of places I can save an attachment to?

Thanks,
Mike

---

### Post by michael.fries on 2007-01-26
The question may also be answered if I could find out where on the "usual" hierarchy shown by the file browser the shared folders on the network exist under "Computer".  I don't even know if they do or not, but they may.

What's funny is that event though I have a "folder" on my desktop, when I use the terminal window and the command "ls -al", that folder does not appear.  

When I use the file browser, on the left, there are 5 places, one of them is this network drive.  Clicking on this drive, the location bar provides the message "smb://yi".  I am not sure if this is useful, but I thought I would mention it anyway.

Thanks,
Mike

---

### Post by michael.fries on 2007-01-27
Eventually, I found the correct post.  It seems that however the networking tools in UBUNTU found the folder on my network, it did not update fstab, it did it some other, to me unknown, way.  This post was really all I needed, along with a hint I found somewhere to install smbfs!

[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

