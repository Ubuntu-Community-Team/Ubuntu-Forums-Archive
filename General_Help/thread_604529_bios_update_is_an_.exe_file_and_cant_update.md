---
title: "bios update is an .exe file and cant update"
date: 2007-11-06
forum: General Help
---

### Post by 1feistymedic on 2007-11-06
I have a compaq Presario 5834.  I have had some glitchy problems where after every reboot it sometimes recognizes my second cd rom drive and sometimes does not.  these are the original drives.  I think somehow my bios has been corrupted.  

Compaq provides updates called "rompaqs" and these are .exe files that have to be placed on a floppy disk then reboot the system.  Since I have no remnants of windoze left on my system (using feisty 7.04), how do I run the update?

P.S. I made sure both drives work and replaced the ide cables.  Like I said, sometimes both drives show up, sometime only the master.  (i tried CS and Master/slave)

---

### Post by dward526 on 2007-11-06
If you can get a hold of one, use a windows 98 disk(or other disk that allows you to access the 'command line', start up and go to the DOS prompt.  Insert your floppy and run the .exe.  There is a way to put the 'command line' functions on the floppy so that it boots from it.  If anyone knows that, it would be helpful in this situation.

Second thought, try restarting with the 'rompaq' on a floppy to begin with.  Their pack may contain the necessary files to run itself if it is a BIOS flash from start up.

---

### Post by mc4man on 2007-11-06
I'm thinking maybe your asking how to create the floppy disk. I'm not sure of the wording but maybe something like this    -      dd if=<name of file> of=/dev/fd0

---

