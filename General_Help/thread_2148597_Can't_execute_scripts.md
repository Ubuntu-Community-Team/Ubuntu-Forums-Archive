---
title: "Can't execute scripts"
date: 2013-05-25
forum: General Help
---

### Post by ohmy28 on 2013-05-25
I have some Shell Scripts that I use but when I try to open them, it wont open. They worked perfectly on 12.10 but can't get them working here. I try opening them, and Pypar2 comes up and I have no clue what that is. The script is a simple open Nautilus in Root so I don't have to type it in terminal.

---

### Post by chadk5utc on 2013-05-26
first check permissions on them, are they executable? ls filename -ltr   do you own the file? do you have permissions to run them?
have you done anything to them in Windows and then copied them to your Buntu machine? Windows text editors can change the file format causing issues in Linux.
try sudo chmod +x filename.sh
then ./filename to run the script or sudo ./filename.sh   as needed.

---

### Post by ohmy28 on 2013-05-26
Checked Permissions and it's executable. Don't know what filename -ltr is, can you explain it a little? Can't find it on Google. I do have permission to run them and they haven't been touched in Windows. It's wierd though, it was working fine only until I upgraded to 13.04

---

### Post by Klausp on 2013-05-26
He meant ```
ls -l <filename>
``` to see if you have execution permission on the file. The "l" stands for "long list" which prints the permissions of the file in the first column, the owner of the file and the group on the third and fourth.

To change ownership:
```
chown <yourusername> <filename>
```

To make it executable ("+x") for the user that owns it ("u"):
```
chmod u+x <filename>
```

---

### Post by ohmy28 on 2013-05-26
Ok, running ls -l got me 

> maxo@Dayman:~/Desktop/Stuff/Guide$ ls -l OpenasRoot.sh
-rwxr-xr-x 1 maxo maxo 649 Jun 15  2012 OpenasRoot.sh


And after running the other commands nothing happened but still no luck.

---

### Post by kalmos on 2013-05-26
It would be helpful to see (1) the contents of [FONT=courier new]OpenasRoot.sh[/FONT] and (2) the command you are executing to run the script. Alternatively, you might explain what you expect the script to do and what it does instead.

---

### Post by ohmy28 on 2013-05-26
What's inside:

```
#!/bin/bash
#
# this code will determine exactly the path and the type of object,
# then it will decide use gedit or nautilus to open it by ROOT permission
#
#
# Nov 19, 2010
#Copyright by Nguyen Duc Long <Email: longnd.s8@gmail.com>
################################################## ##################################

# Determine the path
if [ -e -n $1 ]; then
obj="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
else
base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
obj="$base/${1##*/}"
fi
# Determine the type and run as ROOT
if [ -f "$obj" ]; then
gksu gedit "$obj"
elif [ -d "$obj" ]; then
gksu nautilus "$obj"
fi

exit 0
```

I got it from here a long time ago [http://ubuntuforums.org/showthread.php?t=1685916](http://ubuntuforums.org/showthread.php?t=1685916)

---

### Post by HiImTye on 2013-05-26
that's a nautilus script, not one run from a terminal. put it in ~/.gnome2/nautilus-scripts/ and remove the extension (the literal filename shows as the menu item) and it will appear in Nautilus when you right vlick under the sub menu 'Scripts'

---

### Post by ohmy28 on 2013-05-26
Ok, I did it and still no luck. It opens only in PyPar2, whatever that is

---

