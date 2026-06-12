---
title: "backup with bacula"
date: 2008-04-10
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-04-10
Hi all,
I'm new and this is my first post, so I hope I'm somewhat in the right category with this.

I have Bacula running on a Debian server and the backup seems to run OK. I'm backing up Linux (Kubuntu) and Mac OSX machines. Also I have Webmin on the server. I'm not afraid of a terminal but I simply prefer a GUI if possible.
So, here is my challenge: I tried to restore a backup but I was not able to select the files I want to restore. I backed up  5 computers with about 2TB of data and I can see the file on the server. But in Webmin I am not able to select a backup.

I know it's hard to help from far away but it would be great if someone who knows about Bacula would be able to point me to the right direction or tell me what sort of info I need to provide to help identifying the problem.

Thanks for any help,
Steve

---

### Post by Linux&amp;Gsus on 2008-04-10
Is there no one who has an idea?
:cry:

---

### Post by spmccann on 2008-04-12
I'm looking at bacula as a solution for myself. Whilst looking through the doc i believe that you need specify which machines and accounts have restore permissions.  I think the default apart from the "admin" machine is that each machine can only see its own set of backups. Its a valid security precaution.

 The guys in the bacula forum are quite good, it might be more effectivrto post the query there if you haven't already. Hope this helps.

Sean

---

### Post by Linux&amp;Gsus on 2008-04-14
Thanks for your reply.
The security precaution sounds good to me. But when I'm logged in as root via webmin then I believe I should see all backup files. Unless I'm missing something. Not that I'm an expert or anything, I just thought that I should be able to see it all.

I guess I have some more work to do to make it happen. What good is a backup for if you can't use access it...  :lolflag:

Maybe I should configure it all over again. Chances are that I made a mistake along the way.


Cheers,
Steve

---

### Post by hauge on 2008-04-14
There are no default that restricts the visibility of backups...

I just tried the webmin-bacula interface and it seems to be of little use when it comes to restoring. The interface is not capable of browsing the backup database.

My preference is to use the **bat **graphical interface for doing restores (and handling all interactive stuff). I must admit that it can be a challenge to get it up and running but worthwhile the effort. Bat is an excellent tool that also handles restores very well. The current SourceForge version of bacula is 2.2.8 while Ubuntu is 1.38.11.

Regards
Jan

---

### Post by Linux&amp;Gsus on 2008-04-15
Is BAT the same as bacula-tray-monitor? I have that installed on my Laptop but I have no clue how to start it. The only message I get is: "Gtk-WARNING **: cannot open display:"
That just doesn't tell me anything that would make sense.

The version also confuses me. In Webmin it tells me that I have Bacula 2.2.8 but when in a terminal I get the following output:
---------------------
myServer:~# bacula-sd --version
bacula-sd: invalid option -- -
Copyright (C) 2000-2005 Kern Sibbald.

Version: 1.38.11 (28 June 2006)
---------------------
I personally would trust the command line more but I know that I installed 2.2.8 from source. Anyways, I'll look more into how to get the BAT going. Is that actually available for Mac OSX as well?

Cheers,
Steve

---

