---
title: "very slow mplayer, possible virus ?"
date: 2007-05-31
forum: General Help
---

### Post by Peter Sommer-Larsen on 2007-05-31
My linux system has allways worked so nice, but in the last ½ year it has started to
have some problems. One is, that I cant commit pictures to my cvs server, and another
is, that my mplayer takes a long time to start up.! I dont have either an antivirus program
or a firewall, so maybe Ive got a virus. I thought that the use of firewalls and antivirus
was not needed in Linux.

Is there a way to fix this problem or a way to find the possible virus ?

Thx
Peter

---

### Post by Gio-van-I on 2007-05-31
Viruses are made for specific operating systems. Windows being the biggest player most viruses are made for it. Of course there are viruses for Linux too, but very few. With linux having a better program/user security you will most likely have to give a virus permission to run.

This all means it is very hard to get viruses for Linux but it's still possible.
To prevent getting infected don't just run every thing you get of the net. Make sure it's safe. Also getting a firewall running and a virus scanner.

To get a firewall look up firestarter in your package manager.
To get a virus scanner search for virus in your package manager. It should give some results.

If you want to find out why your system is slow try opening your system monitor to find out what's using up your processor.

I haven't been infected yet myself, but I hope you can use this information in some way.

---

### Post by Peter Sommer-Larsen on 2007-05-31
I have been using the top-command, and it seem like there is nothing that swallows
my CPU or memory. Ive tried to grep some of the wierd processes, but they look just fine.
Is it really necessary to have a firewall .? I will try to run a virus scan.
If i type the following command i get;

$ apt-cache search virus,

exim4-daemon-heavy - exim MTA (v4) daemon with extended features, including exiscan-acl
f-prot-installer - F-Prot(tm) Antivirus installer package
aegis-virus-scanner - A virus scanner for Linux/Unix systems
amavis-ng - AMaViS "Next Generation"
amavis-stats - Virus statistics RRDtool frontend for Amavis
amavisd-new - Interface between MTA and virus scanner/content filters
amavisd-new-milter - Interface between sendmail-milter and amavisd-new
avscan - GTK frontend for the Clam AntiVirus scanner (ClamAV)
clamassassin - simple virus filter wrapper for ClamAV
clamav-getfiles - Update script for clamav
clamcour - courier filter for clamav to virus scan incoming mail
clamsmtp - virus-scanning SMTP proxy
dansguardian - Web content filtering
frox - Transparent caching ftp proxy
graphdefang - create graphs of your mimedefang spam and virus logs
havp - HTTP Anti Virus Proxy
klamav - KDE frontend for ClamAV
libfile-scan-perl - Perl lib to scan files for viruses
libspf2-2 - Sender Policy Framework library, written in C
libspf2-dev - Header and development libraries for libspf2
mailscanner - email virus scanner and spam tagger
messagewall - An SMTP proxy daemon, designed to help keep out unwanted email
nomarch - Unpacks .ARC and .ARK MS-DOS archives
p3scan - transparent POP3-proxy with virus- and spam-scanning
partimage - backup partitions into a compressed image file
php4-clamavlib - PHP ClamAV Lib - ClamAV Interface for PHP4 Scripts
php5-clamavlib - PHP ClamAV Lib - ClamAV Interface for PHP5 Scripts
picalib - Set of PICA helper scripts and configuration files
proxsmtp - multi purpose SMTP Proxy
python-clamav - Python bindings to ClamAV
renattach - Rename attachments on the fly
sanitizer - The Anomy Mail Sanitizer - an email virus scanner
stepbill.app - Get rid of those nasty Wingdows viruses
sylpheed-claws-clamav - Clam AntiVirus plugin for Sylpheed Claws
sylpheed-claws-gtk2-clamav - Clam AntiVirus plugin for the Sylpheed-Claws GTK2 mail client
viruskiller - Game about viruses invading your computer
xbill - Get rid of those Wingdows Viruses!
clamav - antivirus scanner for Unix
clamav-base - base package for clamav, an anti-virus utility for Unix
clamav-daemon - antivirus scanner daemon
clamav-docs - documentation package for clamav, an anti-virus utility for Unix
clamav-freshclam - downloads clamav virus databases from the Internet
clamav-milter - antivirus scanner for sendmail
clamav-testfiles - use these files to test that your Antivirus program works
libclamav-dev - clam Antivirus library development files
libclamav1 - virus scanner library

is there something specific in recommendation ?

---

### Post by jpeddicord on 2007-06-06
Clamav, if you are paranoid about viruses, is a great option. You shouldn't have to worry much about a firewall; Ubuntu has one on (but hidden) by default.

---

