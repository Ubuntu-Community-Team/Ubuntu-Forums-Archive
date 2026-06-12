---
title: "Access Windows Partition from UBUNTU"
date: 2006-11-16
forum: General Help
---

### Post by EGE-FB on 2006-11-16
Hi, 

I would like to be able to access my Windows partition from Ubuntu and be able to read and write to it. Is there a tutorial on this? 

One more thing, how do I delete the "Examples" folder in my HOME folder? I can't seem to delete it for some reason (there's a little lock icon on the folder). 

Thanks

---

### Post by Ramses de Norre on 2006-11-16
Take a look [here](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only).
And I was able to just delete the examples folder, it's a symlink to some folder under /usr. Try "**unlink Examples**" in terminal if it wont work.

---

### Post by Griff on 2006-11-16
> **EGE-FB said:**
> 
One more thing, how do I delete the "Examples" folder in my HOME folder? I can't seem to delete it for some reason (there's a little lock icon on the folder). 

Thanks
Open up the terminal then:
```
sudo rm Examples
```

---

### Post by EGE-FB on 2006-11-16
Thanks for the help, "unlink Examples" seemed to work :). 

Now I'm trying the Windows portion.. Ill give an update soon.

---

### Post by EGE-FB on 2006-11-16
It says "E: Couldn't find package ntfs-3g" when I try to install that package..  What do I do?

---

### Post by Buck2348 on 2006-12-26
> **EGE-FB said:**
> It says "E: Couldn't find package ntfs-3g" when I try to install that package..  What do I do?In case you're still watching this thread, I think that "Couldn't find package" means you haven't got the right repository enabled in your /etc/apt/sources.list file.  Here is my file if you'd like to copy and paste it in yours.  Make a backup first.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

```
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

# Treviño's Beryl-SVN Ubuntu Repository
 # GPG key: 81836EBF
 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
Regards,
Buck

---

