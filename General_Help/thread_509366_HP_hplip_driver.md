---
title: "HP hplip driver"
date: 2007-07-25
forum: General Help
---

### Post by Adaminla on 2007-07-25
I have an HP Deskjet D2360 and am running Dapper on a home built machine.  Printer seems to work OK (installed driver is hplip 1.7.4a) and was noticing that HP has a new driver out (hplip 2.7.6) with patch. Has any one installed this driver? Any coments?

---

### Post by linuxwizard on 2007-07-25
IMO As long as the printer works and no problems or issues I would leave it alone If it is not broke don't fix it. The way I look at it is how much different is that new driver really going to make and what issues will occur with it. Is it worth it ?

---

### Post by Adaminla on 2007-07-26
Thanx, on the whole I agree with you, but the new driver has a Device Manager which will tell me if I'm starting to run low on ink. I went ahead and installed the new driver and printer works fine except for the Device Manager. Now have an icon in Applications>Accessories>HP Device Manager that does nothing when I click it. Any suggestions?

---

### Post by Sef on 2007-07-26
> Thanx, on the whole I agree with you, but the new driver has a Device Manager which will tell me if I'm starting to run low on ink. I went ahead and installed the new driver and printer works fine except for the Device Manager. Now have an icon in Applications>Accessories>HP Device Manager that does nothing when I click it. Any suggestions?

I wonder if it is something to do with Dapper.   I had the same problem with it as you do.     When I upgraded to Edgy, then I could see my ink levels.

---

### Post by linuxwizard on 2007-07-26
i use the HP Toolbox which tells me my ink level plus alot of setting I can change to config the printer. I have 3 HP printers using on  Dapper Ubuntu/Kubuntu, Edgy Ubuntu/Kubuntu,  Feisty Ubuntu/Kubuntu. I see my ink levels in all of them. Not sure about Applications>Accessories>HP Device Manager. I don't have that listed.

---

### Post by Adaminla on 2007-07-26
Thanx, linuxwiwz abd sef, How do I get HP tools?

---

### Post by linuxwizard on 2007-07-26
System > Preferences > HPLIP Toolbox

System > Administration > HPLIP Toolbox

If they are not showing up in your menu you will have to add them > right click on Applications > Menu Layout window will come up > under menu left side look for Preferences click on it > you will see a list of applications on the right side that are install on your system find HPLIP Toolbox > Click on box to the left of HPLIP Toolbox now it will show up in menu   Now do the same for Administration. When done close. Now go and see if they are listed in your menu if you click on HPLIP Toolbox it should now tell you to install Python-qt 3 > go to Synaptic to install  (3 packages will be installed) > now open up HPLIP toolbox

---

### Post by rbmorse on 2007-07-26
Or, from a terminal window you can type

hp-toolbox

---

