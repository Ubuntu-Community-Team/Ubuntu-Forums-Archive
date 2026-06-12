---
title: "Needing important Linux file restores"
date: 2007-08-21
forum: General Help
---

### Post by raevin on 2007-08-21
Searched the forum and wasn't able to find anything that I need for this...

Kubuntu 7.04

How do you recover files that were deleted in /bin?  (Example: sudo, ls, etc...)

Thinking of repartitioning my Linux hard drive to have two Linux OS' installed, and just copy the entire directory of files needed from the fresh partition over to the old one, and try to boot to my old one again...but not sure if this would really work, and don't want to chance screwing something up.

Reason for me not just starting from scratch is because there's a few programs (HTTP server, PHP, etc...)  that I don't want to have to reconfigure and such.  But, if I must then I will do that...

Anyone know of preferably any non-destructive ways to handle this issue by chance?

---

### Post by astralsin on 2007-08-21
the configuration isnt in the binary, its in configuration files.  for php, its /etc/php5/php.ini and for apache its /etc/apache2/httpd.conf just copy those files

---

### Post by raevin on 2007-08-21
> **astralsin said:**
> the configuration isnt in the binary, its in configuration files.  for php, its /etc/php5/php.ini and for apache its /etc/apache2/httpd.conf just copy those files

I think you're mis-understanding me.

What I need to do is basically have all the files in the /bin directory (among probably every other file since I can't even launch Konqueror) restored (seems like they were all deleted or something).

I can't run even "ls" or "sudo"/"su", because it says "ls" can't be found in /bin or whatnot.

I just don't want to erase my hard drive and lose all the config files I have that are good...I just want to restore the files that were deleted (ala: copy all the files from a clean Linux install to the partition in trouble)...nor can I boot my computer up anymore from that particular HD, because of the fact every file seems to have been deleted.

(Was done by mistake, so yeah...my fault, but...meh.)

---

### Post by bodhi.zazen on 2007-08-21
IMO you are best off copying the config files and re-installing.

---

### Post by raevin on 2007-08-21
> **bodhi.zazen said:**
> IMO you are best off copying the config files and re-installing.

Is there any other ways though?  Really not wanting to do that unless it's impossible any other way.

---

### Post by kuja on 2007-08-21
It sounds like your installation is in really bad shape, you really are better off reinstalling at that point. Fixing the problem would require a lot more effort and leave lots of room for user error. Besides, files deleted via rm can't be restored without a) special software the likes of which I do not have and can't give exmples of or b) re-getting and replacing files manually (the hard way). At any rate, it's not worth the effort, just back up and reinstall.

---

### Post by raevin on 2007-08-21
> **kuja said:**
> It sounds like your installation is in really bad shape, you really are better off reinstalling at that point. Fixing the problem would require a lot more effort and leave lots of room for user error. Besides, files deleted via rm can't be restored without a) special software the likes of which I do not have and can't give exmples of or b) re-getting and replacing files manually (the hard way). At any rate, it's not worth the effort, just back up and reinstall.

Alrighty...prob. would be the quicker way too.  Thankfully I can access Linux partitions via Windows (hopefully I didn't screw that up either.)

Thanks for the help all.

---

