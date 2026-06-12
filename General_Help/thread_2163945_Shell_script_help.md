---
title: "Shell script help"
date: 2013-07-20
forum: General Help
---

### Post by 7hr08ik on 2013-07-20
At my home I have 2 PCs, my main windows gaming rig, and an  ubuntu 13.04 file server. (NOT running ubuntu server just plain ubuntu)
  I have the OS drive encrypted with luks (through installation)
  But i have 5 Truecrypt ecrypted HDDs. They need to stay truecrypt for  my needs. I have the following 2 scripts setup to mount my drives on  boot of the PC.
  This simple one to open terminal and run the next script-
  ```

#!/bin/bash 
sleep 10  
gnome-terminal -e /home/kun7/.TrueCrypt/mount_truecrypt_volumes.sh
```  

And then the following code runs to get truecrypt password and mount  drive to my specified points (needs to goto specified points for my  other programs/libraries/shortcuts etc
  ```

#!/bin/bash 

echo "Enter password ..."  

oldConfig=`stty -g` 
stty -echo 
read password 
stty $oldConfig  

echo "Opening Pandora's Box ..."   

truecrypt -t /dev/sdb5 /media/P --password="$password"  -k "" --protect-hidden=no 
truecrypt -t /dev/sda1 /media/B --password="$password"  -k "" --protect-hidden=no 
truecrypt -t /dev/sdd1 /media/M --password="$password"  -k "" --protect-hidden=no 
truecrypt -t /dev/sde1 /media/V --password="$password"  -k "" --protect-hidden=no 
truecrypt -t /dev/sdf /media/S --password="$password"  -k "" --protect-hidden=no  

echo "Drives mounted ... Close when ready"  

exit 0
```

  This works great for what I need. On occasion. My problem is that I  have 2 drives connected via a PCI card. NORMALLY they are detected by  the OS as sdb5 and sda1, but every now and then they get identified as  sdc5 and sdd1. 
  This causes my script return...
  
```

Enter password ... 
Opening Pandora's Box ... 
Enter your user password or administrator password:  

Error: No such file or directory: /dev/sdb5 Incorrect password or not a TrueCrypt volume.  
Enter password for /dev/sda1: Error: No such file or directory: /dev/sdd1 
Incorrect password or not a TrueCrypt volume.  

Enter password for /dev/sdf: 
```  

What I'm wanting to do is to add an "if error" command at the end of  my script to tell it. "If error, use this instead" and then list the  alternate mount paths when the OS changes the drive points.
  I think that makes sense.

Because of the way the pci card, and truecrypt work, if the PC boots up with the alternate dev`s then some of the NEW dev point match my script and some dont, and it messes with my links/librarys. So im thinking of something like this-

```

#!/bin/bash 

echo "Enter password ..."  

oldConfig=`stty -g` 
stty -echo 
read password 
stty $oldConfig  

echo "Opening Pandora's Box ..."   

truecrypt -t /dev/sdb5 /media/P --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sda1 /media/B --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sdd1 /media/M --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sde1 /media/V --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sdf /media/S --password="$password"  -k "" --protect-hidden=no 

***IF ERROR, RUN THE FOLLOWING SCRIPT INSTEAD***

truecrypt -t ***NEW /DEV/ SLOT /media/P --password="$password" -k "" --protect-hidden=no && ...etc...etc

echo "Drives mounted ... Close when ready"  

exit 0
```

But i dont know how to write the IF/ELSE command for this. Can anyone help?

---

### Post by Cheesemill on 2013-07-20
Instead of your method it would probably just be easier to specify the drives by their UUID as this never changes. For example...
```
truecrypt -t /dev/disk/by-uuid/25f8c629-d0c8-4c39-b4c2-aacba38b5882 /media/P --password="$password"  -k "" --protect-hidden=no
```

You can find the UUID of your drives by doing...
```
ls -l /dev/disk/by-uuid/
```

---

### Post by 7hr08ik on 2013-07-20
Ive tried that already, but because of the way truecrypt works, the UUID`s are only available when the drives are mounted. If i try and get the UUID`s with the drives unmounted i only get a response for the OS drive. And my script just crashes without doing anything.

```

function mount-truecrypt () {     
local dev=$1     
local mnt=$2     
local alternative_dev=$3     

truecrypt -t $dev $mnt --password="$password"  -k "" --protect-hidden=no || \       
    truecrypt -t $alternative_dev $mnt --password="$password"  -k "" --protect-hidden=no 
} 
mount-truecrypt /dev/sdb5 /media/P /dev/sdc5
```

This was suggested to me  by a friend but this causes problems because not the dev`s are still recognised and dont swap to the alternative_dev. They arre just all in the wrong place. And means i will have to setup my links, librarys and everything eeverytime i start the PC.

Thats why im thinking a script to run 1 long command, to mount the specified /dev/ in the correct mount folder.

If the long command returns an error, then to run the secondary long command. And that way with either one, i get the correct /dev/ mounted in the correct /mount/ keeping my links and librarys all working. But i don`t understand how to write the IF/ELSE script

---

### Post by 7hr08ik on 2013-07-20
Well i have this script as of now...

```

#!/bin/bash

echo "Enter password ..."

oldConfig=`stty -g`
stty -echo
read password
stty $oldConfig

echo "Opening Pandora's Box ..."

truecrypt -t /dev/sda1 /media/P --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sdb5 /media/B --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sdd1 /media/M --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sde1 /media/V --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sdf /media/S --password="$password"  -k "" --protect-hidden=no

if [ $? -ne 0 ]
then
   echo "Oops! Something went wrong."
   echo "I'm still half alseep"
   echo "Trying alternative hamster wheels..."
   truecrypt -t /dev/sde1 /media/P --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sdf5 /media/B --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sdb1 /media/M --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sdc1 /media/V --password="$password"  -k "" --protect-hidden=no && truecrypt -t /dev/sdd /media/S --password="$password"  -k "" --protect-hidden=no
   
else
   echo "Drives mounted ... Close when ready"
fi

exit 1
```

Right now my PC is using the alternative /dev/ points so i can test this works....It's not...

It get to the first drive, fails, and gives me a truecrypt error msg asking for the correct password.....all because in the first command sda1 is now the OS drive, but normally sda1 would be recognised as the truecrypt volume connected to my PCI card.

So i need an IF command for "If sda1 is already mounted/ fails to mount, then move on..."

---

### Post by 7hr08ik on 2013-07-20
ok im getting irritated now. 

Ive got a working script. but i need to figure out 2 things,

1. How to get the "if" command to figure out what /dev/ the OS drive is on.

2. How to stop the rest of the dammed hard drives from changing /dev/ positions everytime the computer starts up!!!!

---

### Post by 7hr08ik on 2013-07-20
> **Cheesemill said:**
> Instead of your method it would probably just be easier to specify the drives by their UUID as this never changes. For example...
```
truecrypt -t /dev/disk/by-uuid/25f8c629-d0c8-4c39-b4c2-aacba38b5882 /media/P --password="$password"  -k "" --protect-hidden=no
```

You can find the UUID of your drives by doing...
```
ls -l /dev/disk/by-uuid/
```

Because of the way truecrypt works i cant use this, but is it possible to do the same thing but with hard-drive serial numbers, or model numbers? something a bit more permanent......i cant use the /dev/ as they change randomly due to 2 of the drives being on a PCI card

---

### Post by steeldriver on 2013-07-20
DISCLAIMER: I HAVE NEVER USED TRUECRYPT

I'm pretty sure truecrypt will refuse to mount a partition that either (a) doesn't contain a truecrypt volume or (b) is already mounted - so couldn't you just loop over all the /dev/sdXn block devices and try each in turn?

You could skip any devices that are already mounted by checking mtab e.g. something like

```

for blockDevice in /dev/sd??; do
  if ! grep -q "$blockDevice" /etc/mtab; then
 
    # blockDevice isn't currently mounted - attempt
    # to mount it as a truecrypt volume

  fi
done

```

Also doesn't truecrypt have a thing called "favorite volumes" for doing this kind of ting out of the box?

---

### Post by Vaphell on 2013-07-20
not that i know anything about truecrypt but can't you assign fixed mount points to these partitions in fstab?

---

### Post by Cheesemill on 2013-07-20
Try using the drive serial numbers instead of the UUID.

Find out what they are by doing...
```
ls -l /dev/disk/by-id/
```

---

