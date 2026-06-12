---
title: "Help me to create free online backup tool?"
date: 2006-11-29
forum: General Help
---

### Post by sam_uk on 2006-11-29
As i have trashed my system a couple of times doing stupid things I think it would be great if there was a way for newbies to create on line backups.

I initially figured one way to do this is to use the gmailfs file system. I have documented my attempt here [http://www.mepis.org/docs/en/index.php/Free_Online_Backup_howto](http://www.mepis.org/docs/en/index.php/Free_Online_Backup_howto)

Whilst I have been researching this I have found a few automated online backup facilities for Doze and Mac and it surprises me that no linux hackers have ever created a easy to use, free automated backup service.

So this is what i would like to help create.


Spec; 

1) I would like somthing that could be installed by new users using a GUI.

2) It should use the largest free online service as it's primary backup. Currently I believe that this is [http://www.rarhost.com/](http://www.rarhost.com/)


  3) It would be great if it also backed up files to another service so data is not dependent on the fortunes of any one company. maybe somthing like [http://mihd.net/](http://mihd.net/) or maybe [http://www.streamload.com/](http://www.streamload.com/)  

So is anyone with scripting skills up for helping me?

Thanks

Sam

---

### Post by feest on 2006-11-29
well if you have a massive server you could make an uploader, i've created one before ([www.upstream.co.nr](www.upstream.co.nr)) however this one may be slow in other countrys than the netherlands because i have only one server so you guys should use something like imageschack :P

but yes there is something like gmaildrive, however this is for windows (maybe wine works) i know there are apps to make online backups (mostly commercial) but they often are made for win

---

### Post by sam_uk on 2006-11-30
> **feest said:**
> well if you have a massive server you could make an uploader, i've created one before ([www.upstream.co.nr](www.upstream.co.nr)) 

Thanks for the reply (first ever on these forums!) I was more thinking about a way to 'automatically' back up files to an existing commercial service.

I also notice that on the terms of your service you have; 

"5. Upstream cannot be used as an online (backup) storage place for files that don't need to be online." 
Which is kind of what I am hoping to achieve..




> **feest said:**
> 
i know there are apps to make online backups (mostly commercial) but they often are made for win

Yes quite, this is the thing i would like to tackle...

anyone out there willing to help???

Thanks

Sam

---

### Post by Rinzwind on 2006-11-30
Maybe I am looking at this from a too simple POV but why can't this consist of just 2 lines of code?

First you create an ISO of your home-directory with 'dd if=/home/ of=/backup.iso' (or a gzip/bzip file (whatever you like)) and secondly an FTP command where you move this file to a remote location.

---

### Post by sam_uk on 2006-11-30
> **Rinzwind said:**
> Maybe I am looking at this from a too simple POV but why can't this consist of just 2 lines of code?

First you create an ISO of your home-directory with 'dd if=/home/ of=/backup.iso' (or a gzip/bzip file (whatever you like)) and secondly an FTP command where you move this file to a remote location.

I dont know of any decent sized free ftp servers, maybe there are some- i will go and google.. I would also want to encrypt my data before uploading it to an untrusted third party..

<edit>

[http://www.thefreesite.com/Free_Web_Space/](http://www.thefreesite.com/Free_Web_Space/) I found this but all the free ftp- able space is very small as compared to the services i list in my initial post..

I still think there is a way to go..

Thanks

Sam

---

