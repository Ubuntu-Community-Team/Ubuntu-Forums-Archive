---
title: "shred didn't shred"
date: 2012-10-29
forum: General Help
---

### Post by Matt 6:27 on 2012-10-29
System is 64bit 12.04 Ubuntu. I recently used shred to get rid of several files, after which I ran photorec to see how the shredding fared.  To my surprise, photorec recovered quite a few of the files I presumed were shredded. More may have been recoverable, but I stopped the process midstream.   I used the following command: "shred -u -z -n15 [file name]", which I thought was overkill, but went for it anyway.  Any ideas why the files persist?

---

### Post by HermanAB on 2012-10-29
Shred is not useful on modern journaled file systems.  Encrypt your data,then when you need to delete it, hit yourself upside the head with brick to forget the password.

---

### Post by aromo on 2012-10-29
> **HermanAB said:**
> hit yourself upside the head with brick to forget the password.

LOL that's a painful way to shred a file!

---

### Post by philinux on 2012-10-29
> **Matt 6:27 said:**
> System is 64bit 12.04 Ubuntu. I recently used shred to get rid of several files, after which I ran photorec to see how the shredding fared.  To my surprise, photorec recovered quite a few of the files I presumed were shredded. More may have been recoverable, but I stopped the process midstream.   I used the following command: "shred -u -z -n15 [file name]", which I thought was overkill, but went for it anyway.  Any ideas why the files persist?

Did you reboot before trying photorec? I'd be interested to see the difference.

---

### Post by cryptotheslow on 2012-10-29
What kind of files were these? And had you previously edited or changed them?

Just thinking that several applications save the previous version of the file when you make changes. For example if you use gEdit to change an existing file called "test.txt" you will end up with both a "test.txt" and a "test.txt~" file. The latter will not be displayed by Nautilus unless you show hidden files. So maybe you shredded the current version, leaving the former behind - which is what photorec is recovering.

---

### Post by Matt 6:27 on 2012-10-30
> **HermanAB said:**
> Shred is not useful on modern journaled file systems.  Encrypt your data,then when you need to delete it, hit yourself upside the head with brick to forget the password.


Right, I understand the journaled file issue, but read somewhere on the forum that shred will work on ext3 and ext4 file systems.  Is that not the case?

With respect to encrypting my files, that works fine except, as you know, it creates a new .gpg file, but retains the original.  If shred can't chew up that original, the encryption and brick method doesn't really add anything... except a bump and a headache.

---

### Post by Matt 6:27 on 2012-10-30
> **philinux said:**
> Did you reboot before trying photorec? I'd be interested to see the difference.


Good question, but I did reboot.  I ran photorec the morning after shredding.  Thx for the thought.

---

### Post by Matt 6:27 on 2012-10-30
> **cryptotheslow said:**
> What kind of files were these? And had you previously edited or changed them?

Just thinking that several applications save the previous version of the file when you make changes. For example if you use gEdit to change an existing file called "test.txt" you will end up with both a "test.txt" and a "test.txt~" file. The latter will not be displayed by Nautilus unless you show hidden files. So maybe you shredded the current version, leaving the former behind - which is what photorec is recovering.


Thanks Crypto, good point.  File types ranged from open office docs to pics.

I wasn't targeting a specific file or type, just testing both shred and photorec.  There may come a time when I want to shred something and be comfortable it is truly unrecoverable. Based on this preliminary test, I'm not there yet.

---

### Post by Habitual on 2012-10-30
```
df -hT
``` output please.

---

### Post by Matt 6:27 on 2012-10-30
> **Habitual said:**
> ```
df -hT
``` output please.

```
matt6-27:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sde1      ext4      228G   12G  205G   6% /
udev           devtmpfs  994M  4.0K  994M   1% /dev
tmpfs          tmpfs     401M  1.2M  400M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs    1002M  728K 1002M   1% /run/shm
```

---

### Post by Matt 6:27 on 2012-11-03
> **Matt 6:27 said:**
> Right, I understand the journaled file issue, but read somewhere on the forum that shred will work on ext3 and ext4 file systems.  Is that not the case?

With respect to encrypting my files, that works fine except, as you know, it creates a new .gpg file, but retains the original.  If shred can't chew up that original, the encryption and brick method doesn't really add anything... except a bump and a headache.


The more I look at this issue, the more I view it as a genuine security matter.  Merely encrypting a file does not ensure its privacy.  As stated above, obviously at some point you have to decrypt it to use the file, and at that point, it becomes vulnerable to file recovery applications. E.g., a basic photorec scan has recovered multiple iterations of a file I routinely decrypt (if only briefly), view/modify, then re-encrypt & shred the original.  

Short of a complete degaussing, drive re-format, or high speed drill bit through the disk platters, what are people doing to ensure old files can't be recovered?

---

### Post by HermanAB on 2012-11-03
No, don't just encrypt a file - first encrypt the 'whole disk'.  If your 'whole disk' is encrypted, then you can use gpg to encrypt individual files for export to other systems, eg Dropbox, because all the temporary files stored in random places on your system are then encrypted too.

---

### Post by Matt 6:27 on 2012-11-03
> **HermanAB said:**
> No, don't just encrypt a file - first encrypt the 'whole disk'.  If your 'whole disk' is encrypted, then you can use gpg to encrypt individual files for export to other systems, eg Dropbox, because all the temporary files stored in random places on your system are then encrypted too.

Ok, so the individual files are encrypted, not just their directories?

Sounds like I'm in for a re-install, unless there's a way to encrypt the whole drive w/o reformatting/reinstalling.

As to the first part of my question: is there no way to permanently shred (for lack of a better term) files on my ext4 system?

Thanks

---

### Post by Backtrack2012 on 2013-03-12
> **Matt 6:27 said:**
> 
As to the first part of my question: is there no way to permanently shred (for lack of a better term) files on my ext4 system?


I'm finding myself in a similar situation. At installation of Ubuntu 12.10, I didn't select full disk encryption. I am also looking at a reinstall. I came across this thread while researching backups, reinstalls, and secure data deletion. Here's what I've learned so far.

Paraphrased from the Shred Manual (in terminal: man shred): Shred relies on assumption that the file system overwrites data in place. Many modern file system designs do not satisfy this assumption. This includes journaled file systems like Ext3 and Ext4. My Ubuntu 12.10 install is an Ext4 journaled file system. Shred will have limited effectiveness with these files.

What I've found out about Secure Delete (search in Ubuntu Software Center): Secure Delete is a more advanced version of the “shred” command. Instead of just overwriting your files with random data, Secure Delete uses a combination of random data, zeros, and special values developed by cryptographer Peter Gutmann to ensure files are irrecoverable. It also assigns a random value for the filename to further obscure data.

My DuckDuckGo and Google search of "does secure delete work on journaled file systems" brought up a number of articles and discussions, including here on Ubuntu Forum. This one is a good start: [http://techthrob.com/2010/10/04/do-secure-delete-tools-work-with-journaled-filesystems/](http://techthrob.com/2010/10/04/do-secure-delete-tools-work-with-journaled-filesystems/)

I see your last entry was last November. What were your solutions?

---

### Post by HermanAB on 2013-03-12
The only secure way to erase a disk is by invoking a special routine that is in the disk controller of every drive made in the last ten years or more.  The disk controller can make the head travel over the whole disk, including the space between tracks and in bad sectors.  

Ordinary software cannot do that while the disk controller is in normal operation mode.  Programs like shred can only work on the file system, on tracks and on good sectors.  Shred cannot write to the file system journal, write between tracks or write to bad sectors.  You can invoke the secure delete utility from hdparm.

Here is the whole story:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

The only other secure way to handle the erase issue is by encrypting the whole disk when you install Linux.  Then to erase the disk, you just forget the key.

One method that is better than shred and its ilk is dd (or cat).  Data Definition can write over the whole disk on all tracks, including journals, but it still cannot write between tracks or on bad sectors.  For practical purposes though, if you use dd to write /dev/urandom over the whole disk, your data is as good as gone.  Only the military may be able to recover some of it.

---

### Post by pixiq on 2013-03-12
> **HermanAB said:**
> The only secure way to erase a disk is by invoking a special routine that is in the disk controller of every drive made in the last ten years or more.  The disk controller can make the head travel over the whole disk, including the space between tracks and in bad sectors.  

Ordinary software cannot do that while the disk controller is in normal operation mode.  Programs like shred can only work on the file system, on tracks and on good sectors.  Shred cannot write to the file system journal, write between tracks or write to bad sectors.  You can invoke the secure delete utility from hdparm.

Here is the whole story:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

The only other secure way to handle the erase issue is by encrypting the whole disk when you install Linux.  Then to erase the disk, you just forget the key.

One method that is better than shred and its ilk is dd (or cat).  Data Definition can write over the whole disk on all tracks, including journals, but it still cannot write between tracks or on bad sectors.  For practical purposes though, if you use dd to write /dev/urandom over the whole disk, your data is as good as gone.  Only the military may be able to recover some of it.

I conclude that you recommend encrypting the whole disk. What about Ubuntu's encrypted home, that is offered at the installation?

Please describe how to run this SecureErase from hdparm! I guess it should be used for all of us who have not yet encrypted our disks, and want to wipe all traces.

---

### Post by zero2xiii on 2013-03-13
Hay,

Will "dd if=/dev/null" not solve the issue?

It writes null to the entire file location on the drive, thus overwriting the content on disc.

When ever I want to securely erase files I run this command on the file:
```
dd if=/dev/urandom of=/path/to/file bs=512
```

Just a thought.

Cheers

---

