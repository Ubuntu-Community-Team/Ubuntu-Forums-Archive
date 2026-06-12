---
title: "problem regarding mounting ntfs system into /dev/hda1"
date: 2005-04-30
forum: General Help
---

### Post by young on 2005-04-30
Hello there,



           I checked out the ubuntu guide (pretty helpful so far) to see how I would
    mount my ntfs system (for windows XP) into the /dev/hda1/ (for my ubuntu).

          Everything works smoothly so far, but I just want to know if it would be possible for me to edit things like text files or even my java program in windows xp, using the mount technique.   So far, this is the only thing I know:

```
 sudo mount /dev/hda1 /home/young/windows -t ntfs -o umask ='some number'

```

        I just don't know which number i have to type in to set the permissions.  Thank you in advance.


                                                                                                    Cheers,

                                                                                                                Young

---

### Post by jodef on 2005-04-30
Write access is only available on FAT partitions, NTFS write access is at best experimental and could result in data corruption or loss hence it's not covered in the guide.

---

### Post by young on 2005-04-30
Hi there,

             Thank you very much for your reply.  Now I get it.  Is there any way I could edit 
     my text or java files in Windows from Ubuntu? I do have significant amount of .java 
     .pl and c++ files saved in Windows system.  

                                                                                             Cheers,
                                                                                                                   Young

---

