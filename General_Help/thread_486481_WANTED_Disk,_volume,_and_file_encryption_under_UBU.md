---
title: "WANTED: Disk, volume, and file encryption under UBUNTU"
date: 2007-06-28
forum: General Help
---

### Post by Fenryr on 2007-06-28
OK, I need an encryption prg that works similar to PGPDisk or Truecrypt under XP...I'd like a simple interface, and pretty strong algorhythms, and the ability to 'nest' encrypted files would be nice, too...Any suggestions?

---

### Post by ungluun on 2007-06-28
T r u e C r y p t
Free open-source disk encryption software for Windows Vista/XP/2000 and [SIZE="4"]Linux[/SIZE]

:p?

---

### Post by Fenryr on 2007-06-28
Tried that, can't get it installed...Maybe I'm doin' something wrong here?

---

### Post by Polygon on 2007-06-28
your doing something wrong, as i have it working on my computer...

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

did you try downloading the .DEB from the website? scroll down and select ubuntu 32 or 64 bit

---

### Post by Fenryr on 2007-06-28
Ok, I'm not gettin' the thing to run, and can't even find the manual mentioned in the README file...Is this supposed to be run entirely from the command line? I unpacked the .deb, and while I can FIND it, I can't RUN it, and it won't even tell me if it needs something else...Not exactly 'user friendly' is it? Didn't have any trouble settin' it up to run in Windows...What about PGPdisk? I know PGP was ported long ago...

---

### Post by Polygon on 2007-06-28
what EXACTLY is not working with the deb? post specific errors or else we cant help you!

and yes currently truecrypt for mac/linux is command line. But once you install truecrypt, you can install a GUI for it, called forcefield

try running these instructions, it will install truecrypt and forcefield

> 
wget [http://www.truecrypt.org/downloads/truecrypt-4.3a-ubuntu-7.04-x86.tar.gz](http://www.truecrypt.org/downloads/truecrypt-4.3a-ubuntu-7.04-x86.tar.gz)
wget [http://bockcay.de/stuff/programs/forcefield/forcefield_current_all.deb](http://bockcay.de/stuff/programs/forcefield/forcefield_current_all.deb)

sudo apt-get install python-crack python-pexpect cracklib2

tar xfz truecrypt-4.3a-ubuntu-7.04-x86.tar.gz
dpkg -i truecrypt-4.3a/truecrypt_4.3a-0_i386.deb
rm -rf truecrypt-4.3a truecrypt-4.3a-ubuntu-7.04-x86.tar.gz

sudo dpkg -i forcefield_current_all.deb


then it should be under applications > accessories

---

### Post by Fenryr on 2007-06-28
Ok, on the first two lines. (links?) I get:

 wget [http://www.truecrypt.org/downloads/t....04-x86.tar.gz](http://www.truecrypt.org/downloads/t....04-x86.tar.gz)
--23:03:54--  [http://www.truecrypt.org/downloads/t....04-x86.tar.gz](http://www.truecrypt.org/downloads/t....04-x86.tar.gz)
           => `t....04-x86.tar.gz'
Resolving [www.truecrypt.org](www.truecrypt.org)... 72.36.226.2
Connecting to www.truecrypt.org|72.36.226.2|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:03:54 ERROR 404: Not Found.

 wget [http://bockcay.de/stuff/programs/for...urrent_all.deb](http://bockcay.de/stuff/programs/for...urrent_all.deb)
--23:04:14--  [http://bockcay.de/stuff/programs/for...urrent_all.deb](http://bockcay.de/stuff/programs/for...urrent_all.deb)
           => `for...urrent_all.deb'
Resolving bockcay.de... 83.151.27.222
Connecting to bockcay.de|83.151.27.222|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:04:16 ERROR 404: Not Found.


I recognize a 404, the file's not there...However, I HAVE the file (truecrypt-4.3a-ubuntu-6.10-x86.tar.gz) sitting on my desktop.**

sudo apt-get install python-crack python-pexpect cracklib2
Reading package lists... Done
Building dependency tree... Done
python-crack is already the newest version.
python-pexpect is already the newest version.
cracklib2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ tar xfz truecrypt-4.3a-ubuntu-7.04-x86.tar.gz
tar: truecrypt-4.3a-ubuntu-7.04-x86.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


 dpkg -i truecrypt-4.3a/truecrypt_4.3a-0_i386.deb
dpkg: requested operation requires superuser privilege


 rm -rf truecrypt-4.3a truecrypt-4.3a-ubuntu-7.04-x86.tar.gz

 sudo dpkg -i forcefield_current_all.deb
dpkg: error processing forcefield_current_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 forcefield_current_all.deb


And that's pretty much what I'm stumped at...What is 'superuser privilege', and how do I grant it? What else am I missing?

Thanks in advance...

---

### Post by Qu4k3R on 2007-06-28
I had installed Truecrypt and Forcefield with automatix.

You could use automatix repos, or install automatix.

TrueCrypt only runs on terminal console. Forcefield is the Truecrypt Interface (GUI).

---

### Post by wbdavis on 2007-07-02
Did you just copy and paste from the quote, or did you use the actual links? It truncated the links (you can tell because it put the ... in the middle of the link) Just making sure.

---

### Post by ldgregory on 2008-01-14
> **Fenryr said:**
> 
 wget [http://www.truecrypt.org/downloads/t....04-x86.tar.gz](http://www.truecrypt.org/downloads/t....04-x86.tar.gz)
--23:03:54--  [http://www.truecrypt.org/downloads/t....04-x86.tar.gz](http://www.truecrypt.org/downloads/t....04-x86.tar.gz)
           => `t....04-x86.tar.gz'
Resolving [www.truecrypt.org](www.truecrypt.org)... 72.36.226.2
Connecting to www.truecrypt.org|72.36.226.2|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:03:54 ERROR 404: Not Found.


Just go to [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php) and download the package for the version of Ubuntu you have. Put it in a temp folder like YOUR HOME DIRECTORY/temp.

> **Fenryr said:**
> 
 wget [http://bockcay.de/stuff/programs/for...urrent_all.deb](http://bockcay.de/stuff/programs/for...urrent_all.deb)
--23:04:14--  [http://bockcay.de/stuff/programs/for...urrent_all.deb](http://bockcay.de/stuff/programs/for...urrent_all.deb)
           => `for...urrent_all.deb'
Resolving bockcay.de... 83.151.27.222
Connecting to bockcay.de|83.151.27.222|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:04:16 ERROR 404: Not Found.


Go to [http://bockcay.de/stuff/programs/forcefield/](http://bockcay.de/stuff/programs/forcefield/) and download the latest version. Also stick that in the same temp folder you used for Truecrypt.

> **Fenryr said:**
> 
I recognize a 404, the file's not there...However, I HAVE the file (truecrypt-4.3a-ubuntu-6.10-x86.tar.gz) sitting on my desktop.**


Which is going to be part of your problem as I explain below.

> **Fenryr said:**
> 
sudo apt-get install python-crack python-pexpect cracklib2
Reading package lists... Done
Building dependency tree... Done
python-crack is already the newest version.
python-pexpect is already the newest version.
cracklib2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Everything worked fine here.

> **Fenryr said:**
> 
$ tar xfz truecrypt-4.3a-ubuntu-7.04-x86.tar.gz
tar: truecrypt-4.3a-ubuntu-7.04-x86.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


So the problem here is you had the file truecrypt-4.3a-ubuntu-6.10-x86.tar.gz on your desktop. The instructions he provided are having you unarchive the file with the name truecrypt-4.3a-ubuntu-7.04-x86.tar.gz. You get the error because you specified the wrong filename.

> **Fenryr said:**
> 
 dpkg -i truecrypt-4.3a/truecrypt_4.3a-0_i386.deb
dpkg: requested operation requires superuser privilege


You've got two problems here. One is that you were unsuccessful in unarchiving the file, so the corresponding truecrypt-4.3a subfolder containing the file truecrypt_4.3a-0_i386.deb wasn't created. You didn't get that error though because for you to install an app under Ubuntu, you need superuser privileges. you do that by prefacing the command with the word 'sudo'. It will then ask you for your root (administrator) password. You created this when you installed Ubuntu. Hope you remembered it. It's the same password you enter when you install any software on your machine which you might be more familiar with having gone through System->Administration->Synaptic Package Manager.

So, you're command would have actually been:
sudo dpkg -i truecrypt-4.3a/truecrypt_4.3a-0_i386.deb


> **Fenryr said:**
> 
 rm -rf truecrypt-4.3a truecrypt-4.3a-ubuntu-7.04-x86.tar.gz


Nothing happened here, because you didn't have the right files to delete. That's what rm does, short for remove. You would have been removing the truecrypt archive file you downloaded with wget earlier, as well as the corresponding folder that was created if you'd been able to successfully unarchive it.

> **Fenryr said:**
> 
 sudo dpkg -i forcefield_current_all.deb
dpkg: error processing forcefield_current_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 forcefield_current_all.deb


At least you had the sudo in this command. However, you got a 404 not found when you used wget to try and get this file. Since it didn't exist, you got the error. You didn't have to unarchive this file like you did with the TrueCrypt file because it's a .deb package. When you unarchived the TrueCrypt file it created a directory and stuck the .deb file for TrueCrypt in it.

> **Fenryr said:**
> 
And that's pretty much what I'm stumped at...What is 'superuser privilege', and how do I grant it? What else am I missing?

Thanks in advance...

Well, like I said earlier, manually go to those two sites and download the latest files for your version of Ubuntu. You can get that info by clicking System->About Ubuntu.

Once you have those files, use the commands provided to unarchive and install, but replace the filenames with the correct ones for the files you downloaded. You should receive no errors at any point during this. If you do, stop and look at the command you just tried to execute and verify the use of sudo and that the filenames are correct.

---

