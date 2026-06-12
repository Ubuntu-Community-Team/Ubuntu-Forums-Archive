---
title: "trouble changing home directory for a user"
date: 2007-01-04
forum: General Help
---

### Post by dmension7 on 2007-01-04
Hi, 
I'm trying to share my documents between windows and linux.
For this purpose,  documents for a user say Sam are on an ext3 partition inside the folder:
/home/Documents and Settings/sam

Now, when i try to tell ubuntu to use this folder "/home/Documents and Settings/sam" as the home folder for sam, it seems to get confused due to the spaces in the path. I believe it tries to look for a directory "/home/Documents". 
Also I realise that the double quotes "" are not saved in the folder path even though I type them when setting the path.

Can anyone guide me as to how I can put in the path with spaces?

I'm using the 6.06 LTS version

Thanks,
Ali

---

### Post by SyvanX on 2007-01-04
Well if it's just a problem with not recognizing spaces, then a backslash ( \ ) will do in front of the spaces.

The path would look like 
/home/Documents\ and\ Settings/sam

Are Windows and Linux on the same computer or are they different computers?  Either way, I don't think it should be necessary to change your Home Directory location.

It seems pretty dubious to share an ext3 partition with windows, especially modifying the location of your home directory in linux.

---

### Post by Ocxic on 2007-01-04
i agree wil SyvanX it would be safer and better to use a fat partition for sharing files. you would want a windows crash to mess up your home partition.

---

### Post by khedron on 2007-01-04
If you just want to share documents, you could try something like **ln -s "/home/Documents and Settings/sam/My Documents" /home/sam/Documents **.

Just depends on what you want.

NB. In Linux, your home directory doesn't just contain your work. If you view hidden files, you will see that all your user configuration files are stored in /home/sam , e.g. Evolution's user data is stored in /home/sam/.evolution . If you merge your home directories, you could get random files from one OS cluttering up the window in the other OS (the Windows ext2 driver doesn't do hidden files). I would recommend just creating /home/sam/Documents and linking.

---

### Post by dmension7 on 2007-01-04
Hey Guys,
Thanks for the tips. The \[space] does not work. (yes it works when you try to do a cd, but not when you put that in the home folder path).
I resolved the problem by creating a symbolic link to the "Document and Settings" folder called "ds" and set the home path as /home/ds/sam and it works now.

I know it sounds strange to use and ext partition with windows. I'm using the IFS Driver in windows ([http://www.fs-driver.org/](http://www.fs-driver.org/)) 
The idea is to migrate over to linux (slowly). I have most of my stuff in windows now and will need to operate both OSes in parallel (and synchronized) for some time.

Thanks for your help.
Ali

---

