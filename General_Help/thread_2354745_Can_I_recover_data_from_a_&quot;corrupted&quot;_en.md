---
title: "Can I recover data from a &quot;corrupted&quot; encrypted drive?"
date: 2017-03-05
forum: General Help
---

### Post by kaikalur on 2017-03-05
I recently overwrote my old Kubuntu SSD with new Ubuntu 16.04 ISO :( by doing dd if=<iso> of=/dev/sdb. At that time I was running linux from my HDD. In stead of /dev/sdc (the USB drive), I used /dev/sdb which overwrote my SSD. And it turns out that disk had an encrypted partition. There are few file that I want to recover from that drive. dd won't help because of the encryption. So I'm hoping someone can help me with this issue. Thanks!

---

### Post by TheFu on 2017-03-05
Welcome to the forums.

I suspect that data is only available on the backups you've already made.  Overwriting the beginning blocks of any encrypted storage is really bad. This is usually where all the encryption header and decryption keys are stored.

Whenever using encryption, having excellent backups is mandatory.

I hope you had backups.

---

### Post by kaikalur on 2017-03-05
Unfortunately no, I did not make any backup. However,  that SSD had 3 partitions - /boot, swap and /home and only /home/<my user name> was encrypted. That's why I'm hoping that writing < 2G at the beginning of the disk probably left the other part of the disk intact. And I have the password that's why I'm hoping if I can make a filesystem in the untouched part of the drive, I can probably get the data back.

---

### Post by HermanAB on 2017-03-06
In my experience, if there is one bit wrong on an encrypted disk, then you are SOL...

---

### Post by TheFu on 2017-03-06
In the original post, you said there was an encrypted partition.  If the partition is encrypted and the beginning header area was overwritten, backups are the only method.

OTOH, if it was just an encrypted HOME and there were multiple accounts, look for the how-to restore an encrypted HOME page.  If any of the encrypted areas were overwritten, that would probably be the encryption header which effectively destroys all access to the data. [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) - there are other links at the top of that page for other specific types of encrypted HOMEs.

Backups are much easier.

---

### Post by kaikalur on 2017-03-06
Sorry if it was not obvious but all the three partitions were on that SSD. When I overwrote the entire disk with Ubuntu ISO, the partition table is also gone. So I'm trying to figure out how to get the old partition table back so that I can mount /home/username and then follow the steps from your previous reply. Thanks again!

---

### Post by 0+-. on 2017-05-27
Sorry to bump this, but I have the same problem; I had Lubuntu installed with an encrypted /home (not full disk encryption) and I accidentally overwrote the first 40MB of my hard drive with dd. When I try to boot, it says:

[I]error: unknown filesystem.
Entering rescue mode...
grub rescue>
[/I]
From what I've read, it seems like I won't be able to recover my data but I want to be completely sure before I reinstall Lubuntu because I had about a years worth of work on there.

Thanks in advance.

---

### Post by oldfred on 2017-05-27
If /home not in first 40MB. Was it a separate partition?

 Encrypted /home
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase)

---

### Post by 0+-. on 2017-05-29
Hi oldfred, I'm not sure if it was a separate partition; I just followed the normal Lubuntu 16.04 installation wizard and chose the option for encrypting /home. I don't have the mount passphrase generated at install because I saved it in /home. :oops:=d> That first link you gave says I will still be able to use the ecryptfs wrapped passphrase if it's still on the hard drive.

The thing is, I think the partition table got corrupted (since it was the first 40MB of the HD that got wiped).  This happened a while ago and I think I used testdisk to try and fix it but didn't get anywhere. There's currently one 99GB partition with unknown file system and 1.1GB unallocated. Maybe I will use testdisk again and see what I can do.

---

### Post by 0+-. on 2017-06-15
I fixed it! :smile: Here's what I did, for anyone else who gets this problem:

[LIST=1]
[*]Use testdisk to find the Linux partition and rewrite the partition table. 
[*]Use ```
fsck.ext4 -p -y -b superblock -B blocksize device
``` to fix the file system and restore the missing/corrupted superblock from a backup superblock (which I found a list of, using testdisk). I used the last one. 
[*]The partition then became visible on the desktop / file manager and had a 'lost and found' folder with lots of folders with randomly numbered names; one of them was the encryped home folder. 
[*]Use ```
sudo ecryptfs-recover-private
```There was an error complaining about some unrelated file so I ran it again with the path to the encrypted folder. Thankfully the wrapped passphrase was still there so I just put my login passphrase and was able to retrieve my files and reinstall Lubuntu! :-\" 
[/LIST]

---

