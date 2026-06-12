---
title: "problems with hackers"
date: 2007-08-30
forum: General Help
---

### Post by rickusr on 2007-08-30
I am a new user to Ubuntu and I tried it as a way of dealing with a computer hacker. They quickly started to hack our machine in Ubuntu. I don't know if any of you can help. I can compile a bunch of information about the hacking and maybe that can assist the community in creating a better distro that is harder to hack. I personally hate any hacker ( except white hat ) or more truthfully, vandallism by these people.
  I cannot always participate due to being locked out of forums and other actions by this hacker but I will attempt to keep at it and give as much to the community as possible. Bear with me. 
  First is the matter of root. We don't have actual root. I did a new install and then Sudo -l and got root with a list of files. These listed the permissions and included 13 files. the hacker came back and made a change and I could not access the root file since. Now I sudo and it tells me that  user " " has access to the followning files 
ALL ( ALL ). 
  If I go to the file manager and type   /root    I get a window with no files listed. If I go to home I get home and desktop and examples. Is there a file named  /standard   that is part of a install? Do I have a stripped version of Ubuntu Feisty Fawn? 
  I have more information to provide but I will bring more up in the next few weeks.

---

### Post by rickusr on 2007-08-30
I have a problems with hackers. They have stripped a number of files and altered a number of files. I did sudo -l and got a listing of /root files. I can't get that listing anymore. I go to /root and it shows an empty window. I go to my home folder and I expect to see /standard/examples and I don't get the standard file. I only get the home/name/desktop/examples. Is my OS stripped?
  I have more information on other aspects of this hacking and I will try to offer them as much as I can until the hacker locks me out of this forum. 
Constant, chronic problems in any and every OS. I got a stalker on my hands.  Maybe more later.  Thanks

---

### Post by cookies on 2007-08-30
> **rickusr said:**
> I have a problems with hackers. They have stripped a number of files and altered a number of files. I did sudo -l and got a listing of /root files. I can't get that listing anymore. I go to /root and it shows an empty window. I go to my home folder and I expect to see /standard/examples and I don't get the standard file. I only get the home/name/desktop/examples. Is my OS stripped?
  I have more information on other aspects of this hacking and I will try to offer them as much as I can until the hacker locks me out of this forum. 
Constant, chronic problems in any and every OS. I got a stalker on my hands.  Maybe more later.  Thanks

/root IS empty by default. (It has some hidden files)

 /standard/examples is now just Examples. Relax, you're fine.

---

### Post by rickusr on 2007-08-31
I did discribe a few things with this hacker situation and I will discribe more. 
  This computer is not connected to the internet. I did install a version of Ubuntu on it and it is hacked but that is the case with whatever OS, I install. I do not know the hacker personally. They were hired to obstuct my worker advocacy and so I have been hacked for years. This is nothing new. I don't want to get into this but only to explain what the computer is doing and maybe learn from that. I am not any kind of computer expert but I will do my best to explain what the machine does and does not.
  I do not have a properly functioning shell. I do not have a C shell or tcsh or a C compiler. When I attempt to do the following command I get this result;

     open /etc/
Bad file name or command

or sometimes it tells me that there is a bad file discriptor

  If I do get a file to come up and I highlight it and then hit enter to bring it up the shell ignores the enter and no file will come up.
  Certain files are empty. These include all /sys/   files. None will come up or they will deny me access. Many files in the /etc/ are encrypted or the permissions have benn changed. You cannot open them because the encription app. has been deleted so there is no way to decrypt the file so it cannot open. These include /shadow  or /shadow files and /insmod/  files. I will provide a complete list of these files as time progresses along with as much information as possible over this hacked computer.
   more later

---

### Post by FuturePilot on 2007-08-31
open /etc is not a valid command, that's why it's giving you errors. If you want to view /etc you should try ```
nautilus /etc
```
You can't open certain files because you do not have root privileges, or sometimes you need root privileges to edit a file. If you feel like you have a stalking hacker, perhaps you need to call the authorities.

---

### Post by asmoore82 on 2007-08-31
please observe the proper definition of "hacker" ...
the people who give you freedom of choice in Operating Systems are hackers.

the make-believe person who is "hacking into" your systems would be a "cracker."

other than that, I don't know what else to say ...

---

### Post by raijinsetsu on 2007-08-31
Pretty sure a hacker is anyone who takes apart someone else's program and puts it back together, either to learn how it works or to change it(for better or for worse). A cracker, is someone who breaks security systems....

As for the problem at hand, it sounds like everything is fine and that files are just in different places than you are used to. If your computer is not on the net, then there is no chance of someone hacking or cracking your computer unless they get into your house/office/...

---

### Post by bodhi.zazen on 2007-08-31
> **rickusr said:**
> I did discribe a few things with this hacker situation and I will discribe more. 
  This computer is not connected to the internet....

<clip>



Well if you are not connected to the internet, then the only way you can be "hacked" is via physical access to your box.

Physical access = bad news. The only way to be secure is to limit physical access. The next best thing is encryption.

[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)
	[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

	[http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)

---

### Post by kidders on 2007-08-31
Hi there,

Your post is very hard to follow. What gives you the impression your Ubuntu has been hacked into?

> **rickusr said:**
> I personally hate any hackerThat's a curious statement to make if you're looking for help on a Linux forum!

---

### Post by bapoumba on 2007-08-31
Threads merged.

---

### Post by glotz on 2007-08-31
[http://www.introversion.co.uk/uplink/](http://www.introversion.co.uk/uplink/) :D

On a more serious note, have you considered a hardware failure?

---

### Post by rsambuca on 2007-08-31
Dudes!  Look at the OP's post count.  Can you say "Troll"?

---

### Post by Lord Illidan on 2007-08-31
If your computer is not connected to the net, there is no way a remote hacker can access your pc..he needs physical access.

---

### Post by por100pre1 on 2007-08-31
Is your computer a desktop? If so use a laptop, and carry it with you wherever you go, even to the restroom.

---

### Post by strabes on 2007-09-01
This guy is a troll.

---

### Post by rickusr on 2007-09-01
To the forum;
  Thanks for advice and your feedback. Now I do admit that I am not the best with Linux. I will however continue with what I have on my computer. 
  I did use media from a linux magazine and after the install I did contact them and told them of my situation and they took the media and checked it and reported to me that the media was fine. With this in mind lets go forward with what I found. 

I have a bunch of files that are not able to be accessed. These include a number of /dev and /etc files. These all have some kind of encryption and the encryption application has been deleted or hidden. These files are in the /dev  or /etc directories and these are encrypted.
  When you click on these files you get an error message.

Error:  Cannot open /etc/apt/trustdb.grp: No application suitable for automatic installation is available for handling this kind of file.

These are the /etc files that display a red X on its icon in the filemanager window.
/etc/apt/secring.gpg
/etc/apt/trustdb.gpg
/etc/at.deny
/etc/group  ( there are two different files for /etc/group )
/etc/gshadow ( there are two different files for /etc/gshadow )
/etc/passwd
/etc/shadow ( there are two different files for /etc/shadow )
etc/sudoers

These are the /dev files that display a red X on its icon in the filemanager window.
/dev/acpi
/dev/console
/dev/core
/dev/fuse
/dev/hpet
/dev/initctl
/dev/kmem
/dev/kmsg
/dev/loop0
/dev/lp0
/dev/mem
/dev/oldmemory
/dev/parport0
/dev/port
/dev/ppp
/dev/psaux
/dev/ram
/dev/ram ( 1-15 )
/dev/scd0
/dev/sda
/dev/sda ( 1-7 )
/dev/sg0
/dev/snapshot
/dev/stderr
/dev/stdout
/dev/usbdev1.1_ep00
/dev/usbdev1.1_ep81
/dev/usbdev2.1_ep00
/dev/usbdev2.2_ep00
/dev/usbdev2.3_ep00
/dev/usbdev2.3_ep81
/dev/usbdev2.3_ep83
/dev/usbdev2.4_ep00
/dev/usbdev2.4_ep05
/dev/usbdev2.4_ep81
/dev/usbdev3.1_ep00
/dev/usbdev3.1_ep81
/dev/usbdev4.1_ep00
/dev/usbdev4.1_ep81
/dev/usblp0
/dev/vcs
/dev/vcs ( 1-8 )
/dev/vcsa
/dev/vcsa ( 1-8 )
/dev/vesa ( 1-8 )
/dev/watchdog

  Click on the file system icon and you get a group of files. Only one of these has a red X on it and that is /lost+found. I click on this file and get the following error message;

This folder contents could not be displayed.
You do not have the permissions necessary to view the contents of " lost+found ".   OK

  I try to sudo on /lost+found and get this message on the terminal.

Couldn't get a file discriptor referring to the console
Couldn't get a file discriptor referring to the console

I go to the /bin  files and there is one file with a red X and that is /bin/ismod-modutils
I click on this file and get this error message box.
Error message
The link " Ismod-modutils is broken. Move it to trash?
Cancel                             Move to trash

  This is more of what I am discovering with this install. I do want to point out that I did wipe the hard drive and then did a new install with the media from that magazine. This is the results from that brand new install. At no time was the machine on the internet. These are the files that I got after that install. 
  I am only presenting what I have as part of this install. I am offering information on this system after this new install. At some point maybe these files can be opened and then the real truth of what has been altered can be answered, not just for me but for this community.
more later

---

### Post by rickusr on 2007-09-01
o the forum;
  Thanks for advice and your feedback. Now I do admit that I am not the best with Linux. I will however continue with what I have on my computer. 
  I did use media from a linux magazine and after the install I did contact them and told them of my situation and they took the media and checked it and reported to me that the media was fine. With this in mind lets go forward with what I found. 

I have a bunch of files that are not able to be accessed. These include a number of /dev and /etc files. These all have some kind of encryption and the encryption application has been deleted or hidden. These files are in the /dev  or /etc directories and these are encrypted.
  When you click on these files you get an error message.

Error:  Cannot open /etc/apt/trustdb.grp: No application suitable for automatic installation is available for handling this kind of file.

These are the /etc files that display a red X on its icon in the filemanager window.
/etc/apt/secring.gpg
/etc/apt/trustdb.gpg
/etc/at.deny
/etc/group  ( there are two different files for /etc/group )
/etc/gshadow ( there are two different files for /etc/gshadow )
/etc/passwd
/etc/shadow ( there are two different files for /etc/shadow )
etc/sudoers

These are the /dev files that display a red X on its icon in the filemanager window.
/dev/acpi
/dev/console
/dev/core
/dev/fuse
/dev/hpet
/dev/initctl
/dev/kmem
/dev/kmsg
/dev/loop0
/dev/lp0
/dev/mem
/dev/oldmemory
/dev/parport0
/dev/port
/dev/ppp
/dev/psaux
/dev/ram
/dev/ram ( 1-15 )
/dev/scd0
/dev/sda
/dev/sda ( 1-7 )
/dev/sg0
/dev/snapshot
/dev/stderr
/dev/stdout
/dev/usbdev1.1_ep00
/dev/usbdev1.1_ep81
/dev/usbdev2.1_ep00
/dev/usbdev2.2_ep00
/dev/usbdev2.3_ep00
/dev/usbdev2.3_ep81
/dev/usbdev2.3_ep83
/dev/usbdev2.4_ep00
/dev/usbdev2.4_ep05
/dev/usbdev2.4_ep81
/dev/usbdev3.1_ep00
/dev/usbdev3.1_ep81
/dev/usbdev4.1_ep00
/dev/usbdev4.1_ep81
/dev/usblp0
/dev/vcs
/dev/vcs ( 1-8 )
/dev/vcsa
/dev/vcsa ( 1-8 )
/dev/vesa ( 1-8 )
/dev/watchdog

  Click on the file system icon and you get a group of files. Only one of these has a red X on it and that is /lost+found. I click on this file and get the following error message;

This folder contents could not be displayed.
You do not have the permissions necessary to view the contents of " lost+found ".   OK

  I try to sudo on /lost+found and get this message on the terminal.

Couldn't get a file discriptor referring to the console
Couldn't get a file discriptor referring to the console

I go to the /bin  files and there is one file with a red X and that is /bin/ismod-modutils
I click on this file and get this error message box.
Error message
The link " Ismod-modutils is broken. Move it to trash?
Cancel                             Move to trash

  This is more of what I am discovering with this install. I do want to point out that I did wipe the hard drive and then did a new install with the media from that magazine. This is the results from that brand new install. At no time was the machine on the internet. These are the files that I got after that install. 
  I am only presenting what I have as part of this install. I am offering information on this system after this new install. At some point maybe these files can be opened and then the real truth of what has been altered can be answered, not just for me but for this community.
more later

---

### Post by rsambuca on 2007-09-01
rickusr - OK, I apologize for referring to you as a troll.  Now, moving on, I think you are having problems coming from windows due to the fact that with ubuntu, you do not run as an "administrator" like most people do in windows.  This is due to security issues.  If someone is able to hack into your system, they will receive the permissions that you have.  Thus, if you have limited permissions while running ubuntu, then the hacker would also have limited permissions.

A few notes of caution.  I don't think you should be messing around with "sudo" in the terminal unless you are trying to do very specific things as you can really start to damage your rig if you do.

---

### Post by Hendrixski on 2007-09-01
> **rsambuca said:**
> rickusr - OK, I apologize for referring to you as a troll.  Now, moving on, I think you are having problems coming from windows due to the fact that with ubuntu, you do not run as an "administrator" like most people do in windows.  This is due to security issues.  If someone is able to hack into your system, they will receive the permissions that you have.  Thus, if you have limited permissions while running ubuntu, then the hacker would also have limited permissions.

A few notes of caution.  I don't think you should be messing around with "sudo" in the terminal unless you are trying to do very specific things as you can really start to damage your rig if you do.

Hey Rickusr.  welcome to the Ubuntu Community.  I remember when I first tried Linux there were a lot of things that seemed very strange to me as well, but when I found out they were normal it made a lot of sense to me.  Now I wonder why Windows does it differently.

For example file permissions, as quoted above.  In Windows you run with the priveledges to do EVERYTHING on your computer.  When a hacker breaks into Windows they just pretend to be you, and thus they can edit anything.  With Ubuntu, if the hacker breaks into your computer and pretends to be you there isn't much they can do.  They would have to become the root user, which is very difficult.  As long as you don't run as the root user, the hacker can't run as the root user either.

What many people have pointed out is true.  If your computer is not connected to the internet then there is no way for anybody to access it other than to personally access the computer.  If you are worried about it, I would encourage you to install some security software.  "Firestarter" is a program that monitors your firewall.  when you install Ubuntu it automatically puts up a firewall for you, with firestarter you can see what that firewall is doing for you.  Since there are no open ports in Ubuntu, it is very difficult for somebody from the outside to open one and get it.

:-) hope that helps.

---

### Post by SPr on 2007-09-01
Just to add to what others have said: what you are describing is normal behaviour rather than hacking/cracking.

---

### Post by Officer Dibble on 2007-09-01
This could be more serious that just hacking or cracking, I think the possibility of cranial interferance should be considered here.

This person is suffering inexplicable problems that only an experienced user could describe as terminological inexactitudes. I feel that Rickusr would benefit from a brilliant utility call tin-foil.gz.

Tin-foil.gz, once properly packaged, will provide cranial coverage from all free-ranging frequencies likely to over-ride synaptic routing thus preventing further involuntary imposed errors.

This is especially needed as Rickusr is not connected to the Internet when these things happen. You can see the advantages of properly packaged tin-foil.gz here:

[http://fermentation.typepad.com/photos/uncategorized/2007/06/27/tinfoil.jpg](http://fermentation.typepad.com/photos/uncategorized/2007/06/27/tinfoil.jpg)

---

### Post by partsdale on 2007-09-01
> **rickusr said:**
> 
At some point maybe these files can be opened and then the real truth of what has been altered can be answered, not just for me but for this community.
more later

if not a troll then at least 'trollish'

---

### Post by Agrezar on 2007-09-01
LOL wow :D

---

### Post by rickusr on 2007-09-02
To the forum;
  This is a continuation of the previous threads.

These are empty.

/root
/initrd
/lib
/mnt
/opt
/srv

Other red X files/scripts are the following;

/sbin/kallsyms
/sbin/ksyms
/ismode.modutils
/sbin/mmod.modutils

/bin/ismod.modutils

/proc/kcore
/proc/smsg
/proc/sysrq-trigger
/proc//vmcore

/var/backups/group.bak
/var/backups/gshadow.bak
/var/backups/passwd.bak
/var/backups/shadow.bak
/var/cache/apt/archives/lock
/var/cache/cups/job.cache
/var/cache/cups/remote.cache
/var/cache/debconf/conf.dat
/var/cache/debconf/passwords.dat
/var/cache/run/crond.reboot
/var/cache/run/system-tools-backends.pid
/var/lib/gdm
/var/lib/slocate
/var/spool/cups

NOT with a red X but just to see what was in these files I tried to open them. I get this error message.
Error: Cannot open /tmp/ssh:MnXqza5407/agent .5407: No application is known for this kind of file. 
                                    OK
/tmp/ssh:MnXqza5407
/tmp/ssh:MnXqza5407/agent
/tmp/mapping-rick
/tmp/virtual-rick-Gh9M6p

more later

---

### Post by rsambuca on 2007-09-02
For some reason I find this terribly amusing!  I can't wait to see what rickusr writes next. :popcorn:

---

### Post by Gremlinzzz on 2007-09-02
rickusr if you would like too see this hacker/cracker take a look in the mirror.
:guitar:

---

### Post by scrooge_74 on 2007-09-02
To rickusr:

This links should be very help full

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://www.linuxnewbie.org/](http://www.linuxnewbie.org/)
[http://www.tldp.org/](http://www.tldp.org/)
[http://www.tldp.org/](http://www.tldp.org/)
[http://google.com/linux](http://google.com/linux)

:lolflag:

---

### Post by st33med on 2007-09-02
First off, to state the obvious, all of what you are saying is normal behavior. The reason that you can't open some files is because they are binary. If you want to write in binary, you need to learn how to make binary scripts (in which I haven't the faintest clue how) and download a binary editor from Package Manager, like, say, beav. However, it is not recommended to mess with a programs binary because that can mess up it's functioning.
  Empty folders mostly aren't empty. They are just hidden by adding a period before a folder/file. To reveal these folders in Nautilus (the file browser), hit Ctrl-h. These files are hidden for, either privacy reasons or it is critical for programs to run. When you have a fresh install, you aren't going to have every folder have something in it, however, don't delete these folders since some programs rely on these folders for storage.

---

### Post by rickusr on 2007-09-03
To the forum;
  I am bringing this information to this forum not for someone's amusement but to allow the community to view this information for the benefit of the community as a whole. One way to go forward is to list the inaccessible files and other aspects of this hacker or cracker or intruder or whatever you care to call it.  With this in mind I am including more information. There is more inaccessible files and so I am including these as I list the complete number of  these inaccessible files. Later it is hoped that the community can help get these files/scripts open so we can learn from this. 

These files/scripts have a red X and are inaccessible  ( permissions or encrytion or other ).

/usr/X11R6/bin/OpenOffice
/usr/bin/OpenOffice

/proc/1/fd
/proc/1/fd/auxv
/proc/1/environ
/proc/1/mem
/proc/1/mountstats
/proc/1/setc
NOTE:  There are a number of other /proc/ folders and so substitute the number 1 for these /proc/ files. All of thse processes have these same files inaccessible. fd, auxv, environ, mem, mountstats, setc. There was a total of 83 of these folders. Here are the numbers of these files.

 1, 2, 3, 4, 5, 6, 7, 30, 31, 32, 95, 115, 117, 118, 119, 2145, 2146, 2202, 2203, 2206, 2207, 2503, 2702, 3620, 4266, 4267, 4269, 4270, 4271, 4272, 4516, 4622, 4676, 4678, 4699, 4715, 4716, 4722, 4730, 4739, 4742, 4757, 4770, 4785, 4804, 4818, 4819, 4842, 4843, 4863, 4934, 4939, 5058, 5075, 5110, 5124, 5224, 5262, 5265, 5266, 5268, 5271, 5273, 5285, 5286, 5290, 5293, 5299, 5302, 5303, 5312, 5216, 5322, 5324, 5325, 5330, 5342, 5344, 5357, 5363, 5401, 5409, 5583

/proc/acpi/dsdt
/proc/acpi/event
/proc/acpi/fadt
/proc/tty/driver
/proc/self/root/lost+found
/proc/self/root/bin/ismod.modutils
/proc/self/root/dev/disk/by-id/scsi-1ATA_Maxtor_2F040L0_F1FAYGFE
/proc/self/root/dev/disk/by-id/scsi-1ATA_Maxtor_2F040L0_F1FAYGFE_part1 
/proc/self/root/dev/disk/by-id/scsi-1ATA_Maxtor_2F040L0_F1FAYGFE_part2 
/proc/self/root/dev/disk/by-id/scsi-1ATA_Maxtor_2F040L0_F1FAYGFE_part3 
/proc/self/root/dev/disk/by-id/scsi-1ATA_Maxtor_2F040L0_F1FAYGFE_part5 
/proc/self/root/dev/disk/by-id/scsi-1ATA_Maxtor_2F040L0_F1FAYGFE_part6
/proc/self/root/dev/disk/by-id/scsi-1ATA_Maxtor_2F040L0_F1FAYGFE_part7


/proc/self/root/dev/disk/by-path/pci:0000:00:1f,1-scsi0:0:0:0
/proc/self/root/dev/disk/by-path/pci:0000:00:1f,1-scsi0:0:0:0_part1
/proc/self/root/dev/disk/by-path/pci:0000:00:1f,1-scsi0:0:0:0_part2
/proc/self/root/dev/disk/by-path/pci:0000:00:1f,1-scsi0:0:0:0_part3
/proc/self/root/dev/disk/by-path/pci:0000:00:1f,1-scsi0:0:0:0_part5
/proc/self/root/dev/disk/by-path/pci:0000:00:1f,1-scsi0:0:0:0_part6
/proc/self/root/dev/disk/by-path/pci:0000:00:1f,1-scsi0:0:0:0_part7

/proc/self/root/dev/disk/by-uuid/0c650e3f-9288-4111-a3c9-C3e89a9dbf74
/proc/self/root/dev/disk/by-uuid/5b8ac213-b852-44b2-9ab7-9097581d9918
/proc/self/root/dev/disk/by-uuid/6de423a8-56da-11dc-8e7a-259ea590db93
/proc/self/root/dev/disk/by-uuid/44d7c148-2286-4ad0-Beef-d3910ef28c65
/proc/self/root/dev/disk/by-uuid/240c503a-3c95-447e-9a2d-42ee568cc4b8

/proc/self/root/dev/fd/19
/proc/self/root/etc/cups/ppd/ssl
/proc/self/root/etc/ppp/chap-secrets
/proc/self/root/etc/ppp/pap-secrets
/proc/self/root/etc/ssl/certs/private
/proc/self/root/etc/X11/X-wrapper-conig
/proc/self/root/etc/at.deny
/proc/self/root/etc/group
/proc/self/root/etc/gshadow  ( 2 of these )
/proc/self/root/etc/passwd
/proc/self/root/etc/shadow     ( 2 of these )
/proc/self/root/etc/sudoers

more later

---

### Post by kidders on 2007-09-03
Although I somehow doubt it makes any difference, note that your question has already been answered several times.

> **Hendrixski said:**
> I remember when I first tried Linux there were a lot of things that seemed very strange to me as well, but when I found out they were normal it made a lot of sense to me.

> **SPr said:**
> what you are describing is normal behaviour

> **st33med said:**
> all of what you are saying is normal behavior.

---

### Post by bapoumba on 2007-09-03
Just to show you, with one of the files you mentioned, that I have exactly the same thing, see the screenshot.
These files you cannot open as a regular user, they are system file. Either you need to gain admin privilege to open them, or they are not viewable at all.

Edit: one useful link:
[https://help.ubuntu.com/]("https://help.ubuntu.com/")

---

### Post by rsambuca on 2007-09-03
> **rickusr said:**
> To the forum;
  I am bringing this information to this forum not for someone's amusement but to allow the community to view this information for the benefit of the community as a whole. One way to go forward is to list the inaccessible files and other aspects of this hacker or cracker or intruder or whatever you care to call it.  With this in mind I am including more information. There is more inaccessible files and so I am including these as I list the complete number of  these inaccessible files. Later it is hoped that the community can help get these files/scripts open so we can learn from this. 

more later

Despite numerous posts by more learned individuals that these files are normal,  you continue to spend your time browsing your file system, and I continue to be amused.

If you want to unlock these permissions, perhaps you should just open a file browser as the root (aka superuser).  This way, you will be able to not only view many of these files, you will be able to most likely cause your system to be completely unusable.

To open the browser as root, open a terminal (Applications -> Accessories -> Terminal) from the top menu bar.  Then enter the following command and press enter```
gksudo nautilus
```You will then be prompted to enter your root password to open the file browser.  Just make sure that you have another computer with internet access close by, so that you can report the carnage to these forums, as we are all still very interested.

Good Luck!

:popcorn:

---

### Post by por100pre1 on 2007-09-03
I haven't seen nothing unusual in all files you have listed. That's the usual behavior. The problem here is that you insist in changing their behavior. If you change the behavior on many of those files, you'll end up having real problems on your system. Just keep your eyes on your home folder and backup your files often. :)

---

### Post by jso2897 on 2007-09-03
Rickusr: Let me take another tack, here. Exactly what computing function is it that your computer will not perform?
None of the stuff regarding these files you have reproduced here is abnormal. You are not connected to the net.
 Exactly what actual, functional problem leads you to believe that there is ANYTHING wrong with your machine?
And while some have made some comments that are less than kind, I would seriously say to you : if you are really convinced that there are a lot of people out there trying to make you life hard, steal data from you, hack your computer - all in utter absence of any evidence, perhaps you should consider the possiblity that you are having some sort of mental/emotional difficulties. I say this as a friend - just like physical illnesses, these sorts of problems will generally get worse if not treated, and there is no shame, and a great deal of wisdom, in finding someone to discuss any possible issues you are having with.

---

### Post by FuturePilot on 2007-09-03
Everything the OP has described is normal. Certain files just can't be opened. Like in Windows, you can't open .dlls.
I'm rather perplexed by this thread.:-?

---

### Post by scrooge_74 on 2007-09-03
Somebody quick put the "DON FEED THE TROLL" sign on the title of the thread.

But i should would like to hear the outcome of opening and toying with those files as superuser :)

---

### Post by bodhi.zazen on 2007-09-04
> **Officer Dibble said:**
> This could be more serious that just hacking or cracking, I think the possibility of cranial interferance should be considered here.

This person is suffering inexplicable problems that only an experienced user could describe as terminological inexactitudes. I feel that Rickusr would benefit from a brilliant utility call tin-foil.gz.

Tin-foil.gz, once properly packaged, will provide cranial coverage from all free-ranging frequencies likely to over-ride synaptic routing thus preventing further involuntary imposed errors.

This is especially needed as Rickusr is not connected to the Internet when these things happen. You can see the advantages of properly packaged tin-foil.gz here:

[http://fermentation.typepad.com/photos/uncategorized/2007/06/27/tinfoil.jpg](http://fermentation.typepad.com/photos/uncategorized/2007/06/27/tinfoil.jpg)

:lolflag:

I suspect this may be close to the truth.

I am closing this thread now as IMO the OP question has been asked and answered.

rickusr : The best advice I can give to you is, as may others have pointed out, your computer seems to be operating normally.

---

