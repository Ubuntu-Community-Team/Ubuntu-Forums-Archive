---
title: "Linux version of WordPerfect Office"
date: 2013-10-28
forum: General Help
---

### Post by cecilieaux on 2013-10-28
I purchased the CD from ebay, but it says there are libraries missing, etc. that I don't quite understand. I have a lot of documents in WP format and WP has a search and replace that Libre Office can't match.

Does anyone know how to install Corel WP Office 8 for Linux in Ubuntu 12.04 LTS?

---

### Post by Mark Phelps on 2013-10-28
Sorry to tell you this, but you may not be able to get that working.  WordPerfect for Linux was discontinued in 2005.

The faq linked has answers to many common questions:  [http://linuxmafia.com/wpfaq/]("http://linuxmafia.com/wpfaq/")

---

### Post by SeijiSensei on 2013-10-28
I'd try an older Linux distribution like RedHat/CentOS 3 or 4.  Here's a [link to the CentOS 4 downloadable ISOs]("http://mirror.hmc.edu/centos/4/isos/").  You might consider installing [VirtualBox](http://www.virtualbox.org/) on your machine (following [these instructions](https://www.virtualbox.org/wiki/Linux_Downloads)), then creating a CentOS4 virtual machine to run WordPerfect in.

---

### Post by sgage on 2013-10-28
WP Office 8 for Linux didn't really work all that great in its heyday. I have a copy of it around here somewhere. There is an 'Alternate Find/Replace' extension for LibreOffice that might make it quite adequate for your needs. 

                                [Alternative dialog Find & Replace for Writer (AltSearch)]("http://extensions.openoffice.org/en/project/alternative-dialog-find-replace-writer-altsearch")

---

### Post by cecilieaux on 2013-10-28
> **SeijiSensei said:**
> I'd try an older Linux distribution like RedHat/CentOS 3 or 4.  Here's a [link to the CentOS 4 downloadable ISOs]("http://mirror.hmc.edu/centos/4/isos/").  You might consider installing [VirtualBox](http://www.virtualbox.org/) on your machine (following [these instructions](https://www.virtualbox.org/wiki/Linux_Downloads)), then creating a CentOS4 virtual machine to run WordPerfect in.

This sounds like major surgery to me. But it might be worth exploring. Of course, Virtualbox doesn't seem to work right for me. I get the error:

> Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

---

### Post by cecilieaux on 2013-10-28
> **sgage said:**
> WP Office 8 for Linux didn't really work all that great in its heyday. I have a copy of it around here somewhere. There is an 'Alternate Find/Replace' extension for LibreOffice that might make it quite adequate for your needs. 

                                [Alternative dialog Find & Replace for Writer (AltSearch)]("http://extensions.openoffice.org/en/project/alternative-dialog-find-replace-writer-altsearch")

Open/Libre Office find and replace, even the downloadable alternates simply cannot find and replace line-break returns.

---

### Post by PeterRJG on 2013-10-29
There are a lot of online tools that can do that. [http://www.textfixer.com/tools/remove-line-breaks.php](http://www.textfixer.com/tools/remove-line-breaks.php) is one that I use frequently.

---

### Post by SeijiSensei on 2013-10-29
> **cecilieaux said:**
> This sounds like major surgery to me. But it might be worth exploring. Of course, Virtualbox doesn't seem to work right for me. I get the error:

The VirtualBox installer needs to compile a kernel module from source each time the kernel is upgraded.  If your system doesn't have development tools, you'll get that error.  Take the approach described on the VirtualBox site [I linked to above]("https://www.virtualbox.org/wiki/Linux_Downloads") and follow the directions for "Debian-based" distributions to add the Oracle repository. Then when you install VirtualBox it will pull in the needed dependencies for you like the gcc compiler and the dkms module compilation system.

---

### Post by bapoumba on 2013-10-29
> **cecilieaux said:**
> Open/Libre Office find and replace, even the downloadable alternates simply cannot find and replace line-break returns.

[https://help.libreoffice.org/Common/List_of_Regular_Expressions](https://help.libreoffice.org/Common/List_of_Regular_Expressions)

Juste tried it, working :)

Edit : I should probably say what. in Search & Replace, tick regexp and search for \n (will search for line break) and replace with \n (will replace with paragraph break).

---

### Post by neu5eeCh on 2013-10-30
FYI: I love WordPerfect. I also bought WP8 for Linux just to see if I could get it working. Having said that, I currently use WP X3 in VirtualBox running on WindowsPro 2000. It works flawlessly. Just beautiful. Quick and responsive. Better than Wine could ever do.

And here's the kicker:

Running in VB, it uses less memory than LibreOffice running natively!!! :shock:

---

### Post by neu5eeCh on 2013-10-30
> **cecilieaux said:**
> Does anyone know how to install Corel WP Office 8 for Linux in Ubuntu 12.04 LTS?

Another thought: WP8 *can* run on 12.04. As I understand the process, you have to first install WP for Linux on Ubuntu 8.04.4 first. 

[http://www.wpuniverse.com/vb/showthread.php?31659-WordPerfect-8.0-for-Linux-Installation-steps-on-Ubuntu-8.04.4-LTS](http://www.wpuniverse.com/vb/showthread.php?31659-WordPerfect-8.0-for-Linux-Installation-steps-on-Ubuntu-8.04.4-LTS)

Or 8.1 on 10.04

[http://www.wpuniverse.com/vb/showthread.php?31688-WordPerfect-8.1-for-Linux-Installation-steps-for-Ubuntu-10.04](http://www.wpuniverse.com/vb/showthread.php?31688-WordPerfect-8.1-for-Linux-Installation-steps-for-Ubuntu-10.04)

You then have to copy the relevant directories into 12.04. I haven't actually done any of this, but it **is** possible. There's a youtube video of someone running WordPerfect 8 on 12.04:

[http://www.youtube.com/watch?v=TnEbaaZEEEE](http://www.youtube.com/watch?v=TnEbaaZEEEE)

Why the poster didn't detail how he/she did it is a mystery. Canonical is developing a new packaging system, however, and I wonder if it would be possible for someone to "package" a WordPerfect for Linux installation -- sans license to keep it legal?

---

### Post by peter53 on 2013-11-29
If you have WP 2000 Office for Linux, including WP 9, it will not run on any version of Ubuntu. You need a distro from 2002, such as Slackware 8.2. This is because it requires libc6 at 2.2.* or earlier.

If you have WP 8.0 for Linux, you could install it in Ubuntu 8.04 or earlier and then upgrade Ubuntu to a later version.

If you have WP 8.1 for Linux, you can install it in any Ubuntu (including the current version).

In any case some effort will be necessary.

See my own website: [http://www.xwp8users.com](http://www.xwp8users.com) 

Best wishes,
Peter Stone

---

### Post by peter53 on 2013-11-30
Correction to my last message:

I should have referred to Slackware 8.1, not 8.2.

---

