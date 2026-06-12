---
title: "install file .run, .sh or .bin"
date: 2004-10-27
forum: General Help
---

### Post by crashd on 2004-10-27
Hi all!
This is my problem: if I try to install this format of file: .bin , .sh or .run , nautilus it says to me that it is impossible to open the file (and I do it from root!).
This it happens also with the games on Cd like quake 3 or soldier of fortune, even if on other distros (using kde), the autorun worked automatically with a GUI installer.
Have got an idea? 
Thanks.

Sorry for my bad english  :roll: 
bye

---

### Post by HungSquirrel on 2004-10-27
Make sure the file is executable.  In Nautilus, right-click on the file, then choose Properties.  In the Permissions tab, make sure Owner: Execute is checked.

---

### Post by crashd on 2004-10-27
[QUOTE=HungSquirrel]Make sure the file is executable.  In Nautilus, right-click on the file, then choose Properties.  In the Permissions tab, make sure Owner: Execute is checked.[/QUOTE]
not works   :-(

---

### Post by im_ka on 2004-10-27
do you just click the file in nautilus?

try to run it from the command line.

```
sh whatever.sh
```
or
```
./whatever.sh
```

---

### Post by crashd on 2004-10-27
[QUOTE=im_ka]do you just click the file in nautilus?

try to run it from the command line.

```
sh whatever.sh
```
or
```
./whatever.sh
```[/QUOTE]
thanks!
but...
this not works with programs like azureus (is only with GUI) or with the games CDs because they do not let to modify the permissions even with chmod +x . :-(

---

### Post by crashd on 2004-10-28
you how to if you must for example use azureus or quake3?  ](*,)

---

### Post by Rancoras on 2004-10-28
What is the name of the file you are trying to run for each of those programs?

---

### Post by crashd on 2004-10-28
[QUOTE=Rancoras]What is the name of the file you are trying to run for each of those programs?[/QUOTE]
azureus [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/) [http://voxel.dl.sourceforge.net/sourceforge/azureus/Azureus_2.1.0.4_linux.GTK.tar.bz2](http://voxel.dl.sourceforge.net/sourceforge/azureus/Azureus_2.1.0.4_linux.GTK.tar.bz2)

limewire [http://www.limewire.com/](http://www.limewire.com/)
 [http://www9.limewire.com/beta/LimeWireLinux.bin](http://www9.limewire.com/beta/LimeWireLinux.bin)

mute [http://mute-net.sourceforge.net/](http://mute-net.sourceforge.net/)
[http://mesh.dl.sourceforge.net/sourceforge/mute-net/MUTE_fileSharing-0.3-t_UnixSource.tar.gz](http://mesh.dl.sourceforge.net/sourceforge/mute-net/MUTE_fileSharing-0.3-t_UnixSource.tar.gz)

 unrealtournament 2004 demo [http://www.unrealtournament.com/](http://www.unrealtournament.com/)
 and game on cd..

thanks for the interest
bye

---

### Post by Rancoras on 2004-10-28
No, I mean the name of the actual file you're needing to run.  Use azurues as an example.  Is it azureus.sh or what?

---

### Post by FLeiXiuS on 2004-10-28
[QUOTE=Rancoras]No, I mean the name of the actual file you're needing to run.  Use azurues as an example.  Is it azureus.sh or what?[/QUOTE]
 Azureus' start file is an executable file with no extension.  (Bash File)

```

cd /path/to/azureus/
./azureus

```

---

### Post by Rancoras on 2004-10-28
So, still using azureus as an example.  You extracted the file you downloaded.?  You then cd into it and run ./azureus ?  What happened when you did that?

---

### Post by markw on 2004-10-28
You might want to try right click on the desktop and create a launcher. You get a fancy icon that way to [img]http://www.ubuntuforums.org/images/smilies/icon_smile.gif[/img].

---

### Post by crashd on 2004-10-29
[QUOTE=markw]You might want to try right click on the desktop and create a launcher. You get a fancy icon that way to [img]http://www.ubuntuforums.org/images/smilies/icon_smile.gif[/img].[/QUOTE]
what launcher?

---

