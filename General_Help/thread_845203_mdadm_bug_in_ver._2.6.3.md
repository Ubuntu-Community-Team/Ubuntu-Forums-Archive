---
title: "mdadm bug in ver. 2.6.3"
date: 2008-06-30
forum: General Help
---

### Post by randknu on 2008-06-30
I was growing my raid5 array when i needed to reboot. Mdadm should handle this. But when i'm trying to assemble again i get an error:
failed to restore critical section for reshape, sorry.

So i search for this error and it appears that 2.6.3 has a bug in it. Upgrading to 2.6.4 or 2.6.7 will fix it.

Apperantly 2.6.5 and 6 have serious bugs in them.

So how do i upgrade it?
The repository reports i have the latest version. (which is bull)

I downloaded 2.6.4 manually and tried to "make" it but i just get page up and page down with errors.

This guy has the exact same problem as i do:
[http://www.issociate.de/board/post/486857/Failed_RAID5_array_grow_after_reboot_interruption;_mdadm:_Failed_to_restore_critical_section_for_res.html](http://www.issociate.de/board/post/486857/Failed_RAID5_array_grow_after_reboot_interruption;_mdadm:_Failed_to_restore_critical_section_for_res.html)

If anyone has another way to correct this matter please feel free to reply...

I am pretty fresh in linux so...

---

### Post by randknu on 2008-07-02
Anyone?
At least tell me how to update mdadm manually... And i can take it from there.

---

### Post by randknu on 2008-07-03
Since noone wants to help me, i have fixed it myself.
I booted via ubuntu 7.10 live cd, installed mdadm and simply assembled the device.

It started rebuilding right away with no error messages at all.

Mdadm in 8.04 is old, buggy and outdated. Please update the package.

---

### Post by unlotto on 2008-07-05
I'm very glad I found this post of yours randknu. I had the same issue, and I was about to believe what mdadm was telling me.

What I did to fix it was to download the 8.10 package (v 2.6.4) from [http://packages.ubuntu.com/intrepid/mdadm]("http://packages.ubuntu.com/intrepid/mdadm") and simply make, make install. This also worked perfectly.

---

### Post by randknu on 2008-07-07
I don't know why that failed with me. All i got when i tried "make" was a pagefull of errormessages. And running "make install" afterwards awarded me with even more errormesssages.

And yes i tried with "sudo" in front, i even tried "sudo -i"
It made no apperent difference.

But the library should be updated with the new version.

---

### Post by qisback on 2008-07-07
damn I wish I found this post about 2 hours ago, I just spent all that time debugging Grow.c and editing it.

After compiling my edited version I was able to resume the reshape with 1 failed drive.

Although my method worked it would have been quicker to have updated it with a know working and "bug free" version.


The way that mdadm should be installed manually btw is.

sudo apt-get purge mdadm *[COLOR="Red"]- removes your existing mdadm[/COLOR]*

sudo apt-get install build-essentials *[COLOR="Red"]- installs all compiler and make tools[/COLOR]*

wget <your mdadm package> *[COLOR="Red"]- downloads mdadm from a url[/COLOR]*

tar zxvf <your mdadm package> *[COLOR="Red"]- extracts the package[/COLOR]*

cd <you mdadm package> *[COLOR="Red"]- changes directory to extracted package[/COLOR]*

sudo make [COLOR="Red"]*- compiles the package*[/COLOR]

sudo make install *[COLOR="Red"]- "installs" the package[/COLOR]*


so for example I would do


sudo apt-get purge mdadm
sudo apt-get install build-essentials
wget [http://freshmeat.net/redir/mdadm/29423/url_tgz/mdadm-2.6.4.tgz](http://freshmeat.net/redir/mdadm/29423/url_tgz/mdadm-2.6.4.tgz)
tar zxvf [http://freshmeat.net/redir/mdadm/29423/url_tgz/mdadm-2.6.4.tgz](http://freshmeat.net/redir/mdadm/29423/url_tgz/mdadm-2.6.4.tgz)
cd mdadm-2.6.4
sudo make -j5 *[COLOR="Red"]- -j5 just means compile using 5 cores (n + 1)[/COLOR]*
sudo make install


I hope that helps your in future.

---

### Post by randknu on 2008-07-08
I'm glad that this helped someone though it was originally me that needed help.
The pressure on this forum is very high and the post will fall back to the second page in just a few hours, and then nobody even bothers to check it out.

Anyway, thanks for the support guys, i will try to install 2.6.4 or 2.6.7 again with your tips qisback.

---

### Post by mdmbkr on 2008-08-22
I am running 8.04, a reshape was interrupted, and manually upgrading mdadm overcame the problem.  Thanks for the help.

---

### Post by acpatel on 2008-08-24
This is a really big problem actually.  Turns out that upgrading to 2.6.7-3ubuntu4 (source from intrepid) doesn't allow it to work -- I ended up with:
mdadm --assemble --force /dev/md0 /dev/sdi1 /dev/sdf1 /dev/sdg1 /dev/sdj1 /dev/sdd1 /dev/sdb /dev/sdh1 /dev/sdk1 /dev/sdc1 /dev/sde1
mdadm: superblock on /dev/sdi1 doesn't match others - assembly aborted

Downloading mdadm-2.6.4 source from Neil Brown's site (out of desperation, to be honest), gets me this:
root@Brak:/home/acpatel/Desktop/md264/mdadm-2.6.4# mdadm --version
mdadm - v2.6.4 - 19th October 2007
root@Brak:/home/acpatel/Desktop/md264/mdadm-2.6.4# mdadm --assemble --force /dev/md0 /dev/sdi1 /dev/sdf1 /dev/sdg1 /dev/sdj1 /dev/sdd1 /dev/sdb /dev/sdh1 /dev/sdk1 /dev/sdc1 /dev/sde1
mdadm: /dev/md0 has been started with 10 drives.
root@Brak:/home/acpatel/Desktop/md264/mdadm-2.6.4# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdi1[0] sde1[9] sdc1[8] sdk1[7] sdh1[6] sdb[5] sdd1[4] sdj1[3] sdg1[2] sdf1[1]
      3907070976 blocks super 0.91 level 5, 128k chunk, algorithm 2 [10/10] [UUUUUUUUUU]
      [=========>...........]  reshape = 45.5% (222478464/488383872) finish=2253.4min speed=1962K/sec
      
unused devices: <none>

But now I am fearful about moving to 8.10 when it comes out and whatever version of mdadm it has -- there are significant bugs in 2.6.5, 2.6.6, and near as I can tell 2.6.7.

Anand

---

### Post by soulstorm666 on 2008-11-22
This is f*** awesome...why do you let this bug slip into intrepid?

I just got my raid back ! By removing the current mdadm package and installing version 2.6.4. Thanks guys...!!!

If this is a known bug for so long , why on earth are you releasing it with intrepid... man... that gave me a lot to think about...

---

### Post by acpatel on 2008-12-07
Turns out that this is fixed in 2.6.8 -- at least my raid works in 2.6.8, when it would never work under 2.6.7. :guitar:

Give it a shot!

[http://www.kernel.org/pub/linux/utils/raid/mdadm/mdadm-2.6.8.tar.gz](http://www.kernel.org/pub/linux/utils/raid/mdadm/mdadm-2.6.8.tar.gz)

Anand

---

### Post by fjgaude on 2008-12-08
An array I created over two years ago works just fine in 2.6.7 as it did in 2.6.3. Never tried 2.6.4.

Will wait to see how 2.6.8 works out.

---

