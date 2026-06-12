---
title: "Change permissions automatically for new files added to folder"
date: 2013-10-20
forum: General Help
---

### Post by miceagol on 2013-10-20
I have a folder **/home/filer/felles**, where I want all files added to get read and write permissions for a specific group. I have applied the command
```
sudo chmod g+s /home/filer/felles
``` 
which applies the parent folder group to all new files.

However, even if the parent folder **felles** is writeable to the group, all new files added only becomes readable to the group.

Is there anyway to make all files added to the folder automatically read & write for the group?

---

### Post by Morbius1 on 2013-10-22
I haven't spent much time with 13.10 yet ( I have these little non-LTS releases in a VBox VM ) but if you open a terminal and type:
```
umask
```
You will notice that it comes back with 0022 which means that any new file created will have permissions of 644. This is different from what it did the last few releases where the default was 0002. The "g+s" setting requires that new files have permissions of 664. You can always set umask to 002 in .bashrc if you spend your whole life in the terminal and make sure every other user does the same but it won't help you if you use Nautilus. All of the other 642 places ( that may be a slight exaggeration ) where you can set umask don't seem to work either and that's when I found a bug report: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1240686)

This was found so early after the 13.10 release the fix may actually show up in 13.10 eventually so if you are patient it will fix itself. Otherwise it will end up in 14.04.

If you can't wait I have a suggestion and that is to take control of the situation yourself with bindfs. Try the following experiment to see how this works:
[1] Install bindfs
```
sudo apt-get install bindfs
```
[2] Create a couple of Test directories

*** Create a hidden directory:
```
sudo mkdir /.Test
```
*** And an non-hidden directory:
```
sudo mkdir /Test
```
*** Use bindfs to mount one to the other:
```
sudo bindfs -o perms=0660:+X,force-group=plugdev /.Test /Test
```
Now copy a file to /Test. It's permissions will be 660 and it's group will be plugdev. To undo the mount:
```
sudo umount /Test
```
[COLOR=#0000cd]* Note: The only reason I chose plugdev as the group is that it's already available.*[/COLOR]

To make this permanent you have a couple of options:

*** Add the line without sudo to rc.local
*** Or, Add a line to /etc/fstab with a different syntax:
```
bindfs#/.Test    /Test    fuse    perms=0660:+X,force-group=plugdev    0    0
```
*** Or, The way I do this is with an Upstart Job which is in my opinion the most reliable and safest way to do these sorts of things:

_*Create an upstart file:*_
```
gksu gedit /etc/init/bindfs-mounts.conf
```
_*With this content:*_
```
# Remount Directories with Bindfs
#
description "Bindfs Remounts"

start on stopped mountall

script
bindfs -o perms=0660:+X,force-group=plugdev /.Test /Test
end script
```

---

