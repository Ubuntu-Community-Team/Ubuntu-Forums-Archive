---
title: "change privileges on mounted external volumes"
date: 2014-10-13
forum: General Help
---

### Post by Cbhihe on 2014-10-13
I cannot change owner or privileges on two mounted NTFS and FAT external volumes. I have gotten rid of the nosuid option in the automount config I have, thinking I had a problem there. My fstab file looks like:

```
UUID=8AA83F90A83F7A31 /mnt/Music-hold ntfs-3g defaults,rw,users,suid,auto,locale=en_US.UTF-8,x-g
vfs-show 0 0
UUID=16F00142077A6EAE /mnt/TW_DB-BIN auto nofail,ro,user,nodev,exec,suid,x-gvfs-show,x-gvfs-name=tw_db-bin 0
 0
```
_From Terminal_, I still can't do - on either volumes :
```
sudo chown user-name:user-name /mnt/Music-hold
sudo chmod -R g+rwx /mnt/Music-hold
```

_From GUI_, I ran [FONT=courier new]gksu[/FONT] to launch [FONT=courier new]nautilus[/FONT] and change privileges from the 'properties' sub-menu of the volume. 
 I get what I have seen repeatedly on UF's posts: zero change.

What gives ? Am I missing something in my fstab file ? Can someone help ?
Cheers.

---

### Post by TheFu on 2014-10-13
NTFS and fat-whatever do not support permission controls in the file system.
The only way to control those is at mount time using uid= and gid= options.

If you need UNIX permission controls, then I'm afraid you need to use a UNIX file system.

At least as far as I know.

---

### Post by Cbhihe on 2014-10-16
@TheFu:
So, for an  external device volume /dev/sdb1, declared as NTFS-3g, 
I set the following options on the relevant line of my [FONT=courier new]/etc/fstab[/FONT]:
```
rw,users,auto,uid=1000*[SIZE=1](that's me)[/SIZE]*,umask=0002,...
```
By default, [FONT=courier new]gid=0[/FONT][FONT=courier new][SIZE=2][FONT=system]. 

[/FONT][/SIZE][/FONT]I wanted to set umask to 6002, but it is not possible to specify the first octal digit in the umask value. Makes you kind of wonder why it's there in the first place, if it cannot be used.
[FONT=courier new][SIZE=2][FONT=system]
[/FONT][/SIZE][/FONT]I mounted the volume /dev/sdb1 and as expected, I got for directories:
```
> ls -la _/my-path/any-directory_
drwxrwxr-x   my-user-name   root  .... 
> sudo chmod -R ug+s _/my-path/any-directory_
> ls -la _/my-path/any-directory_
drwxrwxr-x    my-user-name   root ... 
```
not at all what I wanted ! I want [FONT=courier new]drwsrwsr-x[/FONT], so i tried:
```
> su; find /_my-path_ -type d -exec chmod ug+s '{}' \; exit
```
And that did not produce any result either, no error message (syntax of command is correct anyway). Nothing but a quiet exit 0.

So I guess any file system not Ux or Ux-like not only does not support usual rwx permission tweaks from the command-line but also can take neither +s nor +t. 

Bummer.

---

