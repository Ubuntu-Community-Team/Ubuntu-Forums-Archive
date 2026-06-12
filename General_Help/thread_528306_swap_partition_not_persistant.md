---
title: "swap partition not persistant"
date: 2007-08-17
forum: General Help
---

### Post by Nathan_M on 2007-08-17
I've been using a swap file, but I decided I want to use a partition instead, because swap files don't support hibernation. So I created a partition, 2 GB in size using GParted with the filesystem linux-swap. Then I did this:

```
$ free
             total       used       free     shared    buffers     cached
Mem:       1026460     902560     123900          0      87988     455236
-/+ buffers/cache:     359336     667124
Swap:            0          0          0
$ sudo mkswap /dev/sda4
Setting up swapspace version 1, size = 2146791 kB
no label, UUID=dcff966f-84f0-41ea-a29a-34dc7e5c6a20
$ sudo swapon /dev/sda4
$ free
             total       used       free     shared    buffers     cached
Mem:       1026460     903632     122828          0      88028     455472
-/+ buffers/cache:     360132     666328
Swap:      2096472          0    2096472
```

All seems good, right? I run a few applications, open a few large files, run [FONT="Courier New"]$ free[/FONT] again, and the swap space is used. I go to hibernate, and the system hibernates as it should. Then when I start up, it starts up as if I had shut down normally, and [FONT="Courier New"]$ free[/FONT] shows no swap space. If I run the above commands again, after any restart ubuntu completely forgets about it. How can I make my swap partition persistant?

---

### Post by lloyd_b on 2007-08-17
You need to add a line to the file "/etc/fstab":
```
/dev/sda4  none   swap   sw   0   0
```

With this line in fstab, when the system starts up, it will automatically enable this swap space.

Note: You'll need a "sudo" in order to edit that file.

Lloyd B.

---

### Post by Nathan_M on 2007-08-17
Ok, thanks. Swap is persistent now, but hibernate still doesn't work. The system hibernates as it should, but starts up as if I hadn't selected hibernate. Can anyone help?

---

### Post by louieb on 2007-08-17
Don't know if this is related. But found the UUID of my swap partition had changed and swap wasn't being used. To get hibernate to work again had to put correct UUID in 2 places.
/etc/fstab
/etc/initramfs-tools/conf.d

Then had to run      
     ```
sudo dpkg-reconfigure  initramfs-tools 
```

---

