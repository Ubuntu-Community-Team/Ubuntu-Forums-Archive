---
title: "Creating a virtual CD-ROM drive"
date: 2007-08-19
forum: General Help
---

### Post by digilink on 2007-08-19
I would like to create a read/write virtual CD-R drive under Ubuntu for creating ISO images and ripping tracks from iTunes in a vmware virtual machine (Windows XP Pro. 

I have been searching for the past two hours and I'm not coming up with anything :| I'm not eve sure what I want to do is possible. 

I have a dedicated 5gb partition I would like to use for this task. Basically, I want the ability to create a standard iso9660 filesystem that I can read/write to, and looks like  CD-R drive under windows so I can burn my iTunes tracks. 

I've been beating my head up against the wall and I'm hoping someone can help me!

---

### Post by UK-Wobbie on 2007-08-19
> **digilink said:**
> I would like to create a read/write virtual CD-R drive under Ubuntu for creating ISO images and ripping tracks from iTunes in a vmware virtual machine (Windows XP Pro. 

I have been searching for the past two hours and I'm not coming up with anything :| I'm not eve sure what I want to do is possible. 

I have a dedicated 5gb partition I would like to use for this task. Basically, I want the ability to create a standard iso9660 filesystem that I can read/write to, and looks like  CD-R drive under windows so I can burn my iTunes tracks. 

I've been beating my head up against the wall and I'm hoping someone can help me!

So you need something like [**DAEMON Tools**]("http://www.daemon-tools.cc/dtcc/index.php?") what can run ISO files on Windows Xp.. As a CD Drive?


I got something what is called [**AcetoneISO2 **]("http://www.acetoneteam.org/central.html") What can run ISO files like a Drive! It can run DVD ISO files to.
You may have to instill fuseiso from your download list! To get it working :)

For burning have a go on K3B :)

---

### Post by capink on 2007-08-19
To create an iso image:

```
mkisofs -o outputfile.iso -r -J -l /path/to/directory/to/create/the/iso/from
```



To mount an iso image:

```
sudo mount -o loop -t iso9660 /path/to/the/iso/file /mnt
```

---

### Post by thinsoldier on 2007-08-26
any way in the gui to do
sudo mount -o loop -t iso9660 /path/to/the/iso/file /mnt

or associate double clicking a .iso with a script that will perform
sudo mount -o loop -t iso9660 /path/to/the/iso/file /mnt

---

### Post by capink on 2007-08-26
> or associate double clicking a .iso with a script that will perform

You can do this in thunar as follow:

1. Goto Edit > Configure custom actions.

2. Add a New Custom Action by pressing on the ( + ) button.

3. Press on the basic tab and enter the following:


```
Name: Mount Iso
Description: Mount ISO on /mnt
Command: gksudo "umount /mnt" && gksudo "mount -o loop -t iso9660 %f /mnt"
```


4. Press the Appearance and conditions tab:

```
File Pattern:*.iso
```

and highlight only (Other files)


I don't use nautilus, but I think a similar solution using nautilus scripts would be possible. You will have to look for that.

---

### Post by thinsoldier on 2007-08-26
Acetoneiso2 doesnt live up to it's feature list but it does mount .iso files.
It won't convert .nrg to .iso and I deleted that .nrg before I remember to test mounting .nrg

---

### Post by tenjin1 on 2007-12-17
> **capink said:**
> You can do this in thunar as follow:

1. Goto Edit > Configure custom actions.

2. Add a New Custom Action by pressing on the ( + ) button.

3. Press on the basic tab and enter the following:


```
Name: Mount Iso
Description: Mount ISO on /mnt
Command: gksudo "umount /mnt" && gksudo "mount -o loop -t iso9660 %f /mnt"
```


4. Press the Appearance and conditions tab:

```
File Pattern:*.iso
```

and highlight only (Other files)


I don't use nautilus, but I think a similar solution using nautilus scripts would be possible. You will have to look for that.

Thx capink! I use Thunar too...but I use /media directory for all my mount points. That way I can see all the devices that are mounted in /media in my "Places" menu and also keep a clean desktop. So for anyone who would rather mount in /media instead of /mnt....try this.
.
I am using a different command and it works beautifully for mounting/unmounting a ISO file. First I made a directory called iso in /media/iso.
```
sudo mkdir /media/iso
```

then in Thunar..
-Edit > Configure custom actions.

-Add a New Custom Action by pressing on the ( + ) button.

```
Name: Mount ISO
Description: Mount ISO 
Command: sudo mount %f -o loop -t iso9660 /media/iso 
```


-Then in Appearance and conditions tab:

```
File Pattern:*.iso; *.ISO
```

and check the box: Other Files


Then I made a Custom Action for Unmounting:

in Thunar..
-Edit > Configure custom actions.

-Add a New Custom Action by pressing on the ( + ) button.

```
Name: Unmount ISO
Description: Unmount ISO 
Command: sudo umount %f /media/iso 
```


-Then in Appearance and conditions tab:

```
File Pattern:*.iso; *.ISO
```

and check the box: Other Files

Now we are finished and you will be able to right-click on a ISO file and Mount/Unmount it in Thunar!

Hope that helps someone!
:guitar:

---

### Post by madjr on 2008-03-29
you can also mount isos with a gui using **gmount-iso** (in the repos or add/remove)

theres also:
[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

---

### Post by bulletxt on 2008-03-29
if AcetoneISO doesn't convert an nrg to iso, it's because it is already an ISO! just rename it to *.iso and mount it. actually, AcetoneISO can directly mount nrg files..

---

