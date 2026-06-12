---
title: "Rsync, Couple of Queries"
date: 2017-09-18
forum: General Help
---

### Post by taylrox on 2017-09-18
Good evening all,

I have around 500Gb of files (totaling around 10Gb a pop) and I've been looking at the best way to do a copy/file backup onto an external HDD (USB 3.0). I originally just drag and drop copied but this took absolutely ages (hours and hours), not to mention I found problems whilst doing so such as files not copying properly, partial copying, severe slowing down during copying (going from ETA's of round 1 hour to 56+ hours). 

Looking into the various ways to copy multiple files, large ones at that, I've come across a lot of people recommending Rsync. Now, in my newbness I'm getting myself confused with the different ways of using this and with all the little letter commands that follow it. How do I copy large files from one directory to another using rsync? 

Do I simply put:```
 rsync destination/of/source/folder destination/of/copyto/folder ?
```

And also, if there are already files in the copy to folder, this won't overwrite them/remove them will it? And lastly, when I have copied over the files, should I create more in the source folder (removing the old files) and then wish to copy the new files over, do I just use the same command? And will that just copy the files into the destination folder along side the existing ones?

And lastly, is rsync fail safe (or as near as you can get) with copying large files over in one go? Should the copy balls up do I just run it again?

Any help with this would be greatly appreciated. Any alternatives to this would also be welcomed.

Regards,

Tayl.

---

### Post by taylrox on 2017-09-18
[B]Update:
[/B]After Googling and trolling through various sites I think I got the jist of it. I ran the following command:

rsync -arvzP /source/directory/ /end/directory/ 

And even with this I am noticing a rapid drop in speed when it gets about 25% into the transfer/copy. It goes at around 15Mb per second for the first 25% but then drops down to plodding along at 1mb per second for the remainder of the copy.

Any clues on what's going on here/how to copy at the same continuous speed?

Regards,

Tayl.

---

### Post by Dennis N on 2017-09-18
Is the destination drive formatted ext4? Unless your external disk is ext4 filesystem, time stamps may not test as equal due to differences in accuracy with FAT32 times, and cause copy to take place anyway. To see in real time what files are being copied, include the -i option. Use the -n option for a trial run.

another option (must use terminal, not file manager):

**cp** does have an update option so not every file would get copied. With recursive also, that would be **cp -ru**. So often this is sufficient. The **-n** option in **cp** will only add new files to your backup.

I think slowing of copy speed as copying progresses is normal with big file transfers. I see it too.

---

### Post by taylrox on 2017-09-18
Hi Dennis,

Many thanks for the reply.

Using cp in the command I assume is the same sort of text as rsync'ing? For example: ```
cp -ru /folder/origin/ /newfolder/forfiles/tobecopiedinto/
```

Is adding the -n syntax to the -ru ok? For example: -nru?


The filesystem of the external HDD is NTFS. I couldn't format it to  ext4 as I'm not sure on whether or not the software on my devices would  be able to read it.

Regards,

Tayl.

---

### Post by C.S.Cameron on 2017-09-18
grsync is rsync with a GUI. I find it a lot easier to use.

---

### Post by SeijiSensei on 2017-09-19
> **taylrox said:**
> The filesystem of the external HDD is NTFS. I couldn't format it to  ext4 as I'm not sure on whether or not the software on my devices would  be able to read it.
You're going to lose important information about the filesystem if you try to copy it with rsync to an NTFS-formatted device.  NTFS doesn't know about *nix permissions or primitives like symbolic links.  

Most anything can read an ext4 filesystem exported via Samba.  If you want to mount an ext4 device natively in Windows, you can use [ext2fsd](http://www.ext2fsd.com/?page_id=16).

---

### Post by taylrox on 2017-12-09
Hi all,

My apologies for reviving an old thread but the tutorials online are confusing me. With the CP command, is there any way of adding a certain syntax to show you the progress/speed of the copies in the terminal? 

Regards,

Tayl.

---

### Post by Dennis N on 2017-12-09
> **taylrox said:**
> With the CP command, is there any way of adding a certain syntax to show you the progress/speed of the copies in the terminal? 

Use -v option to see progress but I think rate of transfer not possible with cp terminal command. 'Progress' here means it will list each file as it is copied.
```
dmn@Sydney ~/work/testing/f1 $ cp -v * ../f2
'file1' -> '../f2/file1'
'file2' -> '../f2/file2'
'file3' -> '../f2/file3'

```
In rsync, the -i option will display the copied files as each is copied.
```
dmn@Sydney ~/work/testing/f1 $ rsync -i * ../f2
>f+++++++++ file1
>f+++++++++ file2
>f+++++++++ file3

```

---

