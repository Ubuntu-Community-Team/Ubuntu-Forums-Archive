---
title: "What is the best way for ftp transfers"
date: 2007-05-29
forum: General Help
---

### Post by SteveHillier on 2007-05-29
Hi guys
Can I have some clues as to the best way to set file permissions to allow ftp transfers to hosted web sites.
Synopsis
Ubuntu Dapper web server with php & mysql.
web site root /var/www/sitename
permission on folder set to 777 (mainly because that was easiest when I initially set it up).  To access the web site I really need 775 permissions in order that the html and php files can be displayed, but I need 772 for the ftp work.
However when I set the permissions to 775 the ftp client (hey, even more amazing I am using the ftp client built into Windows Vista!!) then the ftp client cannot see the folders.
When I did transfer the files with these folder settings the resultant permissions did not have execute rights so the website would not display.

I can set the folders to 777 but that seems a bit risky and does not solve my ftp problem.
Should I change the ownership of the folder to my ftp-users group (but then how does that affect me if I want to change files locally).  I could then set it manually to 775 and write the files via ftp and execute OK but does it allow the execute rights on the transferred files.

I then really need files to inherit directory rights.  I believe I can do this in Samba but that will affect the whole machine not just the directories I am interested in.  So is there a specific way of making sure files and child folders in a directory can inherit parental rights?  And if there is, how is this done (I notice a 'sticky' flag on the permissions window)?  And is this the best way to do it?

I apologise to all of you real computer people out there for the fact that I have been locked into a Microsoft dominated world since 1983 and have become blinkered to the existence of proper computing.  You see how it affects me, I cannot think of a sensible username for myself and have to use SteveHillier instead!!   And the fact that I have uppercase in there tells me I have got a long way to go before I am fully converted.
Steve

---

### Post by fanatik on 2007-05-29
hi Steve,

you sound confused! actually, so am I after reading this, but i will give you some advice...

you should never need to have 777 on any directory or file - this is very bad securitywise, especially for systems connected to the interweb. try to avoid that if at all possible. try to use groups if you can.

the umask defines the permissions when files are created, this is set system-wide and can be overridden for individual users. its set systemwide in /etc/profile on my edgy install its 022. now what this means is that if you create a file it'll take off 022 from it (files are 666 by default), leaving 644, if you create a dir (they are 777 by default) it'll take off 022 leaving 755.

now, the sticky bit, t, on permissions, can be seen on /tmp, for example (ls -ld /tmp will show it). what this means is that only people that own the files can delete them, if the sticky bit is not set, then anyone that can write to the directory containing the files can delete them!

a couple of good articles on this are here:

[http://www.hackinglinuxexposed.com/articles/20030417.html]("http://www.hackinglinuxexposed.com/articles/20030417.html")
[http://www.hackinglinuxexposed.com/articles/20030424.html]("http://www.hackinglinuxexposed.com/articles/20030424.html")

sorry if this doesn't actually help you!

---

