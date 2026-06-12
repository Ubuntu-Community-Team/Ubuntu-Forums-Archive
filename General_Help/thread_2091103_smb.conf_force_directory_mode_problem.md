---
title: "smb.conf: force directory mode problem"
date: 2012-12-04
forum: General Help
---

### Post by tetzschner on 2012-12-04
Hi guys

Been struggling with this problem for hours (and yes, I gone through the man smb).

The problem is that setting:

**force directory mode = 0770**

is resulting in linux-file-permission **750**

if I try:

**force directory mode = 0777**

is resulting in linux-file-permission **755**

It seems like something is unmasking the file-permission.

Any ideas how to solve this problem?


As a note, the:

**force create mode = 0770**

is working as expected.

The last settings I have tried:

```
        force group = users
        create mask = 0770
        force create mode = 0770
        security mask = 00
        force security mode = 0770
        directory mask = 0770
        force directory mode = 0770
        directory security mask = 00
        force directory security mode = 0770

```

With kind regards, Ole

---

### Post by Morbius1 on 2012-12-04
It is confusing. It is also frustrating and non intuative - at least for me. I think you have the right idea that you must use all of these parameters to enforce the permissions but you need to set "security mask" and "directory security mask" to 0770 as well.

To be honest with you If I need to absolutely positively enforce permissions I take it out of the hands of Samba and put it into the hands of bindfs. If I have a directory at say ... /mnt/Share and I want all folders to have permissions of 770 and all files to have permissions of 660 with the group = users I have bindfs make it so:

```
 sudo bindfs -o perms=0660:+X,group=users /mnt/Shared /mnt/Shared
```[COLOR=Blue]*You are mounting a folder to itself with a "view" specified by the bindfs options. It will look and act a lot like an ntfs partition ( in that it's permissions are immutable ) at that point.*[/COLOR]

All existing and new files / folders will have group = users and have permissions of 660 / 770. It's impervious to whatever Samba thinks it's doing to permissions. I either add that line without sudo to rc.local or set up a special upstart job to have it done at boot time.

---

### Post by tetzschner on 2012-12-04
Hi Morbius1

Thanks for your reply.

Yes it is very frustrating and confusing. I have been using samba for ages and never hit this wall.

I have tried setting both **security mask** and **directory security mask** to 0770. It does not make any difference.

I also tried **unix extensions = no** but still the same problem.

I have tried rebooting as well (after a complete **apt-get upgrade **and **apt-get dist-upgrade**) but still the same problem.

Not to be ungrateful but I would really like to solve this without bindfs. 

There must be other people out there with the same problem?. The whole idea in SAMBA must be to share files.

Almost my complete smb.conf:

```
[global]
        server string = %h server (Samba, Ubuntu)
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
        force group = users
        create mask = 0770
        force create mode = 0770
        security mask = 0770
        force security mode = 0770
        directory mask = 0770
        force directory mode = 0777
        directory security mask = 0770
        force directory security mode = 0770
        hosts allow = 10.0.0., 127., 192.168.255., 192.168.1., 192.168.3.

[marketing]
        path = /home/backup/marketing
        valid users = my_user1, my_user2
        read only = No

```

Kind regards, Ole

---

### Post by Morbius1 on 2012-12-04
I created an smb.conf that matched yours in an Ubuntu 11.10 VBox guest icluding having all these masks and modes in the [global] section instead of in the share definition and I cannot reproduce your error. The only difference is that I forced the group to plugdev since both users were already members.

Using 2 different users I added some stuff and editing things and saved and here is the result from the server:
> 
ls -al /home/backup/marketing
total 16

drwxrwx--- 3 root   plugdev 4096 2012-12-04 14:36 .
drwxr-xr-x  3 root   root    4096 2012-12-04 14:26 ..
drwxrwxr-x 2 morbius  plugdev 4096 2012-12-04 14:31 Test
-rwxrwx---  1 tester plugdev    5 2012-12-04 14:36 test.txt
Not sure why the "Test" folder I added ended up with 775 instead of 770 but that's why I use bindfs. But in no cases did I end up with 755.

I don't have an answer, sorry. THe only thing I can suggest is yet another workaround. The way you have this set up both valid users have write access to each others files so you can get the same result by forcing all users to be the same:
> [marketing]         
path = /home/backup/marketing         
valid users = my_user1, my_user2
        [COLOR=Blue]**force user = my_user1**[/COLOR]
        read only = No"valid users" will restrict who can access the share but once they are in "force user" will convert them all to my_user1. You will no longer need the masks and modes and force group.

---

### Post by bab1 on 2012-12-04
> **tetzschner said:**
> Hi guys

Been struggling with this problem for hours (and yes, I gone through the man smb).

The problem is that setting:

**force directory mode = 0770**

is resulting in linux-file-permission **750**

if I try:

**force directory mode = 0777**

is resulting in linux-file-permission **755**

It seems like something is unmasking the file-permission.

Any ideas how to solve this problem?


With kind regards, Ole

It looks like you're misunderstanding the parameters.
```
**force [COLOR="Red"]directory[/COLOR] mode = 0770**

is resulting in linux-[COLOR="Blue"]**file-permission**[/COLOR] **750**

```

Directory modes are for the creation of directories not the files in them.  There can be unexpected results if you first apply directory mask (for directories) or create mask (for files) parameters.  

For the most part I use the underlying file system security rather than Samba's modes and masks for may shares.  All of my Samba shares are created on ext4 file systems.  I can't tell by the information you have provided so I will just ask.  Is this share on an ext3 or 4 formatted partition?

---

### Post by tetzschner on 2012-12-05
Hi bab1

I know. I was just using the term **file-pemission** for both files and directory.

But anyway, thanks for your reply.

Kind regards, Ole

---

### Post by tetzschner on 2012-12-05
Hi Morbius1

You are very dedicated in helping other ubuntu users and I'm very grateful for that.

The problem is solved.

On the same server there is another share that does not have the **valid users** limit (all smb users have full access to this share). It is the only difference (except **path** of course). This share is behaving as expected.

So the first conclusion are that **valid users** are causing the problem.

Therefore I tried to change **UMASK** (in /etc/login.defs) to 002. This solved the problem.

Thanks for all the advices.

Kind regards, Ole

---

### Post by jrssystemsnet on 2013-04-10
> **tetzschner said:**
> I tried to change **UMASK** (in /etc/login.defs) to 002. This solved the problem.

**YES!**  This, finally, fixed this issue for me.  Nothing else did - force create, force security, unix extensions, nothing else worked.  THIS did.  THANK YOU!

---

### Post by robert-oswald on 2013-09-05
Hi,

for me the problem got solved by setting:
 
[global]
  obey pam restrictions = no

[share]
   create mask = 000
   directory mask = 000
   force create mode = 660   #permissions I want on all files
   force directory mode = 770 #permissions I want on all directories


Obey pam restrictions is overriding masks and create modes on pre existing files and folders and pulls the umask bits. 
Unfortunately it´s enabled in Ubuntus default smb.conf, samba default is "no".

Cheers

---

### Post by jrssnet on 2013-09-05
> **robert-oswald said:**
> Hi,

for me the problem got solved by setting:
 
[global]
  obey pam restrictions = no

[share]
   create mask = 000
   directory mask = 000
   force create mode = 660   #permissions I want on all files
   force directory mode = 770 #permissions I want on all directories


Obey pam restrictions is overriding masks and create modes on pre existing files and folders and pulls the umask bits. 
Unfortunately it´s enabled in Ubuntus default smb.conf, samba default is "no".

Cheers

Oh, excellent - thank you Robert-Oswald, this is much better than diddling with the umask.  I really just want what I set in smb.conf to be **obeyed** by Samba, not have to go diddling around all over the system!

---

