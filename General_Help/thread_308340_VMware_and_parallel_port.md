---
title: "VMware and parallel port"
date: 2006-11-27
forum: General Help
---

### Post by peterx14 on 2006-11-27
Hi all,

I am running Edgy and VMware Workstation 5.5.3 and I needed to get a hosted Windows VM to print. However, since my printer (Canon LBP-800 doorstop) is unsupported in Linux, I can't have Windows print thru Edgy; it must print direct to the printer. The problem was that VMware couldn't see my parallel port.

To cut a long story short, based on info found here:
[http://www.murrayc.com/blog/permalink/2005/12/24/wheres-my-parport0/](http://www.murrayc.com/blog/permalink/2005/12/24/wheres-my-parport0/)

I have a work around, which is:```

sudo modprobe ppdev
sudo chmod 666 /dev/parport0
sudo rmmod lp
```

I'm pretty-much a total newbie though, so I'd like to know how best to set this up permanently. I could write a script to run the above and then start VMware, but is that the best way to do things?

Any advice welcome!! :D

Peter.

---

### Post by peterx14 on 2006-12-15
Okay... a minor update; I've added my user to the "lp" group ([after jumping through a few hoops -- see here](http://www.ubuntuforums.org/showthread.php?t=317547)) so I don't need to chmod the parport0 device to access it.

So now I only need to do the following before starting VMware:
```
sudo modprobe ppdev
sudo rmmod lp
```

---

### Post by Portable_Jim on 2007-01-07
great. Thanks !! the ONE reason for me using vmware - now hope is rekindled...

...but windows does not recognize the  port!?!

Please help.

---

### Post by Portable_Jim on 2007-01-07
> **Portable_Jim said:**
> great. Thanks !! the ONE reason for me using vmware - now hope is rekindled...

...but windows does not recognize the  port!?!

Please help.
found the answer! 
1. Log in
2. Control Panel --> add hardware --> (a few more steps - you have already connected the hardware) 
3. add printer --> local printer -->LPT1 --> (printer model) --> (few other options)

The test page worked.

---

### Post by megamaced on 2007-02-25
Is there a more permanent solution to this? Those commands work great but it's a bit annoying having to enter them everytime I use VMware.

---

### Post by doogy2004 on 2007-02-26
When I get home I will post a script to fix this when the system boots, in the script I have also addressed the httpd issue with the MUI

---

### Post by megamaced on 2007-02-28
> **doogy2004 said:**
> When I get home I will post a script to fix this when the system boots, in the script I have also addressed the httpd issue with the MUI

Cool

---

### Post by doogy2004 on 2007-03-02
I used the commands from other places and put it all into a script that puts those commands into the /etc/init.d/rc file.  

sorry for the wait, here it is.

to use this script do the following

```
$ cd
$ nano mui-fix
```

Enter the following into the file
```
#Fix VMware Server MUI httpd fix

#define variable
rcfile=/etc/init.d/rc
fixfolder=/var/run/vmware/httpd/

echo "#vmware httpd fix <<start>>" | sudo tee -a $rcfile
echo "mkdir "$fixfolder | sudo tee -a $rcfile
echo "chgrp nogroup "$fixfolder | sudo tee -a $rcfile
echo "chmod 700 "$fixfolder | sudo tee -a $rcfile
echo "/etc/init.d/httpd.vmware start" | sudo tee -a $rcfile
echo "#vmware httpd fix <<end>>" | sudo tee -a $rcfile

#Fix VMware parallel port
echo "modprobe ppdev" | sudo tee -a $filename
echo "chmod 666 /dev/parport0" | sudo tee -a $filename
echo "rmmod lp" | sudo tee -a $filename
```

Press CTRL+X
Press Y
Press ENTER

```
$ chmod 777 mui-fix
```

You can now run the script with the following command

```
$ sudo ./mui-fix
```

if the script has run correctly there should be no output

you can verify that the script has run by
```
$ nano /etc/init.d/rc
```
press PAGE DOWN till you reach the bottom and you should see where the script has inserted text

WARNING!!!
This script needs to only be run ONCE.  I have not properly created the script to do error checking or check to see if it has already been run.  Once I get the script to a point that I'm completely happy with it and I will be sending it off to be included into Automatix.

Check out Automatix at [http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by doogy2004 on 2007-03-05
I noticed that i forgot to take out some of my comments that i had in for testing, please update the script.  remove the information that the script put in the rc file, save the rc file and run the script again.

---

### Post by bsfah3 on 2008-06-13
So in case anyone else comes upon this the way I fixed this was to create a file in /etc/init.d called fix_vmware.
```
cd /etc/init.d
sudo touch fix_vmware
```

then open up fix_vmware and enter the following lines (use whatever editor you like best)

```
#! /bin/sh
chmod 666 /dev/parport0
rmmod lp
```

save the file and make it executeable

```
sudo chmod +x /etc/init.d/fix_vmware
```

and finally used update-rc.d to run it at the default runlevels

```
sudo update-rc.d fix_vmware defaults
```

Is there a better way to do it?  Probably... this seems to have worked for me though without having caused trouble.  Good luck!

---

