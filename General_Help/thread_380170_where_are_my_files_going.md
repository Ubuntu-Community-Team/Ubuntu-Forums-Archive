---
title: "where are my files going??"
date: 2007-03-09
forum: General Help
---

### Post by icehammer on 2007-03-09
everytime i select a file and press delete.. the file goes permanently!! it doesn't show in trash...!!

i've lost many imp files coz of this.. how to correct this?

---

### Post by xadder on 2007-03-09
In Linux/Unix delete (rm) usually means delete! If you want thinks in trash I think you need to drag them there. Or you can bring up the menu from the file-browser - it has a move to trash option.

---

### Post by Darko Beta on 2007-03-09
You can also right-click "move to trash."

---

### Post by flossgeek on 2007-03-09
It sounds like you have the "*Include a Delete command that bypasses Trash*" selected. Open Nautilus, (the file browser)go to "*Edit>Preferences*", in the dialog box that appears select the "*behavior tab*" and look at the two "Trash" options. 

Selecting the "*Ask before emptying the Trash or deleting files*" will enable a prompt when deleting trash for example. If you see that "*Include a Delete command that bypasses Trash*" is **CHECKED** then **UN-CHECK** it and click close. Now when you delete it should go straight to trash.

---

### Post by geirha on 2007-03-09
Sometimes when I delete stuff on other filesystems than where /home/ is, it doesn't get deleted, and doesn't show up in my trash-can. If this is what happens to you, then you will find your files at the root of the filesystem in a folder called ```
.Trash-username
```

You can search for them by typing this in a terminal:
```
for dir in $(mount | grep '^/dev/' | cut -d' ' -f3) ; do ls -ld $dir/.Trash-$USER ; done
```

To view these in nautilus, you need to switch on 'show hidden files'. You can toggle that option by hitting CTRL+H

---

### Post by wpshooter on 2007-03-09
> **flossgeek said:**
> It sounds like you have the "*Include a Delete command that bypasses Trash*" selected. Open Nautilus, (the file browser)go to "*Edit>Preferences*", in the dialog box that appears select the "*behavior tab*" and look at the two "Trash" options. 

Selecting the "*Ask before emptying the Trash or deleting files*" will enable a prompt when deleting trash for example. If you see that "*Include a Delete command that bypasses Trash*" is **CHECKED** then **UN-CHECK** it and click close. Now when you delete it should go straight to trash.

It sounds like to me that the default parameter has been changed.  I believe that by default that the Include a delete command that bypasses Trash is OFF, i.e. not checked !!!

---

### Post by icehammer on 2007-03-10
no, its checked in nautilus... (as in, the bypass trash option is unchecked)

and when i mean delete, i mean i'm deleteing it from nautilus only.. it doesn't show up in trash!!

it does in .Trash-icehammer... but its too inconvinient as i have 9 partitions.. going to all 9 and deleting all files manually is a bit of a pain..

any other way>?>?

---

### Post by geirha on 2007-03-10
You could make a script, and create a launcher to it on the Desktop. 'Empty Trash' or something. 

Something like this perhaps (NOTE: haven't tested this myself!)

```

#!/bin/bash
LOGFILE=$(mktemp -t emptytrash.XXXXXX)

for dir in $(mount | grep '^/dev/' | cut -d' ' -f3) ; do 
    [ -d $dir/.Trash-$USER ] && rm -rfv $dir/.Trash-$USER >>$LOGFILE
done

# Pop up a window showing which files where deleted
zenity --text-info --title="Empty Trash" --filename=$LOGFILE --width=600 --height=400

# remove the temporary file
rm -f $LOGFILE

```

---

### Post by cmost on 2007-03-10
> **icehammer said:**
> everytime i select a file and press delete.. the file goes permanently!! it doesn't show in trash...!!

i've lost many imp files coz of this.. how to correct this?

I'm slightly confused.  Why are you deleting "many imp files" in the first place?  Even if you intend them to end up in the trash, the trash bin is NOT a safe place to store files you might need later my friend.  I highly recommend you create some sort of archiving system such as an external USB memory key or backup files you might not need to a CD and then trash that at some later date.

---

