---
title: "Problem opening Software Center"
date: 2015-11-01
forum: General Help
---

### Post by mike378 on 2015-11-01
After installing Ubuntu (Unity) on Chromebook using Crouton, I went to Ubuntu and licked on "Ubuntu Software Center" and got this pop-up message: "Sorry, can not open the software database. Please re-install the "software-center" package.  

I then went to the terminal and  typed "sudo apt-get install software-center". Afterward, I got a number of lines, one of them saying "software-center is already the newest version". Then I typed "gksu software-center" and got the following message: "Gtk -Message: Failed to load module "unity-gtk module" and a pop-up window similar to the one described above. 

Please help, thx. Mike.

---

### Post by PaulW2U on 2015-11-01
> **mike378 said:**
> I then went to the terminal and  typed "sudo apt-get install software-center". Afterward, I got a number of lines, one of them saying "software-center is already the newest version". 
Mike, try the following command which will **reinstall** the Software Centre rather than try to **install** it.
```
sudo apt-get install --reinstall software-center
```
I've just tried it on a spare PC and the database/catalog is rebuilt. Hopefully that will solve your problem.

---

