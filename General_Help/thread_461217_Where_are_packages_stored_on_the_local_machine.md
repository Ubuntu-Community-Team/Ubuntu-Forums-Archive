---
title: "Where are packages stored on the local machine?"
date: 2007-06-01
forum: General Help
---

### Post by wjhildreth on 2007-06-01
Hello all,

So many questions and so little time ....

Anyway, when you use apt-get to download and install packages, where are the packages stored? Or are they just downloaded and deleted after install?

I am in serious play mode trying to figure out Ubuntu, and was wanting to burn some of the larger packages to a CD to make sort of what I call a local repository.

Can someone point me to where the .debs are stored?

Many thanks for your time and energy.

Regards,

Joe Hildreth

---

### Post by pbw on 2007-06-01
/var/cache/apt/archives/

--pbw

---

### Post by wjhildreth on 2007-06-01
Thanks for the quick response. Now, can I burn debs to a CD and use the CD as one of my sources? Is there anything I need to do special to make that work?

Regards,

Joe

---

### Post by pbw on 2007-06-01
See apt-move for making a cd repo out of your cache, you'll have to install it (sudo apt-get install apt-move).. here's a rundown for you - [https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto) 

Or you can just burn the debs, pop the cd in and use dpkg to install them.

-- pbw

---

### Post by adamz70 on 2007-06-04
Hey everyone, does anyone know if is there a noob's apt-move?

The process described in the 'how-to' looks somewhat tedius, and i'm thinking if there's Automatix-style progams to automate their installation, perhaps there's another one to automate the moving of repositories?

I'm trying to take the archives from a working Edgy machine to a POS i've got to run Xubuntu without working USB ports (!!!)

Thanks in advance!!

---

### Post by pbw on 2007-06-04
I don't know of any such tool, but apt-move really isn't difficult. Just read and follow the steps. It doesnt take long.

---

### Post by adamz70 on 2007-06-04
Oh, cool. No problems, I was just being lazy & thought I'd ask!

;)

---

### Post by wjhildreth on 2007-06-05
> **pbw said:**
> See apt-move for making a cd repo out of your cache, you'll have to install it (sudo apt-get install apt-move).. here's a rundown for you - [https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto) 

-- pbw

Thanks pbw for the link and info.

Regards,

Joe Hildreth

---

### Post by pbw on 2007-06-05
You're welcome Joe, hope it helps.

---

### Post by moiovo on 2008-05-23
> **pbw said:**
> I don't know of any such tool, but apt-move really isn't difficult. Just read and follow the steps. It doesnt take long.

I tried to configure apt-move from [https://help.ubuntu.com/community/AptMoveHowto]("https://help.ubuntu.com/community/AptMoveHowto") but on step 3 ("Because ubuntu repository structure, not all packages are inserted into the Packages.gz file by apt-move. We must remake Packages.gz with the help of apt-ftparchive.") after copying " [B]cd /mirrors/debian
apt-ftparchive packages pool/main/ \
  | gzip -9c > dists/dapper/main/binary-i386/Packages.gz
[/B]" in a terminal I receive this Error: **"Unable to open   - fopen (2 No such file or directory)"**
can anyone tell me what have I done wrong?
thanks

---

