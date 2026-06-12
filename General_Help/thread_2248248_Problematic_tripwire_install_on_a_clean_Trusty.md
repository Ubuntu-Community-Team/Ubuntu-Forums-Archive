---
title: "Problematic tripwire install on a clean Trusty"
date: 2014-10-13
forum: General Help
---

### Post by Cbhihe on 2014-10-13
I installed tripwire 2.4.2.2-3 (twice in a row with a remove/purge in between) and got this:

```
> sudo apt-get update;  sudo apt-get install tripwire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tripwire
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1407 kB of archives.
After this operation, 10.7 MB of additional disk space will be used.
Get:1 http://ftp.udc.es/ubuntu/ trusty/universe tripwire amd64 2.4.2.2-3 [1407 kB]
Fetched 1407 kB in 19s (71.5 kB/s)                                             
Preconfiguring packages ...
Selecting previously unselected package tripwire.
(Reading database ... 404284 files and directories currently installed.)
Preparing to unpack .../tripwire_2.4.2.2-3_amd64.deb ...
Unpacking tripwire (2.4.2.2-3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up tripwire (2.4.2.2-3) ...
[COLOR=#b22222]chmod: cannot access '/etc/tripwire/site.key': No such file or directory
chmod: cannot access '/etc/tripwire/[HOST]-local.key': No such file or directory[/COLOR]
```
[SIZE=1]
[/SIZE][I][SIZE=1]Note that, perhaps because of the above, _Ubuntu Software Center_ hung on the install from the GUI. I had to kill the Software Center's install process and subsequently remove/purge any partially installed tripwire dependencies before reinstalling from Terminal.  
[/SIZE]
[/I][INDENT]What are the missing [FONT=courier new]site.key[/FONT] and [FONT=courier new]xxxxx-local.key[/FONT] ? 
Do they have anything to do with the prior install of either an encryption package or with starting a specific service ?  How do I proceed ? 
[/INDENT]

As I read the manual page for tripwire as well as [FONT=courier new]/usr/share/doc/tripwire/README.Debian[FONT=arial], I [/FONT][/FONT]see that it is recommended to move both DB and binary to a read-only - optionally remote - volume.  So I readied a 2 GB read-only NTFS formatted SD card to be automatically mounted, in order to transfer my first baseline DB on it.[INDENT]Should I really also sudo copy the tripwire binary, [FONT=courier new]/usr/sbin/tripwire[/FONT],  to the SD card and symbolic-link both files to their original location: /var/lib/tripwire/_database-name_ for the DB and /usr/sbin/_tripwire_ for the binary ?
[/INDENT]
It seems unusual to have to move the binary.

Cheers.

---

