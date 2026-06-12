---
title: "Evolution can't read backed up data"
date: 2016-03-20
forum: General Help
---

### Post by neela on 2016-03-20
I had a disk read error at boot time. Per suggestion on a different thread, I booted from a Live USB and moved the data to a NAS drive.

Some of the data are mail files from evolution -- i.e., the directory ~/.local/share/evolution. After I reinstalled Ubuntu on the same hard drive -- hoping that the drive may have a bit more life in it, I copied the files back. Now I am unable to open the mail files. Also, when I go to look at the files on the NAS drive, I can see that the files exist with reasonable size when I list them in the directory, but when I try to do anything else -- such as more, chmod etc, I get the message " No such file or directory". The file names are not normal -- not sure if that is important. Here is an example file name:  1441817462.22547_2.newlaptop:2,RS.

I have never seen file names with a comma. Would appreciate if anyone can help with the retrieving my old email. 

Thank you. 
Neela

---

### Post by neela on 2016-03-21
On further analysis I find that I am unable to even list the files or even copy them back to ubuntu (14.04) from the NAS drive. When I stepping into the bottom most directory and do 'ls -l', I need a sudo in front of it. Because the ownership is nobody:nogroup. Then each files is listed in the following manner:  "ls: 1441817555.22547_7838.new-laptop:2,: No such file or directory".  I tried to change the ownership and that didn't work.

I am able to see them from a Windows machine though.

I don't think this is an evolution problem. Not sure what it is though..

---

### Post by howefield on 2016-03-21
> **neela said:**
> Some of the data are mail files from evolution -- i.e., the directory ~/.local/share/evolution. After I reinstalled Ubuntu on the same hard drive -- hoping that the drive may have a bit more life in it, I copied the files back.

You may need to copy more than the ~/.local/share/evolution folder back, Evolution may spread the config files over more than one location (it certainly used to) but not having used Evolution for some years, I am not sure which paths you would need.

---

### Post by neela on 2016-03-21
Thanks for your response.  The issue is I am not able to copy the files back.  Says file or directory not found.  The files are there.  The ls command lists each file and says it is not found.  From the Windows side I can peek into the files.

---

