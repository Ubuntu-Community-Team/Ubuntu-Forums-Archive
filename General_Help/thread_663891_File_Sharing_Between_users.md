---
title: "File Sharing Between users"
date: 2008-01-10
forum: General Help
---

### Post by shavenlunatic on 2008-01-10
Hi,

I've read a few threads on here relating to sharing folders between 2 users on 1 machine but couldn't seem to find a solution to my problem:

I have a torrents folder which I created as /usr/share/Downloads/Torrents/

I have 2 users on the machine, A & B

I creaded a group (named dls) and added both user A and user B to this group.  Now looking at the "Downloads" and "Torrents" folder permissions I see

Owner: Root  (create & delete files)
Group: dls (create & delete files)

So, all looks well.  Unfortunately, if user A sets off a file downloading into the folder (or creates a folder in there), user B has no write access to these files (they show with a padlock next to the icon when user B is logged in).. and vice-versa

Any ideas?

---

### Post by shavenlunatic on 2008-01-10
hmm, just had an additional thought.. if what I am looking to do is a bit of a headache.. would an alternative be possible...

say I'm using deluge to download the torrents, is it possible to run deluge as user A while logged in as user B?  (much like the sudo command but with another user...

---

### Post by peitschie on 2008-01-10
Hi :)

Can you open a terminal to the /usr/share/Downloads/Torrents/ and post the results of running the following command:
```
ls -Rl
```

This will tell us what the permissions on each file/folder are.

It is possible to do what you want, without too much hassle I believe by modifying the default file umask (see [http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html) for a good explanation).

---

### Post by capink on 2008-01-10
I get around this problem by dowloading torrents into fat32 partition mount with the option umask=002

If you don't have any fat32 try adding the option grpid=groupid to your  ext2/3 partition in fstab. I have not tried this option and I do not recommed adding it to your root partition.


> grpid or bsdgroups / nogrpid or sysvgroups
              These  options  define  what group id a newly created file gets.
              When grpid is set, it takes the group id  of  the  directory  in
              which  it is created; otherwise (the default) it takes the fsgid
              of the current process, unless the directory has the setgid  bit
              set,  in  which case it takes the gid from the parent directory,
              and also gets the setgid bit set if it is a directory itself.

---

### Post by jken146 on 2008-01-10
You could write a bash script to change the permissions (recursively) of the directory you want to share.  It could be run at startup or shutdown or maybe logoff.  It would need to be run as root.

---

### Post by shavenlunatic on 2008-01-11
> **peitschie said:**
> Hi :)

Can you open a terminal to the /usr/share/Downloads/Torrents/ and post the results of running the following command:
```
ls -Rl
```

This will tell us what the permissions on each file/folder are.



quite a long list so I'll just post some snippets (and edit to protect the innocent :) )

```

./A TV Series.S07E03.PDTV.XviD-XOR:
total 179476
drwxrwxrwx 2 USERB USERB     4096 2007-11-11 19:58 Sample
-rw-rw-rw- 1 USERB USERB      441 2007-11-11 20:26 A TV Series.s07e03.pdtv.xvid-xor.nfo
-rw-rw-rw- 1 USERB USERB 15000000 2007-11-11 20:38 A TV Series.s07e03.pdtv.xvid-xor.r00


./A Different TV Series.S02E08.HDTV.XviD-LOL:
total 358692
-rw-rw-rw- 1 USERA USERA     4036 2007-11-13 21:59 A Different TV Series.208.hdtv-lol.nfo
-rw-rw-rw- 1 USERA USERA 15000000 2007-11-13 22:38 A Different TV Series.208.hdtv-lol.r00

```

hope that sheds a little light on it, I'll take a read of the link you posted shortly and see what I can make of it..cheers :)



> I get around this problem by dowloading torrents into fat32 partition mount with the option umask=002

Yes, well, I do have an NTFS drive which I used to dump all my downloads to but a) it started getting full and b) gets upset if I download a file of 4GB in size :)

I guess using the NTFS drive is an option but it's more of a workaround than a solution... hopefully a last resort eh :)

---

### Post by MartynA on 2008-01-11
I wonder if SGID could solve this problem. The SGID (sticky group id, or something) will cause all new files created to have the group owner as the owner of the directory, no matter who caused the creation.

chmod g+s /usr/share/Downloads/Torrents/

If it doesn't work just use chmod g-s to remove it.

---

### Post by shavenlunatic on 2008-01-11
> **MartynA said:**
> I wonder if SGID could solve this problem. The SGID (sticky group id, or something) will cause all new files created to have the group owner as the owner of the directory, no matter who caused the creation.

chmod g+s /usr/share/Downloads/Torrents/

If it doesn't work just use chmod g-s to remove it.

giving it a whirl now ... cheers, Ill post findings

---

### Post by shavenlunatic on 2008-01-11
> **shavenlunatic said:**
> giving it a whirl now ... cheers, Ill post findings

ok, i ran

```
sudo chmod g+s /usr/share/downloads/Torrents/ 
```

created a test folder and created a test file within that folder, I logged out and in as other user.. folder shows as locked and file read only :(

---

### Post by capink on 2008-01-11
> **MartynA said:**
> I wonder if SGID could solve this problem. The SGID (sticky group id, or something) will cause all new files created to have the group owner as the owner of the directory, no matter who caused the creation.

chmod g+s /usr/share/Downloads/Torrents/

If it doesn't work just use chmod g-s to remove it.

SGID is not a not sticky bit or something similar. It stands of set group id. It is meant only for executable files. When an executable has the SGID set, anyone runnig this executable ( provided he have premission to run it ) well assume the same group as that of the executable. (he will not assume the group in the broad sense, only for operation performed by the executable).

Gtk Programs does not support SGID. If it did, we could have simply changed the group of the deluge executable and make it SGID. Then, every file created by deluge would have belonged to the group we wanted.

---

### Post by MartynA on 2008-01-11
Ok, can you confirm the permissions on those files?

I imagine the problem is that the new files are being created with the right group ownership, but with the wrong permissions. Thus, although they are being created belonging to group dls they still have default permissions on them.

---

### Post by MartynA on 2008-01-11
> **capink said:**
> SGID is not a not sticky bit or something similar. It stands of set group id. It is meant only for executable files. When an executable has the SGID set, anyone runnig this executable ( provided he have premission to run it ) well assume the same group as that of the executable. (he will not assume the group in the broad sense, only for operation performed by the executable).

Gtk Programs does not support SGID. If it did, we could have simply changed the group of the deluge executable and make it SGID. Then, every file created by deluge would have belonged to the group we wanted.

I believe SGID is intended for directories as well, I've tested it myself and it does work.

"In Linux and Solaris, when SGID is set on a directory files created in that directory will have their GID automatically reset to that of the directory's GID"

[http://www.hccfl.edu/pollock/AUnix1/FilePermissions.htm](http://www.hccfl.edu/pollock/AUnix1/FilePermissions.htm)

---

### Post by shavenlunatic on 2008-01-11
...

---

### Post by chrisccoulson on 2008-01-11
What you could use is ACL's (Access Control Lists) to set the shared permissions. ACL's are a lot more flexible than standard Unix file permissions, and you can set default permissions so that new files inherit these permissions. You can install acl support and also a GUI for modifying ACL's (which integrates with Nautilus) from the repository.

```
sudo apt-get install acl eiciel
```

Note, that you have to mount the filesystem with the 'acl' option to get ACL support. You'll need to specify the option in your /etc/fstab. I suggest you have a read online about ACL's.

As an example, I have a folder /home/shared which I want to only be readable by members of the group shared-ro and read/writable by members of a group called shared-rw. Files created by members of shared-rw should be writable by other members of shared-rw and readable by members of shared-ro, without having to mess about with scripts. I set the ownership of /home/shared to root:root and standard permissions to 750.

For the shared permissions, I use the following ACLs:
```
sudo setfacl -R -m g:shared-ro:rX /home/shared
sudo setfacl -R -m g:shared-rw:rwX /home/shared
```
which sets up all the permissions recursively for both groups. The '-m' is a modify switch, the 'g:' is for group (I would use 'u:' for specifying permissions of a user)

To set default permissions, I do:
```
sudo setfacl -R -m d:g:shared-ro:rX /home/shared
sudo setfacl -R -m d:g:shared-rw:rwX /home/shared
```
The 'd:' tells setfacl to set the default permissions, which all new files will inherit.

I think this is the type of thing you're after.

See:
```
man setfacl
```

Hope that all makes sense

---

### Post by MartynA on 2008-01-11
I think the only way we could do it with regular permissions would be to change the permissions on newly created files, which probably isn't a good idea. I would suggest following chrisccoulson's idea, if you need any help just post.

---

### Post by #Reistlehr- on 2008-01-11
I havent read everything here, but an idea would be umask the directory.

You can change the default permissions of files in the directory, to whichever you like.

remember umask subtracts permissions.

umask 022

will change the default of 666 to, 644 (rw-r--r--) and will change 777 to 755 (rwxr-xr-x).

the umask command is nomally defined in the .profile and sometimes .login which is loaded on startup. (i've seen it in .bashrc)

So if you 
chmod the dir with
```
chmod -R 777 /path/to/dir
```

and change the umask for both users, you shouldnt have a problem.

---

### Post by peitschie on 2008-01-11
Hiya.

Just to confirm, SGID sticky bits will not work.  They do set the group owner of the files to be the same, they DO NOT however set the file to the appropriate permissions (in this case 775 or 664), and hence the file stays read-only for the other user.

You can get around this by using umask, however, that affects your permission creation for ALL files, which is probably not the effect you want!

I think chrisccoulson's idea sounds promising, give that a whirl maybe and let us know how you go :)

---

### Post by shavenlunatic on 2008-01-24
> **chrisccoulson said:**
> What you could use is ACL's (Access Control Lists) to set the shared permissions. ACL's are a lot more flexible than standard Unix file permissions, and you can set default permissions so that new files inherit these permissions. You can install acl support and also a GUI for modifying ACL's (which integrates with Nautilus) from the repository.

```
sudo apt-get install acl eiciel
```

Note, that you have to mount the filesystem with the 'acl' option to get ACL support. You'll need to specify the option in your /etc/fstab. I suggest you have a read online about ACL's.

As an example, I have a folder /home/shared which I want to only be readable by members of the group shared-ro and read/writable by members of a group called shared-rw. Files created by members of shared-rw should be writable by other members of shared-rw and readable by members of shared-ro, without having to mess about with scripts. I set the ownership of /home/shared to root:root and standard permissions to 750.

For the shared permissions, I use the following ACLs:
```
sudo setfacl -R -m g:shared-ro:rX /home/shared
sudo setfacl -R -m g:shared-rw:rwX /home/shared
```
which sets up all the permissions recursively for both groups. The '-m' is a modify switch, the 'g:' is for group (I would use 'u:' for specifying permissions of a user)

To set default permissions, I do:
```
sudo setfacl -R -m d:g:shared-ro:rX /home/shared
sudo setfacl -R -m d:g:shared-rw:rwX /home/shared
```
The 'd:' tells setfacl to set the default permissions, which all new files will inherit.

I think this is the type of thing you're after.

See:
```
man setfacl
```

Hope that all makes sense

that's exactly what i needed, thanks fella

incidentally, to get acl working you need to edit /etc/fstab and replace 'defaults' with acl on the drive in question, reboot (or remount) and bob's your uncle..  :)

---

### Post by shavenlunatic on 2008-01-24
to add to  this, file permissions still eem to go screwy switching between users so I had to write a small script to ruun each time I launch deluge

```
#!/bin/bash
clear
gksu 'setfacl -R -m g:dls:rwX /home/shared'
gksu 'setfacl -R -m d:g:dls:rwX /home/shared'
deluge
```

---

### Post by bernardfrancois on 2008-02-03
What do you mean exactly with 'file permissions still seem to go screwy switching between users'? What happens when you don't use that script?

---

### Post by shavenlunatic on 2008-02-07
the original issue occurs if I don't use that script, the creator of the file takes control of it

---

### Post by grof on 2008-02-07
Hello,

I setup ACL on my ubuntu and it works. But it works on newly created folder and files in the folder where I set up default permissions. 

When I copy some other folder to the folder with default ACL permissions, this copied folder have not permissons from folder above. On other hand do not inherited permissons from parent folder. Why?

Why this works only on newly created folders but not on copied folders??

---

### Post by chrisccoulson on 2008-02-07
Good point! I see the same behaviour as well

---

### Post by grof on 2008-02-07
But why this happened??

---

### Post by grof on 2008-02-08
In my kubuntu 7.10 ACL works well with newly created folders/files, moved and copied existing folder/files into folder with ACL default permissions. I tried in Konqueror and Dolphin. All works good.

Today I will try with fresh copy of ubuntu 7.10 on my VirtualBox...

---

### Post by grof on 2008-02-08
Hmmm, if I install Dolphin into my ubuntu's GNOME, than Dolphin works well with ACL inheriting but Nautilus or Tunar do not.

If I try copy dirs and files on console, out of GNOME  with *cp* command than inheriting do not work.

So, it works only with Dolphin.

From other side, if I work in kubuntu, than works with Dolphin and Konqueror but do not with installed Nautilus or with *cp* command at console.

Now I do not understand anything...:confused:

---

