---
title: "Is there a way to set MySQL datadir to a network share?"
date: 2008-03-19
forum: General Help
---

### Post by barney_xuf on 2008-03-19
This is probably the wrong place to ask, but maybe some of you have already done this, so I'm attempting to mine your knowledge.

I want to set the datadir of MySQL to a network share, *e.g.,* //sharename/datadir.  I've tried a few things in my.cnf, but of course it's not as simple as I'd hoped.

Reason for doing is so that I don't have to maintain multiple data structures:  I want all my OS partitions to see the same data.  I'm using WinXP on one partition, then there are three Ubuntu partitions, Xfce, Gnome, and KDE - still haven't decided which is best for my purposes <sigh />.  However part of my testing involves database-driven web development, and doing an SQL dump every time I boot into another partition, then importing it into the current MySQL, is just too unwieldy <chuckle />.

Have any of you resolved such an issue, or am I in virgin territory?  (I'm also checking the MySQL areas, but thought I might get a quicker/better answer here.)

Make a good day ...
                            ... barn

---

### Post by kidders on 2008-03-20
Hi there,

Storing a MySQL database remotely is an exceptionally ill-advised idea imo, as is allowing more than one server to share the same underlying files. There is no way MySQL can *stop* you mounting a remote filesystem into /var/lib/mysql, for instance, but I would expect doing so to make an awful mess.

Exporting & importing SQL dumps seems the best option. Depending on what you're doing, something involving replication might also work for you.

---

### Post by jimv on 2008-03-20
You need to mount the share to a folder on your Ubuntu drive first.  (this can be ANY folder, ANYWHERE on your drive, though most people make a folder in /media)

Use this command to mount it temporarily (for testing)

[INDENT]smbmount //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword[/INDENT]

And once you know that it works, put an entry in your /etc/fstab file like this to make it mount on startup:

[INDENT]//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0[/INDENT]

Then you can set your my.cnf to look at the directory you have the share mounted on.  As far as MySQL is concerned, a network share mounted to a folder is the same as a regular folder.  Kind of like the same thing as Mounting a share to a drive letter in Windoze, but using folders instead of drive letters.

Also, don't all of your Linux partitions see your MySQL data folder anyway...since it's just on a different Ext3 partition?  The only OS you have that couldn't see that partition is XP.  So you could leave the database where it is, point all of your MySQL installs in your various distributions at that particular folder, and then download and install an Ext3 driver for XP and point MySQL in XP at the data folder on your Linux partition.

You can find an Ext3 driver at [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by barney_xuf on 2008-03-20
> **kidders said:**
> Hi there,

Storing a MySQL database remotely is an exceptionally ill-advised idea imo, as is allowing more than one server to share the same underlying files. There is no way MySQL can *stop* you mounting a remote filesystem into /var/lib/mysql, for instance, but I would expect doing so to make an awful mess.

Exporting & importing SQL dumps seems the best option. Depending on what you're doing, something involving replication might also work for you.

Ah-h-h ... well, I can see your point, but this is perhaps a bit different than your current concept.  I've been doing this for years with Windows.

I have a home LAN - not exposed to the world at large - that is router/switch based.  Connected to the router is a stand-alone drive (NAS) that holds my Apache DocRoot and MySQL data files.

The rationale behind this is pretty simple.  I may be working from one machine this morning and from another this afternoon.  I have to have the servers installed on each system, of course, but by having the data files and Apache web on the NAS, I don't have to mess with replication, SQL dump and import, or any other such tasks - I can spend my time working on the projects at hand, rather than *preparing *to work on 'em.  Since I'm never working with the data files from more than one machine at any given time, corruption, while possible, is unlikely.

As mentioned, I've been doing this for years - a decade, in fact, come August of this year.  There's never been a problem from this configuration, although I have screwed up the data files a few times with bad coding <sigh />.

Now that I'm bouncing back and forth from Windows to Linux - there are some things I simply have to do in Windows, like it or not - I'd prefer to continue as I've done in the past.  And I'm reasonably certain there's a way ... I'm just too new to Linux to divine it immediately.  It will happen, I'm certain, but I was attempting to shorten the process.  Spending a tenth to an eighth of my work time transferring data files is counter-productive.

'Preciate the response, though ... at least I know someone is reading my stuff <chortle />.

Make a good day ...
                            ... barn

---

