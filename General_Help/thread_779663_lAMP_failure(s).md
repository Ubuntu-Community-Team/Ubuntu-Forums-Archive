---
title: "lAMP failure(s)"
date: 2008-05-02
forum: General Help
---

### Post by barney_gul on 2008-05-02
Folk,

I've run out of options/ideas/straws-to-grasp.

Every time I reboot 8.04, I lose Apache2, MySQL5, & PHP5.

Well, I don't really lose them - phpMyAdmin can see my databases - but I just can't access them via PHP script.  Nor by a few other tools that are MySQL specific *e.g., *browser, admin, and so forth.  

I reinstall, everything looks good ... but I cannot make any user other than root access the MySQL system.  And, although I [finally] discovered how to log in as root, I still cannot browse AMP files.

Last 6-7 times I rebooted, I could at least use Firefox to browse my local Web ... now I can't even do that.

Firefox sees the PHP test page, and it sees the Apache2 installed page, but it simply will not see development pages that try to access MySQL.  OK, it sees the PHP pages, but any database access is shot.  I can run MySQL from a terminal window ... but can't see it from a browser script.

This worked, several reboots ago, but not any longer, and I cannot find a cause for the change.

If it matters;
[LIST]
[*]Ubuntu (Gnome) v8.04 (Hardy Heron)
[*]2.8 G CPU, Gateway box
[*]1 G ram
[*]32 G+ free space on 8.04 partition
[/LIST]

If I cannot get a resolution to this, I'm gonna hafta go back to Windows ... I need to do whatever it takes to pay the bills ... and, to date, Ubuntu is more unstable than WinXP, at least in my experience.

I really wanna stay with Linux, but I have to put food on the table, ya know?

'Preciate any help that might come my way.

Make a good day ...
                ... barn

---

### Post by Monicker on 2008-05-02
Your apache error logs should show any problems with php accessing the database.  Have you checked those yet?

Also, if you can't connect to mysql via its admin tools, it should be throwing numeric error codes that have a brief description.  What are some of those errors?  What is in /var/log/mysql.log?

---

### Post by barney_gul on 2008-05-03
I'm at a loss on this one - not the first time in the last couple of decades+ - but everything seems to have come back.

I *bit the bullet* and did a reinstall of AMP via Synaptic.

Magically, all that seemed to have been lost has reappeared <groan />.

Not groaning that it did, just groaning that I don't know ***why***!

However - at least until the next reboot! - all seems well.

Yes, I did check the logs ... every damned one that I could find, anyway ... and they gave no particular hint(s).

What really confuses me is that I still cannot copy the MySQL files from the other partition, even as root ... but somehow that did happen, even though it was not visible to me, from my original effort.

Still don't know how to get to some of the other files on the failed partition.  Even if I boot as *root*, still cannot change some of the permissions on that partition.

In fact, I'm having a bit of a problem getting to other partitions, in general.  I'm certain I'll find it somewhere in the docs, but it is a frustration at the moment.  I'd like to save some of my stuff, and some of my downloads to them, but that option just doesn't seem available.

As I said, I'm reasonably certain it's in the docs ... I just haven't found it ... and I hate being the short circuit between the seat and the keyboard, *i.e., *an eye-dee-ten-tee problem <sigh />.

'Preciate the response, though ... maybe you can tell me what happened <chortle />.

Make a good day ...
                   ... barn

---

