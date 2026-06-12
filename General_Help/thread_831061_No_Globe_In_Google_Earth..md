---
title: "No Globe In Google Earth."
date: 2008-06-16
forum: General Help
---

### Post by antlachance on 2008-06-16
Hey,

     I installed Google Earth Linux yesterday, but didn't have time to actually start it and give it a test.  So today I open the program, and the screen where the Earth should be is partially grey.  So I click the grey and it goes away, but, there is still no globe.  The stars are there and moving appropriately when i click and drag, but no earth.

Any help would be greatly appreciated,

Anthony

---

### Post by imon9 on 2008-06-16
it is a known bug with google earth 4.3beta.

if u want to, u have to run as administrator:
sudo /opt/google-earth/googleearth (through terminal)
or gksu /opt/google-earth/googleearth (by F2)

else, use google-earth 4.2

---

### Post by antlachance on 2008-06-16
Thanks.  Ill just go with 4.2.

---

### Post by nc_jed on 2008-06-17
Same prob, solution reported by imon9 was fine.

antlachance:  At the risk of sounding like a dick, all you need to do is right-click the Applications menu, Edit Menus, Choose Internet, Double click 'Google Earth' to edit.  On the 'Command' line, add **gksu**.  Seems easier than uninstalling/downloading/reinstalling...

---

### Post by antlachance on 2008-06-17
It probably was, but everything went perfectly during the uninstall of 4.3 and the install of 4.2 so I'm happy.

---

### Post by Talkless on 2008-08-23
I have removed .config/Google directory and that helped.

---

