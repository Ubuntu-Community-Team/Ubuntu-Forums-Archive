---
title: "[SOLVED] Symlink multiple directories into one?"
date: 2008-01-02
forum: General Help
---

### Post by ravid on 2008-01-02
Hello All, 

I just installed Mythbuntu on an old box that i had laying around and put it into my living room as a MPC.  This compliments the household of three ubuntu boxes and one mac (totally windowless! sweet!).  Anyway my question is this.  

On the myth box, i have mounted several network shares (using fstab), and now i want to sym link all the video folders across those various mount points to ONE video folder for easier access.

Eg. /mountpoint1/TV-PC1, /mountpoint2/TV-PC2, /mountpoint3/TV-PC3  ALL pointing to /media/TV so all the files are accessible in one folder.

I know vista has something called directory junctions, im gonna assume that we have something comparable, i just don't know how to do it  :)

Any help is appreciated!
Cheers!
RaViD

---

### Post by PeterJS on 2008-01-02
What you're looking for is unionFS, good news bad news, good news it there are 3 implementations: funionFS, unionFS, and auFS. The first two of which are in the ubuntu repositories. Bad news is they all seem to be in some sort of competition over who can produce the worst documentation.

---

### Post by ravid on 2008-01-03
Perfect!  I'll have a look and play with it when i get home tonight... I'll let you know how it goes!  

Thanks  :)

---

### Post by ravid on 2008-01-03
Hey i got it working!  And your right.. there really wan't any documentation to speak of for any of those projects (and what there was seemed squarly aimed at developers creating LiveCD's).  However i did find an article at Linux Journal [here]("http://www.linuxjournal.com/article/7714")  that managed to sort things out for me.  

Basically what i did for those wanting to know:

1) created a mount point for my new union (/media/union)
2) ran command:

sudo mount -t unionfs -o dirs=/media/dir1:/media/dir2 none /media/union

That was about it... i also installed an extra package called unionfs-tools (i think) and it has a command unionfsctl that lets you add and remove and manage directories in your union.

Thanks again for the help!
Cheers!
RaViD

---

