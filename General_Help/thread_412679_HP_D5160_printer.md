---
title: "HP D5160 printer"
date: 2007-04-18
forum: General Help
---

### Post by dangermouse28 on 2007-04-18
Has anyone else tried using a HP Photosmart D5160 printer?

I had an old Deskjet 890C installed and working perfectly on Dapper when I bought a nice new D5160. Tried installing it using the existing Printing tools - but no joy - well it's hardly surprising - Dapper is older than the printer after all! 

Googled around and eventually found HP's own hplip source package which I installed exactly as per instructions. This installed the HP-Setup utility and worked ok until I needed to use the old 890C again. Now it won't work at all. Neither Ubuntu's printing facility or HP-Setup can see it, much less print from it.

Do I have some sort of driver conflict? Will the D5160 play nicely natively in Feisty without any other packages?

---

### Post by PrivatePickle on 2007-04-22
I purchased the D5160 while using dapper and have since upgraded to feisty and have not had any problems.  
I have only done standard printing of documents and off the web, I have not tried printing directly on a cd or dvd in Ubuntu yet.

Edit:  I purchased this printer while using edgy not dapper.

---

### Post by dangermouse28 on 2007-04-23
Did you just use the normal method of printer installation or did you have to use HP's own package?

---

### Post by PrivatePickle on 2007-04-23
I used the normal method of printer installation (this was in edgy not dapper as I stated in my previous post).  I remember there
being an HP entry listed under either Preferences or Administration but it never did anything.
When I upgraded to Feisty this entry disappeared.  Under the printer properties it lists the driver as
hpijs (recommended).  I also searched synaptic for hplip and it was listed as installed so I 
uninstalled it and 'hplip - data' with no problem.  Printer still works the same as it did before so I
don't think it was using the hplip driver.

---

