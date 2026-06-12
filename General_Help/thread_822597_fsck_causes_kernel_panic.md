---
title: "fsck causes kernel panic"
date: 2008-06-08
forum: General Help
---

### Post by BeardedChimp on 2008-06-08
Hey, ubuntu (x64) on trying to boot, is forcing a fsck, and in turn this causes a kernel panic.
Here is the log for booting up on 'recovery mode'

Ubuntu Hardy
Kernel: both 2.6.24-17-generic and 2.6.24-16-generic 

During bootup in 'recovery mode'
fsck 1.40.8
/dev/sda3 was not cleanly unmounted, check forced.

ata3.00: exception Emask 0x1 SAct 0x0 SErr 0x100000 action 0x0
ata3.00: CPB resp_flash 0x11: , CMD error
ata3: SError: {DISPAR }
ata3.00 cmd c8/00:6c:d8:38:a3/00:00:00:00:00/e4 tag 0 dma 55296 in
ata3.00 status: { DRDY ERR }
ata3.00: error: { UNC }

HARDWARE ERROR
CPU 0: Machine Check Exception 4 Bank 4: b200000000070f0f
TSC ed4932c899
This is not a software problem!
Run through mcelog --ascii to decode and contact your hardware vendor
Kernel panic - not syncing: Machine check
Clocksource tsc unstable (delta - 4687310665 ns)

I also tried using the fedora live cd (my ubuntu one is scratched) and it gave similar results when running fsck manually.

fsck /dev/sda3
fsck 1.40.8
/dev/sda3 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
CPU 0: Machine Check Exception: 0000000000000004
CPU 0: Banks 4: 3200000000070f0f
Kernel panic - not syncing: CPU context corrupt


I can still mount sda3 (on the fedora live cd) absolutely fine, and view all files etc. So i'm a bit confused as to whether the drive is dead, or if it is saveable etc.

As a side note could someone please tell me how I can prevent ubuntu forcing the fsck. To be honest this is a serious problem in my opinion, my computer was totally unusable because there is no way for me to skip the fsck, which very almost messed up my revision for some exams. There should be a way for the user to overide the fsck if needed. Or is there a hidden option you can set in grub I don't know about?

Cheers for any help

---

### Post by andygrav on 2009-07-14
Disclaimer: I am not a hardware or filesystem expert but seeing as no one else has replied here goes ...

Could it be an "obscure" hardware problem possibly memory, cpu or disk cable.

Have you tried running memtest86 which is on several distributions install cds/dvds. cpuburnin to test the cpu or replace the disk cable.

If it isnt due to hardware problems then I would report it as a bug against fsck, if its reproducible on another machine (see below).

To recover the data that is on the drive 
dd bs=512 if=/dev/{your_partition} of=/{some_dir}/image conv=noerror,sync
no error skips if it encounters an error and sync fills the destination blocks that were bad on the source with zeros  
the partition of=... has to have enough free space to hold the whole partition, not just the used part of the partition.
Then you can check the logs to see if there were errors reading the data.
Then you could do an fsck like this
# losetup /dev/loop0 /some_dir/image
# fsck -f /dev/loop0
if theres no error you can go ahead and mount it
# mount /dev/loop0 /mnt
If you still get a kernel panic then you could send the file to another machine and try fsck again - if it still panics then its a bug with fsck or the kernel.

To get the machine to boot without fscking the disk (which I wouldnt recommend.)
tune2fs -C 0 -T now /dev/{your_partition}
to pretend that it has never been mounted and that it was last checked now.
I cant find a clean/dirty flag in the data structures
[http://jno.glas.net/data/prog_books/lin_kern_2.6/0596005652/understandlk-CHP-18-SECT-2.html](http://jno.glas.net/data/prog_books/lin_kern_2.6/0596005652/understandlk-CHP-18-SECT-2.html) 

Andy Bailey
[http://www.hazlorealidad.com]("http://www.hazlorealidad.com")

---

