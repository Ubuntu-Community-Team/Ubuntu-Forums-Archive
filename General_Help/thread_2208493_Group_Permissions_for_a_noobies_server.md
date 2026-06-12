---
title: "Group Permissions for a noobies server"
date: 2014-02-28
forum: General Help
---

### Post by Gannas on 2014-02-28
[SIZE=2]Hi all! I'm having a problem with accessing a directory on my ubuntu (12.04) samba server. First the background. I have four users on this server, 1 the sudo then[/SIZE] 3 other users with permissions of 0750. Now these users can access their own home directory's and create files for themselves. Here comes the problem I'm having. I created a group "houseshare" and added all users to it. I then created a directory called "housefiles" and then chown the group to it. I then exited my terminal and accessed my personal user account using filezilla. I could do my normal things within my home directory, which I had previously done ( uploading/download photos, music etc ). But when I tried to access the dir "housefiles" I could look in it, with filezilla. But I couldn't do anything else. So I need to change the permissions for the group, I'm thinking. I haven't done this as of yet, since I'm still new to ubuntu. So I'm asking for any kind of direction to fix this and I could learn from. Also I haven't done anything to filezilla as in changed settings, etc.

---

### Post by sandyd on 2014-02-28
> **Gannas said:**
> [SIZE=2]Hi all! I'm having a problem with accessing a directory on my ubuntu (12.04) samba server. First the background. I have four users on this server, 1 the sudo then[/SIZE] 3 other users with permissions of 0750. Now these users can access their own home directory's and create files for themselves. Here comes the problem I'm having. I created a group "houseshare" and added all users to it. I then created a directory called "housefiles" and then chown the group to it. I then exited my terminal and accessed my personal user account using filezilla. I could do my normal things within my home directory, which I had previously done ( uploading/download photos, music etc ). But when I tried to access the dir "housefiles" I could look in it, with filezilla. But I couldn't do anything else. So I need to change the permissions for the group, I'm thinking. I haven't done this as of yet, since I'm still new to ubuntu. So I'm asking for any kind of direction to fix this and I could learn from. Also I haven't done anything to filezilla as in changed settings, etc.

By default - directories are chmoded 755 - which means that
[LIST]
[*]The owner has full permissions
[*]The group that the folder belongs to has permission to enter the directory and read files
[*]Anyone else has permission to enter the directory and read files
[/LIST]

This can be illustrated by creating a folder, and performing ls -l
```

resurrectedstar@TinaFey:~# sudo mkdir /mount/1
resurrectedstar@TinaFey:~# ls -l /mount
drwxr-xr-x  2 root   root        4096 Feb 28 12:28 1

```
In the first column, the first letter 'd' indicates that it is a directory, the next three letters denote the owner's permissions (rwx), the next three letters after that denote the group's permission (rx) where permissions that are not set are marked with a '-'. The last three letters in the first column denote the permissions that any other users have.

You will want to chmod the directory to 775 - which will mean
[LIST]
[*]The owner has full permissions
[*]The group that the folder belongs to has full permissions
[*]Anyone else has permissions to enter the directory and read files
[/LIST]
```

resurrectedstar@TinaFey:~# sudo chmod 775 /mount/1
resurrectedstar@TinaFey:~# ls -l /mount
drwxrwxr-x  2 root   root        4096 Feb 28 12:28 1
```
If you want to write to files inside the folder that already exist, you will have to chmod those files to 664 (by default, they are 644)

---

### Post by bab1 on 2014-02-28
> **Gannas said:**
> Hi all! I'm having a problem with accessing a directory on my ubuntu (12.04) samba server. First the background. I have four users on this server, 1 the sudo then 3 other users with permissions of 0750. Now these users can access their own home directory's and create files for themselves. Here comes the problem I'm having. I created a group "houseshare" and added all users to it. I then created a directory called "houseflies" and then chown the group to it. I then exited my terminal and accessed my personal user account using filezilla. I could do my normal things within my home directory, which I had previously done ( uploading/download photos, music etc ). But when I tried to access the dir "housefiles" I could look in it, with filezilla. But I couldn't do anything else. So I need to change the permissions for the group, I'm thinking. I haven't done this as of yet, since I'm still new to ubuntu. So I'm asking for any kind of direction to fix this and I could learn from. Also I haven't done anything to filezilla as in changed settings, etc.

I assume you created the directory *houseflies* **outside of the /home file system**.  When you create a directory where group ownership and permissions control access your should do something like this:

[LIST]
[*]Create the directory (sudo mkdir -p /srv/samba/housefiles)
[*]Set group ownership (sudo chown root:houseshare /srv/samba/housefiles)
[*]Set the correct correct file permissions (sudo chmod 2775 /srv/samba/housefiles)
[/LIST]

At this point you have a container that will hold a the common files and directories.  Any file or directory created will have the group user of *houseshare*.  This inheritance is set by the leading 2 (in 2775) of the chmod command.  The default umask should be 0002 so all files will have permissions of 0664 and directories will have permissions of 2775.

The only problem with this is a bug in Ubuntu 13.10 with Gnome/Unity.  This reverted the umask to 0022 which create files with 0644 and directories with 0755.  There is a fix for this to bring 13.10 back the the umask that is set in earlier Ubuntu versions and the upcoming 14.04 LTS version.  If you are running 13.10 you can follow these instructions```


install **[COLOR="#0000FF"]upstart 1.11-0ubuntu1[/COLOR]** from Trusty (14.04)

    Download latest published package for your architecture:
   [URL="https://launchpad.net/ubuntu/trusty/+package/upstart"] https://launchpad.net/ubuntu/trusty/+package/upstart
[/URL]
    Install with:
    sudo dpkg -i upstart_1.11-*.deb

    Reboot.


```...I have applied this patch myself and it works fine.

You can read about this bug (#1240686) [here]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686").

---

### Post by bab1 on 2014-02-28
> **sandyd said:**
> By default - directories are chmoded 755 - which means that
[LIST]
[*]The owner has full permissions
[*]The group that the folder belongs to has permission to enter the directory and read files
[*]Anyone else has permission to enter the directory and read files
[/LIST]

This can be illustrated by creating a folder, and performing ls -l
```

resurrectedstar@TinaFey:~# sudo mkdir /mount/1
resurrectedstar@TinaFey:~# ls -l /mount
drwxr-xr-x  2 root   root        4096 Feb 28 12:28 1

```
In the first column, the first letter 'd' indicates that it is a directory, the next three letters denote the owner's permissions (rwx), the next three letters after that denote the group's permission (rx) where permissions that are not set are marked with a '-'. The last three letters in the first column denote the permissions that any other users have.

You will want to chmod the directory to 775 - which will mean
[LIST]
[*]The owner has full permissions
[*]The group that the folder belongs to has full permissions
[*]Anyone else has permissions to enter the directory and read files
[/LIST]
```

resurrectedstar@TinaFey:~# sudo chmod 775 /mount/1
resurrectedstar@TinaFey:~# ls -l /mount
drwxrwxr-x  2 root   root        4096 Feb 28 12:28 1
```
If you want to write to files inside the folder that already exist, you will have to chmod those files to 664 (by default, they are 644)

The root directory of the shared file system needs to have the sgid bit set so the group ownership will continue.  This means 2775 rather than 0775.  The OP's version is important to check so the umask bug doesn't bite the users.

---

