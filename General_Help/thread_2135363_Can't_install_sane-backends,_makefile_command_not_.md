---
title: "Can't install sane-backends, makefile: command not found."
date: 2013-04-14
forum: General Help
---

### Post by Luxx on 2013-04-14
I thought I posted this hours ago but I can't find it now.

I am trying to get an all-in-one printer/scanner to work, Epson Artisan 730. The printer was automatically detected when it was plugged in and printing a test page worked fine. I can't get the scanner to work. Xsane is telling me, "no devices available." 

sane-find-scanner gives me:
found USB scanner (vendor=0x04b8 [EPSON], product=0x087b [EPSON Artisan 730 Series]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

scanimage -L gives me:
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

I discovered that sane-backends was not installed and can't find it in Software Center, tried downloading it from launchpad, but couldn't get the file to cooperate.

This is where I am right now---------------------------

I went to [https://alioth.debian.org/frs/?group_id=30186](https://alioth.debian.org/frs/?group_id=30186) and read the README file, downloaded the 3 parts and md5 to Downloads folder -
sane-backends-1.0.23.tar.gz.1
sane-backends-1.0.23.tar.gz.2
sane-backends-1.0.23.tar.gz.3
sane-backends-1.0.23.tar.gz.md5

command:
cd Downloads
cat sane-backends-1.0.23.tar.gz.[1-3] > sane-backends-1.0.23.tar.gz

Then checked the file -

command:
md5sum -c sane-backends-1.0.23.tar.gz.md5

Then ran:
sudo tar zxvf sane-backends-1.0.23.tar.gz

cd sane-backends-1.0.23
sudo ./configure

	I got the error 
	./configure: line 2221: config.log: Permission denied

Looking at the permissions of the folder named "sane-backends-1.0.23" in Downloads I found it belonged to group/user 500 and it was locked.

I ran

gksudo nautilus

I navigated to file system> home> user> Downloads> sane-backends-1.0.23, right-clicked and selected Properties, Permissions. Changed Owner to my username and Group to users and changed Folder acces to Create and delete files.

I tried running ./configure again but permission was denied so I ran:
sudo ./configure           
make
makefile

But then makefile also gave me problems. I got the error:
makefile: command not found.
I don't know how to get any further with this. Please help.


Edit: I found that some of the files and folders in the folder still belonged to user/group 500/500, so I changed the permissions on those. I know there is a more efficient way of doing this from termianl, but couldn't remember the syntax, and looking it up didn't really help since I couldn't find what it looked like in real life.

Also, thinking I may have gotten a bit lost with the commands I tried it again using "sudo make install" which seemed successful in terminal, but there is no change.

---

