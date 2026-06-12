---
title: "Prob w/ Open Office word processor"
date: 2007-01-25
forum: General Help
---

### Post by Hickeydog on 2007-01-25
I don't know if this is the correct place to post this, but I'll give it try
I am trying to save a document using OpenOffice word processor.  I want to save it on my XP partition so I can access it from XP.  It says I cannot save it because the file I am trying to save does not exist.  Bassically, when I go to save, it comes up the error "could not save physix.doc.  /media/hrd2/curtis/physix.doc does not exist"  I know it doesn't exist becaue I AM TRYING TO SAVE IT!!!!!! grrrrrr.  that's almost as annoying as XP's errors.  oh well.  I tried to save it under my Ubuntu partition too, but I got the same error message.  The only place I could save it was my Ipod.  I tried to edit the permissions under the hdd settings, but it comes back with the error message "sorry, couldn't change the permisions of "filesystem."" It as if I could, but when I try, I get that error message.  I can't even get to the permissions page of my XP partition.  Any help as far as editing hdd permisions would be a greatly appreciated.

---

### Post by slimdog360 on 2007-01-25
Were you trying to save it to a NTFS partition? if so then that would be a great part of your problem right there. Im not sure why it wouldnt save to your Ubutnu partition, was it your /home folder to which you were trying to save? If not then try it there, or your desktop.

A few links you may want to look at
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_permissions")
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Hard_Drive]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Hard_Drive")

---

### Post by Hickeydog on 2007-01-25
ah.  Yes.  my xp partition is NTFS.  I wanted to save it there because then I could access it on the network.  I have not yet figured out how to network Ubuntu with a windows network.  last time I tried, I almost jumped off a bridge.  thanx 4 the help

---

### Post by keith11 on 2007-01-31
Please correct me if I am wrong but I think you are trying to save a file on a NTFS partition. As far as I know, you can't write to an NTFS partition which means you can't save on that drive. If you meant by networking Ubuntu and Windows that you want to see files saved from Ubuntu in Windows, then all you have to do is convert that particular windows partition to a FAT32 partition from being an NTFS one. You can use partition magic (in windows) for that. Hope this helps.

---

