---
title: "Problem mounting linux shares on Mac"
date: 2014-11-01
forum: General Help
---

### Post by James Wilde on 2014-11-01
I have an embarrassing problem.

I am tryiing to mount the two partitions on a usb disk attached to my 14.04.01 linux box onto my Mac.  I have installed samba, I have configured the partitions for sharing, including changing the rights.  I have them set to be used by registered users.  I have even created a separate account to login with.  None of this works.  When I try to mount the disks - or even just log into the machine from my Mac, it bombs out.  'A problem has occurred'.

I have checked the rights in a terminal window, and I see that these two partitions have 700 rights.  I cannot change this either with chmod as myself nor with sudo.  When I select the disks and click on properties, I see the equivalent of 700 there.  Even here I cannot change this.  I have created an administrator account on the ubuntu box, and even that account cannot read the two disks, let alone write to them.  I have now marked the disks as to be available to guests, but I can't see that the rights have changed.  Later: they haven't.  I have also discovered that I can't mount these two disks on my wife's Windows box either, so the problem is definitely on the Linux box.

I have noticed that occasionally I cannot ping the linux box from the other two, and that i then get an 'incomplete' record in arp, and this applies in both directions.

Any suggestions very welcome.

---

### Post by James Wilde on 2014-11-01
PS not even root can change the rights on these usb disks

---

### Post by James Wilde on 2014-11-01
Further developments:

Found this reference: [http://askubuntu.com/questions/333287/external-hard-disk-read-only](http://askubuntu.com/questions/333287/external-hard-disk-read-only) and followed the first bit.  Mounted the disk with:

sudo mount -t ntfs -o rw,uid=1000,gid=1000,user,exec,umask=000,blksize=4096 /dev/sdb2 /media/james/3TB1

Discovered I could cut out blksize as this was handled by Paragon NTFS-3g.  Now I have my disk partition 1 with 777 rights.  But I still can't mount it on the Mac. <sigh>

Can it be something I have missed in Samba?  Have just installed samba but not configured anything.

---

### Post by Morbius1 on 2014-11-01
If you run the following command you will see the problem:
```
getfacl -t /media/james
```
There is only one user ( other than root ) that will able to access anything mounted under /media/james and that's james.

Create a new mount point one level higher:
```
sudo mkdir /media/3TB1
```
Then change your mount to reflect the new mount point.

---

### Post by James Wilde on 2014-11-01
Thans, Morbius.  Now I can - with a certain amount of difficulty - get these two partitions to show in Finder on the Mac.  How permanently they will be visible there is another matter which I may have to take up in a Mac forum.  However, I suppose I now should make sure these two disks mount in the new place when I boot my Linux box, and I suppose that's a case of putting a couple of lines in /etc/fstab.

But the big thing is that you got these two disks to show up so they could be mounted elsewhere,  Thanks a jillion for that.

BTW I can only mount them as guest, and of course I had to change the rights to 777.  Anything I can do about that?

James

---

### Post by Morbius1 on 2014-11-01
> Thans, Morbius.  Now I can - with a certain amount of difficulty - get these two partitions to show in Finder on the Mac.
What's the difficulty. They don't show up automatically?

[COLOR=#0000cd]**EDIT**[/COLOR]: You know, in it's entirety your posts are confusing me. You might want to post the output of the following commands so we can see how you are set up:
```
 testparm -s
```
```
 net usershare info --long
```

---

### Post by James Wilde on 2014-11-01
First of all, thanks a lot for your patience and help.

Now here's the output of those two commands:

```
james@james-ubuntu:/media$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[3TB1]"
Processing section "[3TB2]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[3TB1]
    comment = Ubuntu File Server Share
    path = /media/james/3TB1
    read only = No
    create mask = 0777
    guest ok = Yes

[3TB2]
    comment = Ubuntu File Server Share
    path = /media/james/3TB2
    read only = No
    create mask = 0777
    guest ok = Yes
james@james-ubuntu:/media$ net usershare info --long
[3TB1]
path=/media/3TB1
comment=
usershare_acl=Everyone:F,
guest_ok=y

[3TB2]
path=/media/3TB2
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

As to why it was a little complicated, the thing is that I am trying to mount the shares on the Mac by signing in with a user name and password, and it isn't working.  And then, when I accept that I'll have to log in as guest, I get two windows up.  Now I'm used to having my mounts in a column on the Mac, and I hope I have now got it to work.  I still have to restart the Mac and see if they come up automagically.

---

### Post by Morbius1 on 2014-11-01
> As to why it was a little complicated, the thing is that I am trying to  mount the shares on the Mac by signing in with a user name and password,  and it isn't working.
It's a 2-step process to do this in Linux.

[1] You need to actually create the user in Linux.
[2] Then you need to add him to the samba password database. 

For example let's say you want to allow me to access the share.

** You need to add another user to your linux box named morbius.
** Then you need to add me to samba:
```
sudo smbpasswd -a morbius
```

But you have a bigger problem. There are two ways to create a samba share. One way is through smb.conf like this one:
> [3TB1]
    comment = Ubuntu File Server Share
    path = /media/james/3TB1
    read only = No
    create mask = 0777
    guest ok = Yes
Another way is through Nautilus like this one:
> [3TB1]
path=/media/3TB1
comment=
usershare_acl=Everyone:F,
guest_ok=y
You can use both methods if you have your wits about you but in this case you are using both methods, naming them the same thing - [3TB1] for example, but they have different paths.

You should get rid of the ones in smb.conf if the path is now /media/3TB1 and /media/3TB2.

---

### Post by James Wilde on 2014-11-01
Wow!  I didn't see that I had two conflicting shares.  The /media/james/3TB1 comes probably from the system.  I have now created two lines in fstab:

```
# Loading big drive
UUID=710BF22E1FADA547    /media/3TB1    ntfs    rw,user,exec,umask=000    0    1
UUID=4A34D80934D7F5C3    /media/3TB2    ntfs    rw,user,exec,umask=000    0    1
```

and presumably it is from here that the /media/3TB1 share arises.  I'll have to see how to get rid of the automatic one.  I've rmdir'd them now and I'll reboot the linux box to see if they stay away.

---

### Post by James Wilde on 2014-11-01
It worke.  After reboot the /media/james/3TB1 was still gone.

---

