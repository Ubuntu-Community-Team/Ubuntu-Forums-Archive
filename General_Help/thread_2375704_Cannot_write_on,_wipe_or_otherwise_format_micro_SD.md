---
title: "Cannot write on, wipe or otherwise format micro SD card"
date: 2017-10-26
forum: General Help
---

### Post by jeanloup on 2017-10-26
I'm going to try and keep this quick.

I have been trying to format the Micro SD I used in my dashcam. It was getting full and I decided to clear all the videos on it, none of which needed to be kept. However just to be safe I decided to try to back up all files. something must have gone awry with the card reader I used at the time because I now can't seem to do much on the card itself.

I can't format the card in the dashcam itself and plugging it in gives me a "memory error" message.

I can read the videos on it ok still but I can't delete folders and files seem locked up.

I tried a ```
sudo mount -o remount,rw /media/jean-loup/9016-4EF8/
``` to fix the read-only errors I was getting trying to do an rm-fr as root and while it appears to work (a subsequent rm -fr after the remount shows files and folders disappearing in Nautilus) checking again on it later shows no difference, even though an ls command after the rm shows an empty folder.

I tried formatting with the built-in function in Nautilus but it gives me a timeout error. Following that I followed suggestions to try to format it with GParted and that just does nothing. It seems to go through the steps without error message but whether I format the card as fat32 or ntfs it just ends up returning to its initial state of apparent lock down

And yet videos on it can be played, there's nothing visibly corrupted.

I also tried doing a fsck with no success. I tried multiple times and the errors sometimes vary but attempting corrections does nothing at all. I tried after remounting, I tried while mounted and while unmounted and it has no effect at all.

I'm at a loss what to do. Here's a quick copy of the last fsck I ran if that lights anyone's lantern:
```

jean-loup@Lapland:~$ sudo fsck /dev/sdi1
fsck from util-linux 2.27.1
fsck.fat 3.0.28 (2015-05-16)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
/DCIM/13750526/17500024.MOV
  File size is 295681771 bytes, cluster chain length is > 295698432 bytes.
  Truncating file to 295681771 bytes.
/DCIM/17650708/18040017.MOV
  File size is 295747307 bytes, cluster chain length is > 295763968 bytes.
  Truncating file to 295747307 bytes.
/DCIM/27351105/19270033.MOV
  File size is 290700243 bytes, cluster chain length is > 290717696 bytes.
  Truncating file to 290700243 bytes.
/DCIM/27351105/19270033.MOV  and
/DCIM/23450918/17390020.MOV
  share clusters.
1) Truncate first to 271581184 bytes
2) Truncate second to 284327936 bytes
? 2
/DCIM/23450918/17390020.MOV
  File size is 295583467 bytes, cluster chain length is 271581184 bytes.
  Truncating file to 271581184 bytes.
/DCIM/37900112/04350009.MOV
  File size is 233182635 bytes, cluster chain length is > 233209856 bytes.
  Truncating file to 233182635 bytes.
/DCIM/41400217/23590024.MOV
  Contains a free cluster (952217). Assuming EOF.
/DCIM/41400217/23590024.MOV
  File size is 295878379 bytes, cluster chain length is 273514496 bytes.
  Truncating file to 273514496 bytes.
/DCIM/13750526/17500024.MOV  and
/DCIM/50100525/04590008.MOV
  share clusters.
1) Truncate first to 154206208 bytes
2) Truncate second to 232751104 bytes
? 2
/DCIM/50100525/04590008.MOV
  File size is 230594755 bytes, cluster chain length is 154206208 bytes.
  Truncating file to 154206208 bytes.
/DCIM/17650708/18040017.MOV  and
/DCIM/51200605/04290001.MOV
  share clusters.
1) Truncate first to 236290048 bytes
2) Truncate second to 295632896 bytes
? 2
/DCIM/51200605/04290001.MOV
  File size is 295485163 bytes, cluster chain length is 236290048 bytes.
  Truncating file to 236290048 bytes.
/DCIM/86171008/11160002.MOV
  Contains a free cluster (373027). Assuming EOF.
/DCIM/86171008/11160002.MOV
  File size is 222401435 bytes, cluster chain length is 151322624 bytes.
  Truncating file to 151322624 bytes.
/DCIM/23450918/17390020.MOV  and
/DCIM/85971005/18470001.MOV
  share clusters.
1) Truncate first to 57245696 bytes
2) Truncate second to 96272384 bytes
? 2
/DCIM/85971005/18470001.MOV
  File size is 295517931 bytes, cluster chain length is 57245696 bytes.
  Truncating file to 57245696 bytes.
Reclaimed 29430 unused clusters (964362240 bytes).
Free cluster summary wrong (8998 vs. really 41328)
1) Correct
2) Don't correct
? 1
Perform changes ? (y/n) y
/dev/sdi1: 250 files, 938736/980064 clusters

```

I'm on Ubuntu 16.04 not that I think it matters much...

---

### Post by SeijiSensei on 2017-10-26
Try formatting it as FAT32 or NTFS.  Any better?

```
sudo mkfs -t ntfs /dev/sdi1
```

or

```
sudo mkfs -t vfat /dev/sdi1
```

---

### Post by jeanloup on 2017-10-27
I tried ntfs as well (with gparted) and when it refreshed the device I was back where I started again. 

The irritating thing is that it seems like it's doing what you're asking it to do because no error message appears but then it refreshes and I'm back to the original fat32 with the same amount of data used.

I'll try formatting with mkfs tonight instead of gparted but I don't have great confidence this will make much difference. Thanks for suggesting it though

---

### Post by sudodus on 2017-10-27
It is possible that the micro SD card is failing. But there might be other problems too, that disturb the communication between the computer and the card. You can get useful tips from the following link,

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

Let us hope that there is 'only' confusion :-)

---

### Post by jeanloup on 2017-10-27
Yes my next stage is to see if I get better luck on Windows 10 and I might try using an adapter though I'm not sure why that would work better than plugging the MicroSD directly in the card reader.

But thank you for the link it gave me a few other options to try. Hopefully I can finally get it formatted and usable again

---

### Post by sudodus on 2017-10-27
Good luck :-)

---

