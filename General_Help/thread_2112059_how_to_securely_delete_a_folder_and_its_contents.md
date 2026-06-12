---
title: "how to securely delete a folder and its contents"
date: 2013-02-03
forum: General Help
---

### Post by GMachine_24 on 2013-02-03
Hello. Go 49ers!

I want to overwrite a folder and its contents many times. Overwriting files in Ubuntu is easy - I can use 'shred' or 'srm'. [I have secure-delete and shred installed.] I can go into a folder and, using the *, easily overwrite all the files/contents in that folder.

But what if I want to overwrite a folder and its contents, including files, sub-folders and their files, etc. and, in the end, overwrite the top folder's information so there is no record of it - or as little as possible?

As I said earlier, it seems the overwriting programs and tools are only good on single files - and I have many folders and sub-folders to overwrite along with their contents. Even the top folder in question is a sub-folder of another folder/directory - in this case "Downloads" - but I don't want to erase/overwrite or delete "Downloads".

I have been looking for how to do this for quite some time. I've been using Ubuntu for more than a decade and I still cannot figure it out.

Thanks.

---

### Post by omeomi on 2013-02-05
You can just use srm for that like this:
```
srm -r ~/Downloads/Folder
```
where Folder is the folder you want to delete. The -r option will recurse into all the subfolders as well.

---

### Post by 3rdalbum on 2013-02-05
> **GMachine_24 said:**
> I have been looking for how to do this for quite some time. I've been using Ubuntu for more than a decade and I still cannot figure it out.

Think laterally; if you've wanted to securely delete files and folders for years*, then you may be interested in having an encrypted /home.

When you delete data that is on an encrypted /home partition, the deleted data is still encrypted and unable to be decoded without your decryption password. Same as your non-deleted data.

Next time you install Ubuntu, encrypting your home partition or whole disk may be a really good idea. Then you can just delete things normally and pretty well not worry that they'll be retrievable. And if you forget to delete something... it still won't be retrievable without your password.

*You can't have used Ubuntu for a decade; the first version was released in October 2004. I know what you mean though.

---

### Post by Calinou on 2013-02-05
Encryption slows down stuff a lot though.

---

### Post by GMachine_24 on 2013-02-05
):P

Hi: thank you for your replies.

omeomi - you know, I looked into that folder delete using srm with a -r and I thought I read that some files inside the top folder would not be removed and overwritten. I will check again. Thanks.

3rdalbum - Thank you for your reply. Yes, many of my *nix installs have a TrueCrypt partition. But here's the thing and maybe my lack of understanding of how this works is the problem here - but I have moved a file from a TrueCrypt partition to "trash" and it is not encrypted when it gets to trash. Or, perhaps, I'm not doing that correctly and I need to close the encrypted partition and stop running TrueCrypt before that moved file will appear encrypted. Meanwhile - it's funny, I figured someone might bust me on the 10-year reference. Ha. Should have been more careful. But I have been running some version(s) of Linux for more than a decade - my first foray was in 1995 with an Open Suse install - I was a computer neophyte and it did not go far. I believe Fedora was my first successful Linux install and that was pretty great, really. Still have a fond place in my heart for Fedora and have a USB flash drive with the latest live Fedora beta version on that. It's all good - and I HATE that phrase.

Calinoua; re: "Encryption slows down stuff a lot though." I have only used TrueCrypt to create/encrypt a standalone partition on an Ubuntu install. I really can't tell the difference using that partition or an unencrypted partition - but I've never encrypted an entire install.

Thanks again for your replies.

---

### Post by sudodus on 2013-02-05
> **3rdalbum said:**
> ...
When you delete data that is on an encrypted /home partition, the deleted data is still encrypted and unable to be decoded without your decryption password. Same as your non-deleted data.

Next time you install Ubuntu, encrypting your home partition or whole disk may be a really good idea...

Use encrypted home; your trashcan will be encrypted too ;-)

But don't forget your password/passphrase!

---

### Post by zero2xiii on 2013-02-05
Hay,

Hate to point out the obvious, but will dd not work? if the other.. Methods.. Fail?

such as:
```
dd if=/dev/random of=/some/folder/here bs=512
```
[COLOR="Silver"][STRIKE]This should write random data to the folder location on the harddrive? Might fill up the drive though. Not sure, have never used it on a folder before.[STRIKE][/COLOR]
Oh nevermind, I now remember that dd does not work on folders, only files. Sorry hehe :$.

Also +1 for the encrypted /home and +1 for the slow down unless on a very stream line system.

Might I recommend using a flash (or partition) for sensitive data, encrypting only that? Will make it a lot easier, and wont slow down the entire system "for just one folder"

Cherz and good luck

---

### Post by sudodus on 2013-02-05
> **zero2xiii said:**
> Hay,

Hate to point out the obvious, but will dd not work? if the other.. Methods.. Fail?

such as:
```
dd if=/dev/random of=/some/folder/here bs=512
```This should write random data to the folder location on the harddrive? Might fill up the drive though. Not sure, have never used it on a folder before.

Also +1 for the encrypted /home and +1 for the slow down unless on a very stream line system.

Might I recommend using a flash (or partition) for sensitive data, encrypting only that? Will make it a lot easier, and wont slow down the entire system "for just one folder"

Cherz and good luck

You can use dd to make zeros (or random bytes) of the free space (making a huge file until the disk is full, and then remove the file). It is slow but possible. But with modern file systems with journaling, and with modern drives with extra hidden areas, data can still remain. But if the data have only been written after encryption (as with encrypted home), you won't have to worry about what is stored on the physical media.

If you are really paranoid, you need also encrypted swap (which comes with encrypted home in Ubuntu) and encrypted /tmp, which you have to fix yourself, or put /tmp in ramdrive.

---

### Post by Paqman on 2013-02-05
> **GMachine_24 said:**
> 
I want to overwrite a folder and its contents many times. 

Multiple overwrites won't increase security, it'll just waste time. A single pass with random data (or even just zeros) will prevent any software tool from recovering your data.

---

