---
title: "Click to Execute"
date: 2007-08-22
forum: General Help
---

### Post by scombest on 2007-08-22
So I just installed synergy between my linux box and my mac. I was wondering if there was a way to make a file to execute the synergy start script by just clicking on it and leave the icon on the desktop to avoid opening terminal and typing and remembering my ip. if it helps the code i need to run is:

synergyc ***.**.***.**

thanks.

---

### Post by pjman on 2007-08-22
I know it's not exactly what your looking for but I've set synergy to automatically start by 

system --> preferences --> sessions

Choose new and then enter the command. Now it will start every time you log in :-)

---

### Post by tekkenlord on 2007-08-22
That's easy. Just open your favourite editor and type the following:

#!/bin/bash
synergyc ***.**.****.**

and then make the script executable by

chmod +x <name_of_the_file>

You will issue the last command without the "<>" and with the appropriate file name of course. Hope it helps!

---

### Post by scombest on 2007-08-22
this does make a fine shell script but does not allow me to execute by clicking, now when clicked it just opens up a text editor. any other ideas?

---

### Post by tekkenlord on 2007-08-23
Are you sure you gave the file executable rights? Try

ls -l <file_name>

and post the output.

---

