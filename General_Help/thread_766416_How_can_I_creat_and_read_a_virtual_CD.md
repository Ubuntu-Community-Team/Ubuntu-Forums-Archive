---
title: "How can I creat and read a virtual CD?"
date: 2008-04-25
forum: General Help
---

### Post by Vietred on 2008-04-25
I have just switch from Windows Xp to Kubuntu 7.10 and I'm totally new to Linux. Can I create and read a virtual CD(iso file) with Kubuntu 7.10 like I do it on Windows XP by using Blindread and Daemon Tools?[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by justleen on 2008-04-25
to mount an iso file on /media/iso/ :
```
 sudo mount -o loop -t iso9660 <filename.iso> /media/iso/ 
```

to create an iso image, you can use dd
```
 dd if=/media/cdrom of=/home/username/image.iso

```

---

### Post by kpkeerthi on 2008-04-25
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)
[http://www.acetoneiso.netsons.org/viewpage.php?page_id=1](http://www.acetoneiso.netsons.org/viewpage.php?page_id=1)

debs are available from their home pages.

---

### Post by russo.mic on 2008-04-25
Easier way is of course to use K3B or something and just burn a cd to an image rather than to your burner.

Russo

---

### Post by Vietred on 2008-04-25
> **justleen said:**
> to mount an iso file on /media/iso/ :
```
 sudo mount -o loop -t iso9660 <filename.iso> /media/iso/ 
```

to create an iso image, you can use dd
```
 dd if=/media/cdrom of=/home/username/image.iso

```

When I try mounting my FIFA.iso on /media:/sda6/ by typing:
```
 sudo mount -o loop -t iso9660 <FIFA.iso> /media:/sda6/ 
```
```
 sudo mount -o loop -t iso9660 FIFA.iso /media:/sda6/ 
```
```
 sudo mount -o loop -t iso9660 /media:/sda6/FIFA.iso 
```
Konsole always report: "FIFA.iso:No such file or directory"

---

### Post by kpkeerthi on 2008-04-25
YOu need create the mount point first
```
sudo mkdir **[COLOR="Red"]/media/fifa[/COLOR]**
```
Then
```
sudo mount -o loop -t iso9660 /full/path/to/iso-file.iso **[COLOR="Red"]/media/fifa[/COLOR]**
```

---

### Post by Vietred on 2008-04-25
> **kpkeerthi said:**
> YOu need create the mount point first
```
sudo mkdir **[COLOR="Red"]/media/fifa[/COLOR]**
```
Then
```
sudo mount -o loop -t iso9660 /full/path/to/iso-file.iso **[COLOR="Red"]/media/fifa[/COLOR]**
```

It still not work.:| Nothing changed after I followed your guide.
I downloaded acetoneiso2_2.0.1_x86.deb and installed it. But how can I use it?

---

### Post by kpkeerthi on 2008-04-25
Can you post the 'exact' output from your terminal after you run this
```
sudo mount -t iso9660 /full/path/to/iso-file.iso /media/fifa -o loop 
```

---

### Post by kpkeerthi on 2008-04-25
Make sure your path to the iso file is correct.

---

### Post by kpkeerthi on 2008-04-25
> **Vietred said:**
> I downloaded acetoneiso2_2.0.1_x86.deb and installed it. But how can I use it?

There is a manual in acetoneiso website. Also search in [http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by Vietred on 2008-04-25
> **kpkeerthi said:**
> Can you post the 'exact' output from your terminal after you run this
```
sudo mount -t iso9660 /full/path/to/iso-file.iso /media/fifa -o loop 
```

sudo mount -t iso9660 /media:/sda6/FIFACD2.ISO /media/fifa/ -o loop
/media:/sda6/FIFACD2.ISO: No such file or directory
hongviet@Viet-PC:~$ sudo mount -o loop -t iso9660 /media:/sda6/FIFACD2.ISO /media/fifa
/media:/sda6/FIFACD2.ISO: No such file or directory

---

### Post by kpkeerthi on 2008-04-25
Apparently the path to ISO appears incorrect (as I could see from the command output). Where exactly is your ISO file located? Somewhere in your home directory?

---

### Post by kpkeerthi on 2008-04-25
**/media:/sda6/FIFACD2.ISO** does not appear to be valid. Are you trying to access **/media/sda6/FIFACD2.ISO**. Can you post the output of ```
ls -R /media
```? Do you have a folder by name **/media:**?

---

### Post by Vietred on 2008-04-25
> **kpkeerthi said:**
> **/media:/sda6/FIFACD2.ISO** does not appear to be valid. Are you trying to access **/media/sda6/FIFACD2.ISO**. Can you post the output of ```
ls -R /media
```? Do you have a folder by name **/media:**?

sudo mount -o loop -t iso9660 /media/sda6/FIFACD2.ISO /media/fifa
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Look like it scan all my HD when I type "ls -R /media" but I'm sure that the directory is right.

---

### Post by kpkeerthi on 2008-04-25
OK so you gave **/media:** last time. But it actually is **/media** and thats why it did work.
And ls -R /media will only list your /media and subfolders.

Change your command to
```
sudo mount -o loop /media/sda6/FIFACD2.ISO /media/fifa
```

or

```
sudo mount -o loop -t auto /media/sda6/FIFACD2.ISO /media/fifa
```

---

### Post by Vietred on 2008-04-25
> **kpkeerthi said:**
> OK so you gave **/media:** last time. But it actually is **/media** and thats why it did work.
And ls -R /media will only list your /media and subfolders.

Change your command to
```
sudo mount -o loop /media/sda6/FIFACD2.ISO /media/fifa
```

or

```
sudo mount -o loop -t auto /media/sda6/FIFACD2.ISO /media/fifa
```

sudo mount -o loop -t auto /media/sda6/FIFACD2.ISO /media/fifa
mount: you must specify the filesystem type
When I click on "Storage Media" in Konqueror, the location bar display "media:/". But when I go to folder media from root, it display "/media"

---

### Post by Vietred on 2008-05-21
I know what's my problem. sda6 is a windows partition (NTFS format). If I move the ISO file to my home folder and follow your guide, it'll work well. Sorry for annoying. :)
PS: I can't add files to soundkonverter from a windows partition too.

---

