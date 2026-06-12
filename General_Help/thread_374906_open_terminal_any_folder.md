---
title: "open terminal any folder"
date: 2007-03-03
forum: General Help
---

### Post by stchman on 2007-03-03
Hello all, in other linux distros you can open a terminal in any folder.  I was wanting to know if  you can do the same in Ubuntu.

Thanks

---

### Post by stchman on 2007-03-03
I found it in the synaptic package manager under nautilus-open-terminal.  Very useful.

---

### Post by stchman on 2007-03-05
> **stchman said:**
> I found it in the synaptic package manager under nautilus-open-terminal.  Very useful.

It should be installed by default IMO.

---

### Post by ardchoille42 on 2007-03-05
> **stchman said:**
> It should be installed by default IMO.

It was, at one time, but someone took it out of the default install.

---

### Post by stchman on 2007-03-08
> **ardchoille42 said:**
> It was, at one time, but someone took it out of the default install.


WHY!!!!!  The open terminal in the folder you are in is extraordinarily useful.  Before I found out where it was I was freaking lost.

---

### Post by ardchoille42 on 2007-03-08
> **stchman said:**
> WHY!!!!!  The open terminal in the folder you are in is extraordinarily useful.  Before I found out where it was I was freaking lost.

I don't know whether it was the gnome devs or the ubuntu devs that removed it, but it was a bad decision. The nautilus-open-terminal package should be part of the default install for any distro which uses gnome as its default desktop.. but that is only my opinion.

---

### Post by milton1 on 2007-03-08
Not an ubuntu decision. This is still a default functionality in kde/kubuntu.

---

### Post by tlacuache on 2007-03-08
Here's a nautilus script which I think is more useful than the "nautilus open terminal" package's way of doing things. If you execute the script with a file selected or no files selected, it opens the terminal in the current directory. If you execute the script with a subdirectory selected, it opens the terminal in that subdirectory.

```

#!/bin/sh
base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
if [ -z "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
     dir="$base"
else 
     while [ ! -z "$1" -a ! -d "$base/$1" ]; do shift; done
     dir="$base/$1"
fi
gnome-terminal --working-directory="$dir"

```

If you don't know how to use nautilus scripts, google around or check [this]("http://g-scripts.sourceforge.net/faq.php") out.

-SG

---

