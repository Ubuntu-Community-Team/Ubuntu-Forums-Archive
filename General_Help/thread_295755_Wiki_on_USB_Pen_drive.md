---
title: "Wiki on USB Pen drive"
date: 2006-11-08
forum: General Help
---

### Post by disabled_20220313 on 2006-11-08
Evening all,

I was hoping to set up a Wiki on my USB pen drive. Had a quick google, but don't find any instructions.

I can't imagine it'd be too hard, just need a shove in the right direction.

Would also need to build in something like LaTeX to let me write formulas, any idea how I would build that in?

Thanks,

---

### Post by procras on 2006-11-08
I am not sure what you really want to do.

Depends on the wiki you are using. And how you want to use it.

Suppose you need the following servers
apache
mysql

Your wiki data would probably need data in two places
/var/www/wikiname
databases tables

Possible approachs:
A: USBPEN to carry backupfiles of wiki and database files.
Linux on your boxes in different locations, (or LIVE distro on CD run but do not install, bit slow) 
and data on USBpen
- Backup everything into tar.bz2 files and move these back and forth
on the usbpen. Should be able to have simple scripts to do this. You would need to backup the wiki files
$ tar cvf writablelocation/uniquename_wiki.tar /var/www/wikiname
$ bzip2 writablelocation/uniquename_wiki.tar
This takes care of the wiki files
$ mysqldump --opt --databases wikidatabasename -u root -p > writablelocation/uniquename_wiki.sql
$ bzip2 writablelocation/uniquename_wiki.sql
This takes care of the database files

Then cp these backup files onto your USBpen and carry that with you and reverse the process etc.

B:Use the PEN as part of the filesystem for the computer and use the PEN to hold the wiki files and database files.

Create a nice filesystem on the USB pen
Mount the pen
use a link from /var/www/wikiname to point to the mountpoint of the pen
$ ln -s /var/www/wikiname /media/usbpen/wikiname
? use a link from /var/lib/mysql/mysql for the database files, but this looks a bit dangerous

C: Have a live distro on the USBPEN with your wiki and Mysql on it.
This sounds like a nice option. But would probably require more homework to set up than the two options above.

Hope my confused ramblings point you in the right direction.

---

### Post by scooper on 2006-11-08
[TiddlyWiki]("http://www.tiddlywiki.com/") is a wiki in a single file.  It's completely self-editing javascript and html, and requires no external database, web server, etc.  Basically you can just save their [empty file]("http://www.tiddlywiki.com/empty.html") using Save As by right-clicking the link.  After copying the html file to your USB stick you can open it with the browser and enable the javascript to save in place.

I've used it a bit and it works remarkably well for light-duty needs.

---

### Post by disabled_20220313 on 2006-11-09
Thanks for you help both,

I realised today that to run a wiki you need a constant "program" to generate the pages etc

And seeing as I can't be sure of which computer I'm plugging it into I can't really do that.

That tiddlywiki should do the trick for some stuff though. Thanks.

Got any directions for setting up a local wiki on my main machine??

Thanks again

---

