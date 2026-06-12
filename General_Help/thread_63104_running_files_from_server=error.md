---
title: "running files from server=error"
date: 2005-09-07
forum: General Help
---

### Post by dbrine on 2005-09-07
I am trying to play or execute files from my server but I always get an error, unless I copy the files my my pc? I could always play music, open PDF's etc from the server using windows?

 Example when I try to play a music file over the network, "Couldn't display "smb://dave@192.168.1.10/wd-6...ngels%20(Remix%20Version).wma".

---

### Post by amohanty on 2005-09-07
typically for programs like your media player or xpdf you need to provide the display.
If you are the only user using the local machine the display probably is :0

You can find out what your display id is by typeing the following in the terminal
echo $DISPLAY

so try the following on the terminal
<program name> --display:0 <program arguments>

depending on the app you are trying to run you could possibly replace the --diaply arg with -D or -d

<program name> --help 
will give you a list of the available args in most cases.

HTH
AM

---

### Post by bdamon on 2005-09-07
[QUOTE=dbrine]I am trying to play or execute files from my server but I always get an error, unless I copy the files my my pc? I could always play music, open PDF's etc from the server using windows?

 Example when I try to play a music file over the network, "Couldn't display "smb://dave@192.168.1.10/wd-6...ngels%20(Remix%20Version).wma".[/QUOTE]



I think you will find if you mount the share instead of trying to use smb:// everything will work as expected.

---

