---
title: "Back Up Documents Folder to Flash Drive"
date: 2008-04-23
forum: General Help
---

### Post by igfud on 2008-04-23
Hello,

I'm interested in backing up my Documents folder to a USB flash drive.  I don't care about any of the settings or system files, but I'd like to backup my Documents daily.  Are there any simple tools or scripts that might do this?  Since I'm using a laptop, I'm mot sure if an automatic schedule would work as I'm not sure when the computer is on or when the drive is plugged in.  Are there any quick ways of doing this on a daily basis?

Thanks,
igfud

---

### Post by ibuclaw on 2008-04-23
You can add a script in your logout file.
So that it saves the file to a tarball and stores it somewhere in the filesystem/on the pen drive.

```
 gksu gedit /etc/gdm/PostSession/Default 
```

Will get you there.

And before the line that says "exit 0"
Have something like this:
```

if [ -d "$HOME/Documents" ]
then
    export name=$(whoami)
    export time=$(date | awk '{print $2$3"_"$6}')
    tar cvf $name-Documents-$time.tar.gz $HOME/Documents
    mv $name-Documents-$time.tar.gz /media/**FLASHDRIVE**/BACKUP/
fi

```
That will save tarballs of your Documents folder.
The naming convention is simple enough:
**username**-Documents-**date**_**year**
ie:
iain-Documents-Apr24_2008.tar.gz
Is that verbose enough for you?

Regards
Iain

---

### Post by BandD on 2008-04-23
I like to use rsync (it is a command line program, but you can use Grsync as a graphical frontend).  It will do progressive backups, so it will only backup things that have changed since your last backup.  I use it to backup my laptop's /home to an eternal hard drive.

It has an insane amount of options that should suit almost anyone's needs.

---

### Post by igfud on 2008-04-24
> Is that verbose enough for you?

Perfect!! That is exactly what I was looking for.  Thanks!

I'll also look into rsync--sounds like it would be another good method of maintaining backups.

igfud

---

