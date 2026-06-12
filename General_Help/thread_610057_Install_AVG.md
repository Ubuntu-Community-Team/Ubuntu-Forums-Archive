---
title: "Install AVG"
date: 2007-11-11
forum: General Help
---

### Post by djm-uk on 2007-11-11
Yes I know there is already one but it seems to make life difficult (eg download from the command line!) & seems to have grown like topsy - currently at about 23 pages in flat view...

Download the Linux package from the web site free.grisoft.com - I did a search for 'linux' which got me to the AVG free for Linux page & there is a debian/ubuntu package listed.

D/load the package in the browser, 'open' it & install it via the GUI.

Now if you try & update you will probably get an error 'Cannot run avgupdate' so do the following to set the permission on the files:-

open a terminal window (via Applications / accessories) & execute the following commands...(As documented in lots of other places on the web)

sudo chmod 775 /opt/grisoft/avg7/bin/avgupdate
cd /opt/grisoft/avg7/var/
sudo chmod 777 run
sudo chmod 777 update/log

Now when you try & update you will probably get 'cannot download avgupdate.ctf'

Go into System/administration/users & groups
Click on 'manage groups' button 
Scroll right down the list to find the 'avg' group & click on it then properties button
Put a tick next to your user name.
OK/Close your way out
now LOG OUT AND BACK IN AGAIN

Update should work...

---

### Post by K.Mandla on 2007-11-14
Moved to General Help.

---

