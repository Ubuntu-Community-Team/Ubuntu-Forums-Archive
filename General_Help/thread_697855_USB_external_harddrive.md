---
title: "USB external harddrive"
date: 2008-02-15
forum: General Help
---

### Post by topic58 on 2008-02-15
I'm in on my 5th Lacie external harddrive now. This time in big trouble I think. I couldn't write to it so I fixed that in terminal "sudo chmod 777 -R disk"
Still problems, so I formatted it to ext 3. Now it worked nice in my old pc with Ubuntu. When mounting the same disk in my new pc with Ubuntu the filesystem couldn' t be recognized. :( Well, another format back to vfat (fat32). But Gnome Partition Editor just kept working, never to be ready. After 2 hours I interupted the process.
Now I can mount the Lacie, but all files are very strange, just some very odd signs in the filenames... When trying to format the disk again in Gnome Partition Editor it just keeps seeking for disks, unable to find my unmounted Lacie. Without Lacie no problems finding my other two disks. SO WHAT TO DO HERE? Is the disk bad news or is there still hope for it go get going? Please someone!

---

### Post by topic58 on 2008-02-16
Anyone out there who knows what to do?

---

### Post by topic58 on 2008-02-16
I know there are a lot of gurus out there knowing everything about this. Some really tricky problems have been solved thanks to you. Maybe I'm in the wrong forum thread here??
Looks like this.

---

### Post by topic58 on 2008-02-16
Maybe use fdisk in terminal instead of Gnome Partiton Editor? But how to do this? And how to be root-owner of the USB-disk? Tried everything, but with error because of the strange text in the disc...

---

### Post by topic58 on 2008-02-16
sudo mke2fs -j /dev/sdc1
stops here: write inode tables 64/3727
I guess the USD-drive is kaputt...

---

