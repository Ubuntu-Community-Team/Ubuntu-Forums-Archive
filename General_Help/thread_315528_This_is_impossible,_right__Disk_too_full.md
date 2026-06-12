---
title: "This is impossible, right?  Disk too full?"
date: 2006-12-09
forum: General Help
---

### Post by Gen2ly on 2006-12-09
I wasn't paying mind last night when I noticed that I had run out of disk space :neutral: 

So I said I'll fix it in the morning.  I started deleting files (couple hundred MB.)  Then I ran df -h, and got this! :
> [FONT="Monospace"]Filesystem            Size  Used Avail Use% Mounted on
/dev/hda9             3.4G  3.3G     0 100% /
varrun                 93M   88K   93M   1% /var/run
varlock                93M     0   93M   0% /var/lock
procbususb             93M  116K   93M   1% /proc/bus/usb
udev                   93M  116K   93M   1% /dev
devshm                 93M     0   93M   0% /dev/shm[/FONT].. is that possible?  What the frak is happening?

---

### Post by taurus on 2006-12-09
You only have 3.5GB for Ubuntu.  Depends on what you have installed.  Remember what stuff you installed on your Ubuntu?

You can clean out the cache with

```
sudo apt-get clean
```

---

### Post by Gen2ly on 2006-12-09
Yes,   but-  I already deleted over 200 MB.   Doesn't make sense.

---

### Post by taurus on 2006-12-09
What doesn't make sense?  You only use 3.3GB out of 3.4GB but 5% of your disk is reserved for journaling if you use ext3 filesystem...

Again, you can clear out your cache to create some space on your harddrive...

```
sudo apt-get clean
```

---

### Post by Gen2ly on 2006-12-09
I deleted an additional 400 MB to be sure, restarted and fsck'd the partion with my rescue disk, then:
> [FONT="Monospace"]root@todd-partridge-mac:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda9             3.4G  3.3G     0 100% /
varrun                 93M   88K   93M   1% /var/run
varlock                93M     0   93M   0% /var/lock
procbususb             93M  120K   93M   1% /proc/bus/usb
udev                   93M  120K   93M   1% /dev
devshm                 93M     0   93M   0% /dev/shm[/FONT]

...strange, but I think my disk is locked.

---

### Post by taurus on 2006-12-09
Again, what other apps did you install on your machine?  If you do a standard install, it wouldn't take up more than 2GB!!!

Also, did you download and save some stuff to your $HOME directory?  Should look in there as well...

---

### Post by lha on 2006-12-09
Empty the trash bin if you haven't done it already...

---

### Post by Irony on 2006-12-09
Type;

[PHP]gksudo nautilus[/PHP]

and then delete anything in;

[PHP]/root/.Trash[/PHP]

and

[PHP]/.Trash-root[/PHP]

Note; press Ctrl+H to view these hidden folders.

---

### Post by Gen2ly on 2006-12-09
Ok:
> sudo apt-get clean
thanks for the tip.

Emptied trashes.

Removed semi-unwanted packages from Synaptic.

I figure around now I've ridded about 900 MB from my drive.

You guessed it:
> root@todd-partridge-mac:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda9             3.4G  3.3G     0 100% /
varrun                 93M   96K   93M   1% /var/run
varlock                93M     0   93M   0% /var/lock
procbususb             93M  120K   93M   1% /proc/bus/usb
udev                   93M  120K   93M   1% /dev
devshm                 93M     0   93M   0% /dev/shm

This is bit frustrating.  ](*,)  Some of these things would have been nice to keep.
You're right though taurus, how could I have deleted these files if my disk were locked?
A bit of background:  Last night I was compiling a kernel when I ran out of disk space.  Does this help?

---

### Post by lha on 2006-12-09
> **Dirk.R.Gently said:**
> 
A bit of background:  Last night I was compiling a kernel when I ran out of disk space.  Does this help?

Have you rebooted after you run out of space? Maybe some process is still going on and is filling your hard drive by writing stuff to a log file infinitely. Check how much stuff you have on /var. 'du -sh /var/' gives me some Permission denieds and 220M /var/, 'sudo du -sh /var/' gives 224M. Maybe you have an enormous log file there. 'find /var/ -size 10M' searches for every file larger than 10 MB in /var, try if it finds something. Check /tmp, as well.

---

### Post by Dubbayoo on 2006-12-09
How about listing what apps you have installed. 3.5GB is not a lot of space. This is mine:

steve@ubu:~$ dh
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda1              33G   14G   18G  43% /**
varrun                759M  132K  759M   1% /var/run
varlock               759M  4.0K  759M   1% /var/lock
procbususb             10M  484K  9.6M   5% /proc/bus/usb
udev                   10M  484K  9.6M   5% /dev
devshm                759M     0  759M   0% /dev/shm
lrm                   759M   18M  742M   3% /lib/modules/2.6.15-27-686/volatile
jeeves:/home           21G   11G  8.9G  55% /mnt/home
jeeves:media           29G  7.2G   19G  28% /mnt/music
/dev/hda1             231G  143G   76G  66% /data

9GB of that 14GB used is my /home directory. I actually only nfs mount /home/%user%/files/ so my / is really 5GB used.

---

### Post by Gen2ly on 2006-12-09
lha (love the name, btw) you're onto something there.

I did a > du --max-depth=1 -hc last night and was well below a 1000MB.  Now I look and > 1.1G    /var/eeek!
I'll try to find what it is.
BTW,> find /var/ -size 10Mdidn't work

---

### Post by Dubbayoo on 2006-12-09
likely /var/cache

> steve@ubu:~$ sudo du -s /var
**770296**  /var
steve@ubu:~$ sudo apt-get clean
steve@ubu:~$ sudo du -s /var
**259052**  /var


---

### Post by lha on 2006-12-09
> **Dirk.R.Gently said:**
> 

BTW,
find /var/ -size 10M
didn't work
Whoops, try
```
find /var -type f -printf "%s\t%p\n"|sort +0n
```

---

### Post by Gen2ly on 2006-12-09
Omg :eek: 
> [FONT="Monospace"]879783936       /var/log/cups/access_log[/FONT]

That can't be true?!  

Did compiling the kernel do this? or is there something more?  

Should I just try and delete it?

---

### Post by lha on 2006-12-09
> **Dirk.R.Gently said:**
> 
Did compiling the kernel do this? or is there something more?  

Should I just try and delete it?

CUPS is a printing layer (Common UNIX Printing System), so I doubt compiling caused this problem.

I'd try if removing that file and rebooting helps. You may want to look what's going on in /var/log/cups/access_log before removing it, though. It may give a hint on what is going wrong. Of course, keep an eye on that file to make sure it won't grow that big again.

---

### Post by kapilg_it on 2006-12-09
deleting access logs does effect anything on a desktop system.

---

### Post by Gen2ly on 2006-12-09
"You may want to look what's going on in /var/log/cups/access_log before removing it, though."

lol, lha.  I don't think my computer has the ability to handle such a large file.

kapilg_it, does or doesn't?

---

### Post by lemonsCC on 2006-12-09
i had this issue also...check you log files....mine were growing at about 5megs a minute.  The solution..reinstall

---

### Post by Cronjob on 2006-12-09
I'd suggest using something like 'filelight' to show your disk usage. Drill down until you find what is consuming most of your filespace so you can then decide if it is something unusual or not.

For example, you might find that you have a 68gb .xsession-errors log in your home directory that grew overnight until it consumed all of your drive space.

Filelight is only about 330kb, so you should have no problem grabbing it via aptitude.

---

### Post by kapilg_it on 2006-12-10
One more solution may be that you can ,create a cron job to compress various log file or rather delete them if found older than some specific time.
you can use webmin 8) for better overall control our you system usage (memory and size).
Using Webmin in system pane you have a logfile rotation option where you can set roatation schedule details.

OR 
Using log analyzers create report of logs them delete or compress them:cool:

---

### Post by Gen2ly on 2006-12-10
I deleted the access log been running it the last few hours and no more problems! :)
Appreciate the help guys!  

Though its still a mystery as to how it all came about.  I'll have to try this filelight and webmin .

---

### Post by freeflyer57 on 2007-02-08
I was shocked to find out that I only had 5 GB left on my computer. It turned out to be 28 GB in my cache. Thanks a lot for the post. It helped me a lot.

---

### Post by yamraaj on 2007-11-14
i have a 2gb /var partition. of late i am unable to install or uninstall packages. the error:

> dpkg: unable to fill /var/lib/dpkg/updates/tmp.i with padding: No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

so i did this:

> $ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda2 20G 6.6G 13G 35% /
varrun 995M 224K 995M 1% /var/run
varlock 995M 0 995M 0% /var/lock
procbususb 995M 124K 995M 1% /proc/bus/usb
udev 995M 124K 995M 1% /dev
devshm 995M 0 995M 0% /dev/shm
lrm 995M 39M 957M 4% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1 99M 33M 62M 35% /boot
/dev/sda7 112G 26G 81G 25% /home
/dev/sda6 9.9G 1.1G 8.4G 11% /opt
/dev/sda5 2.0G 68M 1.9G 4% /tmp
/dev/sda3 2.0G 2.0G 0 100% /var

so my 2 gb is being eaten up by varrun and varlock! how do i tackle this?i think the problem started when i tried to install a LAMP server

I am even unable to unisnstall packages now because of no space on var

my /var does not have any .Trash directory

PL PL PL help me out!!!

---

### Post by miesnerd on 2007-11-15
hey I'd like to chime in.
I am running a linux box at the U for multimedia stuff for a lab (actually, its Ubuntu Studio.
Anyways, to work with multimedia files, I installed an extra HD and partitioned it. Now I can move files there, but I wonder, can I move /home to that drive?
How can I use that space effectively?
I had to do the apt-get clean to be able to open firefox.

---

### Post by yamraaj on 2007-11-16
pl help me someone ... i am a complete newbie :(
i cant even uninstall packages now (i tried uninstalling apache2)

---

### Post by lha on 2007-11-17
> **yamraaj said:**
> 
so my 2 gb is being eaten up by varrun and varlock! how do i tackle this?i 

It seems that varrun and varlock do not fill your /var. They only use 224 K and 0 K, respectively. The second number from left is the 'used' column. Try to use the instructions in the earlier posts to free some space.

---

### Post by lha on 2007-11-17
> **miesnerd said:**
> I installed an extra HD and partitioned it. Now I can move files there, but I wonder, can I move /home to that drive?


You'll have to move the directories that are in your current /home to the new drive. Then, you have to alter /etc/fstab so that the new hd gets mounted to /home. See, e.g., [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive").

---

### Post by yamraaj on 2007-11-17
> **lha said:**
> It seems that varrun and varlock do not fill your /var. They only use 224 K and 0 K, respectively. The second number from left is the 'used' column. Try to use the instructions in the earlier posts to free some space.

when i view /var through nautilus it tells me 0 bytes left. but properties of /var/lock and /var/run say that each has 995mb of free space

sudo apt-get clean frees up 0 bytes when i do it

also, i have no ./Trash directory (i did do ctrl H)

how could i proceed?

its very frustrating as i cant even uninstall packages ia synaptic, nor can i update to gutsy

PS. even on restarting i get a popup saying 100% memory used in var

---

### Post by lha on 2007-11-17
> **yamraaj said:**
> 
sudo apt-get clean frees up 0 bytes when i do it

also, i have no ./Trash directory (i did do ctrl H)

how could i proceed?


Use
```
find /var -type f -printf "%s\t%p\n"|sort +0n
```
to find the largest files under var. In particular, check /var/log.

---

### Post by yamraaj on 2007-11-19
> 98102   /var/lib/dpkg/info/gnome-applets-data.md5sums
98477   /var/lib/dpkg/info/libsc-doc.list
98490   /var/lib/defoma/x-ttcidfont-conf.d/id-cache.sub
98676   /var/lib/dpkg/info/eclipse-source.md5sums
99275   /var/lib/dpkg/info/postgresql-8.2.list
99399   /var/lib/dpkg/info/samba-common.templates
100667  /var/lib/dpkg/info/eric.md5sums
101602  /var/lib/dpkg/info/cupsys.md5sums
104503  /var/lib/dpkg/info/gnome-user-guide.md5sums
105529  /var/lib/dpkg/info/texlive-latex-base.md5sums
105544  /var/lib/dpkg/info/eclipse-source.list
106550  /var/lib/scrollkeeper/scrollkeeper_docs
106581  /var/lib/dpkg/info/quanta-data.md5sums
107590  /var/lib/python-support/python2.5/pmg_tk/skins/normal/__init__.pyc
107723  /var/lib/defoma/libwmf0.2-7.d/id-cache
107800  /var/lib/dpkg/info/qt3-doc.list
110417  /var/lib/dpkg/info/xserver-xorg.postinst
111491  /var/lib/dpkg/info/sun-java6-demo.md5sums
114431  /var/lib/dpkg/info/ant-doc.list
115465  /var/lib/gconf/defaults/%gconf-tree-zu.xml
116522  /var/lib/dpkg/info/scalapack-doc.md5sums
117569  /var/lib/gconf/defaults/%gconf-tree-af.xml
118713  /var/lib/dpkg/info/octaviz.md5sums
119194  /var/lib/dpkg/info/app-install-data.list
122875  /var/lib/dpkg/info/tzdata.md5sums
123351  /var/lib/gconf/defaults/%gconf-tree-nso.xml
123477  /var/lib/dpkg/info/firefox.md5sums
123592  /var/log/kern.log.0
124926  /var/lib/dpkg/info/mysql-server-5.0.md5sums
125508  /var/lib/defoma/fontconfig.d/id-cache
125901  /var/lib/gconf/defaults/%gconf-tree-sr@ije.xml
128798  /var/lib/dpkg/info/boson-data.md5sums
130547  /var/lib/texmf/ls-R-TEXMFDIST-TETEX
134049  /var/log/installer/syslog
134504  /var/lib/dpkg/info/dia-common.md5sums
135455  /var/lib/dpkg/info/openssh-client.preinst
139008  /var/log/wtmp.1
140033  /var/lib/dpkg/info/x11-common.templates
142253  /var/lib/gconf/defaults/%gconf-tree-wa.xml
142446  /var/lib/dpkg/info/linux-image-2.6.20-16-generic.list
142567  /var/lib/dpkg/info/linux-image-2.6.20-15-generic.list
142580  /var/lib/dpkg/info/texlive-latex-recommended.list
143185  /var/lib/gconf/defaults/%gconf-tree-is.xml
148162  /var/lib/dpkg/info/libqt4-dev.md5sums
148516  /var/lib/dpkg/info/foomatic-db.list
151552  /var/log/mail.warn
152148  /var/lib/scrollkeeper/C/scrollkeeper_extended_cl.xml
153314  /var/lib/dpkg/info/ant-doc.md5sums
154089  /var/lib/dpkg/info/postgresql-8.2.md5sums
154849  /var/lib/dpkg/info/libsc-doc.md5sums
155128  /var/lib/texmf/web2c/mf.base
157815  /var/lib/dpkg/info/postfix.templates
159406  /var/lib/dpkg/info/passwd.templates
161822  /var/lib/dpkg/info/openoffice.org-common.list
171466  /var/lib/dpkg/info/texlive-fonts-recommended.list
172102  /var/lib/gconf/defaults/%gconf-tree-hy.xml
181006  /var/lib/dpkg/info/linux-image-2.6.20-16-generic.md5sums
181105  /var/lib/dpkg/info/linux-image-2.6.20-15-generic.md5sums
185702  /var/lib/dpkg/info/texlive-latex-recommended.md5sums
188073  /var/lib/dpkg/info/qt4-doc.list
191206  /var/lib/dpkg/info/qt3-doc.md5sums
196934  /var/lib/dpkg/info/tex4ht-common.list
201381  /var/lib/dpkg/info/app-install-data.md5sums
204597  /var/lib/texmf/ls-R-TEXLIVE
206445  /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_source_Sources
210948  /var/lib/dpkg/info/grass-doc.list
213039  /var/lib/dpkg/info/openoffice.org-common.md5sums
217531  /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-amd64_Packages
221055  /var/lib/dpkg/info/libgcj7-dev.list
221136  /var/lib/dpkg/info/dictionaries-common.templates
228099  /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_source_Sources
230559  /var/lib/texmf/web2c/mptopdf.fmt
233699  /var/lib/dpkg/info/foomatic-db.md5sums
237568  /var/log/messages
238550  /var/lib/dpkg/info/scilab-doc.list
239114  /var/lib/defoma/xfont.font-cache
239582  /var/lib/dpkg/info/texlive-fonts-recommended.md5sums
244249  /var/lib/dpkg/info/tango-icon-theme.list
247186  /var/lib/texmf/web2c/tex.fmt
251934  /var/lib/dpkg/info/kdelibs-data.list
257948  /var/lib/dpkg/info/gnome-icon-theme.md5sums
263608  /var/lib/texmf/web2c/pdftex.fmt
265530  /var/lib/dpkg/info/linux-headers-2.6.20-16-generic.md5sums
265629  /var/lib/dpkg/info/linux-headers-2.6.20-15-generic.md5sums
266435  /var/lib/gconf/defaults/%gconf-tree-ku.xml
270028  /var/log/installer/initial-status.gz
270336  /var/log/mail.info
273730  /var/lib/gconf/defaults/%gconf-tree-mr.xml
274432  /var/log/mail.log
283556  /var/lib/dpkg/info/tex4ht-common.md5sums
291637  /var/lib/dpkg/info/linux-headers-2.6.20-16-generic.list
291703  /var/lib/dpkg/info/linux-headers-2.6.20-15-generic.list
292782  /var/lib/texmf/web2c/etex.fmt
293032  /var/lib/texmf/web2c/pdfetex.fmt
293168  /var/log/lastlog
294912  /var/log/syslog
295669  /var/log/udev
296587  /var/lib/dpkg/info/scilab.list
296944  /var/lib/collectd/users.rrd
307851  /var/lib/dpkg/info/grass-doc.md5sums
308250  /var/lib/dpkg/info/qt4-doc.md5sums
309900  /var/lib/defoma/x-ttcidfont-conf.d/id-cache
325733  /var/lib/dpkg/info/libgcj7-dev.md5sums
332320  /var/lib/mysql/mysql/help_topic.MYD
335723  /var/lib/gconf/defaults/%gconf-tree-bs.xml
336658  /var/lib/gconf/defaults/%gconf-tree-ms.xml
339595  /var/lib/dpkg/info/gnome-icon-theme.list
344824  /var/lib/texmf/web2c/aleph.fmt
346623  /var/lib/dpkg/info/texlive-latex-extra.md5sums
366133  /var/lib/dpkg/info/php-doc.list
375965  /var/lib/dpkg/info/kdelibs-data.md5sums
380452  /var/log/dpkg.log.1
380797  /var/lib/gconf/defaults/%gconf-tree-or.xml
383195  /var/lib/dpkg/info/doc-linux-html.list
386966  /var/lib/dpkg/info/scilab-doc.md5sums
408592  /var/lib/gconf/defaults/%gconf-tree-mg.xml
410033  /var/lib/gconf/defaults/%gconf-tree-az.xml
417275  /var/lib/gconf/defaults/%gconf-tree-hr.xml
418775  /var/lib/gconf/defaults/%gconf-tree-mn.xml
420600  /var/lib/dpkg/info/texlive-latex-extra.list
420935  /var/lib/gconf/defaults/%gconf-tree-ka.xml
436907  /var/lib/python-support/python2.5/libxml2.pyc
443516  /var/lib/texmf/web2c/latex209.fmt
451185  /var/lib/gconf/defaults/%gconf-tree-sk.xml
471816  /var/lib/texmf/web2c/metafun.mem
482695  /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-amd64_Packages
483454  /var/lib/gconf/defaults/%gconf-tree-xh.xml
483702  /var/lib/gconf/defaults/%gconf-tree-nn.xml
490436  /var/lib/dpkg/info/scilab.md5sums
495078  /var/lib/gconf/defaults/%gconf-tree-ml.xml
500907  /var/lib/gconf/defaults/%gconf-tree-be.xml
507267  /var/tmp/kdecache-prithwiraj/ksycoca
523634  /var/lib/gconf/defaults/%gconf-tree-he.xml
571087  /var/lib/dpkg/info/php-doc.md5sums
577182  /var/log/mysql/mysql-bin.000002
580498  /var/lib/dpkg/info/doc-linux-html.md5sums
586245  /var/lib/dpkg/info/linux-headers-2.6.20-16.list
586303  /var/lib/dpkg/info/linux-headers-2.6.20-15.list
588659  /var/lib/gconf/defaults/%gconf-tree-sq.xml
591814  /var/lib/gconf/defaults/%gconf-tree-ro.xml
592208  /var/lib/collectd/df-boot.rrd
592208  /var/lib/collectd/df-dev.rrd
592208  /var/lib/collectd/df-dev-shm.rrd
592208  /var/lib/collectd/df-home.rrd
592208  /var/lib/collectd/df-lib-modules-2.6.20-15-generic-volatile.rrd
592208  /var/lib/collectd/df-lib-modules-2.6.20-16-generic-volatile.rrd
592208  /var/lib/collectd/df-media-cdrom0.rrd
592208  /var/lib/collectd/df-media-disk.rrd
592208  /var/lib/collectd/df-media-PRITHWIRAJ.rrd
592208  /var/lib/collectd/df-opt.rrd
592208  /var/lib/collectd/df-proc-bus-usb.rrd
592208  /var/lib/collectd/df-root.rrd
592208  /var/lib/collectd/df-tmp.rrd
592208  /var/lib/collectd/df-var-lock.rrd
592208  /var/lib/collectd/df-var.rrd
592208  /var/lib/collectd/df-var-run.rrd
592208  /var/lib/collectd/interface-eth0/if_errors.rrd
592208  /var/lib/collectd/interface-eth0/if_packets.rrd
592208  /var/lib/collectd/interface-lo/if_errors.rrd
592208  /var/lib/collectd/interface-lo/if_packets.rrd
592208  /var/lib/collectd/traffic-eth0.rrd
592208  /var/lib/collectd/traffic-lo.rrd
602793  /var/lib/gconf/defaults/%gconf-tree-et.xml
604679  /var/lib/gconf/defaults/%gconf-tree-id.xml
611972  /var/lib/gconf/defaults/%gconf-tree-fa.xml
618893  /var/lib/gconf/defaults/%gconf-tree-tr.xml
625633  /var/lib/gconf/defaults/%gconf-tree-cy.xml
629945  /var/lib/gconf/defaults/%gconf-tree-sl.xml
630784  /var/log/syslog.0
639657  /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-amd64_Packages
640630  /var/lib/gconf/defaults/%gconf-tree-gl.xml
641681  /var/lib/gconf/defaults/%gconf-tree-en_CA.xml
652108  /var/lib/gconf/defaults/%gconf-tree-da.xml
652518  /var/lib/gconf/defaults/%gconf-tree-eu.xml
654514  /var/lib/texmf/web2c/latex.fmt
654549  /var/lib/texmf/web2c/pdflatex.fmt
655940  /var/lib/gconf/defaults/%gconf-tree-zh_HK.xml
658270  /var/lib/gconf/defaults/%gconf-tree-lv.xml
667199  /var/lib/gconf/defaults/%gconf-tree-nb.xml
677444  /var/lib/gconf/defaults/%gconf-tree-sr@Latn.xml
694201  /var/lib/gconf/defaults/%gconf-tree-ne.xml
706074  /var/lib/gconf/defaults/%gconf-tree-ko.xml
721863  /var/lib/gconf/defaults/%gconf-tree-nl.xml
725144  /var/lib/gconf/defaults/%gconf-tree-lt.xml
727675  /var/lib/gconf/defaults/%gconf-tree-ar.xml
729519  /var/lib/gconf/defaults/%gconf-tree-ta.xml
731457  /var/lib/gconf/defaults/%gconf-tree-en_GB.xml
738123  /var/lib/gconf/defaults/%gconf-tree-pt.xml
746918  /var/lib/gconf/defaults/%gconf-tree-bn.xml
754039  /var/lib/gconf/defaults/%gconf-tree-hi.xml
768783  /var/lib/gconf/defaults/%gconf-tree-ca.xml
769833  /var/lib/gconf/defaults/%gconf-tree-vi.xml
778702  /var/lib/gconf/defaults/%gconf-tree-bn_IN.xml
779746  /var/lib/dpkg/info/linux-headers-2.6.20-16.md5sums
779837  /var/lib/dpkg/info/linux-headers-2.6.20-15.md5sums
795689  /var/lib/gconf/defaults/%gconf-tree-sr.xml
823998  /var/lib/gconf/defaults/%gconf-tree-el.xml
826192  /var/lib/gconf/defaults/%gconf-tree-uk.xml
832992  /var/lib/gconf/defaults/%gconf-tree-mk.xml
853245  /var/lib/gconf/defaults/%gconf-tree-pa.xml
860108  /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty-updates_main_binary-amd64_Packages
861076  /var/lib/gconf/defaults/%gconf-tree-bg.xml
879790  /var/lib/gconf/defaults/%gconf-tree-th.xml
887472  /var/lib/collectd/load.rrd
888038  /var/lib/gconf/defaults/%gconf-tree-ru.xml
891608  /var/lib/gconf/defaults/%gconf-tree-zh_CN.xml
903179  /var/lib/gconf/defaults/%gconf-tree-gu.xml
924005  /var/lib/gconf/defaults/%gconf-tree-cs.xml
926144  /var/lib/gconf/defaults/%gconf-tree-pl.xml
933004  /var/lib/gconf/defaults/%gconf-tree-zh_TW.xml
934386  /var/lib/gconf/defaults/%gconf-tree-sv.xml
961685  /var/log/installer/partman
967849  /var/lib/gconf/defaults/%gconf-tree-fi.xml
970256  /var/lib/gconf/defaults/%gconf-tree-hu.xml
985266  /var/lib/gconf/defaults/%gconf-tree-it.xml
1005262 /var/lib/gconf/defaults/%gconf-tree-pt_BR.xml
1020195 /var/lib/gconf/defaults/%gconf-tree-ja.xml
1021271 /var/lib/gconf/defaults/%gconf-tree-es.xml
1023645 /var/lib/gconf/defaults/%gconf-tree-de.xml
1041155 /var/lib/gconf/defaults/%gconf-tree-fr.xml
1052162 /var/lib/dpkg/info/xserver-xorg.templates
1075111 /var/lib/gconf/defaults/%gconf-tree-dz.xml
1182736 /var/lib/collectd/memory.rrd
1182736 /var/lib/collectd/partition-8-17.rrd
1182736 /var/lib/collectd/partition-8-1.rrd
1182736 /var/lib/collectd/partition-8-2.rrd
1182736 /var/lib/collectd/partition-8-3.rrd
1182736 /var/lib/collectd/partition-8-4.rrd
1182736 /var/lib/collectd/partition-8-5.rrd
1182736 /var/lib/collectd/partition-8-6.rrd
1182736 /var/lib/collectd/partition-8-7.rrd
1182736 /var/lib/collectd/partition-8-8.rrd
1182736 /var/lib/collectd/swap.rrd
1189912 /var/lib/texmf/web2c/omega.fmt
1306624 /var/log/messages.0
1315452 /var/cache/app-install/mime_menu.p
1355776 /var/log/mail.warn.0
1441792 /var/lib/gcj-4.1/classmap.db
1478000 /var/lib/collectd/cpu-0.rrd
1478000 /var/lib/collectd/cpu-1.rrd
1773264 /var/lib/collectd/processes.rrd
1814585 /var/lib/texmf/web2c/pdfjadetex.fmt
1839606 /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty_main_source_Sources
1843543 /var/lib/dpkg/available
1843543 /var/lib/dpkg/available-old
1845198 /var/lib/texmf/web2c/jadetex.fmt
1911009 /var/lib/dpkg/status
1911009 /var/lib/dpkg/status-old
2330789 /var/cache/man/index.db
2363792 /var/lib/collectd/disk-11-0.rrd
2363792 /var/lib/collectd/disk-8-0.rrd
2363792 /var/lib/collectd/disk-8-16.rrd
2560000 /var/log/mail.info.0
2564096 /var/log/mail.log.0
2650848 /var/lib/aspell/en-common.rws
3255583 /var/cache/debconf/templates.dat
3285443 /var/cache/debconf/templates.dat-old
4200246 /var/lib/gconf/defaults/%gconf-tree.xml
4789308 /var/cache/app-install/menu.p
5242880 /var/lib/mysql/ib_logfile0
5242880 /var/lib/mysql/ib_logfile1
5644181 /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty_universe_source_Sources
5889574 /var/lib/texmf/web2c/cont-en.fmt
6105461 /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-amd64_Packages
10467740        /var/cache/apt/srcpkgcache.bin
10485760        /var/lib/mysql/ibdata1
10508960        /var/cache/apt/pkgcache.bin
17201828        /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-amd64_Packages


these are the last few (the biggest files)...the largest here is 17mb...which are the ones safe to delete?

sorry if i come off as too ignorant...but i really know nothing abt the way these things work :(

---

### Post by yamraaj on 2007-11-19
also...deleting anything doesnt seem to free space...neither does it create a .Trash...whats the command to delete?

---

### Post by yamraaj on 2007-11-19
> **yamraaj said:**
> when i view /var through nautilus it tells me 0 bytes left. but properties of /var/lock and /var/run say that each has 995mb of free space


the other contents of var show zero bytes free space when i view their properties...any reason for this?

---

### Post by atlfalcons866 on 2007-11-19
> **taurus said:**
> You only have 3.5GB for Ubuntu.  Depends on what you have installed.  Remember what stuff you installed on your Ubuntu?

You can clean out the cache with

```
sudo apt-get clean
```

Actuallly the 5% is reserved for the root. The journal has its own file which is around 4094 blocks.

---

### Post by lha on 2007-11-22
> **yamraaj said:**
> these are the last few (the biggest files)...the largest here is 17mb...which are the ones safe to delete?

sorry if i come off as too ignorant...but i really know nothing abt the way these things work :(

The files in /var/log are log files; those are usually safe to remove.

> **yamraaj said:**
> also...deleting anything doesnt seem to free space...neither does it create a .Trash...whats the command to delete?

Well, either you haven't deleted anything, or something is filling your /var. (My guess is that at least the latter is true.) Check what collectd is doing. It has created many 0.5 - 1 MB files. Maybe it is the cause of your troubles. Try if removing a file frees some space. If not, you'll have to find is flooding your /var. Use
```
find /var -type f -mmin -5 -printf "%s\t%p\n"
```
to find which files have changed in the last 5 minutes. Then, remove another file and use the command above again. Hopefully, you'll see which file is growing.

rm removes files.

> **yamraaj said:**
> the other contents of var show zero bytes free space when i view their properties...any reason for this?

/var/lock and /var/run are not in the /var partition, but on a ramdisk. Don't worry about them.

---

