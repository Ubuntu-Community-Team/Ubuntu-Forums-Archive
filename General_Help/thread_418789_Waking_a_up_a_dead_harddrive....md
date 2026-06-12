---
title: "Waking a up a dead harddrive..."
date: 2007-04-22
forum: General Help
---

### Post by HumanAnarchist on 2007-04-22
ok, so I read some where on the great internets that you could wake a dead hard drive up by putting it in the freezer for some hours, and it did actualy work. It did start to spin again :)

I could also mount the drive to access some of the files, but not all. Out of 160GB I could access about 50GB, by mounting the drive. 

So I used 

```

dd if=/dev/sda of=hda.img

```

to dump the whole hard drive to another disk. That image file is 150GB in size. 

My question is now, how can I scan that file for all pictures files? 

-ha-

---

### Post by spin2cool on 2007-04-22
IIRC, you just mount it (correct me if I'm wrong0:

# sudo mkdir /media/recoveredData
# sudo mount /home/asdf/image.img /media/recoveredData

---

### Post by HumanAnarchist on 2007-04-22
it's not just a partition, **sda1**, but the whole drive **sda**

Don't know how to mount that :(

-ha-

---

### Post by dcstar on 2007-04-22
> **HumanAnarchist said:**
> ok, so I read some where on the great internets that you could wake a dead hard drive up by putting it in the freezer for some hours, and it did actualy work. It did start to spin again :)

I could also mount the drive to access some of the files, but not all. Out of 160GB I could access about 50GB, by mounting the drive. 

So I used 

```

dd if=/dev/sda of=hda.img

```

to dump the whole hard drive to another disk. That image file is 150GB in size. 

My question is now, how can I scan that file for all pictures files? 

-ha-

You have to do the reverse onto another hard drive (which will wipe that drive):

```

dd of=/dev/sda if=hda.img

```

Then that hard drive will have the image of the original drive you did the "dd" on, and you should be able to access the data.

You may also be able to mount the dd image using the "loop" option that is used to mount CD-ROMs for direct file access, but I'm not 100% sure on this.

---

