---
title: "mount ubuntu_partition"
date: 2006-12-20
forum: General Help
---

### Post by STREETURCHINE on 2006-12-20
please i have to fix my xserver i have to put my live cd in ,what is the exact command i need to mnt my ubuntu partition so i can try to fix this,
now just to complicate things i am not sure that i backed up my xorg 
although it tells me there is one in /etc/X11/xorg.conf.backup.2006220094659

 sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

 i ran this command to try to recover said file but no such directory
 
so does this mean a complete reinstall
 thanks

---

### Post by pay on 2006-12-20
Try ```
sudo mount /dev/hda3 /mnt/ubuntu
```If hda3 is the partition. and then you can edit your xorg file at /mnt/ubuntu/etc/X11/xorg.conf

---

### Post by STREETURCHINE on 2006-12-20
mount point /mnt/ubuntu does not exist

 that is the error message i get, thanks

---

### Post by pay on 2006-12-20
```
sudo mkdir /mnt
sudo mkdir /mnt/ubuntu
sudo mount /dev/hda3 /mnt/ubuntu
```sorry

---

### Post by STREETURCHINE on 2006-12-20
ok i have managed to mount my hda3/media i have run the command 

 sudo dpkg-reconfigure xserver-xorg

 answered all the questions and am now at this point

 file; backup in /etc/X11/xorg.conf.2oo61220103719

 so what is the command i give now ,thanks

---

### Post by pay on 2006-12-20
It might be easier to just use the xorg.conf file off the liveCD, atleast you know it works;)```
sudo cp -r /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
```

---

### Post by STREETURCHINE on 2006-12-20
sudo cp -r /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf

cp cannot create regular file /mnt/ubuntu/etc/X11/xorg.conf

---

### Post by pay on 2006-12-20
Make sure that you mount the partition with your linux installation.

---

### Post by STREETURCHINE on 2006-12-20
ok i am starting to think maybe i havnt  mounted my disk so i am going to paste my terminal output and you may be able to decipher it

o run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/hda3 /mnt/ubuntu
mount: mount point /mnt/ubuntu does not exist
ubuntu@ubuntu:~$ sudo mount /dev/hda3 /mnt media
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver.xorg
Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed
ubuntu@ubuntu:~$ dpkg --info
dpkg-deb: --info needs a .deb filename argument

Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --help for help about installing and deinstalling packages.
ubuntu@ubuntu:~$ dpkg --help
Usage:
  dpkg -i|--install      <.deb file name> ... | -R|--recursive <dir> ...
  dpkg --unpack          <.deb file name> ... | -R|--recursive <dir> ...
  dpkg -A|--record-avail <.deb file name> ... | -R|--recursive <dir> ...
  dpkg --configure              <package name> ... | -a|--pending
  dpkg -r|--remove | -P|--purge <package name> ... | -a|--pending
  dpkg --get-selections [<pattern> ...]    get list of selections to stdout
  dpkg --set-selections                    set package selections from stdin
  dpkg --update-avail <Packages-file>      replace available packages info
  dpkg --merge-avail <Packages-file>       merge with info from file
  dpkg --clear-avail                       erase existing available info
  dpkg --forget-old-unavail                forget uninstalled unavailable pkgs
  dpkg -s|--status <package-name> ...      display package status details
  dpkg -p|--print-avail <package-name> ... display available version details
  dpkg -L|--listfiles <package-name> ...   list files `owned' by package(s)
  dpkg -l|--list [<pattern> ...]           list packages concisely
  dpkg -S|--search <pattern> ...           find package(s) owning file(s)
  dpkg -C|--audit                          check for broken package(s)
  dpkg --print-architecture                print dpkg architecture
  dpkg --compare-versions <a> <rel> <b>    compare version numbers - see below
  dpkg --help | --version                  show this help / version number
  dpkg --force-help | -Dh|--debug=help     help on forcing resp. debugging
  dpkg --licence                           print copyright licensing terms

Use dpkg -b|--build|-c|--contents|-e|--control|-I|--info|-f|--field|
 -x|--extract|-X|--vextract|--fsys-tarfile  on archives (type dpkg-deb --help.)

For internal use: dpkg --assert-support-predepends | --predep-package |
  --assert-working-epoch | --assert-long-filenames | --assert-multi-conrep

Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg
  --root=<directory>         Install on alternative system rooted elsewhere
  --instdir=<directory>      Change inst'n root without changing admin dir
  -O|--selected-only         Skip packages not selected for install/upgrade
  -E|--skip-same-version     Skip packages whose same version is installed
  -G|--refuse-downgrade      Skip packages with earlier version than installed
  -B|--auto-deconfigure      Install even if it would break some other package
  --no-debsig                Do no try to verify package signatures
  --no-act|--dry-run|--simulate
                             Just say what we would do - don't do it
  -D|--debug=<octal>         Enable debugging - see -Dhelp or --debug=help
  --status-fd <n>            Send status change updates to file descriptor <n>
  --log=<filename>           Log status changes and actions to <filename>
  --ignore-depends=<package>,... Ignore dependencies involving <package>
  --force-...                    Override problems - see --force-help
  --no-force-...|--refuse-...    Stop when problems encountered
  --abort-after <n>              Abort after encountering <n> errors

Comparison operators for --compare-versions are:
 lt le eq ne ge gt       (treat empty version as earlier than any version);
 lt-nl le-nl ge-nl gt-nl (treat empty version as later than any version);
 < << <= = >= >> >       (only for compatibility with control file syntax).

Use `dselect' or `aptitude' for user-friendly package management.
ubuntu@ubuntu:~$ sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
cp: cannot stat `/etc/X11/xorg.conf.backup': No such file or directory
ubuntu@ubuntu:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061220103719
ubuntu@ubuntu:~$ sudo cp -r /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
cp: cannot create regular file `/mnt/ubuntu/etc/X11/xorg.conf': No such file or directory
ubuntu@ubuntu:~$ sudo cp -r /etc/X11/xorg.conf /mnt/media/etc/X11/xorg,conf
cp: cannot create regular file `/mnt/media/etc/X11/xorg,conf': No such file or directory
ubuntu@ubuntu:~$ sudo cp -r /etc/X11/xorg,conf /mnt/hda3/etc/X11/xorg.conf
cp: cannot stat `/etc/X11/xorg,conf': No such file or directory
ubuntu@ubuntu:~$  sudo cp -r /etc/X11/xorg,conf /mnt/hda3/media/etc/X11/xorg.conf
cp: cannot stat `/etc/X11/xorg,conf': No such file or directory
ubuntu@ubuntu:~$

---

