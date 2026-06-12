---
title: "Auto mounting network share using fstab"
date: 2013-01-15
forum: General Help
---

### Post by corydchurch on 2013-01-15
I am trying to auto mount a network ntfs share in Ubunutu. 

I have followed these instructions to the T using Ubuntu 12.10 [HTML]http://ubuntuforums.org/showthread.php?p=12456976#post12456976[/HTML]. After I do
```
sudo mount -a
```

I get
```
mount error (13): Permission denied
```

Can anyone help?

---

### Post by Cheesemill on 2013-01-15
What line did you add to your fstab file?
Can you post the result of...
```
cat /etc/fstab
```

---

### Post by papibe on 2013-01-15
Hi corydchurch. Welcome to the forums ):P

Although it may work, smbfs is a deprecated package. Try installing 'cifs-utils' instead. 

If that doesn't work, could you post the content of your /etc/fstab ?

Regards.

---

### Post by corydchurch on 2013-01-15
thanks for the fast response.

just like the link above instructed, here's my line in fstab:

```
//myurl/media /media/plex cifs auto,iocharset=utf8,uid=1000,gid=1000,credentials=/root/.cifcredentials,file_mode=0775,dir_mode=0775 0 0
```

of course for "myurl" I put my url to the network share.

and here's the entire fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=cbc1cb0d-bdb6-4363-b8b7-872e069b949a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5164db60-3507-4b4d-9229-790b86b5504c none            swap    sw              0       0
//myurl/media /media/plex cifs auto,iocharset=utf8,uid=1000,gid=1000,credentials=/root/.cifcredentials,file_mode=0775,dir_mode=0775 0 0

```

---

### Post by corydchurch on 2013-01-15
> **papibe said:**
> Hi corydchurch. Welcome to the forums ):P

Although it may work, smbfs is a deprecated package. Try installing 'cifs-utils' instead. 

If that doesn't work, could you post the content of your /etc/fstab ?

Regards.

Yes, I have also installed cifs-utils. does that change how I write up my line in fstab?

---

### Post by Cheesemill on 2013-01-15
You have a typo in your fstab file.
```
credentials=/root/.cifcredentials
```should be
```
credentials=/root/.cif[COLOR=Red]s[/COLOR]credentials
```If that's what you've called your credentials file.

---

### Post by corydchurch on 2013-01-15
no I know. I already created the credentials file and forgot the "s" so instead of renaming the file, I just omitted the "s" in the file name in fstab.

---

### Post by papibe on 2013-01-15
Try mounting the share manually on the command line to see if you get a more comprehensive error message:
```
sudo mount -ocredentials=/root/.cifcredentials -t cifs //myurl/media /media/plex
```
Let us know how it goes.
Regards.

---

### Post by corydchurch on 2013-01-15
I get the same thing as sudo mount -a

```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```


I am looking at that page now [HTML]http://linux.die.net/man/8/mount.cifs[/HTML]

but honestly not sure what to look for.

---

### Post by Cheesemill on 2013-01-15
Does your password have any special characters in it?

If so then you may have to surround your password with quotes in the /root/.cifcredentials file...
```
username=rob
password="my!$%password"
```

---

### Post by corydchurch on 2013-01-15
no special characters either. just a word and then a number as the password.

---

### Post by corydchurch on 2013-01-15
ok. I figured it out. I know ive had this issue before when all the settings were actually correct but this time, as my luck would have it, the username wasnt right in the credentials file. I recently changed my account name on my windows 7 machine (the machine to which the network share is actually hardwired) from "admin" to "cory" and I thought that new name was my account name but it looks like my windows account name is still admin. So I put "admin" in the credentials file, ran ```
sudo mount -ocredentials=/root/.cifcredentials -t cifs //10.0.1.10/media /media/plex

```
and it mounted. Like I said, this is the sort of luck Ive been having lately. 

Thanks everyone for your help.

---

### Post by papibe on 2013-01-15
:) Glad you worked it out.

Please mark the thread as Solved when you have the chance (read how to do it [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")).

Regards.

---

