---
title: "Which program to use for Newsgroup?"
date: 2007-01-08
forum: General Help
---

### Post by boom2k1 on 2007-01-08
Which program to use for Newsgroup?

I need those Outlook kind of GUI software for newsgroup. Any people know of any in Ubuntu?

I don't think thunderbird allows users to subscribe to newsgroup.


Thanks

--Is this a really hard question to answer? Why no one seems to be answering me on this seems to be very easy question?

---

### Post by NT4usB on 2007-01-08
Thunderbird works fine for reading and posting to usenet. 
It doesn't do multipart binaries well though.
[http://opensourcearticles.com/thunderbird_15/english/part_08/](http://opensourcearticles.com/thunderbird_15/english/part_08/)

---

### Post by llamakc on 2007-01-08
> **boom2k1 said:**
> Which program to use for Newsgroup?

I need those Outlook kind of GUI software for newsgroup. Any people know of any in Ubuntu?

I don't think thunderbird allows users to subscribe to newsgroup.


Thanks

--Is this a really hard question to answer? Why no one seems to be answering me on this seems to be very easy question?

In the future you can help yourself by searching in Adept/Synaptic or with apt-cache from a commandline. Here's what the latter looks like:

```
ken@nola:~$ apt-cache search newsgroup
gnus - A versatile news and mail reader for Emacsen
knewsticker-scripts - scripts for KNewsTicker, the KDE news ticker
aub - Assembles binary files from USENET
brag - Downloads and assembles multipart Usenet binaries
cksfv - sfv checker and generator
dynamite - PKWARE Data Compression decompressor
fortunes-it - Data files containing Italian fortune cookies
fortunes-spam - fortunes taken from SPAM messages
gnus-bonus-el - Miscellaneous add-ons for Gnus
gup - let a remote site change their newsgroups subscription
ifgate - Internet to Fidonet gateway
klibido - usenet binary grabber for KDE
leafnode - NNTP server for small leaf sites
libnews-newsrc-perl - Manage newsrc files
libnews-scan-perl - News::Scan, Perl module to report Usenet newsgroup stats
mailagent - An automatic mail-processing tool and filter.
newspost - Usenet binary autoposter
nglister - Downloads information from NNTP server
nn - Heavy-duty USENET news reader (curses-based client)
nzb - An nzb based Usenet binary grabber
phpgroupware-nntp - phpGroupWare newsgroup reader module
pimppa - powerful tool to loot binaries from newsgroups smartly
post-faq - post periodic FAQs to Usenet newsgroups
sn - Small NNTP server for leaf sites
statnews - Extracts some useful statistics out of a newsgroup
uqwk - Offline mail and news package creator (NNTP version)
uqwk-spool - Offline mail and news package creator (spool version)
xbuffy - monitor mailboxes and/or newsgroups
xgammon - Implementation of backgammon under X
trn - Threaded USENET news reader, based on rn
trn4 - Threaded USENET news reader, based on rn (4.0 beta test)

```

So at this point, if I wanted to try a news reader, I could install any of the above. Find the one that satisfies your needs. Good luck.

---

### Post by dcstar on 2007-01-08
> **boom2k1 said:**
> Which program to use for Newsgroup?

I need those Outlook kind of GUI software for newsgroup. Any people know of any in Ubuntu?

I don't think thunderbird allows users to subscribe to newsgroup.


Thanks

--Is this a really hard question to answer? Why no one seems to be answering me on this seems to be very easy question?

pan.

---

### Post by boom2k1 on 2007-01-08
thanks. :)

I tried the Synaptic Approach and sadly it didn't return any meaningful results.

I would go with Thunderbird.

By the way, what do you mean by "binary"?

---

### Post by rykel on 2007-01-14
i am interested to find out too... thanks.

---

### Post by NT4usB on 2007-01-14
> **boom2k1 said:**
> thanks. :)

I tried the Synaptic Approach and sadly it didn't return any meaningful results.

I would go with Thunderbird.

By the way, what do you mean by "binary"?

Multi part binaries are movies, mp3's, software, etc. that are posted to the binary newsgroups.
Large files that are split into several parts when uploaded. You'll need a newsreader that can combine and decode files to download these.
I don't do it so I don't have any suggestions for those.

---

### Post by meng on 2007-01-14
I also use Pan Newsreader, although I must admit I use it rarely, as I'm not a big newsgroup kinda guy.

---

### Post by outofnicks on 2007-01-14
If the CLI (command-line interface) isn't your cup of tea, another approach is by the web at:
[http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)

Pan does work good for binaries, which are basically any files that aren't plain text. 

Images, program files (exe's for example) mp3's; any sound or image file, zip, tar.gz, etc.
I think PDF is a binary, but not sure...

[http://en.wikipedia.org/wiki/Binary_file](http://en.wikipedia.org/wiki/Binary_file)

---

### Post by allwin on 2007-01-14
PAN for download of binaries, KNODE for upload of binaries and text posting.  KNODE works best if you have KDE but it works under GNOME just as well.  I was displeased to find that not one hunk of software would BOTH download AND upload multipart binaries.  PAN doesn't (yet) allow you to attach files to posts.

---

### Post by Theimon on 2007-01-14
Newspost is a small program to post binary files. Problem with Newspost is the fact that it doesn't support multiple threads to your newsserver, making posting of files slower than necessary. Powerpost ([http://powerpost.cjb.net](http://powerpost.cjb.net)) under Wine is a good alternative then. At least, when your not on KDE, it'll keep your system free of KDE libs.

---

### Post by nix4me on 2007-01-14
pan

---

### Post by kd7swh on 2007-01-15
Pan for text, Hellanzb for downloading binaries, and newspost for binary posting.

[http://www.hellanzb.com/trac/](http://www.hellanzb.com/trac/)


[http://www.ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb](http://www.ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb)

---

### Post by andrew.46 on 2007-07-22
Hi,

 An alternative that is quite different to the usual GUI newsreaders is slrn:

[http://people.aapt.net.au/~adjlstrong/slrn.html](http://people.aapt.net.au/~adjlstrong/slrn.html)

 Takes a little work to get going but slrn is well worth the effort.

            Andrew

---

