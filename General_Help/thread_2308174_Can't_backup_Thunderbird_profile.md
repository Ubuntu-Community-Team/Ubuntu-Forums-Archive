---
title: "Can't backup Thunderbird profile"
date: 2015-12-31
forum: General Help
---

### Post by PDA1 on 2015-12-31
I can't backup my Thunderbird folder and profile.

I do the usual right-click "copy" on the entire .thunderbird folder.  Move to another folder and try to "paste into the folder".

Here's the error message- Error while copy

The folder "Cache.Trash99983627" cannot be handled because you do not have permissions to read it.

The folder Cache.Trash99983627 is one of the folders part of my Thunderbird profile and has a lock on it.

However, when copying and pasting while in root all works well. Everything copies perfectly.

I've modified the permissions to give read-write access to my user name but the apparently when I'm not in root the copied folder can't even be viewed.

Any ideas how to fix this?

---

### Post by kurt18947 on 2015-12-31
I've not had much luck copy/pasting Thunderbird profiles either. I installed ImportExportTools from addons. I've only used it a couple times but it seems to work as expected. I could choose either profiles or just messages and save to an external storage device.  Once installed - you need to do a restart - it should be on the bottom of the 'tools' menu.

---

### Post by PDA1 on 2015-12-31
> **kurt18947 said:**
> I've not had much luck copy/pasting Thunderbird profiles either. I installed ImportExportTools from addons. I've only used it a couple times but it seems to work as expected. I could choose either profiles or just messages and save to an external storage device.  Once installed - you need to do a restart - it should be on the bottom of the 'tools' menu.

Kurt, I had previously installed ImportExportTools and found it a nuisance.  Glad it worked for you.  I don't want to spend my life learning how to just save/backup my email system so that it'll restore with no troubles.

I'm going to try root again and change the permissions of only the offending folder and see what happens.

'Will reply with the results.

Thanks for the ideas.

---

### Post by PDA1 on 2015-12-31
The problem, for me, is that the permissions set to Thunderbird's folder "Cache....." are for root only.

Ubuntu, somewhere on the web I read, said you shouldn't fool around with using Thunderbird in root ro something similar to that.

Odd, back when using 10.04 I had no troubles backing up my profile.  Cut and paste and that was all that was necessary.

Though I love firefox and Thunderbird it amazes the simple me that Mozilla hasn't come up with an easy way to back up Thunderbird.

Crazy.  This is 2016...(in England) and we still have problems like this?!

---

### Post by Bucky Ball on 2015-12-31
Silly question, but you haven't got Thunderbird open while you are trying to copy that folder? If so, that will lock some files I'd think.

I've never had an issue with your issue when backing up Thunderbird. Changing permission on system/hidden files and folders is probably not a good idea unless you are _absolutely_ sure of the consequences. It may lead to loss of data or security vulnerabilities.

If it copies ok with launching the file manager with 'gksudo nautilus', or whatever you are using, why not stick with that (gksudo when launching graphical apps, not sudo)? gksudo gives you the necessary permissions to perform a copy/paste without changing the permissions of the files/folders permanently, which may not be a good thing to do. There may be good reason a non-root user doesn't have permission to alter that file/folder. If you alter the permission permanently, everyone will have read/write access, depending how you go about it.

---

### Post by PDA1 on 2015-12-31
Bucky,  Thou art an genius!

Yes, TB was closed when I tried the copy.

gksudo worked perfectly allowing me to copy everything.

Thanks.

---

### Post by leunam12 on 2016-01-01
Use rsync
```
rsync -av --delete ~/.thunderbird/ /destination/path/.thunderbird
```

---

### Post by PDA1 on 2016-01-01
> **leunam12 said:**
> Use rsync
```
rsync -av --delete ~/.thunderbird/ /destination/path/.thunderbird
```


I use grsync but hadn't considered it.   I just tried gksudo grsync and it worked perfectly.

The option --delete (deletes) "delete extraneous files from destination dirs" but I'm not sure what that means?

Can you explain it?

Thanks.

---

### Post by leunam12 on 2016-01-02
It means that if a file is deleted in the source directory it will be deleted in the destination, it will give you a more exact copy of the original folder if you backup frequently because not-needed files that no longer exist in the source directory are not kept in the destination. If this is only a one-time copy then --delete is not necessary.

---

