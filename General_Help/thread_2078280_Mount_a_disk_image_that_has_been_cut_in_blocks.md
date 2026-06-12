---
title: "Mount a disk image that has been cut in blocks"
date: 2012-10-30
forum: General Help
---

### Post by Anastasios Marmaras on 2012-10-30
Hello everyone, 

I am wondering if it is possible to mount a disk image that has been cut in blocks (here used to refer to pieces stored in separate files). The easy answer would be to:

```
 cat block1.img block2.img ... blockN.img > whole.img 
```and then to mount it by (at least in a simplified case):

```
 mount -o loop whole.img mountpoint 
```Concatenating the image block would be a costly operation for very large images. I would like to avoid that step.

Any ideas ?

thank you and best regards,
Anastasios



P.S. An explanation of why on earth i would want to do that follows:

The reason why i am asking this is because i am thinking of implementing a backup strategy involving taking an lvm snapshot of a running Ubuntu system and using storeBackup to make incremental snapshots to a network server. StoreBackup has the very useful option of cutting large files into blocks and propagating only the blocks that have changed to the backup target. The bad thing about it is that one ends up with a directory named whole.img containing the individual blocks which i do not know how to mount (say, for individual file recovery) without going through the costly operation of reconstructing the whole first.

And, yes, i could use storeBackup to simply backup the files in the lvm snapshot in the first place but i am a little twitchy about special files (say, sockets, pipes hardlinks and stuff)  and about recovering in the case of catastrophic failure (in which case simply dd-ing an image file is a better recovery strategy)

Alternative strategies are also welcome, of course :)

thanks again,
Anastasios

---

### Post by hjclaes on 2012-11-01
Hi Anastasios,

as far as I know, there is no tool to mount on top of splitted files (with the same length). :confused:

But maybe you can optimize your backup strategy. I think saving only the blocks with storeBackup is not optimal. This always takes much more space than saving files, but you're right, it's very easy to restore a whole system from a dd based backup (storeBackup calls dd).

So, what do you think about the following way to store your backup by running two different backups:

1. Run dd in storeBackup, let's say once a week and use compression (use bzcat for restore). Delete old backups after a month or so (depends on the space you want to use for this).

2. Run a "normal" file based backup from **your **important files every day. This will take a few seconds or a minute or so. Use can use the following settings to minimize space:

linkSymlinks=yes
comprRule= '&::COMPRESSION_CHECK($file)'

If you have big files with little changes in them (mail files, image files), you should use the "blocked file" feature (with compressing). That's basically the same as the stuff you want to use with dd.

Normally, these file based backups will not take much space because of compression and de-duplication, so you can keep your backups for a very long time (probably years).

-----

Conclusion:
You will get backups for restoring after a disk crash with a history of a month or so and have file based backups with very easy access with a very long history.
Naturally, it's useful if you can use a separate partition for you home directory to minimize the size of the dd-based backup.

Additionally, you should check the consistency of your backup, maybe of the source also (against bit rot) from time to time. Also, you could use the replication feature to get one (or more) continuously copy of your backup on a (maybe external) disk.

Hope this helps!?

Best Regards, Heinz-Josef Claes

(btw, I'm the author of storeBackup)

---

### Post by Anastasios Marmaras on 2012-11-05
Hello Heinz-Josef,

Thanks a lot for your response. Wow, it feels like being contacted by one of the stars, seriously! 

I agree with you, a block level backup of all files does not make much sense. And therefore mounting the divided disk image will not be necessary. I decided to separate the /home directory and do, as you suggested, a block level backup of the root device and a file level backup of /home. 

I haven't had the chance to try the replication functionality yet (my backup strategy used to involve simply running storeBackup for a second time on a secondary backup machine). Thanks for the advice, i should try this.

Thanks again for all the advice and for storeBackup, it has been contributing to my peace of mind for over three years.

best regards,
Anastasios

---

### Post by Anastasios Marmaras on 2012-11-05
I marked this thread as solved since i cannot think of another case where cutting a disk image into pieces before mounting it makes sense.

Anastasios

---

