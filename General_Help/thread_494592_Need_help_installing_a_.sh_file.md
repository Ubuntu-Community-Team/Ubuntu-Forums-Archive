---
title: "Need help installing a .sh file"
date: 2007-07-07
forum: General Help
---

### Post by izquierdista on 2007-07-07
Hello, I own a digital notepad called a Digimemo. There is some third party software that allows me to take the notes stored in the digimemo and transfer them onto my linux computer and be able to read them. The software I downloaded was in a .sh format. Whenever I used SUSE it was very easy to install the program all I would do was double click on the .sh file and it would ask me where I wanted to install it and it would work great. 

Unfortunately I tried doing the same thing in ubuntu but I get these error messages, Can anyone help me, I really need to get this thing to work with Ubuntu because I plan to use it during school. from the looks of it I think the program was made for KDE.

n case anyone wants to try installing it so that you can see the error for yourself and maybe tell me how to go about using the program I would be glad to email you the file, I tried attaching it to this post but I get a message that says that the file is too big. I dont care if it doesnt install it on the hard drive as long as the program works that is all I care about. 

Here is the error message that I get when I try to install it in ubuntu:

```
#!/bin/sh
function error()
{
	kdialog --error "$1" --title "Could not install Digital Handwriting Page Viewer"
	exit 1
}

if [ -z `which uudecode` ]
then
	error "You must have uudecode installed to run this installer."
fi

if [ -z `which tar` ]
then
	error "You must have tar installed to run this installer."
fi

if [ -z `which bzcat` ]
then
	error "You must have bzcat installed to run this installer."
fi

INSTALL=`kdialog --getexistingdirectory $PWD`
if [ -z $INSTALL ]
then
	error "You must specify an install directory that already exists."
fi

if [ `which kde-config` ]
then

#DESKTOP=`kde-config --expandvars --install xdgdata-apps`
DESKTOP="`kde-config --localprefix`/share/applnk"
mkdir -p $DESKTOP
touch $DESKTOP/DHWPageViewer.desktop || error "Could not create menu entry."
( cat > $DESKTOP/DHWPageViewer.desktop ) << DESKTOP_END
[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=/bin/sh $INSTALL/DHWPageViewer2.0/wrapper
Icon=$INSTALL/DHWPageViewer2.0/icon.png
Name=Digital Handwriting Page Viewer
Categories=Qt;KDE;Graphics
DESKTOP_END
kbuildsycoca --menutest &> /dev/null
fi

mkdir -p $INSTALL || error "Could not write to install directory."
cd $INSTALL
(uudecode -o /dev/stdout | bzcat -c | tar -xv ) << ENDOFWRAPPER
begin-base64 644 encoded.dat
```

---

### Post by energiya on 2007-07-07
> **izquierdista said:**
> 
Here is the error message that I get when I try to install it in ubuntu:

That's the sh file... what are the errors?

---

### Post by iStealth on 2008-04-18
try this tool 
[http://in.freeshell.org/index.html](http://in.freeshell.org/index.html)

---

