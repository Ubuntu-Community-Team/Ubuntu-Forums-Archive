---
title: "Bash script creation helper"
date: 2007-02-16
forum: General Help
---

### Post by ardchoille42 on 2007-02-16
I have a friend who writes a lot of bash scripts and nautilus scripts and was looking for an easy way to create skeleton scripts, via GUI (she doesn't like CLI-based editors yet), to automate some of her tasks. So, I put my scripting skills to work to write her a script helper. Here is what I came up with:

```

#!/bin/bash

# Query the user for a directory
mypath=`zenity --file-selection --directory --title="Select a directory for the new script..."`

# Query the user for a filename
myfile=`zenity --entry --title="New Bash Script" --text="Please enter a filename for the new script..."`

# Determine whether the user entered a filename or clicked the Cancel button
# Possibly need better error handling here if $myfile returns ""
# Maybe using case?
if [ "$myfile" != "" ]
then

    # Check to see if the returned /path/file already exists
    while [ -e $mypath"/"$myfile ]
    do
        zenity --error --title="New Bash Script" --text="$mypath/$myfile already exists. Please choose another path or filename."
        myfile=`zenity --entry --title="New Bash Script" --text="Please enter a filename for the new script..."`
    done

    # If all is well, create the new file
    touch $mypath"/"$myfile

    # Add the default bash line for a new bash script
    echo "#!/bin/bash" > $mypath"/"$myfile

    # Make the new script executable
    chmod a+rx $mypath"/"$myfile

    # Open the new script in gedit for further processing
    gedit $mypath"/"$myfile

else
    exit 0
fi


```

I realise the command line is more powerful, and I've told her that, but there are those who prefer GUI to CLI. Choice is a good thing, eh?

If there are bash gurus out there who don't mind helping with this, I'd appreciate some comments or enhancements to this script wherever possible.

---

