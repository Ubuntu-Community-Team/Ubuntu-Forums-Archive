---
title: "pam_mount.conf.xml"
date: 2008-05-28
forum: General Help
---

### Post by steever on 2008-05-28
Hi.

We used to be able to authenticate off a samba server using winbind and have the user's network home automatically mounted.  We used to set this mounting up using pam_mount.conf with the syntax
> volume * smbfs servername  &     /home/&         uid=&,gid=10000,dmask=0700 - -

but now  pam_mount uses pam_mount.conf.xml which has a different syntax.

How can we translate the old line into the new xml syntax?

Can anyone help?

Steve

---

### Post by pointone on 2008-05-28
Firstly: your title says "pam_mount.conf.xml", yet you refer to "auto_mount.conf.xml". Which one?

Secondly: I always found "pam_mount.conf.xml" to be EXTREMELY well self-documented; there are about 2 dozen examples covering most any situation. Can you not simply use these examples as a guide?

---

### Post by steever on 2008-05-28
Sorry, pointone, post now changed to read pam_mount.

I guess I can't follow the documentation because I can't get it working, thus posting here.  I can't seem to find the location of the documentation that addresses my particular problem

I wonder, pointone, if you can offer your solution to the problem?

Don't worry, solved my own problem by making a dummy pam_mount.conf file then installing libpam-mount and having it convert the file into a xml

Here it is:

> <volume options="uid=%(USER),gid=10000,dmask=0700" user="*" mountpoint="/home/%(USER)" path="%(USER)" server="servername" fstype="smbfs" />

Thanks for the "help" pointone.

---

### Post by tanveer on 2008-08-05
Hi steever,
Can you please help me out with pam_mount. I joined to AD with LikewiseOpen.

I have installed it on hardy and configured it as follows:
[PHP]
mod@lab1:/etc/pam.d$ ls
atd  common-account.lwidentity.orig  common-password cron  gnome-screensaver  polkit  su chfn common-auth  common-password.lwidentity.orig  cupsys         login              ppp    sudo chsh  common-auth.lwidentity.orig     common-session    gdm         other  samba common-account  common-pammount  common-session.lwidentity.orig   
gdm-autologin  passwd  sshd

mod@lab1:/etc/pam.d$ cat common-account
account required        /lib/security/pam_lwidentity.so unknown_ok
account sufficient      /lib/security/pam_lwidentity.so
account required        pam_unix.so

mod@lab1:/etc/pam.d$ cat common-account.lwidentity.orig 
account required        pam_unix.so
account requisite       pam_krb5.so ignore_root

mod@lab1:/etc/pam.d$ cat common-auth
auth    sufficient      /lib/security/pam_lwidentity.so 
auth    requisite       pam_unix.so nullok_secure try_first_pass
auth    optional        pam_smbpass.so migrate
auth    optional        pam_mount.so use_first_pass

mod@lab1:/etc/pam.d$ cat common-auth.lwidentity.orig 
auth    optional        pam_mount.so
auth    requisite       pam_unix.so nullok_secure
auth    optional        pam_smbpass.so migrate

mod@lab1:/etc/pam.d$ cat common-password
password   sufficient   /lib/security/pam_lwidentity.so 
password   requisite   pam_unix.so nullok obscure md5
password   optional   pam_smbpass.so nullok use_authtok use_first_pass

mod@lab1:/etc/pam.d$ cat common-password.lwidentity.orig 
password   sufficient   pam_unix.so nullok obscure md5 min=4 max=8
password   requisite    pam_krb5.so ignore_root

mod@lab1:/etc/pam.d$ cat common-session
session sufficient      /lib/security/pam_lwidentity.so
session required        pam_unix.so

mod@lab1:/etc/pam.d$ cat common-session.lwidentity.orig 
session required        pam_unix.so
session sufficient      pam_localuser.so
session optional        pam_mount.so


mod@lab1:/etc/pam.d$ cat gdm
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
@include common-pammount

mod@lab1:/etc/pam.d$
[/PHP]
Now when I login as mod which is local user it gives a message like this
pam_mount(pam_mount.c:311) saving authtok for session code
and  upon logout gives this
pam_mount(pam_mount.c:314) clean system authtok (0)

What are these means? But don&#8217;t give these two message when login as AD user.



My pam_lwidentity.conf is as follows" 

[PHP]
[global]
# turn on debugging (default is no)
;debug = yes
;debug_state = yes

# request a cached login if possible (default is no)
# (needs "winbind offline logon = yes" in /etc/samba/lwiuathd.conf)
cached_login = yes

# authenticate using kerberos (default is no)
krb5_auth = yes

# when using kerberos, request a "FILE" krb5 credential cache type
# (leave empty to just do krb5 authentication but not have a ticket
# afterwards)
krb5_ccache_type = FILE

# make successful authentication dependent on membership of one of
# the following SIDs/groups/users (comma-separated)
;require_membership_of =

# create home directory on logon, if it does not exist (default is no)
create_homedir = yes
# set the skel directory. Logon files are not copied if this is unset
skel = /etc/skel
# the file-creation-mask for the home directory (default is 0022)
;umask = 0022

# create .k5login file on logon, if it does not exist (default is no)
create_k5login = yes

# standard PAM try_first_pass option (default is no)
try_first_pass = yes

[/PHP]

My pam_mount.conf.xml file where I added just one line as
[B]
<volume user="*" fstype="cifs" server="server1" path="Users" mountpoint="~/%(USER)/mntfolder" options="uid=%(USER),gid=10000,dmask=0751,workgroup=DOMAINNAME" /> 
[/B]

[PHP]
<?xml version="1.0" encoding="utf-8" ?> 
- <pam_mount>
+ <!-- NOTE: Special characters like < > and & require escaping them to &lt; &gt;
and &amp; according to the XML standard. Though, you really should not use
them in pathnames.

Do not use comments inside tags like <lsof></lsof> - the case is not
handled by the parser.
  --> 
+ <!--  Turn on if you want to debug why some volume cannot be mounted etc.
This can be overriden by user's local configuration. This will also affect
the pmvarrun helper program. To disable, use enable="0" or comment it out
entirely. 
  --> 
  <debug enable="1" /> 
+ <!-- Create mountpoint if it does not exist yet. This is a good thing.

If enabled, and a mountpoint was created by pam_mount, the mountpoint will
be removed again on logout. To disable this behavior, use remove="false".
  --> 
  <mkmountpoint enable="1" remove="true" /> 
- <!-- 
 Loopback device to use to run fsck on loopback filesystems. 
  --> 
  <fsckloop device="/dev/loop7" /> 
+ <!-- Users' local configuration file (if there is none, comment this parameter
out). Will be read as ~/<file>.

Note: you must include either options_allow or options_deny to use this
directive. I recommend also including options_require.

Individual users may define additional volumes to mount if allowed by
pam_mount.conf.xml (usually ~/.pam_mount.conf.xml). The volume keyword is
the only valid keyword in these per-user configuration files. If the
luserconf parameter is set in pam_mount.conf.xml, allowing user-defined
volumes, users may mount and unmount any volumes they specify. The mount
operation is executed under the user account, not with root permissions.

<luserconf name=".pam_mount.conf.xml" />
  --> 
+ <!-- These directives determine which options may be specified in a user config
file (luserconf). You must include one of these directives if you have a
luserconf directive. You may not include both directives.

If you have an options_allow directive, then the options listed in that
directive wil be allowed, and all others rejected. If you have an
options_deny directive, then the options listed will be denied, and all
others permitted.

You may use the wildcard '*' to match all options. I recommend not
permitting the suid and dev options.
  --> 
  <mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" /> 
+ <!-- <mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
  --> 
+ <!-- The options listed in this directive are required for all volumes from a
user config file. That is, any volume specified in a user config file that
does not include these options will be ignored.

Note: you must make sure that a required option is permitted (either by
including it in options_allow, or by not including it in options_deny).

I recommend requiring at least nosuid and nodev.

This is ignored completely if the volume is configured to get its options
and mount point from /etc/fstab.
  --> 
  <mntoptions require="nosuid,nodev" /> 
+ <!-- Commands to mount/unmount volumes. They can take parameters, as shown.

If you change the -p0 argument for lclmount, you'll need to modify the
source in mount.c (it sends the password to the stdin file descriptor of
the child process - look for STDIN_FILENO).

You can specify either absolute paths, or relative ones, in which case
$PATH will be searched. Since some login programs really behave
antisocial, pam_mount will always set its own $PATH.
  --> 
  <path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path> 
  <lsof>lsof %(MNTPT)</lsof> 
  <fsck>fsck -p %(FSCKTARGET)</fsck> 
  <losetup>losetup -p0 "%(before=\"-e\" CIPHER)" "%(before=\"-k\" KEYBITS)" %(FSCKLOOP) %(VOLUME)</losetup> 
  <unlosetup>losetup -d %(FSCKLOOP)</unlosetup> 
  <cifsmount>mount -t cifs //%(SERVER)/%(VOLUME) %(MNTPT) -o "user=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"</cifsmount> 
  <davmount>mount -t davfs %(SERVER)/%(VOLUME) %(MNTPT) -o "username=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"</davmount> 
  <smbmount>smbmount //%(SERVER)/%(VOLUME) %(MNTPT) -o "username=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"</smbmount> 
  <smbumount>smbumount %(MNTPT)</smbumount> 
  <ncpmount>ncpmount %(SERVER)/%(USER) %(MNTPT) -o "pass-fd=0,volume=%(VOLUME)%(before=\",\" OPTIONS)"</ncpmount> 
  <ncpumount>ncpumount %(MNTPT)</ncpumount> 
  <fusemount>mount.fuse %(VOLUME) %(MNTPT) "%(before=\"-o \" OPTIONS)"</fusemount> 
  <fuseumount>fusermount -u %(MNTPT)</fuseumount> 
  <truecryptmount>truecrypt %(VOLUME) %(MNTPT)</truecryptmount> 
  <truecryptumount>truecrypt -d %(MNTPT)</truecryptumount> 
+ <!--  Linux supports lazy unmounting (-l). May be dangerous for encrypted
volumes. May also break loopback mounts because loopback devices are not
freed. Need to unmount mount point (not volume!) to support SMB mounts,
etc. 
  --> 
  <umount>umount %(MNTPT)</umount> 
+ <!--  On OpenBSD try "/usr/local/bin/mount_ehd" (included in pam_mount
package). 
  --> 
  <lclmount>mount -p0 -t %(FSTYPE) %(VOLUME) %(MNTPT) "%(before=\"-o\" OPTIONS)"</lclmount> 
  <cryptmount>mount -t crypt "%(before=\"-o \" OPTIONS)" %(VOLUME) %(MNTPT)</cryptmount> 
  <nfsmount>mount %(SERVER):%(VOLUME) %(MNTPT) "%(before=\"-o\" OPTIONS)"</nfsmount> 
- <!-- 
 mntcheck utility for BSDs which lack /etc/mtab 
  --> 
  <mntcheck>mount</mntcheck> 
  <pmvarrun>pmvarrun -u %(USER) -o %(OPERATION)</pmvarrun> 
+ <!-- Volumes that will be mounted when user triggers the pam_mount module
(usually at login).

    <volume
        user="*" | pgrp="foo" | sgrp="bar"
        invert="1"
        fstype="auto"
        server="..."
        path="..."
        mountpoint="..."
        options="..."
        fskeycipher="..."
        fskeypath="..."
    />


USER is a user for which a volume rule applies, "*" selects all users.

A volume with PGRP attribute will be mounted when a user has that
particular group as its primary group. A volume with SGRP attribute will
be mounted when the user has the group as either primary or secondary.

USER, PGRP and SGRP are mutually exclusive. If neither is present,
USER="*" is assumed.

INVERT will invert the sense of the USER, PGRP or SGRP selector, thereby
making it possible to specify, e.g. "all users not in group xyz".


FSTYPE can be any filesystem type. If /bin/mount or the kernel does not
support it, you will get an error. You can use the special keyword "auto"
which automatically lets the kernel choose a matching filesystem. Note
that the kernel's auto feature only works with currently loaded
filesystems (listed in /proc/filesystem), so you will have to load the
necessary modules _first_ for them to be recognized with "auto". If this
attribute is not present, "auto" is assumed.

The "cifs", "davfs", "smbfs", "ncpfs", "fuse" and "truecrypt" types
override the identically-named kernel filesystems and use the
helper programs as defined above.


SERVER defines the server from which to source. The exact volume path
depends on the filesystem type. SMB uses //SERVER/VOLUME, NFS uses
SERVER:VOLUME. davfs uses SERVER/VOLUME. The attribute may be absent.


PATH specifies the location of the volume, locally or on the server (if
applies), respectively. This attribute is mandatory.


MOUNTPOINT specifies the destination directory onto which the volume is
mounted. '~' expands to the user's home directory as present in the passwd
database, according to sh semantics. "~name" is not supported. If this
attribute is omitted, the location is read from /etc/fstab, which also
requires PATH to be the device of an fstab entry.


OPTIONS specifies mount options. If omitted, and /etc/fstab is used (see
MOUNTPOINT), then the options are also sourced from fstab.


Note that if the mount command has specified an option, e.g. %(KEYBITS)
and you do not specify a value, a warning is printed in the log. The
warning can usually be ignored, except when the option is mandatory.

SMB mounts require the `smbmount` and `smbumount` programs, NCP `ncpmount`
and `ncpumount`. Both SMB and NCP work in ~/.pam_mount.conf.xml.


General examples:

    <volume user="user" fstype="smbfs" server="krueger" path="public"
        mountpoint="/home/user/krueger" />

    <volume user="user" fstype="ncpfs" server="krueger" path="public"
        mountpoint="/home/user/krueger" options="user=user.context" />

    <volume fstype="smbfs" server="krueger" path="homes"
        mountpoint="/home/%(USER)/remote" options="dmask=0711" />

    <volume fstype="davfs" server="https://dev.computergmbh.de/"
        path="/svn/libHX/trunk" mountpoint="/projects/libHX" />

You can use ~ to use whatever home directory the user has (therefore you
can distribute home directories along more than one location. This is
useful for pam_chroot:

    <volume path="/bin" mountpoint="~/bin" options="bind" />

For FUSE mounts, use something like this:

    <volume fstype="fuse" path="sshfs#%(USER)@fileserver:"
        mountpoint="~" />

    <volume fstype="nfs" server="fileserver" path="/home/%(USER)"
        mountpoint="~" />

Some more examples:

    <volume path="/home/%(USER).img" mountpoint="~" fskeycipher="aes-256-ecb"
        fskeypath="/etc/ehd/%(USER)" />

Windows 2000, which requires a domain specified (does it really? works for
me without -jengelh), example (thanks John Knox):

    <volume fstype="smbfs" server="viper" path="%(USER)"
        mountpoint="~" options="dmask=0751,workgroup=WINDOWS_DOMAIN" />

  --> 
  <volume user="*" fstype="cifs" server="server1" path="Users" mountpoint="~/%(USER)/mntfolder" options="uid=%(USER),gid=10000,dmask=0751,workgroup=DOMAINNAME" /> 
+ <!-- Linux encrypted home directory examples, using dm_crypt:

crypt mounts require a kernel with CONFIG_BLK_DEV_DM and CONFIG_DM_CRYPT
enabled as well as all the used ciphers (e.g. CONFIG_CRYPTO_AES_586,
CONFIG_CRYPTO_TWOFISH, etc.). crypt mounts must be in the global config
file /etc/security/pam_mount.conf.xml.

Linux encrypted home directory examples, using dm_crypt:

    <volume fstype="crypt" path="/dev/sda2" mountpoint="/home/user"
        options="cipher=aes" fskeycipher="aes-256-ecb"
        fskeypath="/home/user.key" />

cryptoloop mounts require a kernel with CONFIG_BLK_DEV_CRYPTOLOOP enabled.
cryptoloop mounts must be in the global config
/etc/security/pam_mount.conf.xml. Linux encrypted home directory examples,
using cryptoloop:

    <volume path="/dev/hda123" mountpoint="/home/user"
        options="loop,encryption=aes" />

    <volume path="/home/user.img" mountpoint="/home/user"
        options="loop,user,exec,encryption=aes,keybits=256" />

    <volume path="/home/user.img" />

    <volume path="/home/user.img" fskeycipher="aes-256-ecb"
        fskeypath="/home/user4.key" />

The last two examples (^^) need a line like the following in /etc/fstab:

    /home/user4.img /home/user4 xfs user,loop,encryption=aes,keybits=256,noauto 0 0

OpenBSD encrypted home directory example (see also lclmount above):

    <volume path="/home/user.img" mountpoint="/home/user"
        options="svnd0" />

Volatile tmpfs mount with restricted size (thanks to Mike Hommey for this
example):

    <volume user="test" fstype="tmpfs" path="none" mountpoint="/home/test"
        options="size=10M,uid=test,gid=users,mode=0700" />

See http://www.tldp.org/HOWTO/Loopback-Encrypted-Filesystem-HOWTO.html to
learn how to create a encrypted loopback filesystem.

If the volume's password is different than the user's login password, the
following technique may be used (see also README):

{...} are placeholders, insert the proper value there!

1.  Create a file containing the volume's password (FS key). If you are
    using pam_mount to mount an loopback encrypted volume, this password
    should be generated with /dev/urandom.

    Simple example:
    echo {volume password} | openssl enc -aes-256-ecb >/home/user.key
    Encrypt this file using the user's login password as the key.

    Verbose loopback encrypted volume example:
    a.  dd if=/dev/urandom of=/home/user.img bs=1M count={image size in MB}
    b.  dd if=/dev/urandom bs=1c count={keysize/8} | \
        openssl enc -{fs key cipher} >/home/user.key
        Encrypt this file using the user's login password as the key.
    c.  modprobe -q cryptoloop
    d.  openssl enc -d -{fs key cipher} -in /home/user.key | \
        losetup -e aes -k {keysize} -p0 /dev/loop0 /home/user.img
    e.  mkfs -t ext2 /dev/loop0
    f.  losetup -d /dev/loop0

3.  In pam_mount.conf.xml:
        a.  Set the fs key cipher variable to the cipher used
            (ie: aes-256-ecb).
        b.  Set the fs key path variable to the key's path
            (ie: /home/user.key)

4.  If a user changes his login password, regenerate the efsk that was
    created in step 1b.  A script named passwdehd is provided to do this.

If FSKEYCIPHER is empty, then the user's login password is also the
volume's password.
  --> 
+ <!-- When pam_mount is not used with "use_first_pass" or "try_first_pass" in
the PAM configuration files (/etc/pam.d/), it will have to ask for a
password. This is also the case if pam_mount is the first auth module
in the block.
  --> 
  <msg-authpw>pam_mount password:</msg-authpw> 
+ <!-- In case the 'session' PAM block does not have the password (e.g. on su
from root to user), it will ask again.
  --> 
  <msg-sessionpw>reenter password for pam_mount:</msg-sessionpw> 
  </pam_mount>
[/PHP]

---

### Post by tanveer on 2008-08-05
I can mount with the following command though 
# mount –t cifs //server1/Users /home/local/DOMAINAME/ADUserName/wall –o username=ADUserName

But it prompts for password though. And I login only with username not using DOMAINNAME\Username.

Thanks in advance

---

### Post by franzpv on 2008-08-26
Hi guys:

On Ubuntu 7.10, I added "volume @groupalumnos cifs ateneaserver & /home/pregrado/&/Z username=& - -" to /etc/pam_mount.conf and when a user logged in, a folder named "Z" appeared on the desktop showing his documents. (The users are on a OpenLdap Server). Now, I am updating to Ubuntu 8.04 and can't get the same to work.

I've tried adding the following to /etc/pam_mount.conf.xml
"<volume user="*" fstype="cifs" server="ateneaserver" path="%(USER)" mountpoint="/home/pregrado/%(USER)/Z" options="uid=%(USER),gid=%(USERGID),workgroup=INFORMATICA"/>". It's on the same server, only the clients are getting an update.

Please help.....anything you can think of.

---

### Post by david_kt on 2009-02-12
> **franzpv said:**
> Hi guys:

On Ubuntu 7.10, I added "volume @groupalumnos cifs ateneaserver & /home/pregrado/&/Z username=& - -" to /etc/pam_mount.conf and when a user logged in, a folder named "Z" appeared on the desktop showing his documents. (The users are on a OpenLdap Server). Now, I am updating to Ubuntu 8.04 and can't get the same to work.

I've tried adding the following to /etc/pam_mount.conf.xml
"<volume user="*" fstype="cifs" server="ateneaserver" path="%(USER)" mountpoint="/home/pregrado/%(USER)/Z" options="uid=%(USER),gid=%(USERGID),workgroup=INFORMATICA"/>". It's on the same server, only the clients are getting an update.

Please help.....anything you can think of.

Please remove uid=%(USER),gid=%(USERGID) from option, and check the option in cifmount should already include these:
```

 <cifsmount>mount -t cifs //%(SERVER)/%(VOLUME) %(MNTPT) -o "user=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"</cifsmount> 
```

DK

---

