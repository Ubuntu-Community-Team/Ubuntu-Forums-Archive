---
title: "[SOLVED] Setting up a swap partition"
date: 2007-08-12
forum: General Help
---

### Post by jeremy1138 on 2007-08-12
Hi!  When I initially set up my dual boot system to put Ubuntu on my computer that already had Windows on it I only created one partition upon which to install Linux and I didn't make any allocation for a swap file.  How can I reconfigure my hard drive with Linux and Windows in place so that I can have a swap partition for Linux to use?  What settings to I have to change in Linux so that it will see and use the swap partition once it's in place?  How large should this swap partition be?  My computer has 1024 MB of RAM with 128 allocated to the onboard video card.

Thanks for your help! :)

---

### Post by darksidedude on 2007-08-12
well what you have to do is "make" a swap partition, ( this is weird ubuntu usually makes one for you) use gparted or Qtparted and 
1 resize your ubuntu partition (either ext2 or ext3) 
2 in the frees space make a swap partition

should be good to go, any other questions please let me know:guitar:

---

### Post by jeremy1138 on 2007-08-12
> **darksidedude said:**
> well what you have to do is "make" a swap partition, ( this is weird ubuntu usually makes one for you) use gparted or Qtparted and 
1 resize your ubuntu partition (either ext2 or ext3) 
2 in the frees space make a swap partition

should be good to go, any other questions please let me know:guitar:

Thanks for the reply! 
What should the swap partition be called?  What file system should it use?  Will Linux automatically see it and use it?  How big should it be?

---

### Post by darksidedude on 2007-08-12
swap partions don't need a name ( like virtual ram for windows) it should be between half you ram to 3/4 of ram, the filesystem should be SWAP

---

### Post by dougfractal on 2007-08-12
> **darksidedude said:**
> well what you have to do is "make" a swap partition, ( this is weird ubuntu usually makes one for you) use gparted or Qtparted and 
1 resize your ubuntu partition (either ext2 or ext3) 
2 in the frees space make a swap partition

should be good to go, any other questions please let me know:guitar:



this is good but you must be using a **LiveCD**, DO NOT mount any partitions

> swap partions don't need a name ( like virtual ram for windows) it should be between half you ram to 3/4 of ram, the filesystem should be SWAP
atleast you ram or double recomended.
also mounted in the **sudo gedit /etc/fstab**
> # /dev/sda5
UUID=a6297cdc-e96e-4ee4-bcc8-30bb7fd36c06 none            swap    sw              0       0
/
> sudo fdisk -l
sudo vol_id /dev/hdaX   #  [your swap partion]

---

### Post by jeremy1138 on 2007-08-12
Great!  I'm going to try it right now!  Thanks for your help!

---

### Post by jeremy1138 on 2007-08-12
> **dougfractal said:**
> this is good but you must be using a **LiveCD**, DO NOT mount any partitions

This just confused me...  I'm not using a live cd.  What do I have to do?

---

### Post by dougfractal on 2007-08-12
> **jeremy1138 said:**
> This just confused me...  I'm not using a live cd.  What do I have to do?
Restart the computer using the ubuntu install/liveCD   (or any linux liveCD)

---

### Post by darksidedude on 2007-08-12
glad you got the part about the live cd, that is an important part

---

### Post by jeremy1138 on 2007-08-12
Ok I got the partition made but, according to the system monitor, I still have no swap.  I formatted the new partition with GParted and the file system was linux-swap.  Does anyone know what else I need to do to get this working? 

Thanks for all the help!

---

### Post by jeremy1138 on 2007-08-12
I figured it out...  I went into Gparted in Ubuntu and right clicked on the linux-swap partition and selected swapon.  That did it!  Thanks for all your help everyone! :)

---

### Post by jeremy1138 on 2007-08-12
Quick question.  When does Linux actually use the swap partition?  Is it only when RAM is low?

Thanks!

---

### Post by dougfractal on 2007-08-12
can you do this 

> cat /etc/fstab  #  show your mount conf
sudo fdisk -l  #   list your partitions

---

### Post by meierfra on 2007-08-12
You probably need to  edit the file  /etc/fstab, otherwise you will have to use "swapon" every time you boot your computer.

Use "sudo fdisk -l" to find out the swap device. (Should be something like /dev/sda3 or /dev/hdb2)

Open /etc/fstab via

```
sudo  gedit /etc/fstab 
```

Add the following line at the end:

/dev/xyzu   none           swap         sw            0      0

(where /dev/xyzu is the device you determined earlier)

Save the file. Next time you reboot your swap should be automatically on.


Yes, ubuntu uses the swap partition when it runs out of  ram.  On laptops swap is also used for hibernation.

---

### Post by jeremy1138 on 2007-08-12
> **dougfractal said:**
> can you do this

Alrighty I put those in the terminal and for the first one I got:

```

jeremy@jeremy-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=196eed55-dd11-40c1-9d89-ee19116c1dfb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=44F8DEB9F8DEA906 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=45EF-12C3  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
and for the second one I got:
```

jeremy@jeremy-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           8        8428    67641651    7  HPFS/NTFS
/dev/hda2            9704        9729      208845   88  Linux plaintext
/dev/hda3            9627        9703      618502+  82  Linux swap / Solaris
/dev/hda4            8429        9626     9622935   83  Linux

Partition table entries are not in disk order

```
Does that stuff look right?

---

### Post by dougfractal on 2007-08-12
> **jeremy1138 said:**
> Quick question.  When does Linux actually use the swap partition?  Is it only when RAM is low?

Thanks!

swap is used to hibernate and to store low priority data, so freeing up RAM.

have you got compiz running on your ati ATI Radeon Xpress200M?

---

### Post by jeremy1138 on 2007-08-12
this is the contens of my fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=196eed55-dd11-40c1-9d89-ee19116c1dfb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=44F8DEB9F8DEA906 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=45EF-12C3  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda3 none swap sw 0 0

```
with the changes that you suggested.  Does it look right?

Thanks for all the quick responses!

---

### Post by jeremy1138 on 2007-08-12
> **dougfractal said:**
> swap is used to hibernate and to store low priority data, so freeing up RAM.

have you got compiz running on your ati ATI Radeon Xpress200M?

I can't for the life of me get anything 3d to run on this machine in Linux!  I tried for days!  Do you have any ideas on that?  I have the proprietary ATI driver installed.  Thanks!

---

### Post by meierfra on 2007-08-12
That looks right. You can test it by rebooting.

---

### Post by jeremy1138 on 2007-08-12
> **meierfra said:**
> That looks right. You can test it by rebooting.

Great!  Thanks for all your help and quick responses!  This is what makes Ubuntu and indeed Linux alltogether the best OS out there!  Well done!

---

### Post by dougfractal on 2007-08-12
> 
sudo umount /dev/hda3

> # /dev/hda3
UUID=45EF-12C3  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       

no change to this, and did you format the swap with gparted?

> /dev/hda3   none swap sw 0 0

or better still use the UUID from 
> sudo vol_id /dev/hda3

sudo gedit /etc/fstab
> # /dev/hda3
UUID=XXXXXXXXXXXXXX   none swap sw 0 0"

---

### Post by jeremy1138 on 2007-08-12
> **dougfractal said:**
> no change to this, and did you format the swap with gparted?



or better still use the UUID from 


sudo gedit /etc/fstab

That seems really confusing...  I'm a rookie at this...  What does all that mean?  I'm sorry...

I used Gparted to resize my partitions and make the swap one yes.

---

### Post by yorkie on 2007-08-12
type this into terminal

sudo fdisk -l
 this will show your hard drive partitions see if swap is there

---

### Post by dougfractal on 2007-08-12
gedit aticompiz.sh
paste and save

```
#!/bin/bash
# aticompiz.sh
# by dougfractal
#  compiz-fusion ati x1*** series
#

# **************  UptoDate and tidy *****************************
if [ `lspci | grep -i "vga" | grep -c -i "ati "` -eq "0" ] ; then zenity --error --title="Check error" --text="No ATI card found!" ; exit; fi
sudo apt-get update | tee >(zenity --progress --pulsate --title="Updating repository" --auto-close)
sudo apt-get remove remove --purge compiz-core desktop-effects beryl beryl-plugins-unsupported beryl-vidcap seom beryl-settings | tee >(zenity --progress --pulsate --title="Removing old packages" --auto-close)
sudo apt-get autoremove | tee >(zenity --progress --pulsate --title="Removing old packages" --auto-close)
sudo apt-get upgrade  | tee >(zenity --progress --pulsate --title="Upgrading" --auto-close)
sudo apt-get dist-upgrade | tee >(zenity --progress --pulsate --title="Upgrading distribution" --auto-close)
sudo rm /usr/local/bin/start_beryl.sh
sudo rm /etc/xdg/autostart/beryl.desktop
sudo rm /usr/share/applications/beryl.desktop


#  ***************    ATI      *******************************
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


CODENAME="ubuntu"
if [ `lsb_release -c | grep -c "feisty"` -eq "1" ]  ; then  CODENAME="feisty" ; fi
if [ `lsb_release -c | grep -c "gusty"` -eq "1" ]  ; then  CODENAME="gusty" ;  fi


# *******************  compiz-fusion **********************************************
if [ $CODENAME == "feisty" ] ; then
      if [ `grep -c '^deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) $CODENAME eyecandy' /etc/apt/sources.list` -eq "0" ]; then
            echo "# For compiz
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) $CODENAME eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) $CODENAME eyecandy" | sudo tee -a /etc/apt/sources.list
            wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
            sudo apt-get update |  tee >(zenity --progress --pulsate --title="Updating repository" --auto-close)
            sudo apt-get --assume-yes install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf emerald-themes avant-window-navigator | tee >(zenity --progress --pulsate --title="Installing Compiz" --auto-close)
     fi
fi 
if [ $CODENAME == "gusty" ] ; then     
      sudo apt-get --assume-yes install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf emerald-themes avant-window-navigator | tee >(zenity --progress --pulsate --title="Installing Compiz" --auto-close)
fi

# *** compiz on / off ****
sudo mkdir -p /usr/local/bin
echo "if  [ (ps -A | grep -c \"compiz\") -eq '0' ]; then
     if (( `ps -A -o comm | grep -c '^Xgl$'` == \"1\" )); then
            DISPLAY=:1 compiz --replace -c emerald &
     else echo \"${0}: Error: beryl-manager not launched. Xgl not running?\"
     fi
else
     DISPLAY=:1 metacity --replace &
fi" | sudo tee /usr/local/bin/toggle_compiz.sh
sudo sed -i '1i\#!/bin/bash\n# Toggle compiz within gnome-session' /usr/local/bin/toggle_compiz.sh
sudo chmod a+x /usr/local/bin/toggle_compiz.sh
echo "[Desktop Entry]
Encoding=UTF-8
Name=Compiz Manager
Name[en_US]=Compiz
GenericName=3D Window Manager
Comment=Compiz-Fusion 3D Manager
Comment[en_US]=Compiz-Fusion 3D Manager
Icon=/usr/share/icons/hicolor/scalable/apps/beryl-manager.svg
Exec=/usr/local/bin/toggle_compiz.sh
Terminal=false
Type=Application
Categories=GTK;GNOME;Application;Utility;
StartupNotify=true
X-Ubuntu-Gettext-Domain=compiz-manager" | sudo tee /usr/share/applications/compiz.desktop  

 
#  ***************    xgl ati (or Intel) gnome    *******************************
sudo apt-get install xserver-xgl dbus-x11
echo "Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session" | sudo tee /usr/bin/startxgl.atignome.sh
sudo sed -i '1i\#!/bin/bash' /usr/bin/startxgl.atignome.sh
sudo chmod +x /usr/bin/startxgl.atignome.sh
##  *** Xgl-gnome session ***
echo "[Desktop Entry]
      Encoding=UTF-8
      Name=Xgl Gnome
      Comment=Start an Xgl Session
      Exec=/usr/bin/startxgl.atignome.sh
      Icon=
      Type=Application" | sudo tee /usr/share/xsessions/xgl.atignome.desktop
zenity --info --text="To log into Xgl, logout and from the login screen click \"Options\" and \"Session chooser\". \n\nSelect \"Xgl Gnome\" from the Session menu.\n\nFor now, choose \"Just for this session\"."

zenity --question  --title="Restart" --text="System restart required.\nAre you ready to Restart?"
if [ $? -eq "0" ] ; then sudo shutdown -r now ; fi

# [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
# [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) How To : Compiz Fusion for ATI cards + Xgl in Feisty
```


now check if its worked (safely ?!?)
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
chmod a+x aticompiz.sh
sudo aticompiz.sh
sudo cp /etc/X11/xorg.conf cp /etc/X11/xorg.conf.fglx
wget -O testx http://redballoonlearner.co.uk/doug/ubuntu/testx.sh
chmod a+x testx
./testx xorg.conf.fglx
```

If it didn't work you need to take a risk and reboot maybe into BSOD then   ....   or just ..... (no risk uninstall)
```
sudo apt-get remove fglxr
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
```

---

### Post by yorkie on 2007-08-12
note fdisk -l    space after the k  and -l  l = letter l not number one just in case you are not used to terminal commands

---

### Post by jeremy1138 on 2007-08-12
> **dougfractal said:**
> gedit aticompiz.sh
paste and save

```
#!/bin/bash
# aticompiz.sh
# by dougfractal
#  compiz-fusion ati x1*** series
#

# **************  UptoDate and tidy *****************************
if [ `lspci | grep -i "vga" | grep -c -i "ati "` -eq "0" ] ; then zenity --error --title="Check error" --text="No ATI card found!" ; exit; fi
sudo apt-get update | tee >(zenity --progress --pulsate --title="Updating repository" --auto-close)
sudo apt-get remove remove --purge compiz-core desktop-effects beryl beryl-plugins-unsupported beryl-vidcap seom beryl-settings | tee >(zenity --progress --pulsate --title="Removing old packages" --auto-close)
sudo apt-get autoremove | tee >(zenity --progress --pulsate --title="Removing old packages" --auto-close)
sudo apt-get upgrade  | tee >(zenity --progress --pulsate --title="Upgrading" --auto-close)
sudo apt-get dist-upgrade | tee >(zenity --progress --pulsate --title="Upgrading distribution" --auto-close)
sudo rm /usr/local/bin/start_beryl.sh
sudo rm /etc/xdg/autostart/beryl.desktop
sudo rm /usr/share/applications/beryl.desktop


#  ***************    ATI      *******************************
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


CODENAME="ubuntu"
if [ `lsb_release -c | grep -c "feisty"` -eq "1" ]  ; then  CODENAME="feisty"
if [ `lsb_release -c | grep -c "gusty"` -eq "1" ]  ; then  CODENAME="gusty"


# *******************  compiz-fusion **********************************************
if [ $CODENAME == "feisty" ] ; then
      if [ `grep -c '^deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) $CODENAME eyecandy' /etc/apt/sources.list` -eq "0" ]; then
            echo "# For compiz
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) $CODENAME eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) $CODENAME eyecandy" | sudo tee -a /etc/apt/sources.list
            wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
            sudo apt-get update |  tee >(zenity --progress --pulsate --title="Updating repository" --auto-close)
            sudo apt-get --assume-yes install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf emerald-themes avant-window-navigator | tee >(zenity --progress --pulsate --title="Installing Compiz" --auto-close)
     fi
fi 
if [ $CODENAME == "gusty" ] ; then     
      sudo apt-get --assume-yes install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf emerald-themes avant-window-navigator | tee >(zenity --progress --pulsate --title="Installing Compiz" --auto-close)
fi

# *** compiz on / off ****
sudo mkdir -p /usr/local/bin
echo "if  [ (ps -A | grep -c \"compiz\") -eq '0' ]; then
     if (( `ps -A -o comm | grep -c '^Xgl$'` == \"1\" )); then
            DISPLAY=:1 compiz --replace -c emerald &
     else echo \"${0}: Error: beryl-manager not launched. Xgl not running?\"
     fi
else
     DISPLAY=:1 metacity --replace &
fi" | sudo tee /usr/local/bin/toggle_compiz.sh
sudo sed -i '1i\#!/bin/bash\n# Toggle compiz within gnome-session' /usr/local/bin/toggle_compiz.sh
sudo chmod a+x /usr/local/bin/toggle_compiz.sh
echo "[Desktop Entry]
Encoding=UTF-8
Name=Compiz Manager
Name[en_US]=Compiz
GenericName=3D Window Manager
Comment=Compiz-Fusion 3D Manager
Comment[en_US]=Compiz-Fusion 3D Manager
Icon=/usr/share/icons/hicolor/scalable/apps/beryl-manager.svg
Exec=/usr/local/bin/toggle_compiz.sh
Terminal=false
Type=Application
Categories=GTK;GNOME;Application;Utility;
StartupNotify=true
X-Ubuntu-Gettext-Domain=compiz-manager" | sudo tee /usr/share/applications/compiz.desktop  

 
#  ***************    xgl ati (or Intel) gnome    *******************************
sudo apt-get install xserver-xgl dbus-x11
echo "Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session" | sudo tee /usr/bin/startxgl.atignome.sh
sudo sed -i '1i\#!/bin/bash' /usr/bin/startxgl.atignome.sh
sudo chmod +x /usr/bin/startxgl.atignome.sh
##  *** Xgl-gnome session ***
echo "[Desktop Entry]
      Encoding=UTF-8
      Name=Xgl Gnome
      Comment=Start an Xgl Session
      Exec=/usr/bin/startxgl.atignome.sh
      Icon=
      Type=Application" | sudo tee /usr/share/xsessions/xgl.atignome.desktop
zenity --info --text="To log into Xgl, logout and from the login screen click \"Options\" and \"Session chooser\". \n\nSelect \"Xgl Gnome\" from the Session menu.\n\nFor now, choose \"Just for this session\"."

zenity --question  --title="Restart" --text="System restart required.\nAre you ready to Restart?"
if [ $? -eq "0" ] ; then sudo shutdown -r now ; fi

# [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
# [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) How To : Compiz Fusion for ATI cards + Xgl in Feisty
```


now check if its worked (safely ?!?)
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
chmod a+x aticompiz.sh
sudo aticompiz.sh
sudo cp /etc/X11/xorg.conf cp /etc/X11/xorg.conf.fglx
wget -O testx http://redballoonlearner.co.uk/doug/ubuntu/testx.sh
chmod a+x testx
./testx xorg.conf.fglx
```

If it didn't work you need to take a risk and reboot maybe into BSOD then   ....   or just ..... (no risk uninstall)
```
sudo apt-get remove fglxr
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
```

Wow I'm really new to Linux...  What's this all do?

---

### Post by jeremy1138 on 2007-08-12
Where is the aticompiz file?

---

### Post by dougfractal on 2007-08-12
>  sudo vol_id /dev/hda3

post your output


The above script is an installer I wrote for the ati card . I haven't been able to test it yet, so you are my guinea pig  , only try if you want to risk it.
You may need the LiveCD incase there is a big problem.

---

### Post by jeremy1138 on 2007-08-12
> **dougfractal said:**
> post your output

Here is the output of that command
```

jeremy@jeremy-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           8        8428    67641651    7  HPFS/NTFS
/dev/hda2            9704        9729      208845   88  Linux plaintext
/dev/hda3            9627        9703      618502+  82  Linux swap / Solaris
/dev/hda4            8429        9626     9622935   83  Linux

Partition table entries are not in disk order
jeremy@jeremy-laptop:~$ sudo  gedit /etc/fstab
jeremy@jeremy-laptop:~$ gedit aticompiz.sh
jeremy@jeremy-laptop:~$ sudo vol_id /dev/hda3
Password:
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=2ec24245-e251-47b6-bf86-ad7507957fdc
ID_FS_LABEL=
ID_FS_LABEL_SAFE=

```
Thanks!

---

### Post by jeremy1138 on 2007-08-12
What was all that ATI stuff for?  Will that get my Video card working properly?

---

### Post by dougfractal on 2007-08-12
> # /dev/hda3
UUID=2ec24245-e251-47b6-bf86-ad7507957fdc   none    swap   sw    0 0
put in the sudo /etc/fstab


the above script is an installer I wrote for the ati card . I haven't been able to test it yet, so you are my guinea pig , only try if you want to risk it.
You may need the LiveCD incase there is a big problem.

1)  copy paste the main script into aticompiz.sh
2)  > sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
chmod a+x aticompiz.sh
sudo aticompiz.sh
sudo cp /etc/X11/xorg.conf cp /etc/X11/xorg.conf.fglx
wget -O testx [http://redballoonlearner.co.uk/doug/ubuntu/testx.sh](http://redballoonlearner.co.uk/doug/ubuntu/testx.sh)
chmod a+x testx
./testx xorg.conf.fglx


3) the next little bit is Just incase    ( save this to help.txt)

> cat help.txt

you may need to read it from [ctrl+alt+f1}  trminal
 [ctrl+alt+f7} GUI

---

### Post by jeremy1138 on 2007-08-12
This is what my fstab looks like now:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=196eed55-dd11-40c1-9d89-ee19116c1dfb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=44F8DEB9F8DEA906 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=45EF-12C3  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda3 none swap sw 0 0
# /dev/hda3
UUID=2ec24245-e251-47b6-bf86-ad7507957fdc none swap sw 0 0

```
Is that good?

---

### Post by dougfractal on 2007-08-12
> /dev/hda3 none swap sw 0 0
# /dev/hda3
UUID=2ec24245-e251-47b6-bf86-ad7507957fdc none swap sw 0 0

note the 1st line
> # /dev/hda3 none swap sw 0 0
# /dev/hda3
UUID=2ec24245-e251-47b6-bf86-ad7507957fdc none swap sw 0 0


I 've got to go to sleep now. I'm back in a couple of days:-$

---

### Post by jeremy1138 on 2007-08-12
What will that installer do?  Is there a chance that will get 3d acceleration working or is it just to install my driver?  I have the proprietary driver installed already.  This is my fglrxinfo:
```

jeremy@jeremy-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6650 (8.39.4)

```
Thanks for all your help!  This is great!

---

### Post by jeremy1138 on 2007-08-12
is it all set now?
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=196eed55-dd11-40c1-9d89-ee19116c1dfb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=44F8DEB9F8DEA906 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=45EF-12C3  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda3 none swap sw 0 0
# /dev/hda3
UUID=2ec24245-e251-47b6-bf86-ad7507957fdc none swap sw 0 0

```

---

### Post by dougfractal on 2007-08-12
glxinfo | grep "direct"

---

### Post by jeremy1138 on 2007-08-12
This is what I got with that command:
```

jeremy@jeremy-laptop:~$ glxinfo | grep "direct"
direct rendering: Yes

```

---

### Post by dougfractal on 2007-08-12
gedit  install-compiz-fusion.sh

```
#!/bin/bash
# install compiz-fusion
CODENAME="ubuntu"
if [ `lsb_release -c | grep -c "feisty"` -eq "1" ]  ; then  CODENAME="feisty"; fi
if [ `lsb_release -c | grep -c "gusty"` -eq "1" ]  ; then  CODENAME="gusty"; fi


# *******************  compiz-fusion **********************************************
if [ $CODENAME == "feisty" ] ; then
      if [ `grep -c '^deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) $CODENAME eyecandy' /etc/apt/sources.list` -eq "0" ]; then
            echo "# For compiz
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) $CODENAME eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) $CODENAME eyecandy" | sudo tee -a /etc/apt/sources.list
            wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
            sudo apt-get update |  tee >(zenity --progress --pulsate --title="Updating repository" --auto-close)
            sudo apt-get --assume-yes install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf emerald-themes avant-window-navigator | tee >(zenity --progress --pulsate --title="Installing Compiz" --auto-close)
     fi
fi 
if [ $CODENAME == "gusty" ] ; then     
      sudo apt-get --assume-yes install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf emerald-themes avant-window-navigator | tee >(zenity --progress --pulsate --title="Installing Compiz" --auto-close)
fi

# *** compiz on / off ****
sudo mkdir -p /usr/local/bin
echo "if  [ (ps -A | grep -c \"compiz\") -eq '0' ]; then
     if (( `ps -A -o comm | grep -c '^Xgl$'` == \"1\" )); then
            DISPLAY=:1 compiz --replace -c emerald &
     else echo \"${0}: Error: beryl-manager not launched. Xgl not running?\"
     fi
else
     DISPLAY=:1 metacity --replace &
fi" | sudo tee /usr/local/bin/toggle_compiz.sh
sudo sed -i '1i\#!/bin/bash\n# Toggle compiz within gnome-session' /usr/local/bin/toggle_compiz.sh
sudo chmod a+x /usr/local/bin/toggle_compiz.sh
echo "[Desktop Entry]
Encoding=UTF-8
Name=Compiz Manager
Name[en_US]=Compiz
GenericName=3D Window Manager
Comment=Compiz-Fusion 3D Manager
Comment[en_US]=Compiz-Fusion 3D Manager
Icon=/usr/share/icons/hicolor/scalable/apps/beryl-manager.svg
Exec=/usr/local/bin/toggle_compiz.sh
Terminal=false
Type=Application
Categories=GTK;GNOME;Application;Utility;
StartupNotify=true
X-Ubuntu-Gettext-Domain=compiz-manager" | sudo tee /usr/share/applications/compiz.desktop  

 
#  ***************    xgl ati (or Intel) gnome    *******************************
sudo apt-get install xserver-xgl dbus-x11
echo "Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session" | sudo tee /usr/bin/startxgl.atignome.sh
sudo sed -i '1i\#!/bin/bash' /usr/bin/startxgl.atignome.sh
sudo chmod +x /usr/bin/startxgl.atignome.sh
##  *** Xgl-gnome session ***
echo "[Desktop Entry]
      Encoding=UTF-8
      Name=Xgl Gnome
      Comment=Start an Xgl Session
      Exec=/usr/bin/startxgl.atignome.sh
      Icon=
      Type=Application" | sudo tee /usr/share/xsessions/xgl.atignome.desktop
zenity --info --text="To log into Xgl, logout and from the login screen click \"Options\" and \"Session chooser\". \n\nSelect \"Xgl Gnome\" from the Session menu.\n\nFor now, choose \"Just for this session\"."
```

```
sudo ./install-compiz-fusion.sh
```

 from the Session menu at login
 Session chooser> Select>Xgl Gnome
after login you should find in accessories "Compiz Manager" which will switch compiz on/off

---

### Post by jeremy1138 on 2007-08-12
I'm sorry I'm kinda new to this...  What do I do with that?  Also did you notice that I'm using a 64 bit computer?  I've noticed that a lot of things don't work with this 64 bit machine.  I'll be happy to try this out if it may make things work better for me but I don't want to do anything foolish...

---

### Post by dougfractal on 2007-08-12
Thanks for saying 64bit, but you done the hard bit, installing** flgrx**
All the script does now is add compiz-fusion and the xgl-server which you need to use from the "session"  at login prompt.

I can't see a problem. but if your not sure that ok.

---

### Post by jeremy1138 on 2007-08-12
ok I see...  I'm going to give it a try.

---

### Post by jeremy1138 on 2007-08-12
this is what I get when I try that second command after saving that script you gave me:
```

jeremy@jeremy-laptop:~$ sudo ./install-compiz-fusion.sh
Password:
sudo: ./install-compiz-fusion.sh: command not found

```
Any ideas?

---

### Post by dougfractal on 2007-08-12
gedit install-compiz-fusion.sh


what did you save the new script as ?

---

### Post by jeremy1138 on 2007-08-12
Oh yeah and I have a compiz settings manager in my menu already but I can't turn on desktop effects for some reason...  When I try to I get an error box that says: 'desktop effects could not be enabled...  Any ideas on that?

---

### Post by jeremy1138 on 2007-08-12
> **dougfractal said:**
> gedit install-compiz-fusion.sh


what did you save the new script as ?

This command opened the script that you gave me.

---

### Post by dougfractal on 2007-08-12
my mistake

> chmod a+x ./install-compiz-fusion.sh   # make it exec
sudo ./install-compiz-fusion.sh

from the Session menu at login
Session chooser> Select>Xgl Gnome
after login you should find in accessories "Compiz Manager" which will switch compiz on/off

---

### Post by jeremy1138 on 2007-08-12
this is what I got from those last couple commands:
```

jeremy@jeremy-laptop:~$ chmod a+x ./install-compiz-fusion.sh # make it exec
jeremy@jeremy-laptop:~$ sudo ./install-compiz-fusion.sh
./install-compiz-fusion.sh: line 67: syntax error: unexpected end of file
jeremy@jeremy-laptop:~$ 

```

Should I try to log in to my xgl session now?  usually when I do that the screen looks all garbled.

---

### Post by dougfractal on 2007-08-12
> Should I try to log in to my xgl session now? usually when I do that the screen looks all garbled.

lets try.  WRONG

i've an error in my if's. 

add "; fi "  to the end of both lines

> if [ `lsb_release -c | grep -c "feisty"` -eq "1" ]  ; then  CODENAME="feisty"; fi
if [ `lsb_release -c | grep -c "gusty"` -eq "1" ]  ; then  CODENAME="gusty"; fi

now try

---

### Post by jeremy1138 on 2007-08-12
> **dougfractal said:**
> lets try.

ok be back in a min.

---

### Post by jeremy1138 on 2007-08-12
Ok I have good news and bad news.  The good news is that my swap file stayed enabled or whatever so it's still being used.  The bad news is that everything looked all garbled when I started the xgl session and I had to reboot.  Is there something that I could do instead of rebooting when that happens?  What should I try now?

---

### Post by dougfractal on 2007-08-12
sorry did you see this

> i've an error in my if's.

add "; fi " to the end of both lines

Quote:
if [ `lsb_release -c | grep -c "feisty"` -eq "1" ] ; then CODENAME="feisty"; fi
if [ `lsb_release -c | grep -c "gusty"` -eq "1" ] ; then CODENAME="gusty"; fi
now try


> something that I could do instead of rebooting when that happens?
if the keyboard hasn't locked you can [ctrl+alt+backspace]  === restart X

---

### Post by jeremy1138 on 2007-08-12
ok lines are changed and I'm giving it a go now.

---

### Post by jeremy1138 on 2007-08-12
this is the output of the install command:
```

jeremy@jeremy-laptop:~$ sudo ./install-compiz-fusion.sh
Password:
# For compiz
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
--22:40:31--  http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [text/plain]

100%[====================================>] 4,180         --.--K/s             

22:40:32 (28.50 KB/s) - `-' saved [4180/4180]

OK
Get:1 http://www.getautomatix.com feisty Release.gpg [189B]
Ign http://www.getautomatix.com feisty/main Translation-en_US
Get:2 http://wine.budgetdedicated.com feisty Release.gpg [191B]
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US
Hit http://www.getautomatix.com feisty Release
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:4 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://wine.budgetdedicated.com feisty Release
Hit http://security.ubuntu.com feisty-security Release
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US
Get:5 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US
Hit http://www.getautomatix.com feisty/main Packages
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Get:6 http://archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://wine.budgetdedicated.com feisty/main Packages
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-backports Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security Release
Hit http://wine.budgetdedicated.com feisty/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://archive.ubuntu.com feisty-updates/restricted Packages
Hit http://archive.ubuntu.com feisty-updates/main Packages
Hit http://wine.budgetdedicated.com feisty/main Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Get:7 http://download.tuxfamily.org feisty Release.gpg [189B]
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_US
Ign http://ppa.dogfood.launchpad.net feisty Release.gpg
Ign http://ppa.dogfood.launchpad.net feisty/main Translation-en_US
Ign http://download.tuxfamily.org feisty/eyecandy Translation-en_US
Hit http://download.tuxfamily.org feisty Release
Ign http://ppa.dogfood.launchpad.net feisty/restricted Translation-en_US
Ign http://ppa.dogfood.launchpad.net feisty/universe Translation-en_US
Ign http://ppa.dogfood.launchpad.net feisty/multiverse Translation-en_US
Hit http://download.tuxfamily.org feisty/eyecandy Packages
Hit http://ppa.dogfood.launchpad.net feisty Release
Hit http://download.tuxfamily.org feisty/eyecandy Packages
Get:8 http://download.tuxfamily.org feisty/eyecandy Sources [37B]
Ign http://ppa.dogfood.launchpad.net feisty/main Packages
Ign http://ppa.dogfood.launchpad.net feisty/restricted Packages
Ign http://ppa.dogfood.launchpad.net feisty/universe Packages
Ign http://ppa.dogfood.launchpad.net feisty/multiverse Packages
Ign http://ppa.dogfood.launchpad.net feisty/main Sources
Ign http://ppa.dogfood.launchpad.net feisty/restricted Sources
Ign http://ppa.dogfood.launchpad.net feisty/universe Sources
Ign http://ppa.dogfood.launchpad.net feisty/multiverse Sources
Hit http://ppa.dogfood.launchpad.net feisty/main Packages
Hit http://ppa.dogfood.launchpad.net feisty/restricted Packages
Hit http://ppa.dogfood.launchpad.net feisty/universe Packages
Hit http://ppa.dogfood.launchpad.net feisty/multiverse Packages
Hit http://ppa.dogfood.launchpad.net feisty/main Sources
Hit http://ppa.dogfood.launchpad.net feisty/restricted Sources
Hit http://ppa.dogfood.launchpad.net feisty/universe Sources
Hit http://ppa.dogfood.launchpad.net feisty/multiverse Sources
Get:9 http://repoubuntusoftware.info feisty Release.gpg
Ign http://repoubuntusoftware.info feisty/all Translation-en_US
Ign http://repoubuntusoftware.info feisty Release
Get:10 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://repoubuntusoftware.info feisty/all Packages
Hit http://us.archive.ubuntu.com feisty Release
Err http://repoubuntusoftware.info feisty/all Packages
  404 Not Found
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Get:11 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US
Hit http://archive.canonical.com feisty-commercial Release
Hit http://archive.canonical.com feisty-commercial/main Packages
Failed to fetch http://repoubuntusoftware.info/dists/feisty/all/binary-amd64/Packages.gz  404 Not Found
E: Some index files failed to download, they have been ignored, or old ones used instead.
Fetched 46B in 25s (2B/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package compiz-fusion-plugins-unofficial
compiz is already the newest version.
compiz-gnome is already the newest version.
compizconfig-settings-manager is already the newest version.
compiz-fusion-plugins-extra is already the newest version.
compiz-fusion-plugins-extra set to manual installed.
if  [ (ps -A | grep -c "compiz") -eq '0' ]; then
     if (( 0 == "1" )); then
            DISPLAY=:1 compiz --replace -c emerald &
     else echo "./install-compiz-fusion.sh: Error: beryl-manager not launched. Xgl not running?"
     fi
else
     DISPLAY=:1 metacity --replace &
fi
[Desktop Entry]
Encoding=UTF-8
Name=Compiz Manager
Name[en_US]=Compiz
GenericName=3D Window Manager
Comment=Compiz-Fusion 3D Manager
Comment[en_US]=Compiz-Fusion 3D Manager
Icon=/usr/share/icons/hicolor/scalable/apps/beryl-manager.svg
Exec=/usr/local/bin/toggle_compiz.sh
Terminal=false
Type=Application
Categories=GTK;GNOME;Application;Utility;
StartupNotify=true
X-Ubuntu-Gettext-Domain=compiz-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
Package dbus-x11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dbus-x11 has no installation candidate
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session
[Desktop Entry]
      Encoding=UTF-8
      Name=Xgl Gnome
      Comment=Start an Xgl Session
      Exec=/usr/bin/startxgl.atignome.sh
      Icon=
      Type=Application

```
It appears to have worked...  Shall I try the xgl session again?

---

### Post by dougfractal on 2007-08-12
good luck

althought> Package dbus-x11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dbus-x11 has no installation candidate

I don't know if this is a problem.

also 
> cat /etc/X11/xorg.conf

you might need this
> 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.newbackup
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


---

### Post by jeremy1138 on 2007-08-12
This is the output of that command:
```

jeremy@jeremy-laptop:~$ cat /etc/X11/xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "vbe"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option "KernelModuleParm"           "agplock=0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Enable"
EndSection

```

---

### Post by jeremy1138 on 2007-08-12
Here is the output from the second 2 commands:
```

jeremy@jeremy-laptop:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
jeremy@jeremy-laptop:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2

```

---

### Post by jeremy1138 on 2007-08-12
output from other 3 commands:
```

jeremy@jeremy-laptop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.newbackup
jeremy@jeremy-laptop:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
jeremy@jeremy-laptop:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3

```

---

### Post by dougfractal on 2007-08-12
> glxinfo | grep direct
glxgears

try

> compiz --replace &  #  start compiz
> metacity --replace &  #  end compiz


I've gotto go Bye!!!

---

### Post by jeremy1138 on 2007-08-12
Ok here is the output of the first two commands:
```

jeremy@jeremy-laptop:~$ glxinfo | grep direct
direct rendering: Yes
jeremy@jeremy-laptop:~$ glxgears

```
(I saw the gears) 

And here is the output from the second 2:
```

jeremy@jeremy-laptop:~$ compiz --replace & # start compiz
[1] 6328
Checking for Xgl: jeremy@jeremy-laptop:~$ not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity --replace & # start compiz
[2] 6353

```
I'm not sure if it matters but I am not in the xgl session...  Does that matter for the purpose of these tests?

---

### Post by jeremy1138 on 2007-08-12
ok...  bye...  Thanks for the help!

---

### Post by jeremy1138 on 2007-08-12
I tried to restart with xgl and no dice...  If you see this let me know if there is anything else I may be able to try...  Thanks for the help!

---

### Post by dougfractal on 2007-08-13
sudo gedit /etc/X11/xorg.conf
> Section "Extensions"
        Option      "Composite" "Enable"
EndSection

to 
> Section "Extensions"
Option "Composite" "Disable"
EndSection

---

### Post by jeremy1138 on 2007-08-13
Ok that's done.  Here is my current xorg.conf file:
```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "KernelModuleParm" "agplock=0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```
What's next?  Do I try to start an xgl session?

---

### Post by jeremy1138 on 2007-08-13
Ok I just tried to start the xgl session and no dice, it still looks the same...  It's all garbled with lots of lines through everything and I can't read a thing...

---

### Post by dougfractal on 2007-08-14
I think **Bigfish** had you problem 
[http://forum.compiz-fusion.org/showthread.php?t=2319&highlight=XGL+Desktop+garbled](http://forum.compiz-fusion.org/showthread.php?t=2319&highlight=XGL+Desktop+garbled)
read the whole post, and he has an answer at the end of the page :)

I think we are off topic, so you better start a new thread "XGL Desktop is garbled" ;)
post a link here so that i can follow it.


just check for this in /var/log/Xorg.1.log or /var/log/Xorg.0.log
> (WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work  

post 
> cat /var/log/Xorg.0.log
fglrxinfo

---

### Post by jeremy1138 on 2007-08-14
Hey!  This is the output of:
```

gedit /var/log/Xorg.0.log

```
contents of /var/log/Xorg.0.log
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux jeremy-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 14 17:35:18 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 103c,30ae rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 1002,5a37 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 1002,4374 card 1002,4374 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1002,4375 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1002,4373 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,30ae rev 11 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,30ae rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,30ae rev 02 class 04,01,00 hdr 80
(II) PCI: 00:14:6: chip 1002,4378 card 103c,30ae rev 02 class 07,03,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5955 card 103c,30ae rev 00 class 03,00,00 hdr 00
(II) PCI: 06:02:0: chip 14e4,4318 card 103c,1355 rev 02 class 02,80,00 hdr 00
(II) PCI: 06:06:0: chip 10ec,8139 card 103c,30a4 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:5:0), (0,2,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:20:4), (0,6,7), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xc02fffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) rev 0, Mem @ 0xc8000000/27, 0xc0100000/16, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[1] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[2] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[3] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[4] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[5] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[6] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[1] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[2] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[3] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[4] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[5] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[6] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[7] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[8] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[11] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[12] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[13] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[14] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[6] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[7] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[8] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[9] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[10] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.39.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.39.4
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.393.1                  
(II) ATI Proprietary Linux Driver Build Date: Jul 20 2007 13:50:49
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x5955) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[6] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[7] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[8] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[9] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[10] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x7c4850
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[5] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[6] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[7] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[8] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[9] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[10] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[11] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[12] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[20] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[26] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "KernelModuleParm" "agplock=0"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5955)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x30ae)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc8000000
(--) fglrx(0): MMIO registers at 0xc0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON XPRESS 200M Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.39.4
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: AUO  Model: 1974  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 1
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.600 redY: 0.340   greenX: 0.310 greenY: 0.560
(II) fglrx(0): blueX: 0.150 blueY: 0.115   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1301  h_sync_end 1333 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 804  v_sync_end 808 v_blanking: 816 v_border: 0
(II) fglrx(0):  AUO
(II) fglrx(0):  B154EW01 V9
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0006af741900000000
(II) fglrx(0): 	010f0103802115780a85a599574f8f26
(II) fglrx(0): 	1d505400000001010101010101010101
(II) fglrx(0): 	010101010101ea1a0080502010301520
(II) fglrx(0): 	44004bcf100000180000000f00000000
(II) fglrx(0): 	00000000000000000002000000fe0041
(II) fglrx(0): 	554f0a202020202020202020000000fe
(II) fglrx(0): 	004231353445573031205639200a00cc
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  2 power states available:
(II) fglrx(0):   1. 301/250MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 100/133MHz @ 60Hz []
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.90  1280 1296 1328 1408  800 804 808 816
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   68.90  1280 1296 1328 1408  768 788 792 816
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   68.90  1024 1168 1200 1408  768 788 792 816
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   68.90  848 1080 1112 1408  480 644 648 816
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   68.90  800 1056 1088 1408  600 704 708 816
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   68.90  720 1016 1048 1408  576 692 696 816
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   68.90  720 1016 1048 1408  480 644 648 816
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   68.90  640 976 1008 1408  480 644 648 816
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   68.90  640 976 1008 1408  400 604 608 816
(**) fglrx(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   68.90  640 976 1008 1408  350 579 583 816
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   68.90  512 912 944 1408  384 596 600 816
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   68.90  400 856 888 1408  300 704 708 816 doublescan
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   68.90  320 816 848 1408  240 644 648 816 doublescan
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   68.90  320 816 848 1408  200 604 608 816 doublescan
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.90  1280 1296 1328 1408  800 804 808 816
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   68.90  1280 1296 1328 1408  768 788 792 816
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   68.90  1024 1168 1200 1408  768 788 792 816
(**) fglrx(0): *Mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   68.90  848 1080 1112 1408  480 644 648 816
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   68.90  800 1056 1088 1408  600 704 708 816
(**) fglrx(0): *Mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   68.90  720 1016 1048 1408  576 692 696 816
(**) fglrx(0): *Mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   68.90  720 1016 1048 1408  480 644 648 816
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   68.90  640 976 1008 1408  480 644 648 816
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   68.90  640 976 1008 1408  400 604 608 816
(**) fglrx(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   68.90  640 976 1008 1408  350 579 583 816
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   68.90  512 912 944 1408  384 596 600 816
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   68.90  400 856 888 1408  300 704 708 816 doublescan
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   68.90  320 816 848 1408  240 644 648 816 doublescan
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 48.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   68.90  320 816 848 1408  200 604 608 816 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(**) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): KernelModuleParm: "agplock=0"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc0202000 - 0xc02020ff (0x100) MX[B]
	[7] -1	0	0xc0200000 - 0xc0201fff (0x2000) MX[B]
	[8] -1	0	0xc0003800 - 0xc00038ff (0x100) MX[B]
	[9] -1	0	0xc0003400 - 0xc00034ff (0x100) MX[B]
	[10] -1	0	0xc0003000 - 0xc00033ff (0x400) MX[B]
	[11] -1	0	0xc0002000 - 0xc0002fff (0x1000) MX[B]
	[12] -1	0	0xc0001000 - 0xc0001fff (0x1000) MX[B]
	[13] -1	0	0xc0000000 - 0xc0000fff (0x1000) MX[B]
	[14] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[15] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x2acd649b2000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.39.4
(II) fglrx(0):     Date: Jul 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 17.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=2
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x38000000 FBMappedSize: 0x005e9000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1210)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled

```
And here is the output of fglrxinfo:
```

jeremy@jeremy-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6650 (8.39.4)

```
I created a new post on the topic that you suggested.  The address is [http://ubuntuforums.org/showthread.php?t=525827](http://ubuntuforums.org/showthread.php?t=525827) .  Thanks for your help!  I hope to see you there!

---

