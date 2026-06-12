---
title: "Problem with Adept manager"
date: 2007-12-17
forum: General Help
---

### Post by mastergunner on 2007-12-17
I just installed Kubuntu 7.10 on my new computer and when I have tried using Adept Manager to get some files I get the following:

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 

Can someone help with this. Thanks.

---

### Post by ajmorris on 2007-12-17
hi,
Could you try getting packages with Synaptic please? (system > administration > Synaptic Package Manager)  Also, once in synaptic, press the re-fresh button to update the software in the repositories, if you can download with synaptic after doing this but not adept, please let me know :)

---

### Post by mastergunner on 2007-12-20
I do not have synaptic in Kubuntu. Is there a command sort of like below that can be used:

sudo apt #### $$ sudo apt ####

---

### Post by oscarsfriend on 2007-12-20
I was getting a similar message after messing around today updating to the latest MythTV.  The reason was that whatever command adept runs to install stuff (apt-get I presume) wanted conformation input from the keyboard.  It wanted to know whether to replace a file with a newer version or not -- and every time I tried to install it would give the same error. You can see the output of the command from adept, if you click the "Show Details" button to the right of the progress bar.  To get round this I ran "sudo apt-get install gnuchess" from the terminal, then I was able to input from the keyboard and fix the problem.  Then I removed gnuchess to confirm.  (I picked gnuchess because I didn't know what command to run, and it was small and didn't have any dependencies that I didn't already have installed.  There is probably a better way to do this. ;) )

EDIT: BTW, it was actually installing all the other stuff when it gave the error.

---

### Post by PmDematagoda on 2007-12-20
Do:-

```
sudo apt-get update
```

That will reload your sources.

---

### Post by oscarsfriend on 2007-12-20
Worth a try.  But it didn't work with the problem I was having (which is possibly similar to OP's).  I actually had to install something.

---

### Post by mastergunner on 2007-12-20
I have packages that arent configured. They are locking up everything. How do I get them to configure?

---

### Post by PmDematagoda on 2007-12-20
```
sudo dpkg --configure -a
```

---

### Post by mastergunner on 2007-12-20
Does not work. This is what I get:
rad@Coop:~$ sudo dpkg --configure -a
Setting up gconf2-common (2.20.0-0ubuntu1) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing gconf2-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on gconf2-common (>= 2.20); however:
  Package gconf2-common is not configured yet.
 gconf2 depends on gconf2-common (<< 2.21); however:
  Package gconf2-common is not configured yet.
dpkg: error processing gconf2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgconf2-4:
 libgconf2-4 depends on gconf2-common (>= 2.20); however:
  Package gconf2-common is not configured yet.
 libgconf2-4 depends on gconf2-common (<< 2.21); however:
  Package gconf2-common is not configured yet.
dpkg: error processing libgconf2-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgksu2-0:
 libgksu2-0 depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 libgksu2-0 depends on gconf2 (>= 2.10.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgksu2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on libgconf2-4 (>= 2.13.5); however:
  Package libgconf2-4 is not configured yet.
 gksu depends on libgksu2-0 (>= 1.9.6); however:
  Package libgksu2-0 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on gksu (>= 2.0.0-1ubuntu3); however:
  Package gksu is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2-common
 gconf2
 libgconf2-4
 libgksu2-0
 gksu
 gdebi
 What is going on?

---

### Post by PmDematagoda on 2007-12-20
Open Adept, once it is open uncheck the checkboxes except for the Broken packages filter. Then when you see the packages, remove them all, by the way, these are the ones that should be removed:-

```
gconf2-common
gconf2
libgconf2-4
libgksu2-0
gksu
gdebi
```

This should not be much of a problem, but it may mean that other GNOME applications may also be removed, so make some steps to backup those data on KDE applications if you can.

---

### Post by mastergunner on 2007-12-21
I have done that BUT there is a script that I use that uses these files. WHen I try to run it I have the same problem. WHat gives? By the way the script is Ubuntzilla so I can get the latest Firefox and Thunderbird.

---

