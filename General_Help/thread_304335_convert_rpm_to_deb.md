---
title: "convert rpm to deb"
date: 2006-11-21
forum: General Help
---

### Post by logos34 on 2006-11-21
I'd like to run AVG antivirus on my 6.10 desktop, but I can't seem to convert .rpm to debian.  I'm using the HOW TO below but it doesn't work for me.  I have alien and all the dependencies (I think).  Can't even get started.  Even if I don't really need av I'd still like to know about conversion.  Seems like a very useful tool.

[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

---

### Post by strabes on 2006-11-21
sudo apt-get install alien
sudo alien -i /path/to/file.rpm

there's no GUI for alien. you can also see my blog post [here](http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/) about this.

---

### Post by Demon012 on 2006-11-21
To convert a rpm to a deb file with alien you should only need to do a 
> sudo alien <insert rpm file name here>

For example for your AVG RPM it could be:

> sudo alien avg-10.0.1.rpm

After you run that command alien should then do its magic and create a .deb file in the same directory for you to use.

Hope this helps,

Demon012

---

### Post by logos34 on 2006-11-21
> **Demon012 said:**
> To convert a rpm to a deb file with alien you should only need to do a 


For example for your AVG RPM it could be:



After you run that command alien should then do its magic and create a .deb file in the same directory for you to use.

Hope this helps,

Demon012


I downloaded the free avg71flm-r30-a0791.i386.rpm package. Do I need the registration code beforehand?

---

### Post by logos34 on 2006-11-21
> **logos34 said:**
> I downloaded the free avg71flm-r30-a0791.i386.rpm package. Do I need the registration code beforehand?

UPDATE: Here is what I get:

zazen@zazen-desktop:~$ cd Desktop
zazen@zazen-desktop:~/Desktop$ ls
avg71flm-r30-a0791.i386.rpm  dazuko-2.3.1  link to Favorites
zazen@zazen-desktop:~/Desktop$ rpm -qip --scripts avg71flm-r30-a0791.i386.rpm
zazen@zazen-desktop:~/Desktop$ sudo alien -i avg71flm-r30-a0791.i386.rpm
Password:
argument is not an RPM package
argument is not an RPM package
cpio: premature end of archive
chmod: invalid option -- /
Try `chmod --help' for more information.
mkdir: invalid option -- /
Try `mkdir --help' for more information.
-/debian/changelog: No such file or directory at /usr/share/perl5/Alien/Package/Deb.pm line 330.
find: invalid predicate `-'
zazen@zazen-desktop:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
The following packages were automatically installed and are no longer required:
  python-pyogg python-pyvorbis python-cddb python-eyed3 libsdl-image1.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zazen@zazen-desktop:~$ sudo apt-get autoremove python-pyogg python-pyvorbis python-cddb python-eyed3 libsdl-image1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-pyogg python-pyvorbis python-cddb python-eyed3 libsdl-image1.2
The following packages will be REMOVED:
  libsdl-image1.2 python-cddb python-eyed3 python-pyogg python-pyvorbis
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 905kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 134844 files and directories currently installed.)
Removing libsdl-image1.2 ...
Removing python-cddb ...
Removing python-eyed3 ...
Removing python-pyvorbis ...
Removing python-pyogg ...
zazen@zazen-desktop:~$ sudo alien -i avg71flm-r30-a0791.i386.rpm
Warning: Skipping conversion of scripts in package avg71flm: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
zazen@zazen-desktop:~$ sudo alien -i --scripts avg71flm-r30-a0791.i386.rpm
zazen@zazen-desktop:~$ 


So what now?

---

### Post by nik4221 on 2006-11-21
try:

Convert to .deb file:
$ sudo alien --scripts avg71flm-r30-a0791.i386.rpm

Install .deb file:
$ sudo dpkg -i <.deb file generated>

---

### Post by DJ_Peng on 2006-11-21
> **logos34 said:**
> I downloaded the free avg71flm-r30-a0791.i386.rpm package. Do I need the registration code beforehand?

I'd definitely grab it before you convert it to a .deb. I installed AVG last night after seeing the post about [Windows not being Desktop-ready](http://ubuntuforums.org/showthread.php?t=303498) (I need to get SAM Broadcaster running under Wine and I want to make sure I don't get any buglets as I do) and I forgot to paste my reg code to the text editor before I converted it. Talk about a pain in the *** to get it back.

One thing you'll want to do is to use the file name for the file you download rather than the one in the HOWTO. I know the file I downloaded had a slightly different filename.

---

### Post by logos34 on 2006-11-21
It's installed after all. It showed up in Applications>>Accessories panel.  I was expedting a lot of output.  But where is the .deb file?  Opened it ("AVG for Linux Workstation") and got the updates, and then ran a full sys scan.  Scheduled tests at restart.  (1 infected file - probably an error).  Here's where it is:

zazen@zazen-desktop:~$ whereis avg
avg: /etc/avg.conf
zazen@zazen-desktop:~$ whereis avgscan
avgscan: /usr/bin/avgscan /usr/X11R6/bin/avgscan /usr/bin/X11/avgscan
zazen@zazen-desktop:~$ 

The configuration file and testreports are in /home/zazen/.avg.


Did it convert or what?  And do I need the keep the avg71flm-r30-a0791.i386.rpm folder, or can I chuck it:) ?

---

### Post by noremacyug on 2008-03-12
i'm having an issue with converting a rpm to deb.  i followed the commands and it says it generated a .deb file, however i don't see it anywhere.  here's a pic of what i got.

edit - found the answer to my ordeal.  it's in the home folder, i'm an idiot.

---

### Post by rohan.modi on 2008-05-02
thnx strabes it was really helpful and all of it went out smoothly 
and by the way the deb file will be available in the home folder
:)

---

