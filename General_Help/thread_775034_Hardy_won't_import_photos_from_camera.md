---
title: "Hardy won't import photos from camera"
date: 2008-04-29
forum: General Help
---

### Post by drewcoon on 2008-04-29
Hey, ever since I installed Hardy, plugging a camera into a USB port no longer starts up the import program automatically.

If I try and import through terminal, I get this,

```
drewc@linxp:~$ f-spot-import
libhal.c 1310 : invalid udi:  doesn't startwith '/org/freedesktop/Hal/devices/'. 
error: libhal_device_get_property_type: (null): (null)
libhal.c 1310 : invalid udi:  doesn't startwith '/org/freedesktop/Hal/devices/'. 
error: libhal_device_get_property_type: (null): (null)
libhal.c 1310 : invalid udi:  doesn't startwith '/org/freedesktop/Hal/devices/'. 
error: libhal_device_get_property_type: (null): (null)
gphoto2:usb:000,000
Starting new FSpot server

Unhandled Exception: System.Exception: Unsupported SQLite database version
  at Banshee.Database.QueuedSqliteDatabase.ProcessQueue () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
drewc@linxp:~$ 
```

I have similar issues with removable storage not showing up as icons on the desktop and having to go to /media/ instead, if the two could be related somehow?

Can anyone help me? Thanks in advance :)

---

### Post by savethewabbit on 2008-05-01
hey, i have no advice to give you, but i also have the same problem :\ i click on "import photos" and nothing happens.

---

### Post by enchantedsky on 2008-05-25
Same problem as the OP, but my icon for my digital camera SD card shows up on my desktop. 

I honestly think it is an F-spot problem with Hardy. Perhaps the bug will be worked out over time. In the mean time, try another photo program and set it in the "Removable Drives and Media" menu to automatically execute when you insert it in your computer

---

### Post by diablo75 on 2008-05-25
You should consider filing a bug for this problem.  To learn how, visit:  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by timebomb on 2008-05-26
Just to chime in - I am having the same problem. When I plug the camera in, the window comes up, but when I click "import photos," nothing happens.

That said, I am able to import photos using Picasa. I prefer the Ubuntu dialog, as it retains my date stamps and import the movies on my camera. 

It stopped working when I upgraded to Hardy.

---

### Post by tryl on 2008-06-05
The new f-spot way seems not to work (for everybody?), but you can go back to the old gthunb:

Install gthunb by running this in a terminal:

```
sudo apt-get install gthumb
```

Then go to the &#8220;System&#8221; menu, and then choose &#8220;Preferences&#8221;, and go down to &#8220;Removable Drives and Media&#8221;. Choose the &#8220;Cameras&#8221; tab and then untick the &#8220;Import photographs &#8230;&#8221; under &#8220;Digital cameras&#8221; (there is a nice screen shot at [http://linuxtnt.wordpress.com/2007/07/16/turning-off-ubuntugnomes-annoying-photo-loader/](http://linuxtnt.wordpress.com/2007/07/16/turning-off-ubuntugnomes-annoying-photo-loader/)) and set the command to be

```
gnome-volume-manager-gthumb %h
```

just as on the screen shot, see the link.

This did it form me!

---

### Post by sstalpers on 2008-07-11
I am having a similar problem, but with using "Removable Drives and Media" to automatically import photos to Digikam. Since I upgraded to Hardy I can no longer automatically import photos when I connect my camera. The camera mounts fine (I get a desktop icon, can browse into camera folders) but the import photos dialogue box no longer automatically appears. Running the command ```
digikam --download-from  /media/disk" 
``` directly from the terminal works fine.

It seems that the "Removable Drives and Media Preferences" is not working.  There is also no response if I replace the command in "Removable Drives and Media" by the gthumb command suggested by Tryl or even "xterm". Any suggestions?

---

### Post by sstalpers on 2008-07-16
Ok, I did a clean install of Hardy (for other reasons than this auto import problem) but I still can not enable auto import with Digikam. Hardy auto imports only using f-spot but I would very much prefer using Digikam. 

I managed to stop f-spot from auto importing using [this thread]("http://ubuntuforums.org/showthread.php?t=835715&highlight=automount+f-spot&page=2") by changing System>Preferences>File Management 'Media Handling: Photos' to 'Nothing' (for some obscure reason, System>Preferences>Removable Drives and Media, Digital Cameras no longer has any effect in Hardy). But there is no option to select Digikam.

Does anybody have an idea how to add Digikam as an option to the list of File Management? Perhaps by editing some config file?

---

### Post by indytim on 2008-07-16
This doesn't address directly the issue of direct importing using F-Spot.  I finally reached the limit on the amount of time I was willing to spend "dinking" around trying to get the direct import working.  I went out and bought a multiple format device reader (SD, CF etc).  It installed directly into the old floppy case area and plugged into one of the internal usb ports.  Works like a champ, automounts the media.  I believe the total cost was in the $20-$30 neighborhood.

IndyTim

---

### Post by Sef on 2008-07-16
> Hey, ever since I installed Hardy, plugging a camera into a USB port no longer starts up the import program automatically.

It is a known bug.  This is how I resolved it.

System > Administration > Software Sources > Updates > Pre-released updates (Hardy Proposed) > close

then you should get updates or click on the update manager 

System > Administration > Update Manager > Unclick all (if you don't want all the updates) > then click on F-spot > click apply

After doing that update, F-Spot worked just fine.

If you don't want the Proposed updates > go back and uncheck it in Software Sources.  

Proposed updates are like late beta updates.  Very stable, but still may cause problems.  Only some of the updates will be moved to the final update.

---

### Post by cpetercarter on 2008-07-17
I have tried that, but I cannot find any proposed updates for f-spot.

---

### Post by jason6g on 2008-10-14
well, i came looking for a solution, so i figured i would post here

i have the exact opposite, i wish for nothing to happen other than the drive mounting when i insert my card - aka i do not like the fspot pops up

shame we cant swap installs lol

---

### Post by dahlheim on 2008-10-29
similar problem, different solution here.  i "can't post new topics", so oh well...

i wanted picasa 3 to automatically import photos from an SD card when inserted (SD card from my digital camera), but a bug in Hardy disallows that.  Hardy currently sloppily has two places to configure this, and they don't get along.  the first is System:Preferences:Removable Drives and Media.  the second is found either hidden in the Nautilus menues (the file browser.  Edit:Preferences:Media), or hidden in the System:Preferences Menu (you can expose "System:Preferences:File Management" using the Menu Editor).

if you keep F-Spot installed on your system (or re-install it in my case), then configure both these menus to launch it on Photos insertion, then the script /usr/bin/f-spot-import is called on card insertion.  in my case, i just edited that script to parse the line input and launch picasa (i only tried this with picasa3, not sure if picasa2 behaves similarly but i'm guessing it might):

```

#!/bin/bash

udi="$1"
#xmessage $udi
mount_point=`hal-get-property --udi="$udi" --key=volume.mount_point`
if [ -n "$mount_point" ]; then
      # USB Mass Storage camera: need to pass f-spot a mount point

      # f-spot --import "$mount_point"
      picasa "$mount_point"
else
     # Some other camera try GPhoto2

     bus=`hal-get-property --udi="$udi" --key=usb.bus_number`
     dev=`hal-get-property --udi="$udi" --key=usb.linux.device_number`

     #xmessage $uri
     if [ -n "$uri" -a -n "$bus" -a -b "$dev"]; then
          #f-spot --import "$uri"
          uri=`printf gphoto2:usb:%.3d,%.3d $bus $dev`
          picasa "$uri"
     else
          # maybe it's "file:///folder/folder"...
          f=`echo $udi | cut -c1-7`
          #xmessage $f
          if [ "$f" == 'file://' ]; then
               fn=`echo $udi | cut -c8-`
               #xmessage $fn
               if [ -n "$fn" ]; then
                    #xmessage $fn
                    picasa "$fn"
                    exit 0
               fi
          fi
     fi
fi

xmessage "Not sure what to do with $udi"
exit 1

```

hope this helps somebody else!

---

