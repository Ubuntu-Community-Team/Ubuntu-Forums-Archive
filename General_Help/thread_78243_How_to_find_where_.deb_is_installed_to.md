---
title: "How to find where .deb is installed to?"
date: 2005-10-18
forum: General Help
---

### Post by phend-one on 2005-10-18
I'm still pretty new to this.

I know .deb files are debian based install files that can be installed using the command:
"sudo dpkg -i <package>.deb"

But the problem is, I just ran that command for [glGo]("http://www.pandanet.co.jp/English/glgo/download.html") and I have no idea how to find it or where it is installed to in the linux filesystem.

Any commands I can use to find it? How do I get it into the gnome panel under "Games" ?

Thanks for any help!

---

### Post by Pablo_Escobar on 2005-10-18
You may need to try "locate nameoftheprogram".

About editing panels -> In Breezy there is a tool (SMEG) to edit panels, look for it in Applications.

---

### Post by manicka on 2005-10-18
or open Synaptic and find the package in the database.

Then right click on the package and choose pproperties.

Look in the 'installed files' tab

---

### Post by xmastree on 2005-10-18
[QUOTE=phend-one]But the problem is, I just ran that command for [glGo]("http://www.pandanet.co.jp/English/glgo/download.html") and I have no idea how to find it or where it is installed to in the linux filesystem.[/QUOTE]Does it show up in synaptic? If it does, highlight it, click **properties > Installed files** and you'll see a list of all the files and their paths.

Edit: Damn, you beat me to it!

---

### Post by phend-one on 2005-10-18
Thanks for all the replies.

I tried "locate glGo" but it didn't return anything. Does it matter where in the filesystem I sit? /home? /? /etc?

Yup Synaptic told me the locations! I shall remember this method from now on when installing .deb files. 

:cool:

---

### Post by egon spengler on 2005-10-18
another method is "whereis glco"

---

### Post by manicka on 2005-10-18
[QUOTE=egon spengler]another method is "whereis glco"[/QUOTE]

nice one, thanks :)

---

### Post by matthias_k on 2005-10-18
locate searches a database which is built periodically using updatedb (a cron job runs it every now and then, you may have noticed harddisk activity from time to time).
It probably didn't find the program because it wasn't in the DB yet. Run updatedb and locate should be able to find it. Otherwise, 'find' is your friend.

---

