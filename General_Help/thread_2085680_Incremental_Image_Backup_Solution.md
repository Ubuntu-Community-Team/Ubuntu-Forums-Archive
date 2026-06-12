---
title: "Incremental Image Backup Solution?"
date: 2012-11-18
forum: General Help
---

### Post by jlacroix on 2012-11-18
I am hoping that a solution exists to achieve what I want. Basically, I want to be able to take a snapshot image of my hard drive but prevent certain folders from being a part of the image. For example, I want to skip my Music folder and not have that be part of the image since I already back that up.

Currently, I use Clonezilla as my image backup solution. With it, I can take an image of my PC and restore it bare-metal and be back up and running. However, my laptop has over 100GB of personal files that I don't want to image. As far as I know, I don't think Clonezilla has any ability to skip specific folders.

I know I can create a tar image of my hard drive, and skip folders with that. However, to restore it, I would have to format the drive, restore the tar.gz file, and then reinstall Grub. That's a pain, I'd rather just restore an image (with one step) like you can with Clonezilla, but be able to skip folders.

Is there such a thing? I'm pretty sure there isn't because I've not found anything in my search yet. I asked this question several years ago and turned up nothing, but hopefully something came around since then...

---

### Post by quickk on 2012-11-18
I'm pretty sure that you can do this with rsync.  Here are a few examples that might be useful for you: [http://www.thegeekstuff.com/2010/09/rsync-command-examples/]("http://www.thegeekstuff.com/2010/09/rsync-command-examples/")

[http://www.thegeekstuff.com/2011/01/rsync-exclude-files-and-folders/]("http://www.thegeekstuff.com/2011/01/rsync-exclude-files-and-folders/")

---

### Post by oldfred on 2012-11-18
I only use rsync and assume I will just do a new clean install and restore just my data.

But I have this in my notes. It says you can list the folders you want to include.

       Tar backup script:
[https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html)


> For example, a script can be used to configure which directories to backup, and pass those directories as arguments to the tar utility, which creates an archive file.

---

### Post by jlacroix on 2012-11-18
> **quickk said:**
> I'm pretty sure that you can do this with rsync.  Here are a few examples that might be useful for you: [http://www.thegeekstuff.com/2010/09/rsync-command-examples/]("http://www.thegeekstuff.com/2010/09/rsync-command-examples/")

[http://www.thegeekstuff.com/2011/01/rsync-exclude-files-and-folders/]("http://www.thegeekstuff.com/2011/01/rsync-exclude-files-and-folders/")
Thank you for your reply, but I don't think that's what I'm looking for. I am pretty sure that rsync is used to backup files, but I already do that. I'm looking for an image capture solution that will let me do a bare-metal recovery.

> **oldfred said:**
> I only use rsync and assume I will just do a new clean install and restore just my data.

But I have this in my notes. It says you can list the folders you want to include.

       Tar backup script:
[https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html)
Thank you. I've seen backup scripts similar to that one before. It is good that I can create a snapshot of the entire filesystem, however, that method doesn't seem to allow a bare-metal recovery without having to format the drive and install GRUB manually (unless I missed something). If I can't find anything else, I'll use that method.

---

### Post by drmrgd on 2012-11-19
I think it's going to be an all or nothing kind of thing.  You can either image the whole drive and then easily recover from that image, or you can backup chunks with a tool like rsync (or better, rsnapshot).

---

### Post by clifford junior on 2012-11-19
i was using backintime to do local backups to my external hard disk.

recently though ive been using crashplan. i can use crashplans software to backup to both my external harddrive and to crashplans server. i recommend it to everybody.

---

### Post by SlugSlug on 2012-11-19
am a backintime user but when I tried to restore some sys files it did not replace the *setuid *for files that needed it.

---

### Post by jlacroix on 2012-11-19
> **clifford junior said:**
> i was using backintime to do local backups to my external hard disk.

recently though ive been using crashplan. i can use crashplans software to backup to both my external harddrive and to crashplans server. i recommend it to everybody.
I use Crashplan and recommend it too, but it does not create an image of your machine.

---

