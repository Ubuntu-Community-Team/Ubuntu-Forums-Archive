---
title: "cups-pdf postprocessing help"
date: 2008-04-09
forum: General Help
---

### Post by dpurple77 on 2008-04-09
Hi everybody. 

I am trying to use the postprocessing function of the cups-pdf and going out of my mind. After trying many hours to make it work with the apparmor profile just for the sake of testing i uninstalled apparmor but still no go.
What i do is this. Edit /etc/cups/cups-pdf.conf and changing the line #Postprocessing to Postprocessing /usr/local/bin/PdfName .
PdfName is a script which just for testing purposes displays a zenity info window, which is executable and works like a charm as a standalone. But nothing happens when i print a page from cups-pdf.

ANY suggestions, ideas, or just sympathy is greatly appreciated. I am on the verge of slaying a chicken and soaking my pc with its blood. I am trying on gutsy but also tried hardy beta with the same results. Anybody got postprocessing to work? 

Thank you all in advance.

---

### Post by dpurple77 on 2008-04-10
Some more info for anyone brave enough to give a hand. I am trying to use zenity in my postprocessing script which is the part thats doesn't seem to work. 
When i use a simple touch the file gets created normaly. What i am trying to do is run a postprocessing script that gets the created filename from cups-pdf and pops a zenity window that asks for a filename and a place to save the file so i can effectively move the created pdf from cups-pdf to a place of my choice with a choosen filename. 
The script goes something like this 

#!/bin/bash
FileName=$(zenity --file-selection --save --confirm-overwrite)
mv $1 $FileName

This works beautifully as standalone but not when called from cups-pdf postprocessing. If i put some terminal based command like just a touch it works. So the problem is probably because of the gtk from zenity. I have disabled apparmor just for the sake of the testing. 
Any help greatly appreciated.

---

### Post by bogwan on 2008-04-28
Yesterday I attempted to move an old postprocessing script I wrote from Fedora to Ubuntu 8.04 LTS. I ran into the same problems that you describe.  I solved the Zenity problem this morning and will pursue the apparmor settings problem later.  I thought you might be interested in what I found.

Zenity must communicate with the X windows display that you are using.  cups-pdf does not know about the X session you are running.  The following code sets and exports the DISPLAY and sets and exports XAUTHORITY. 

,,,
CURRENT_PDF="${1}"
CURRENT_USER="${2}"
DISPLAY=:0.0
export DISPLAY
XAUTHORITY=/home/${CURRENT_USER}/.Xauthority
export XAUTHORITY
...

I have attached my script to put it all in context.  If this works for you let me know.

---

### Post by noynac on 2008-04-28
--please delete--

---

### Post by dpurple77 on 2008-05-12
Thank you very very much for your solution. I had given up on the thread and just now saw you answer. Works great!

---

