---
title: "Run Script @ login with root permissions"
date: 2013-12-28
forum: General Help
---

### Post by michikurz on 2013-12-28
Hi
as the title already says I have problems with running a script.
The script does the following
[LIST=1]
[*]mount the device (hdd) 
[*]check if gxmessage is installed, if not --> install it 
[*]do a backup with rsync 
[/LIST]

I have made a udev rule to run the script when the hdd is plugged in. There I have no problem because scripts which are executed by udev rules are executed with root permissions.

Now here is the problem:
The hdd is plugged in as long as I dont need the notebook in school and this time I get no backups then.
So I want the script to be executed at login. I tried this with System Settings -> Preferences -> Startup Programs but it doesent have enough permissions.
I also tried running it with a command in ~/.profile but there is the same problem.

If you want to see the udev rule or my script please tell me :D

I would be glad if anybody could help me
Michael

---

### Post by steeldriver on 2013-12-28
Do you want this to be executed on login for all users, or just for you? If you're using lightdm, you should be able to run a script as root on 'session start', which may do what you want

```

[SeatDefaults]
greeter-session=unity-greeter
[B]session-setup-script=/usr/local/bin/myscript.sh
[/B]allow-guest=false
greeter-hide-users=true
greeter-show-manual-login=true

```

---

### Post by michikurz on 2013-12-28
Hi thank you for your quick reply!

I want this script to be executed just for me.
So with this code my script would be executed after login? Because the script opens a gxmessage where I can or have to choose if I want to do an update or not.

I dont use lightdm because I am using Linux Mint but I hope that this also works with mdm :)

Michael

---

### Post by steeldriver on 2013-12-28
OK in that case I don't think it's going to work

Maybe you could use udisks to mount the hdd without requiring root?

---

### Post by michikurz on 2013-12-28
UPDATE:

automount in nemo is disabled, new udev rule:

```

KERNEL=="sd?1", ATTRS{serial}=="NA******", ATTRS{idVendor}=="0***", ATTRS{idProduct}=="2***", ACTION=="add", ENV{UDISKS_IGNORE}="1", PROGRAM="/path/to/script.sh"
KERNEL=="sd?1", ENV{ID_SERIAL_SHORT}=="S2***********", ACTION=="remove", PROGRAM="/path/to/script.sh"

```

Mounting/unmounting is done in the script.
At login the script is called as Startup-Program.

Here is the mounting/umounting part:
```

#!/bin/bash
MYNAME=michael
MOUNTPOINT=/media/michael/SeagateExpansionDrive
UUID="D8*************"

if [ ACTION=="add"  ]
then
        export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
        export XAUTHORITY=/home/${MYNAME}/.Xauthority
        export DISPLAY=:0.0
fi

#Check wether Device is plugged in or removed
if [ $ACTION == "remove" ]
then
        #Check if already unmounted
#       if [ -e $MOUNTPOINT ]
#       then
                #Unmount and remove
                umount $MOUNTPOINT
                rmdir $MOUNTPOINT
#       fi
        exit 0
elif [ $ACTION == "add" ]
then
        #Mount the drive
        mkdir $MOUNTPOINT
        mount -U $UUID $MOUNTPOINT
else
        #mount the drive
        mkdir $MOUNTPOINT
        mount -U $UUID $MOUNTPOINT
fi

if [ ACTION=="add"  ]
then
        #Check if gxmessage is installed
        if [ ! -e /usr/bin/gxmessage ]
        then
                apt-get install -y gxmessage
                #checking if installation was succesful is done later
        fi
fi

blkid |grep $UUID
if [ $? != 0 ]
then
        #Hard Drive not mounted --> exit
        exit 0
fi

```

Michael

---

