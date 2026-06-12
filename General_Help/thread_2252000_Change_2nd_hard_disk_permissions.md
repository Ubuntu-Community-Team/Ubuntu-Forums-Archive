---
title: "Change 2nd hard disk permissions"
date: 2014-11-08
forum: General Help
---

### Post by Kandoni on 2014-11-08
Hi,

I have a laptop with Ubuntu 14.04 installed, where I have a second hard disk that is mounted. I want to use it as My Folder for all kind of files (pictures,  documents, music...) in order to have the main hard disk only for the  distro and temporal things. [URL="http://www.fotolibre.org/albums/userpics/10071/Captura_de_pantalla_de_2014-11-08_14_54_12.png"]


[IMG]http://www.fotolibre.org/albums/userpics/10071/normal_Captura_de_pantalla_de_2014-11-08_14_54_12.png[/IMG][/URL]

The problem is that I can't modify (write, change, erase,...) any file on it. 

When I check the permissions, only the root can change or modify the disk
[URL="http://www.fotolibre.org/albums/userpics/10071/Captura_de_pantalla_de_2014-11-08_14_55_06.png"]
[IMG]http://www.fotolibre.org/albums/userpics/10071/normal_Captura_de_pantalla_de_2014-11-08_14_55_06.png[/IMG][/URL]

[[IMG]http://www.fotolibre.org/albums/userpics/10071/normal_Captura_de_pantalla_de_2014-11-08_14_55_17.png[/IMG]]("http://www.fotolibre.org/albums/userpics/10071/Captura_de_pantalla_de_2014-11-08_14_55_17.png")

I have tryied to change permissions running ```
gksudo nautilus
``` but I can't see the directory to the 2nd. hard disk when I open nautilus as a root.

Could I use the command ***chmod*** to change permissions from the terminal? How can I see this second harddisk directory from the terminal?

```
usuario@Mountain:~$ ls
Descargas   Escritorio        Imágenes  Plantillas  Release.key    Vídeos
Documentos  examples.desktop  Música    Público     Release.key.1
usuario@Mountain:~$ cd /
usuario@Mountain:/$ ls
bin    dev   initrd.img      lib64       mnt   root  srv  usr      vmlinuz.old
boot   etc   initrd.img.old  lost+found  opt   run   sys  var
cdrom  home  lib             media       proc  sbin  tmp  vmlinuz
usuario@Mountain:/$ 
```

Is the problem just a permission problem or should I change anything else in order to get mounted in other way when I turn on the laptop?

Sorry if this is a very simple question, I am not very skilled with computers. :(

Thanks a lot in advance,

Kandoni

---

### Post by coffeecat on 2014-11-08
The lost+found folder in the partition on the second hard drive tells us it is formatted with a Linux filesystem and all you have to do is run a chown command on the mountpoint while it is mounted, this:

```
sudo chown usuario: /path/to/mountpoint
```

That is, assuming you want write permissions for user usuario. With the file manager open as in your first screenshot, press ctrl-L to get the full path and then post this and I can modify that command for you. it will be something like /media/usuario/something.

---

### Post by oldfred on 2014-11-08
Please attache screen shots not post in line. Not everyone has high speed Internet.
You can easily attach with paperclip icon in advanced editor.

I also like to set both ownership and permissions to be consistent. I also mount partition in /mnt and link the folders directly into /home in place of defaults. I do that when I do a new install so I know defaults have no files otherwise they would be lost. Or you can mount each folder in fstab to directly see them.

With Linux better not to use spaces anywhere as then you have to escape the space or always use quotes around "My Folder". Better to use CamelCase like MyFolder, or underscore like my_folder, or just myfolder.

Note that -R is recursion. All lower level folders & files will also be changed. Never run on system partition.
 sudo chown -R $USER:$USER /mnt/data

   chmod -R a+rwX,go-w /path/to/folder
sudo chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[URL="http://ubuntuforums.org/showthread.php?t=1983336"]
http://ubuntuforums.org/showthread.php?t=1983336[/URL]
 Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

 Mount with Disks -  post by monkeybrain20122 but I would create my own mount point and best to understand configuration options first
[http://ubuntuforums.org/showthread.php?t=2250717&p=13160317#post13160317](http://ubuntuforums.org/showthread.php?t=2250717&p=13160317#post13160317)

Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

---

### Post by Kandoni on 2014-11-08
> **coffeecat said:**
> The lost+found folder in the partition on the second hard drive tells us it is formatted with a Linux filesystem and all you have to do is run a chown command on the mountpoint while it is mounted, this:

```
sudo chown usuario: /path/to/mountpoint
```

That is, assuming you want write permissions for user usuario. With the file manager open as in your first screenshot, press ctrl-L to get the full path and then post this and I can modify that command for you. it will be something like /media/usuario/something.

Ok, first, if I press ctrl-L I get:

/media/usuario/6851987c-c690-4c77-91d6-95b96f255eba

So the command line path in the terminal should be:

```
sudo chown usuario: /media/usuario/6851987c-c690-4c77-91d6-95b96f255eba

```

shouldn't it?

I am the only user of the laptop, so there shouldn't be a problem for the write permissions for usuario.

---

### Post by coffeecat on 2014-11-08
> **Kandoni said:**
> So the command line path in the terminal should be:

```
sudo chown usuario: /media/usuario/6851987c-c690-4c77-91d6-95b96f255eba

```

shouldn't it?

Yes. That will do it.

> **Kandoni said:**
> I am the only user of the laptop, so there shouldn't be a problem for the write permissions for usuario.

Agreed. If you are the only user you don't need any chmod commands.

The mountpoint shows that you have mounted he partition from the file manager, which is fine. If you want the partition mounted every time you boot up, then you will need to edit /etc/fstab and consider whether you want to create a mountpoint in /mnt or /media. oldfred has posted some useful stuff and this exemplifies the difference personal preference has. oldfred prefers /mnt - I prefer /media!

Once you have run the chown command, you don't need to do anything if you subsequently mount in a different mountpoint. Running chown on a mounted filesystem via a mountpoint has the slightly curious effect of changing the ownership of the filesystem itself, not the mountpoint.

---

### Post by Kandoni on 2014-11-08
> **oldfred said:**
> Please attache screen shots not post in line. Not everyone has high speed Internet.
You can easily attach with paperclip icon in advanced editor.

I also like to set both ownership and permissions to be consistent. I also mount partition in /mnt and link the folders directly into /home in place of defaults. I do that when I do a new install so I know defaults have no files otherwise they would be lost. Or you can mount each folder in fstab to directly see them.

With Linux better not to use spaces anywhere as then you have to escape the space or always use quotes around "My Folder". Better to use CamelCase like MyFolder, or underscore like my_folder, or just myfolder.

Note that -R is recursion. All lower level folders & files will also be changed. Never run on system partition.
 sudo chown -R $USER:$USER /mnt/data

   chmod -R a+rwX,go-w /path/to/folder
sudo chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[URL="http://ubuntuforums.org/showthread.php?t=1983336"]
http://ubuntuforums.org/showthread.php?t=1983336[/URL]
 Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

 Mount with Disks -  post by monkeybrain20122 but I would create my own mount point and best to understand configuration options first
[http://ubuntuforums.org/showthread.php?t=2250717&p=13160317#post13160317](http://ubuntuforums.org/showthread.php?t=2250717&p=13160317#post13160317)

Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

Hi oldfred,

The screen shots are linked to the big images by a url, so I thought the images in the post shouldn't be very large. If I have to change something, let me know please, I don't want to make the post very heavy.

I don't have problems changing the permissions in the lower level folders and files, right now the hard disk is empty.

I have to check all the links you give me here in order to learn more  about directing the /home folders to new folders in the mounted 2nd.  hard disk, in order to have the 1st. hard disk just for the sistem and to avoid problems in updates or installations of new distros. But I am sure I will get more questions about it... ;)

Thanks for the quick answer for you and coffeecat, ;)

---

### Post by Kandoni on 2014-11-08
> **coffeecat said:**
> 
The mountpoint shows that you have mounted he partition from the file manager, which is fine. If you want the partition mounted every time you boot up, then you will need to edit /etc/fstab and consider whether you want to create a mountpoint in /mnt or /media. oldfred has posted some useful stuff and this exemplifies the difference personal preference has. oldfred prefers /mnt - I prefer /media!

Once you have run the chown command, you don't need to do anything if you subsequently mount in a different mountpoint. Running chown on a mounted filesystem via a mountpoint has the slightly curious effect of changing the ownership of the filesystem itself, not the mountpoint.

Thanks a lot for your help, that solved my problem and I can add files and folders to the 2nd. disk.

As you say, oldfred has posted some links I have to read to learn more about all this. If I have more doubts I will search for them in the forum and if I don't get the clue I will open a new post.

Thank you both for your quick help. ;)

Kandoni

---

### Post by Kandoni on 2014-11-08
By the way, How can I change the title of the post to mark it as SOLVED?

---

### Post by coffeecat on 2014-11-08
It is. Perhaps you found the thread tools? :)

---

