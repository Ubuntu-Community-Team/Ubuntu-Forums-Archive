---
title: "/dev/sr0 is write-protected [installing software for wifi usb adapter]"
date: 2016-10-13
forum: General Help
---

### Post by hunterni on 2016-10-13
I'm new to linux and stumbling my way through this installation, but I want to run this bash script (install.sh) for my wifi usb adapter. It won't let me run it because the /dev/sr0 drive is write-protected. I've tried:

sudo mount -o rw,remount /media/nick/RTL8811AU

but I get this error:
mount: cannot remount /dev/sr0 read-write, is write-protected

Any ideas, friends?

---

### Post by yetimon_64 on 2016-10-13
You can't remount an optical device to be read/write as the file system on an optical disc is read-only. /dev/sr0 is the system device for cd/dvd drives (optical devices). 

Try copying the contents from the cd/dvd (/media/nick/RTL8811AU) to a location you can write to, like a folder in your home directory, and then from there run the install.sh file. That is make a folder in your home folder and call it "RTL8811AU" then copy the contents of /media/nick/RTL8811AU to it via the file manager window. 

You should then be able to run the installer from the new location. Good luck, yeti.

---

### Post by hunterni on 2016-10-13
Ok, so I now have copied the files to my hard drive, but it's still not letting me run the install script. I'll navigate to the folder and then go:

sudo ./install.sh

But this gives me the error:

sudo: ./install.sh: command not found

Even when I go in as root user it gives me "permission denied".

Am I missing something here?

---

### Post by Jimysbil on 2016-10-13
Your script has probably not executable rights.
Just open a terminal and type:
```
cd [COLOR=#ff8c00]{the folder path of your script}[/COLOR]
sudo chmod +x install.sh
sudo ./install.sh
```

---

### Post by yetimon_64 on 2016-10-13
Navigate to the folder you created in your home folder and check the installer is set as executable. 

To do so in the GUI, right click on the installer and select "Properties" > Permissions Tab > Tick the box on the bottom of the Permissions tab for the file. If it is not set as executable it can give the "permission denied" error you note. There are other possible reasons for that error, most likely is the executable bit not being set.

Edit: Jimysbil got to it first :-)

---

### Post by hunterni on 2016-10-13
Thank you, guys! I'm already amazed at how helpful the linux community is. I'm running into other problems during the installation but it seems like others have encountered similar difficulties so I'm looking at other threads. Appreciate your help!

---

