---
title: "Mount Problems"
date: 2007-12-02
forum: General Help
---

### Post by infinitelink on 2007-12-02
I do this and it gives:

sudo mount /windows
[sudo] password for jb:
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda5 ()


So I installed and opened KDisk free to get the following information:

Device:
UUID=7A94ABC394A8836D

Type:
ntfs-3g

Size:
N/A

Mount Point:

/windows

Free:
0 B

Full %:
N/A


And when trying to mount using KDisk Free I get this message:

Called: mount UUID=7A94A8C394A8836D
mount: according to mtab, /dev/sda5 is already mounted on /windows
mount failed


I remember posting another thread...but it's not re-appearing in any forum searches. : (  (I forgot to subscribe).

Any help????

---

### Post by PmDematagoda on 2007-12-02
Could you post the result of:-

```
cat /etc/mtab
```

---

### Post by infinitelink on 2007-12-02
If I type-in cat /etc/mtab 

The location is not a folder.

so I tried gedit cat /etc/mtab 

and it just starts gedit with a blank file.

---

### Post by PmDematagoda on 2007-12-02
Did you enter the command I gave in a terminal?

And could you post the result of:-

```
ls /etc
```

---

### Post by infinitelink on 2007-12-02
I thought I did...though I re-tried and it gave:

/dev/sda10 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda1 /dos vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda9 /media/sda1 vfat rw,utf8,umask=007,gid=46 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda3 /media/sda2 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda5 /windows fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev,user=jb 0 0


and here's the output for ls /etc :

acpi                    gshadow               opt
adduser.conf            gshadow-              pam.conf
adjtime                 gtk-2.0               pam.d
aliases                 hal                   pango
alternatives            hdparm.conf           papersize
anacrontab              hesiod.conf           passwd
apm                     host.conf             passwd-
apparmor                hostname              pcmcia
apparmor.d              hosts                 perl
apport                  hosts.allow           pnm2ppa.conf
apt                     hosts.deny            popularity-contest.conf
at.deny                 hotplug               power
avahi                   hotplug.d             ppp
bash.bashrc             hp                    printcap
bash_completion         inetd.conf            profile
bash_completion.d       init.d                protocols
belocs                  initramfs-tools       pulse
bindresvport.blacklist  inputrc               purple
blkid.tab               iproute2              python
bluetooth               issue                 python2.5
bogofilter.cf           issue.net             qt3
bonobo-activation       java                  rc0.d
brlapi.key              java-6-sun            rc1.d
brltty                  jvm                   rc2.d
brltty.conf             jvm.d                 rc3.d
calendar                kde3                  rc4.d
chatscripts             kernel-img.conf       rc5.d
compizconfig            laptop-mode           rc6.d
console-setup           ldap                  rc.local
console-tools           ld.so.cache           rcS.d
cron.d                  ld.so.conf            readahead
cron.daily              ld.so.conf.d          resolvconf
cron.hourly             lftp.conf             resolv.conf
cron.monthly            libao.conf            rmt
crontab                 libgda-3.0            rpc
cron.weekly             libpaper.d            samba
cups                    locale.alias          sane.d
dbus-1                  localtime             scim
debconf.conf            logcheck              screenrc
debian_version          login.defs            scrollkeeper.conf
default                 logrotate.conf        securetty
defoma                  logrotate.d           security
deluser.conf            lsb-base              services
devfs                   lsb-base-logging.sh   sgml
dhclient-exit-hooks     lsb-release           shadow
dhcp3                   ltrace.conf           shadow-
dictionaries-common     magic                 shells
discover.conf           magic.mime            skel
discover.conf-2.6       mailcap               sound
discover.d              mailcap.order         ssh
dpkg                    manpath.config        ssl
emacs                   mediaprm              sudoers
environment             menu-methods          sysctl.conf
esound                  mime.types            sysctl.conf~
event.d                 mke2fs.conf           syslog.conf
fdmount.conf            modprobe.d            terminfo
firefox                 modules               texmf
firestarter             modutils              timezone
fonts                   mono                  ucf.conf
foomatic                motd                  udev
fstab                   motd.tail             uniconf.conf
fstab.pre-ntfs-config   mplayer               updatedb.conf
fuse.conf               mplayerplug-in.conf   update-notifier
gai.conf                mplayerplug-in.types  usplash.conf
gamin                   mtab                  vbox
gconf                   mysql                 vim
gdm                     nanorc                vpnc
ggi                     Net                   vpnc.conf
gimp                    netscsid.conf         vpnc.conf~
gnome                   network               w3m
gnome-app-install       NetworkManager        wgetrc
gnome-system-tools      networks              wodim.conf
gnome-vfs-2.0           nsswitch.conf         wpa_supplicant
gnome-vfs-mime-magic    ODBCDataSources       wvdial.conf
groff                   odbc.ini              X11
group                   odbcinst.ini          xdg
group-                  openalrc              xml
grub.d                  openoffice            zsh_command_not_found


Pretty... ; )

---

### Post by PmDematagoda on 2007-12-02
Open mtab for editing using:-

```
sudo gedit /etc/mtab
```

And delete this line:-

```
/dev/sda5 /windows fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
```

Save the file.

Having /windows as a mount point is not really good, make a folder named windows in /media and then do this:-

```
sudo ntfs-3g /dev/sda5 /media/windows
```

---

### Post by infinitelink on 2008-02-05
Thanks for the help thus far... : )

Here's the latest output (after following your instructions):

b@AGFTL:~$ sudo ntfs-3g /dev/sda5 /media/windows
jb@AGFTL:~$ sudo mount /media/windows
mount: /dev/sda5 already mounted or /media/windows busy
mount: according to mtab, /dev/sda5 is already mounted on /media/windows
jb@AGFTL:~$ sudo umount /dev/sda5
jb@AGFTL:~$ sudo mount /media/windows
mount: can't find /media/windows in /etc/fstab or /etc/mtab
jb@AGFTL:~$

---

### Post by PmDematagoda on 2008-02-05
Actually if you had just done:-
```
sudo ntfs-3g /dev/sda5 /media/windows
```
that would have sufficed since your hard drive would then have been mounted to /media/windows and you could then browse your disk.

---

### Post by infinitelink on 2008-02-06
Thanks. : ) 

So I typed:


jb@AGFTL:~$sudo ntfs-3g /dev/sda5 /media/windows
[sudo] password for jb:


and then it gave

jb@AGFTL:~$

but the drive didn't appear on the desktop or in the Places menu. ???

---

### Post by PmDematagoda on 2008-02-06
I am not sure if you will be able to see a volume if you manually mounted it.

Did you try going to the /media/windows folder to see if it was mounted at all?

---

### Post by infinitelink on 2008-02-06
Genius!

You're Genius!

Thanks for the help: it IS there when manually mounted. : ) Any idea how to make it show up without having to go to /media/windows?

And it seems this is a common prob so now when I see people complaining about it I can point them to this forum and maybe it'll apply. : )

---

### Post by PmDematagoda on 2008-02-07
You could make a symbolic link to the /media/windows directory on your Desktop using:-
```
ln -s /media/windows ~/Desktop
```
so that you could access your Windows hard drive when mounted on /media/windows. Keep in mind, if the hard drive is not mounted on /media/windows then you will see nothing when clicking the symbolic link as well.

---

