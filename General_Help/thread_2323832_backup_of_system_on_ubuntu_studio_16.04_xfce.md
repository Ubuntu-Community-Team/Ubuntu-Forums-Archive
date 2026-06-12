---
title: "backup of system on ubuntu studio 16.04 xfce"
date: 2016-05-08
forum: General Help
---

### Post by gaogle on 2016-05-08
successfully installed Ubuntu Studio 16.04 replacing Zorin 9 which would not recognize any USB pen sticks, now on Studio which works very well I am flumuxed on how to back up the entire system on the laptop, can anyone help???

---

### Post by RobGoss on 2016-05-08
Hello and welcome to the forum, There are a number of good open software programs that will allow you to backup your entire system one of my favorites that comes to mind is [Clonezilla ]("http://clonezilla.org/") this program is FREE and it will backup your entire system and give you a peace of mind knowing all your content is safe.

Here are a few screen shots just in case you'd like to see what it can do, [Clkonezilla screen shots ]("http://clonezilla.org/screenshots/?in_path=/00_Clonezilla")

I do recommend when creating a backup to use a external device that way if anything goes wrong with your machine you will still be able to restore your machine if needed

---

### Post by howefield on 2016-05-09
> **gaogle said:**
> successfully installed Ubuntu Studio 16.04 replacing Zorin 9 which would not recognize any USB pen sticks, now on Studio which works very well I am flumuxed on how to back up the entire system on the laptop, can anyone help???

If it is a clone of your partition/disk that you want, Clonezilla as RobGoss suggests is very good but there are limitations with what you can do with the resulting file, not sure I would tout it as a backup tool, perhaps for your own data files you could look at the included Backup utility which allows for single files from the backup to be restored. My own preference is to use rsync to copy data files to a bunch of other drives.

---

