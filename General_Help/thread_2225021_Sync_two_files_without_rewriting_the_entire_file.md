---
title: "Sync two files without rewriting the entire file"
date: 2014-05-19
forum: General Help
---

### Post by GigabyteProduction on 2014-05-19
I am working on a RAM drive setup where I mount a copy of my disk image from inside a tmpfs. I know I should be using tmpfs by itself but I want to save the contents. I want to make a script that will periodicly sync the copy of the disk image that's on my hard drive to the copy that's in the tmpfs. I don't want to just periodiclly run cp and copy the entire image because what if literally only a megabyte has changed since the last sync; I don't want to copy all 12 gigabytes on an interval and put too much stress on my hard drive.

I don't know if anyone has made what I have in mind, so i may have to a tool for myself if nobody has a suggestion, but i want a tool that will read from both files, and when it finds a difference between the two, to replace the part in the hard drive copy with the part in the tmpfs copy. I think i need a binary difference tool but all the ones i found use more ram than i can spare because they're trying to create the smallest patch file. The closest tool to my goal is diff and patch, because i can pipe directly from diff to patch without having to create the patch file, it just patches it live. diff fails me because it uses an enourmous amount of ram to try to make the patch file small, but i don't need it to make a small patch file because i'm not even using a patch file.

```
diff -au /onharddrive/image.img /ontmpfs/image | patch /onharddrive/image.img
```

Is there any tool that can patch a file to match another file without taking an enourmous amoutn of ram and without requiring me to make a patch file?

---

### Post by Gyokuro on 2014-05-19
Hi

Rsync can do the job and the sample you showed whould be with rsync: rsync /path/to/file :/path/to/second/file/ /local/directory/ or whatever you want (you can sync one file to two different directories or even machines, like server1 get synced to server2 and server3). However I think you only need two batch files or combine the whole logic in one batch file where you have to find out which one contains the newest image and that one get synced.

1.) rsync from harddrive.img to tmpfs image
 2.) rsync from tmpfs to harddrive image (you only need to compare time stamps which one is newer get rsynced)

---

### Post by HermanAB on 2014-05-19
rsync and unison.

Read the man pages.  Yes, really.  Read the man pages.

---

### Post by GigabyteProduction on 2014-05-19
ah, i thought rsync was just for two different machines.

thank you both!

> **Gyokuro said:**
> Hi

Rsync can do the job and the sample you showed whould be with rsync: rsync /path/to/file :/path/to/second/file/ /local/directory/ or whatever you want (you can sync one file to two different directories or even machines, like server1 get synced to server2 and server3). However I think you only need two batch files or combine the whole logic in one batch file where you have to find out which one contains the newest image and that one get synced.

1.) rsync from harddrive.img to tmpfs image
 2.) rsync from tmpfs to harddrive image (you only need to compare time stamps which one is newer get rsynced)

The image in tmpfs will always be the newest one, as that is the only one i am mounting. The one on the hard drive is there to make the one in ram.

i know that rsyc when used with two different machines works by sending the differences, but is that also how it puts the file together? I want to make sure i don't write unnecessary data when syncing the images, like if 1 megabyte changes on the actual drive, 1 megabyte should be all that's written on the next sync.

---

### Post by papibe on 2014-05-19
> **GigabyteProduction said:**
> is that also how it puts the file together? 
Yes. The algorithm is the same for local and remote transfers.
> **GigabyteProduction said:**
> I want to make sure i don't write unnecessary data when syncing the images, like if 1 megabyte changes on the actual drive, 1 megabyte should be all that's written on the next sync.
I recommend using the option --inplace, so that no temp files are created and the changes go directly to the final file.

Also, you may want to consider doing this differently. I'd recommend taking a look at the snapshot functionality that btrfs provides.

Hope that helps. Let us know how it goes.
Regards.

---

### Post by GigabyteProduction on 2014-05-19
Could you explain your snapshot idea? I don't understand how a snapshot mechanism will help me keep a hard drive copy of a filesystem in RAM synchronized.

---

