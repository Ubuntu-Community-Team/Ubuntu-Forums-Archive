---
title: "samba. Cannot follow sym links"
date: 2012-10-18
forum: General Help
---

### Post by Drenriza on 2012-10-18
Hey guys.

I have a samba share as follows
```

#======================= Share Definitions =======================

[video1]
   comment = 2.5_Video1_share
   path = /srv/samba/content/path
   follow symlinks = yes
   wide links = yes
   unix extensions = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   ;read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   ;create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   ;directory mask = 0700
   
valid users = nice

```

I can mount and ls the content of the mounted folder just fine on a remote (debian server) system.

But i cannot follow symlinks outside the share.

File permissions on the /srv/ folder recursively is 644 and 777 for symlinks.

Anyone who has a suggestion?

Kind regards.

---

### Post by SlugSlug on 2012-10-18
Are the permissions for the parent directory's where the symlinks point to set?

---

### Post by Drenriza on 2012-10-18
> **SlugSlug said:**
> Are the permissions for the parent directory's where the symlinks point to set?

To test this off this is how the structure is

share is at

/srv/samba/content/path

symbolic link 1

from /srv/test/Xfolder/folderX to /srv/samba/content/path/folderX

symbolic link 2

from /srv/test/Yfolder/Y.mpeg to /srv/samba/content/path/folderX/Y.mpeg

and
> File permissions on the /srv/ folder recursively is 644 and 777 for symlinks.

---

### Post by Drenriza on 2012-10-18
Can the issue be that my share is commented out with the 3 following lines

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   ;read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   ;create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   ;directory mask = 0700

From my understanding permissions on the share and symbolic links will follow?

So if they have 744 rights those rights will follow to where the share is mounted?

---

### Post by SlugSlug on 2012-10-18
I think the path to where your pointing to also needs the permissions.

To test try a sym link to /tmp  and chmod it 777

---

### Post by Drenriza on 2012-10-18
> **SlugSlug said:**
> I think the path to where your pointing to also needs the permissions.

To test try a sym link to /tmp  and chmod it 777

created a text.txt file containing test in /tmp and chmod'ded it with 777 permissions, and linked it to my share with

```
ln -s /tmp/test.txt /srv/samba/content/path/
```

But when i on my remote machine, where i have mounted the share make a 

```
ls -l /video1/
```
ls: cannot read symbolic link /video1/test.txt: Permission denied
ls: cannot read symbolic link /video1/21JumpStreet_EN: Permission denied

---

### Post by SlugSlug on 2012-10-18
> **Drenriza said:**
> created a text.txt file containing test in /tmp and chmod'ded it with 777 permissions, and linked it to my share with

```
ln -s /tmp/test.txt /srv/samba/content/share/
```But when i on my remote machine, where i have mounted the share make a 

```
ls -l /video1/
```ls: cannot read symbolic link /video1/test.txt: Permission denied
ls: cannot read symbolic link /video1/21JumpStreet_EN: Permission denied


ok and if you put a text file in  /srv/samba/content/share/  can you read it?

---

### Post by SlugSlug on 2012-10-18
dunno if its a typo but
/srv/samba/content/share/

is diffrent to whats in your smb.conf

---

### Post by Drenriza on 2012-10-18
> **SlugSlug said:**
> dunno if its a typo but
/srv/samba/content/share/

is diffrent to whats in your smb.conf

Corrected it in my posts.

---

### Post by Drenriza on 2012-10-18
> **SlugSlug said:**
> ok and if you put a text file in  /srv/samba/content/share/  can you read it?

Yes.

If i move it from /tmp to my share, then i can cat the file on the remote host in the mounted share.

It's only as a sym link i have the issue.

---

### Post by SlugSlug on 2012-10-18
is the /tmp dir 777'd ?

---

### Post by Drenriza on 2012-10-18
> **SlugSlug said:**
> is the /tmp dir 777'd ?

/tmp
drwxrwxrwt   4 root root  4096 Oct 18 12:40 tmp

shared folder 
drwxr-xr-x 2 root root 4096 Oct 18 12:25 path

---

### Post by Drenriza on 2012-10-18
If anyone with samba experience can give advice on what to test, try or something else.

Then your most welcome :)

---

### Post by Drenriza on 2012-10-18
I took this line from my share

```
unix extensions = no
```

deleted it from my share

and placed it in global.

Now all works ^_-

Anyone who can tell me why? What difference does it do?

---

