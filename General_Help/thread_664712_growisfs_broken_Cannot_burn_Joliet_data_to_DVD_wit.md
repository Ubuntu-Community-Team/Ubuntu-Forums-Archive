---
title: "growisfs broken: Cannot burn Joliet data to DVD with Ubuntu Gutsy"
date: 2008-01-11
forum: General Help
---

### Post by malibu on 2008-01-11
When I try the following comment to burn a directory to a DVD:

growisfs -input-charset=ISO-8859-1 -Z /dev/scd0 -R -J -pad /BACKUPDIR

The disk burns fine but the first line output is something like the following:

**genisoimage: unexpected directory length 908 expected: 912**

And following that I can't use the disk on Windows at all, only Linux.  This is a big problem for me.

What can I do to fix it?

---

### Post by disturbed1 on 2008-01-11
Bug in CDRKit (Wodim + genisoimage).
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244)

Install mkisofs and link mkisofs against genisoimage.

You can do the following in a term. Caution, this will replace genisoimage with mkisofs.

[B]sudo su
apt-get install mkisofs
mv /usr/bin/genisoimage /root/genisoimage
cp /usr/bin/mkisofs /usr/bin/genisoimage
exit[/B]

The above allows you to become root, install mkisofs, move genisoimage to /root dir for safe keeping, then copies mkisofs as genisoimage.

CDRKit was founded to replace cdrecord and mkisofs as Debian doesn't like CDDL. Problem is, CDRKit is based off of 2-3 year old code, which has bugs, and in the process new bugs have been introduced.

---

### Post by malibu on 2008-01-11
Thank you for your comments, but now I'm more confused then ever!  Check this out:

root@malibu:~/scripts# apt-get install mkisofs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mkisofs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  genisoimage
E: Package mkisofs has no installation candidate

.... So that's confusing, because I already have genisoimage installed, but mkisofs didn't come with it.  I was going to try the copy anyway (actually I've prefer to just ln -s mkisofs genisoimage) , but since I can't get mkisofs I'm SOL.. any ideas?  p-p-p-pleaase?  Thx.

---

### Post by disturbed1 on 2008-01-11
You need to have multiverse repo enabled or get it from here -
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mkisofs&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mkisofs&searchon=names&subword=1&version=gutsy&release=all)

You may also want to install cdrtools, which is a meta package that includes cdrecord, mkisofs, and cdda2wav

---

### Post by malibu on 2008-01-11
Ahh.. I'll bet the repo is what I've been missing all along... I did see cdrtools at one point and tried to install it but that didn't work either.  How do I add the multiverse repo again?  You're right.. I would like to install cdrtools.  Does cdrecord work better then growisfs?

I found the RPM for mkisofs and installed it that way and it seems to be working via the ln to genisoimage.


.....hmmm a little addendum.  I do seem to have multiverse enabled.  Here is a summary of my sources list.  why can't I find cdrtools?

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe
[COLOR="Red"]deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse[/COLOR]
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by disturbed1 on 2008-01-11
I gave you the link to the Ubuntu .deb package above ;)

cdrecord replaces wodim. Only necessary if you've experienced other burning issues. If you haven't I wouldn't fix what is not broken :D

The repo in your sources list has mkisofs, it's listed as the meta package for cdrtools. Strange how my mirror lists mkisofs as its own package.

In Synaptic - click on settings, choose repositories, change your settings here (for future reference).

---

### Post by malibu on 2008-01-11
Ok I've tried Uni of Calgary, Uni of Waterloo (I'm in Canada), and finally the Main repository.. I can't get cdrtools to pop up in Synaptic.. Only cdrskin.

I getcha that I probably don't need to install it but I'd like to understand why.

Oh.. Thanks for the link to the .deb file!  Didn't quite get that from seeing the url.  Didn't know you could get them from the website like that.

Thanks for all the help!  

Perhaps cdrtools isn't in the repositories?

---

