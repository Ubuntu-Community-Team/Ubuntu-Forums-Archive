---
title: "I deleted everything!  Please help."
date: 2006-11-19
forum: General Help
---

### Post by andykrueger on 2006-11-19
I was trying to free some drive space by deleting a few things and somehow ended up deleting basically everything.  After doing that, I was still in the GUI but unable to run anything, even a terminal.  

By booting up in recovery mode I am able to see my current file structure, but it looks like everything is gone.  /home is empty and my personal directory is missing.  

I tried following directions in some similar posts but I have been unable to come up with anything helpful.  I want to believe it might still be possible to recover some of my files... can anyone please help me?  Obviously I'm new to all this and fairly stupid, but I'll take any advice I can get!

---

### Post by DaveBorealis on 2006-11-19
> **andykrueger said:**
> Obviously I'm new to all this and fairly stupid, but I'll take any advice I can get!

Can't help you recover your files (although maybe someone can), but I can tell you that many if not most of us have been there and done that.

I know how you feel!

Best regards,
Dave

---

### Post by Dubbayoo on 2006-11-19
There is no recycle bin in Linux. Gnome has a workalike but I doubt that saves items that are notdeleted via the Gnome UI. You can spend 2-3 trying to figure out how to get everything back or an hour or two reinstalling. 
I would reinstall w/o reformatting the /home partition, hoping you didn't do the giant / like everyone else. Personally I nfs mount /home for reasons like this.

---

### Post by andykrueger on 2006-11-20
Thanks for the responses.  I was unable to recover anything but it's comforting just to know that I'm not the only one who has made this mistake.  More importantly, I learned my lesson: from now on, I'm backing everything up!

---

### Post by xfile087 on 2006-11-20
And make sure you copy your backup to CD or an external HD! Me, being the idiot that I am backed up the other night before re-installing Ubuntu... Only I forgot to copy the backup to an external first!!!

---

### Post by firebadger on 2006-11-20
It is worth noting though, that there are data recovery specialists out there should you deem your data worth the expense.
Deleting from your hard drive is far from final (to somebody with the right equipment) unless you write over it multiple times with random data.

---

### Post by Ramses de Norre on 2006-11-20
A tip if you want a recycle bin: set this in /usr/bin/del and give it execute permissions:```
#!/bin/bash
mv -i -v $* ~/.Trash
```
Now when you use del instead of rm all files get moved to trash.

---

### Post by koenn on 2006-11-20
As I've been seeing a lot of posts about deleted files that needed recovering, I just asked google.
As said earlier in this thread : deleted files are not necessarily gone, and usually they can be recoverd. there are firms who provide this service, but it is often expensive.
Here's a list :
[http://www.google.be/search?q=data+recovery](http://www.google.be/search?q=data+recovery)

Then there's this page for the do it yourself approach
[http://www.stud.tu-ilmenau.de/~mojo/undelete.html](http://www.stud.tu-ilmenau.de/~mojo/undelete.html)
looks promissing, but I haven't tried it. Try at your own risk.

The link to the Linux Ext2fs Undeletion mini-HOWTO on that page doesn't work, but google found a copy at the Linux Documentatiopn Project: [http://tldp.org/HOWTO/Ext2fs-Undeletion.html](http://tldp.org/HOWTO/Ext2fs-Undeletion.html)

Can you still boot and get to a GUI or are you going to have to do this from the command line ? I don't know of any live CD's to run this off, but maybe you can have a look around.

---

### Post by koenn on 2006-11-20
small addendum:
If you're reading this because you've messed up or lost a partition : 
That is an completely different case than recovery of deleted files. 
If you've lost files because youve changed the partition table, you can not see the files because your operating system does not know where to look for them or how to approach them. That's what the partition table is for, and you'll have to look in to tools to fix a lost deleted partition / repair a broken partition table / ... That's a completely different recovery technique  compaired to 'undelete deleted files'.

---

