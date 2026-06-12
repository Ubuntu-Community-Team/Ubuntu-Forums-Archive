---
title: "Help with package installation"
date: 2014-07-22
forum: General Help
---

### Post by aymaged on 2014-07-22
Greetings Dear ubuntu community,

I have a problem with installing a package called **FixParts**.
It is not an official ubuntu package but It is _very nessessary_ for me to get this package installed.
The problem is after downloading the package from the internet and when I try to install it using **dpkg** in the terminal, I get the following error message:

```
ahmad@gypsy:~$ sudo dpkg -i Downloads/fixparts_0.8.8-1_amd64.deb
[sudo] password for ahmad: 
(Reading database ... 181712 files and directories currently installed.)
Preparing to unpack .../fixparts_0.8.8-1_amd64.deb ...
Unpacking fixparts (0.8.8-1) ...
dpkg: error processing archive Downloads/fixparts_0.8.8-1_amd64.deb (--install):
 trying to overwrite '/usr/share/man/man8/fixparts.8.gz', which is also in package gdisk 0.8.8-1build1
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 Downloads/fixparts_0.8.8-1_amd64.deb
ahmad@gypsy:~$ 

```

As you see up, the error is:
```
trying to overwrite '/usr/share/man/man8/fixparts.8.gz', which is also in package gdisk 0.8.8-1build1
```

I looked up the file in the error and found that it is **Read-only** to everyone except the root account.
Is there any way to fix that or to work around it?

It is a strange situation because yesterday, I _successfully_ installed the same package on openSUSE before removing it and installing Ubuntu.

Any Help or Workarounds will be kindly appreciated ...
Or if you can provide an alternative to FixParts it will be great ...


Additional unnecessary information:
Incase anyone is wondering why this package is so important, I need this package to remove some leftover GPT partitioning information that wasn't completely removed by windows when my hard-disk was converted from GPT to MBR, and leaving this straying GPT information often causes confusion to my system and partitioning tools.

FixParts Description Excerpt:
[LIST]
[*]FixParts is a specialized partitioning tool. 
[*]It can remove stray GUID Partition Table (GPT) data, which can be left     behind on a disk that was once used as a GPT disk but then incompletely     converted to the more common Master Boot Record (MBR)     form. 
[/LIST]

Here is a link to FixParts: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by ian-weisser on 2014-07-22
The error means that two different packages both provide the same file (in this case, a manpage). That means the two packages are simply incompatible. One must be removed for the other to install.

But wait a second.

Fixparts *seems to be already included* with the gdisk package.
Indeed, that same upstream link is on the manpage.

---

