---
title: "Burn dual layer dvd?"
date: 2007-05-09
forum: General Help
---

### Post by Digitallysick on 2007-05-09
which is best for this? gnomebaker, or k3b? and how do i do it? I plan on burning a backup copy of an xbox360 game. Anyone know how to do that in linux?

---

### Post by paulyee on 2007-05-15
i want to know that too :D

i will try to use K3B tonite and will post my findings...

---

### Post by willl on 2007-06-16
*cough* and? :---)

---

### Post by Digitallysick on 2007-06-17
i finally used imageburn in wine (its a windows app) and i could burn a backup game and have it play well. Some files might be .nrg which you can burn with nero (they have nero linux now as well)

---

### Post by Mantorp on 2007-06-18
I use this command in the Termina on Ubuntu for 3 months and worked great for my XBOX 360:

growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760  -dvd-compat -speed=2 -Z /dev/hdc=IMAGE.000

All in one Command. /dev/hdc is my DVD-rom, yours maybe different. Instead of IMAGE.000 you can use also IMAGE.iso, depands on your image.
You can find your DVD-rom location in /etc/fstab to see where is your DVD-rom mounted.

For backup a XBOX game see this link

[http://blog.reloadsystems.net/2007/02/02/burning-xbox-360-games-in-linux/](http://blog.reloadsystems.net/2007/02/02/burning-xbox-360-games-in-linux/)

this is all you need.

---

### Post by davidme on 2007-06-22
> **Mantorp said:**
> I use this command in the Termina on Ubuntu for 3 months and worked great for my XBOX 360:

growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760  -dvd-compat -speed=2 -Z /dev/hdc=IMAGE.000

All in one Command. /dev/hdc is my DVD-rom, yours maybe different. Instead of IMAGE.000 you can use also IMAGE.iso, depands on your image.
You can find your DVD-rom location in /etc/fstab to see where is your DVD-rom mounted.

For backup a XBOX game see this link

[http://blog.reloadsystems.net/2007/02/02/burning-xbox-360-games-in-linux/](http://blog.reloadsystems.net/2007/02/02/burning-xbox-360-games-in-linux/)

this is all you need.


And as for the image iso itself ?

"IMAGE.000" can be /media/backups/xbox/name_of_the_image.iso  

?

How about burning images that end with  xbox_360_backup.dvd   Do I rename them to .000 or .iso or burn as is ?

Where do I get "imgbpatch.jar"  synaptic does not have it.

---

### Post by Digitallysick on 2007-06-22
Just my opinion but i used image burn in wine for those type files the .000 and.dvd files , i only used nero for the .iso and .nrg. 
[http://imgburn.com/](http://imgburn.com/)

you can run it in wine, and it works well.

---

### Post by Mantorp on 2007-07-02
> **davidme said:**
> And as for the image iso itself ?

"IMAGE.000" can be /media/backups/xbox/name_of_the_image.iso  

?

How about burning images that end with  xbox_360_backup.dvd   Do I rename them to .000 or .iso or burn as is ?

Where do I get "imgbpatch.jar"  synaptic does not have it.



YES it can be iso or 000, it doesn't matter. You can write the image name like my_image.iso or the path to the image like /home/user/my_games/my_image.iso , works in both ways.
I never seen a XBOX360 image that ends with .dvd. There are games in format .iso or .000 with the small file .dvd. If u have the second type you don't need the .dvd file. In the .dvd file are only the layer break and the name of the image. But if u use the the command growisofs , the layerbeak is already writed in the command.

The imgbpatch.jar u can get here [www.studenti.pef.upr.si/~luka.hrvatin/Razno/imgbpatch.jar](www.studenti.pef.upr.si/~luka.hrvatin/Razno/imgbpatch.jar)
Run it in Terminal with java -jar imgbpatch.jar /path/to/the/image.iso or .000.

---

### Post by RaZoR1394 on 2007-07-18
Thanks works fine. My first burn was an older iso that was not stealth so I had to fix it using XDVDmulleter to use with Ixtreme. I did this in Windows with Virtualbox but I guess Mono with Wine works to. Will try that later.

---

### Post by RaZoR1394 on 2007-07-31
I installed Mono for windows in Wine but XDVDmulleter still won't run under Kubuntu. I think it segfaults but there is no message. Also it seems that some images are not marked as iXtreme compatible anymore after using imgbpatch.jar. I heard some rumors that iXtreme 1.2 still starts some unstealthed backups.

---

### Post by kraymore on 2007-11-16
i'm using gusty and i've tried this command all always get the following output

i'll copy my /etc/fstab entry too

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

 growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760  -dvd-compat -speed=2 -Z /dev/scd0=image.iso
Executing 'builtin_dd if=image.iso of=/dev/scd0 obs=32k seek=0'
:-( write failed: Input/output error

doesn't even prompt me to enter media.  cannot get imgburn to work either it gives me the folllowing error (imburn) Invalid or supported image format!  reason:  first image afile part is less than 2048 bytes in size.  

would really appreciate some help.  dont want to run windows on a secondary computer here

---

