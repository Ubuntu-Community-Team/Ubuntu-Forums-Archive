---
title: "Shared drive over Samba, error transferring large files"
date: 2019-03-06
forum: General Help
---

### Post by zachary3352 on 2019-03-06
Hi! This is my first post, so I'm not sure if this is the right place to put it, but it seemed like the best fit. I have a fair amount of experience with Ubuntu, but I always love to learn more.

I'm setting up a "NAS," a term I'm using lightly here, which is basically just an old computer running Ubuntu Desktop for a Samba share over 1gbit ethernet of a single 10tb drive shucked from a WD Easystore formatted in exfat. I got exfat-utils and exfat-fuse to use the drive with Ubuntu, since seemed like the best format for the drive given my usage with Windows but hosting the drive on Ubuntu.
[SIZE=2]
I got everything set up, and it works well, with transfer speeds around 120mb/s as expected. However, whenever I try to copy a file over ~10GB to the server from Windows connected over ethernet, the transfer gets stuck on "Calculating..." then after about fifteen seconds says there was a network error (0x8007003B). Small files still work fine.

Here's what I've done to try to fix this issue:
- Turning off antivirus (commonly suggested solution in forum posts for fixing error 0x8007003B).
- Disabling file previews in Windows Explorer so I only see file type icons.
- Turning off Windows Firewall.
- Rebooting the machine (and the computer I have mapped to the network share).

I have NOT tried:
- Taking out my 1gbit network card (bought separately since it's an old computer) and trying the internal 100mbit connection.
- Plugging the host PC directly into the server over ethernet.
- Trying to transfer a ~10GB file from a non-Windows device.
- I had trouble figuring out how to change my Samba protocol so I haven't done it successfully.

The only other thing I feel is worth mentioning in this post is my router setup. I have a Verizon Fios Quantum Gateway as my primary since I use the Fios TV service. I plug an Asus router into it over ethernet, and my Windows client PC is plugged into the Asus. The server is plugged directly into the Fios router. I've never had any issues with this setup and transferring between devices plugged into the Asus and devices plugged into the Quantum Gateway, but I suppose it could be an issue spot.

I would really appreciate some help figuring this out. Thanks!

Zachary[/SIZE]

---

### Post by HermanAB on 2019-03-06
Are you sure it is exFAT and not FAT32?

FAT32 has a 4GB file size limit.

---

### Post by zachary3352 on 2019-03-06
Thanks for your response. I just checked, and it is exfat (the 9.1tb drive is the share). I've attached a picture (server name and username redacted intentionally). Might you have another idea?

One other thing to note, the share shows up as NTFS on windows, which is weird.

[IMG]https://photos.app.goo.gl/jUqPfvTufdkCDhzq5[/IMG][IMG]https://lh3.googleusercontent.com/BW80-Y6sem0n3cRFfziGa3rluKNV7_NNbuXMzSRjN4yZA3Ihv5aN_hEnoKnzlCvEvJVszi9AGxmm0URIUmvfR9RrX82SpoYBOYD-GaHRRWvmmD1ATYypp3dOFXBnHK9NVhrKnxl6vXmHKNWoLN3KEC6NpNJY8Kw1_kdZi2bJfg7jtnvviVBT4cgFcwQfsObEwFbCWrosyAdYBb-ZVcYqv7nA6VpR0sq2zBLYDeafjRzmNqhgzq-dVbAXxHIaaeF9zscHm71gUsDQaUhbUtqxSnVVbLSwKrzU8gT8SNWUBAJkuTQDYp28_KYwIxhc6daB8jE9UO3onzzsioZiPLe5asfx-f_acR59gjMh1d1Wk3n2w4d9YEEbf354bOD5O4PJtA-uVSEOV3LpzGkOdVCXhgcBKbejwOHXHdzktKqKlvavdG3L2R66ao9EeTv4H531tja60qlJLd1oi027zThgrvnmJDj_NdWhKDZoDPfq1-FJivPMVMt2maOYIzAjq-oq4N9uPRqdLX14_TFXMU5YoxKCU-Af7NyQ_que8Q4qSwTTqLZO_c05VXU4EtJ-AEp14hoIJeP0kO9iFDc8DgGum7uVBpp2Ea32rWVN_0JOjqwDcEL8PuEMVo9j92BPKqNFF57cZVK_I10JQQE-q4B38dMnX644tJB1CSrxZuLqPUiGNZYQpDsRA6kgVII3MNj8OGyBy3EAFsz0PMC7BkLt6E5CPg=w710-h379-no[/IMG]

---

### Post by HermanAB on 2019-03-06
Anyhoo, whatever the reason for the file size limitation, using NTFS is much better, since it is a B-Tree which is fast and doesn't get fragmented. NTFS is journaled and Windows has the necessary tools to rewind problems using the journal.  So provided that you have access to a Windows system, a corrupted NTFS volume can be fixed quickly and efficiently.

An exFAT volume is not journaled and will eventually get fragmented and corrupted and I cannot even imagine what it will be like to deal with a 10 TB fragmented and buggered disk.

---

### Post by zachary3352 on 2019-03-08
That all makes sense. If I were to switch to NTFS, is there a way I could still host it on Ubuntu/how good is ntfs-3g? If I go ahead with this plan, I'll see if it fixes my file size issue, since it very well might.

Here's my ultimate plan -- I'd like to have two of this setup, with one sitting offsite. Every couple days the onsite drive would be mirrored to the offsite one to prevent data loss in a fire/flood/whatever. Does this make sense?

I really appreciate your help!

---

### Post by Impavidus on 2019-03-09
I'm not too familiar with this stuff, but it's my understanding that Windows doesn't care and doesn't even know what filesystem is used by the server. Windows only has to know it can communicate with the server using samba. Windows can pretend it's NTFS because it has the features of NTFS, as these are provided by the server, but as Windows doesn't have any low-level access to the storage device it could actually use any filesystem supported by the OS running on the server – which means that a native Linux filesystem is probably best.

---

### Post by HermanAB on 2019-03-09
Yes, if the disk is hosted on Linux and there is no dual booting going on and the disk will never be plugged into Windows, then a native Linux FS is preferred and will give the best performance.

For a Terabyte disk, I would recommend using btrfs, since it has journalling and built in deduplication features, so it will be much more efficient.

Note that journalling is not the be all and end all: The OpenBSD FFS does things the right way to begin with, so that journalling is not needed, while ZFS is transactional and has a small event log which it normally doesn't read, but could refer to after a total screw up.

---

### Post by nicholasarussell on 2019-03-10
ex4 has a huge file limit size (limit the maximum size of file in ext4 filesystem. Ext4 has a maximum filesystem size of 1EB and maximum filesize of 16TB.)  just install the ext2fsd

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

Its great and transfering between the 2 OS's would be way easy.

---

### Post by zachary3352 on 2019-03-10
Thanks all for your help, especially HermanAB. I really appreciate it.

Based on your advice, I reformatted the drive as ext4, made a new folder within the drive, and shared that so the lost+found folder doesn't appear in the share. I can now copy files >10GB with ease, transferring at a smooth 112mbps (except the occasional few mbps dip I don't really care about) as expected of my 1gbps card, so I'm really excited about that.

[IMG]https://lh3.googleusercontent.com/tG4OGdSEQC6g1Ib11FCi9ORhkHfuwMtGPxyhfEKHtUMS5d-fSLs4dAsdV17HvIFapCjNKw2_qf4NWa8ROHkOG3XVPjFzG-J3CHqI8_Hypey6O4EOAtNhPnhiv2gxainsDmFGUPg2BrHX7Li9ouJQuk6BEYkCD4ExodK0XXoaZmbMp30lPA1mcTMO8CSDn_1sFaPpTsmNuh-rOJmjMlX_aGEVXHHRvrk0G8CLlmjHOnlXZWBa6HQBUjwsdWAdzkcYxaT7xUbpLoMvkKPLA-anqHiQdODAg81eg5sg7W01bdrBcHumJJfT683ZtaO2-AWA8lAtN0vdnRPcTfHHLIsroi0Fgs9djOr9B_8rVPna2vUClGS7yED0qVIdMxLHXH_9nD0F-QIK3CVc0dKksUQBpV5C7190DTnJWOUZ-256HZ35bGjAsNavIZu4CFzoeTeE0dCBCLjLFa1m6XADJEon8ltG9wV-VxT_QO_EmDcvnN6N65PxYSJ8ksD-TJQYtWW82DltIRssNPwzWb-rbsnKdQA8LsGOTA_T8lSJacURU9DSXUpYzQcZUcqURYYXEc692X6RlgwIhkaFxt6JciC_zV7xmY_TIwfErRP5VmFf6wpL-WV7zSecmS18NTN7_KkbYzutwJOMAt4p1VpCBtQThndv0od8xWxNwoLFfzBu1ge9KU6kpTtF_9ZqrY0dwqaCdX4IG0rbgupJhX1pTPju3FOnmA=w461-h299-no[/IMG]

However, one other question before I close this thread. When I open the properties of the share on a Windows computer, I see that 465GB are used even though there is nothing stored on the server. Is it normal for ext4 to use this much space? The drive is 10TB.

[IMG]https://lh3.googleusercontent.com/PAQPFriPwSbOcor5fuqzRfsCFNZtLfjr_MY_p33MT-v36XcBji9NWkaF4--KppmWo5CRJdoB_zZThWRIho30RPiZvDRYKLO5lYTF_85Nad4-4dsa7GWKLouyaBTLpToH_flnhVTWUqiA8n2wUsmbsjPYvXQQEKQ2XaTLQ74-uuXXblP5AV7MiTJmlEMsvMnfGjrsmj6k-nFJX0gQQJHPi5Zr-yuL0jBJiSUVPKGHpki7l3vbo-6_ectyT7xNA2M5zf4EFSucfu0kmTXvJ8GJot5KMI7UdCIBlYGG6Z08ByMUBSO6eGLugGQAFw-Cw9MPoCJtOEAOSrWS2bm9O_Muus0Jpdj7urv4J7_bdO_N6IlzR0g2IzO46lX-qBlcuGWuWkgy4_FIcOx3ZUSStzVaY5ptdUgJRV1SuiHBv_KLi1wtTLoHY_sseKqiv8msbW7VG1FwRDrUkse_LvsVWj1_pN2zgKJjH0znHCHVH1zrdrOHWMFz8C5aAovf6nHlMrv-r_J203-IKvLnyAWYcMxU4pgIfsTaqpDJw4B9UysTej6uQ5ScMptHIOiI9bpazk__TWExEhaI5Sg_tHX3zG9Jt5kdOe8JmE20RSurHWOJRf7-5JMd3NlEx0Q4F-ykDBfzCT9svFcxEHY-8nqGQokFKHGEQ0x_vx8Ka1G2LV8OYKTY1VovWEQ59GSTc6AfqRMnPnLsbAilyZxSUErGiED07C4BHw=w366-h475-no[/IMG]

Again, thanks everyone for your help. I couldn't do this without you!

---

### Post by Impavidus on 2019-03-11
On an ext4 filesystem, some percentage of the space is reserved for privileged users (root) and not available to ordinary processes. This keeps some space free, preventing fragmentation, and allows important system users to continue functioning and fix the system when ordinary processes no longer function. By default, the percentage of reserved space is 5, which amounts to 500GB, which is 465.7GiB, which is incorrectly reported by Windows as 465GB.

You can change this percentage, if you wish:```
sudo tune2fs -m [percentage] [device]

# For example, to set the reserved space on sdb1 to 2%:
sudo tune2fs -m 2 /dev/sdb1
```
With the option -r you can set the exact number of reserved blocks. See the manual page for tune2fs.

Keep in mind that although 500GB sounds like a lot, it's still only 5% of the drive. If you collect enough files to fill it to 95%, the extra 5% are unlikely to make a difference and using that final 5% will cause fragmentation and slow things down.

---

### Post by zachary3352 on 2019-03-11
Thanks Impavidus for that answer. I've got the server running exactly how I want now, so thanks to everyone as well for that. I'm excited to actually start storing files now!

---

