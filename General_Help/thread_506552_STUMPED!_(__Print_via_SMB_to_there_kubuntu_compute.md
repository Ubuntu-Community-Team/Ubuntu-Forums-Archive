---
title: "STUMPED! :(  Print via SMB to there kubuntu computer."
date: 2007-07-21
forum: General Help
---

### Post by buccinator on 2007-07-21
System Stats:  Feisty Fawn Kubuntu 

I've been working on this problem for like four hours.  It has really stumped me.  Usually I can just find a solution by browsing the internet, yet this one kills me.

To make this easier to explain, let me break it down into a flow chart:

I want this...

[Ubuntu Computer 1] ---> [Drivers] ---> [Samba] ---> [Ubuntu Computer 2] ---> [Cups] ---> [HP LaserJet 1020]

I can get the Laser Jet 1020 to work on the *Ubuntu Computer 2*, yet I cannot get it print using my Samba share remotely on *Ubuntu Computer 1*.  Everything seems like it was done correctly, and their is not indication as to why it is not printing.  There are NO errors when I try to print a test page, using the System Settings -> Administration -> Printing.  

Thus, I am assuming that something has gone funky with the drivers that I am using.  I used various instructions to get the correct drivers to work (since the pre-installed HP LaserJet 1020 drivers don't work).

Also, I made sure that I edited the smb config file appropriately on the Ubuntu Computer 2, and it gets detected absolutely fine (when using the System Settings -> Administration -> Printing).

So, personally I think that this would have worked fine with 90% of the other printers out there, yet the problem is with the HP 1020 itself, in that no one has ever tried this one before by accessing it remotely.

Yes... I've tried it by just using cups by itself, but that was even more of a nightmare.  

PLEASE HELP!!!! :-({|=

Thanks.

---

### Post by buccinator on 2007-07-22
I'm sorry if I'm being impatient.  Does anybody have any suggestions?  Moreover, am I even in the right discussion area for this type of problem?

Thanks!

---

### Post by stmiller on 2007-07-22
Samba printing is a mess, b/c you have to create a user on the machine with the printer, etc. bleh. So don't use samba.

Just replace your /etc/cups/cupsd.conf file with this one:

```
# /etc/cups/cupsd.conf
# Simple CUPS configuration file for a print server
# which serves printers within a private local area network.
# - There is no need for additional security within the print server, ie only authorized
# people can access the machine.

# This setup also allows access to the CUPS "Administrative tasks" system
# via your web browser to http://localhost:631
# File based on Ubuntu 5.10 (Breezy Badger) (Linux version 2.6.12-10-386)
# Server Directives are explained in http://localhost:631/sam.html

# 25/04/2006
# DavidTangye@netscape.net

ConfigFilePerm 0600
LogLevel info
Printcap /var/run/cups/printcap
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
BrowseAddress 10.0.0.0/8
BrowseAddress 172.16.0.0/12
BrowseAddress 192.168.0.0/16

<Location />
AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 10.0.0.0/8
Allow From 172.16.0.0/12
Allow From 192.168.0.0/16
</Location>

<Location /jobs>
AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 10.0.0.0/8
Allow From 172.16.0.0/12
Allow From 192.168.0.0/16
</Location>

<Location /printers>
AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 10.0.0.0/8
Allow From 172.16.0.0/12
Allow From 192.168.0.0/16
</Location>

<Location /admin>
AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 10.0.0.0/8
Allow From 172.16.0.0/12
Allow From 192.168.0.0/16
</Location>
```


And restart with
```

sudo /etc/init.d/cupsys restart
```

---

### Post by buccinator on 2007-07-22
Thanks for your help, stmiller.  I tried what you suggested, yet the jobs never transfer for some reason.  The job get's held up and never is sent to the other machine. :(

---

### Post by tomika on 2007-07-22
I am also having NO LUCK with the Cups network printing from UBUNTU Feisty Fawn 7.04 on AMD 64 bit and on another 32 bit machine all in the same network.

The network printers show up fine and are "Ready". When I try to print a test page, it says PRINTING but nothing comes through.

The strange thing is that on this multi boot  computer I also have SuSE 10.1 and Xandros 4.0 Pro and they both print fine. In fact with Xandros, nothing needed to be done.

I will try looking at the cups file to see if the suggestion by stmiller works.

BTW, I can exchange files between all the different computers but can't print.
I had a similar problem with Fedora Core 5 and 6 so I ditched them.

Ubuntu 7.04 seems to do almost everything I want but fails at network printing. I suspect it is a CUPS issue, but wonder why Xandros and SuSE CAN DO IT.

Also, Feisty is on MSWORK but the printer is on a different NAME server.

I have been working on this quite a lot of hours and hope someone can see the problem/solution clearer.

Thanks

---

### Post by buccinator on 2007-07-23
I SOLVED IT!!!!!

It was a very sneaky problem.  By default (k)ubuntu will firewall other users from using the cups server via various gui based applications.   I went to my Ubuntu Computer #2 and found that one of the printing tools had a default option of disallowing all users EXCEPT the local user.  I simply unchecked this option and made it so that everyone on the LAN could use it.  I didn't even have to edit any files.  Stupid printing programs...  I suggest that everyone delete the little helper programs... because they cause more of a headache than help, as this one in particular had it's own security measures separated from cups.

---

