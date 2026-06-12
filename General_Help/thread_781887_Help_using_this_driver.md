---
title: "Help using this driver"
date: 2008-05-04
forum: General Help
---

### Post by CHUNKYBOWSER on 2008-05-04
How would I get it to work? I still can't figure out .tar.gz files. :(

[http://us.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+XtremeGamer&Product_ID=15853&modelnumber=&driverlang=1033&OS=12&drivertype=0&x=21&y=20](http://us.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+XtremeGamer&Product_ID=15853&modelnumber=&driverlang=1033&OS=12&drivertype=0&x=21&y=20)

---

### Post by TeoBigusGeekus on 2008-05-04
A .tar.gz is an archive, much like .zip or .rar files. Just double click it and extract its contents anywhere you like.

---

### Post by CHUNKYBOWSER on 2008-05-04
> **TeoBigusGeekus said:**
> A .tar.gz is an archive, much like .zip or .rar files. Just double click it and extract its contents anywhere you like.

Then how do I get them to work?

---

### Post by TeoBigusGeekus on 2008-05-04
What is the content of the archive?

---

### Post by CHUNKYBOWSER on 2008-05-04
> **TeoBigusGeekus said:**
> What is the content of the archive?

What exactly do you mean? First, it's the actual folder. Under that folder, there are 3 .txts, a installer which doesn't open anything when I click it, and a .tar.bz2 file. Under the .tar.bz2 file is a folder named "drivers" and it has a ton of stuff under that.

---

### Post by TeoBigusGeekus on 2008-05-04
Are you sure the "installer" isn't a text file with directions for the installation?

---

### Post by CHUNKYBOWSER on 2008-05-04
> **TeoBigusGeekus said:**
> Are you sure the "installer" isn't a text file with directions for the installation?

When I look at its properties it says it's a "shell script".

---

### Post by TeoBigusGeekus on 2008-05-04
If it has an .sh extension

```
sh /path/to/installer/nameofinstaller.sh
```

---

### Post by CHUNKYBOWSER on 2008-05-04
> **TeoBigusGeekus said:**
> If it has an .sh extension

```
sh /path/to/installer/nameofinstaller.sh
```

And I type that in the terminal? What would the name of the installer be? xD I'm sorry I'm such a noob at this. :(

---

### Post by CHUNKYBOWSER on 2008-05-04
Maybe this would help. This is what the Readme file says... I just don't understand what it's telling me to do.

====================================================================


  Sound Blaster X-Fi Linux 32/64-bit Beta Driver Readme File


  April 2008


====================================================================


The purpose of this document is to describe how the X-Fi Linux device 

driver is built, packaged, and released.







Quick install


=============




1) You must have the fully configured source for the Linux kernel and 

   ALSA which you
 want to use for this device driver. Partial installed 

   kernels (e.g. From distribution makers) may be unusable for this 

   action.





2) Run one of the following commands as root in the terminal:





   ./installer
   




   OR




   ./installer --with-alsainc=<ALSA_include_directory>





  * ALSA Source Tree




   
   On 2.6 kernels, the location of the ALSA source include directory


      is parsed automatically from the running kernel.


      If it is not in the standard place, specify the path via

   
   --with-alsainc=<ALSA_include_directory>.



 
   
  On 2.4 kernels, the location of the ALSA source include directory


      must be specified via --with-alsainc=<ALSA_include_directory>.





  * Note

      If integrated ALSA is to be used to build, --with-alsainc option


      must not be specified.









Uninstall


=========




In the terminal,




1) Change directory to /opt/Creative/XFiDrv_Linux_US-1.18





2) Run the following command as root




   ./configure


   make uninstall





 * Note


      For GNOME users, You may need to close the Volume Control

      applet before uninstalling. Right-click the Volume icon on the

      GNOME panel and select "Remove From Panel"





3) Manually delete all files in /opt/Creative/XFiDrv_Linux_US-1.18












Copyright (c) 2008 Creative Technology Ltd. All rights reserved.


====================================================================


  End of Readme File


====================================================================

---

### Post by TeoBigusGeekus on 2008-05-04
Yes, you type it in the terminal. The name of the installer is... the name of the installer, i.e. the name of the file which has an .sh extension.
So if the folder is located on your Desktop, it is named Driverfolder and the installer is named runme.sh
```
sh /home/<yourusername>/Desktop/Driverfolder/runme.sh
```

---

### Post by CHUNKYBOWSER on 2008-05-04
> **TeoBigusGeekus said:**
> Yes, you type it in the terminal. The name of the installer is... the name of the installer, i.e. the name of the file which has an .sh extension.
So if the folder is located on your Desktop, it is named Driverfolder and the installer is named runme.sh
```
sh /home/<yourusername>/Desktop/Driverfolder/runme.sh
```

It's saying it can't open it.

---

### Post by TeoBigusGeekus on 2008-05-04
Ok, I've just read your edit.
Type
```
sudo ./installer 
```
when in the installer's folder. You navigate to a folder with the cd command
```
cd /path/to/folder
```

---

### Post by macaholic on 2008-05-04
Does it have execution privileges? you can give it execution privileges via```
chmod a+x /path/to/file
```

---

### Post by CHUNKYBOWSER on 2008-05-04
What is path/to/folder or path/to/file? Do I have to replace that with something?

---

### Post by TeoBigusGeekus on 2008-05-04
Are you pulling my leg?
Of course you have to replace it... with the actual path to your installer!

---

### Post by CHUNKYBOWSER on 2008-05-04
> **TeoBigusGeekus said:**
> Are you pulling my leg?
Of course you have to replace it... with the actual path to your installer!

OK! *dies*

---

### Post by CHUNKYBOWSER on 2008-05-04
I tried everything, and it's not working. :/

---

### Post by TeoBigusGeekus on 2008-05-04
Please post us the location and the name of the folder.

---

### Post by CHUNKYBOWSER on 2008-05-04
> **TeoBigusGeekus said:**
> Please post us the location and the name of the folder.

OK, before I do that, I have a "installer" in the first folder. Then, in a further down folder under drivers, I have a "install-sh folder. Which one do you want to know?

---

### Post by TeoBigusGeekus on 2008-05-04
The first one.

---

### Post by CHUNKYBOWSER on 2008-05-04
[http://tinypic.com/view.php?pic=xgeeys&s=3](http://tinypic.com/view.php?pic=xgeeys&s=3)

There. I decided to make a picture. xD

---

### Post by TeoBigusGeekus on 2008-05-04
```
cd /home/sean/Desktop/XFiDrv_Linux_US-1.18
```

and then

```
sudo ./installer
```

---

### Post by CHUNKYBOWSER on 2008-05-04
> **TeoBigusGeekus said:**
> ```
cd /home/sean/Desktop/XFiDrv_Linux_US-1.18
```

and then

```
sudo ./installer
```

Now it says "[sudo] password for sean:" Should I enter my password there?

Everytime it's asked me that before it's screwed up. D:

---

### Post by TeoBigusGeekus on 2008-05-04
Yes, type your password (you won't see any characters typed) and press enter.

---

### Post by CHUNKYBOWSER on 2008-05-04
> **TeoBigusGeekus said:**
> Yes, type your password (you won't see any characters typed) and press enter.

Well, I said yes a couple times to agreements... and then it started installation, but then it says this. :/ 

"Installation is in progress. Please wait...









checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 
sean@sean-desktop:~/Desktop/XFiDrv_Linux_US-1.18$"

---

### Post by CHUNKYBOWSER on 2008-05-04
I guess I'll never get sound. :(

---

### Post by TeoBigusGeekus on 2008-05-05
Go to System->Administration->Synaptic Package Manager
Do a search for the cpp, cpp-4.2 and gcc packages.
Are they installed (checkbox green)?
If not, install them and try to run the installer again.

---

