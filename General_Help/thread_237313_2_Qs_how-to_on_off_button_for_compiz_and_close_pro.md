---
title: "2 Qs how-to on off button for compiz and close programs in terminal"
date: 2006-08-16
forum: General Help
---

### Post by onesojourner on 2006-08-16
ok question number one is how do I creat a launcher that will start and stop compiz? I can make one to open compiz but it doesnt close when I click it again. 


Q 2, how do I close a program from the terminal?

---

### Post by 3rdalbum on 2006-08-16
> **onesojourner said:**
> ok question number one is how do I creat a launcher that will start and stop compiz? I can make one to open compiz but it doesnt close when I click it again.

Create a launcher that runs the command "metacity --replace". I don't think you can easily make a launcher that toggles between them, without writing a shell script. Also I won't guarantee that Compiz will start again after being shut down.

> **onesojourner said:**
> Q 2, how do I close a program from the terminal?

killall programname

---

### Post by onesojourner on 2006-08-16
> **3rdalbum said:**
> Create a launcher that runs the command "metacity --replace". I don't think you can easily make a launcher that toggles between them, without writing a shell script. Also I won't guarantee that Compiz will start again after being shut down.



killall programname

alright thanks for the help.

how about a launcher that can open close "thefuture" is that possible?

---

### Post by sirclaudio on 2006-08-16
Create or edit the thefuture script ( sudo gedit /usr/bin/thefuture ) and put this:

> #!/bin/bash

if ps -A | grep -e " compiz.real$" > /dev/null; then
killall cgwd
metacity --replace &
else
gnome-window-decorator --replace &
compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
cgwd --replace &
fi

If it's a new file, then, sudo chmod 755 /usr/bin/thefuture

Create a custom launcher pointing to this script and compiz's icon (/usr/share/compiz/logo24.png) and now you can turn off and on compiz with just a click.

---

### Post by Ramses de Norre on 2006-08-16
Read the XGL/Compiz sticky at the top of the general support forum and scroll down to the "An easy way to restart compiz and switch back to metacity if you don't like it" section, this section tells you how to install a litlle app that does just what you wants.

---

### Post by onesojourner on 2006-08-16
thanks the script did it for me.

---

