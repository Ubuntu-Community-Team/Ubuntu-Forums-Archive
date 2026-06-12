---
title: "I have made a bash script and put it in /bin, how do I run it at bootup?"
date: 2007-04-25
forum: General Help
---

### Post by billdotson on 2007-04-25
I made bash script to automate some backing up of files and I want it to run as a startup program/process (in Feisty) here is the script: 

```

#make sure there is a mount point called /media/Windows first!!

#

mount /dev/sda1 /media/Windows -t ntfs -o nls=utf8,umask=0222
#

cp -ubpR /media/Windows/Program\ Files/Activision/Rome\ -\ Total\ War/saves /media/Ext3_1/rome_saves

cp -ubpR /media/Windows/Documents\ and\ Settings/Bill/Application\ Data/Mozilla/Firefox/Profiles/iL70wrj5.default /media/Ext3_1/firefox_backup

cp -ubpR /media/Windows/Documents\ and\ Settings/Bill/Application\ Data/Thunderbird/Profiles/hln64ls5.default /media/Ext3_1/thunderbird_backup

cp -ubpR /media/Windows/Documents\ and\ Settings/Bill/Application\ Data/Opera/Opera/profile /media/Ext3_1/Opera_backup

cp -ubpR /media/Windows/Documents\ and\ Settings/Bill/My\ Documents/My\ Games/Company\ of\ Heroes/Savegames /media/Ext3_1/coh_saves

cp -ubp -t /media/Ext3_1/swat4_campaign /media/Windows/Program\ Files/Sierra/SWAT\ 4/Content/System/Campaign.ini
cp -ubpR /media/Windows/Program\ Files/Activision/Rome\ -\ Total\ War/saves /media/Ext3_1/rome_saves
cp -ubpR /media/Windows/Documents\ and\ Settings/All\ Users/Documents/STALKER-SHOC/savedgames /media/Ext3_1/STALKER_saves

cp -ubpR /media/Windows/Documents\ and\ Settings/All\ Users/Documents/Monolith\ Productions/FEAR/Save/Profile000/SinglePlayer /media/Ext3_1/FEAR_saves
umount /media/Windows

```

I have gone to sessions and tried adding it in there but nothing.  The owner and group is root:root .  Thanks.

---

### Post by cookfromfrozen on 2007-04-25
A quick and dirty way would be to reference /bin/yourscript.sh in /etc/init.d/bootmisc.sh by putting a line like this at the end:
```
/bin/myscript.sh
```

---

### Post by billdotson on 2007-04-25
yeah.. I don't understand how to do that (referencing).. and also.. my script ( I just wrote up a text file, went to properties and told it to run as a program) is just the name.. there is no .sh after it.

Are you sure that is the only really "easy"way (takes the least amount of work) ?

edit: I just added .sh to the end on the name so yeah.. one step closer, but does it really matter about the extension? the text file itself was executable already.  Also, I know there is a difference but a bin file and a sh file?

Not to say you are wrong or incompetent in any way but could I not go to sessions, startup programs nad put a name in and then have the command be /bin/Windowsfilebackup.sh ?

---

### Post by x1a4 on 2007-04-25
Hi,

Put the script in _/etc/init.d/_ then create symlinks to it in _/etc/rc#.d/_
Where # is the runlevel number the script is to run in (default is 2).

See _/etc/rc#.d/README_ for details on how to name the symlinks.

---

### Post by ebash on 2007-04-25
Add a call to your script in the file /etc/rc.local, that file is always executed after the computer boots.

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Run custom backup
/bin/myscript.sh > /dev/null 2>&1

exit 0

```

---

### Post by billdotson on 2007-04-27
got it done.  >> SOLVED

---

