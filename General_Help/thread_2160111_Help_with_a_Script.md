---
title: "Help with a Script"
date: 2013-07-05
forum: General Help
---

### Post by garyzw on 2013-07-05
I have a script to open a folder as root-- is there a way to add the password to the script so it opens the folder without asking for the password?

> #!/bin/bash
 
# First, please make sure gksudo is installed
# Run 'sudo apt-get install gksu' to make it sure
 
# Get the path
if [ -e -n $1 ]; then
        obj="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
else
        path="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
        selected="$path/${1##*/}"
fi
 
#Check if selected object file or folder
if [ -f "$selected" ]; then
        gksudo gedit "$selected"
elif [ -d "$selected" ]; then
        gksudo nautilus "$selected"
fi
 
exit 0


---

### Post by Habitual on 2013-07-05
Never put passwords in scripts. EVER.

---

### Post by garyzw on 2013-07-05
> **Habitual said:**
> Never put passwords in scripts. EVER.

ya i know that but I want to do it -- security is not a concern on this machine

---

### Post by prodigy_ on 2013-07-05
You don't have to put password in your script to suppress sudo password prompt: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Stonecold1995 on 2013-07-06
Yeah, don't ever put passwords in a file as plaintext.  I'll answer your question though, just so you know.

```
echo 'my password' | sudo -S command
```

---

### Post by Habitual on 2013-07-06
> **garyzw said:**
> ya i know that but I want to do it -- security is not a concern on this machine
Scary.

---

### Post by garyzw on 2013-07-06
Ok where do I put the
 
echo 'my password' | sudo -S command


in the following script to make it work


#!/bin/bash


# First, please make sure gksudo is installed
# Run 'sudo apt-get install gksu' to make it sure


# Get the path
if [ -e -n $1 ]; then
obj="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
else
path="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
selected="$path/${1##*/}"
fi


#Check if selected object file or folder
if [ -f "$selected" ]; then
gksudo gedit "$selected"
elif [ -d "$selected" ]; then
gksudo nautilus "$selected"
fi


exit 0

---

### Post by garyzw on 2013-07-06
> **Habitual said:**
> Scary.

Look this is only temporary and I want to learn a little about scripts also-- if you are scared to do it them don't do it

---

### Post by Cheesehead on 2013-07-06
Yes, but learning the wrong way or insecure way to do things seems counterproductive. Nothing you learn will be terribly useful in the future.
Learning the right way to use commands, on the other hand, seems like a wiser investment of your time and effort.

For example, you can use the dbus-send command to select/deselect/list-selected items in Nautilus without all that mucking about with permissions.

---

