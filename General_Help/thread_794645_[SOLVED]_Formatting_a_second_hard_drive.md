---
title: "[SOLVED] Formatting a second hard drive?"
date: 2008-05-14
forum: General Help
---

### Post by Thelonius on 2008-05-14
I am currently running feisty fawn, and wish to install Gutsy Gibbon. Running an upgrade kept creating problems, so I decided I want to do a clean install. The only thing I want to back up is my music (about 50 gb). I do not have an external hard drive, but I do have a second hard drive on this computer that wasn't formatted when I originally installed feisty. This hard drive shows up in my file browser, but does not allow any kind of access. Is it possible to format this hard drive for use, put my music files on it, and do a clean install of Gutsy without losing them? If so, how would I go about doing this? I would greatly appreciate any suggestions.

---

### Post by macaholic on 2008-05-14
You can format it with gparted. (sudo apt-get isntall gparted) (Located in system Administration Partition Editor) Then you should be able to jsut copy the fiels over, clean isntall and then back again.

---

### Post by Thelonius on 2008-05-14
Install of gparted worked perfectly. However, when prompted what I want to format it to, I selected 'ext3,' because that is what my other major hard drive (the one I'm currently using) appeared to be formated to. There was an error, and now this second hard drive appears to be locked up, and won't let me select another format. Any ideas?

---

### Post by sweeneytodd on 2008-05-14
open gparted delete the partition u r talking about and repartition and reformat, I think its best to use ext2 as ext3 i think is for root directories, i just use ext2 because of this

---

### Post by EXCiD3 on 2008-05-14
Its best if you partition your drives using GParted from the LiveCD. Just boot into it, then do the partitioning. You can copy your files from the LiveCD too if you mount the drives or you can boot into Ubuntu and copy the files there like normal.

---

### Post by Thelonius on 2008-05-14
That makes sense, but there is a slight problem - it is locked up to the point that just deleting it is seemingly impossible. Is there another way to get rid of/undo this failed partition? I enclosed a screenshot if it helps at all.

---

### Post by sweeneytodd on 2008-05-14
have you tried the live cd suggestion

---

### Post by sweeneytodd on 2008-05-14
don't know if you know how to do this but in my bios i can select which hard drive to boot from, so if you can do this, install hardy on ur 2nd drive and then change back, you won't need a live cd this way

---

### Post by EXCiD3 on 2008-05-14
From what i can tell, the partition is not formatted...If it is, you should delete it then create it over again.

---

### Post by Thelonius on 2008-05-14
> **EXCiD3 said:**
> From what i can tell, the partition is not formatted...If it is, you should delete it then create it over again.

I think you are right. . . I deleted it, created it over again, and the new partition appears to have worked perfectly when looking at the gparted window. However, now this hard drive does not appear in my file browser. I attempted to access it through the command prompt, but I received a response that told me I did not have permission. Is there any way to make this hard drive show up again? Thank you for all of your help so far, I really appreciate it.

---

### Post by EXCiD3 on 2008-05-14
Here is how you can mount linux partitions through terminal: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Glad to help, and hope it works for you!

---

### Post by Thelonius on 2008-05-14
That tutorial worked perfectly, my second hard drive is doing just what I want it to now. Thank you all for the help!

---

### Post by EXCiD3 on 2008-05-15
No problem! You should mark this thread as Solved via the Thread Tools menu at the top of the page. Don't forget to thank users for their help by clicking the blue medal on the right of their post. ;)

---

