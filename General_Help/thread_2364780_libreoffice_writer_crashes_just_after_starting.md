---
title: "libreoffice writer crashes just after starting"
date: 2017-06-27
forum: General Help
---

### Post by teodosio on 2017-06-27
I have been using LibreOffice for years and I had never a problem. Recently, having last version of LibreOffice installed on Ubuntu 16.04 it started freezing and closing suddenly. I thought that if I updated to Ubuntu 16.10 that would disappear. I have now Ubuntu 16.10 installed but the problems persists. 
I have re-installed LibreOffice again with no results. The most strange thing is that all the other aplications work properly (Calc, Impress, Draw, Math, Base) except Writer which closes suddenly after I call for it.
If I run libreoffice in terminal by typing "libreoffice --writer" it happens exactly the same with no special error message. My version of LO is 5.3.3.2
Could anyone help me with this?

---

### Post by speartip on 2017-06-28
First Point. The LO you are using is not the stock install of either 16.04 or 16.10, so how did you install it?
Secondly now you have upgraded to 16.10, it reaches end of life next month, so you will either need to keep on upgrading until the next LTS or go back to 16.04.
Anyway to your problem.
2 Things to try. Firstly, open LO, & under tools/options/view, try unticking "use hardware acceleration", some have had problems with this.
Secondly, try deleting your libreoffice config folder, as something in there might be corrupted. It's in the .config folder in your home folder. Obviously you will have to "show hidden files" to see it.
If these 2 things fail, I suggest uninstalling LO, and reinstalling the stock version from the repos.

---

### Post by teodosio on 2017-06-28
Dear speartip,
Thanks for your answer. Yes, I've noticed that the LO version is not the stock version of 16.04 or 16.10. I installed it through the terminal using "sudo apt-get install libreoffice". Previously I had deleted previous LO using sudo apt-get remove --purge libreoffice*, sudo apt-get clean and sudo apt-get autoremove.
I'll try, later, your suggestions and post the result.
Anyway, what is the stock version of the 16.10?
Thanks again.

---

### Post by speartip on 2017-06-28
> **teodosio said:**
> Anyway, what is the stock version of the 16.10?
Thanks again.
Not sure as I only use 16.04, but I think it should be 5.2.x, not 5.3.x.
Maybe someone else can chip in with that one.
Anyway try the other suggestions, they may work.

---

### Post by teodosio on 2017-06-28
I checked and definitely is 5.2.7.
The other suggestions didn't work. Going to uninstall and reinstall stock versions as the 2 other suggestions didn't work. I'll tell about the result. Thanks.

---

### Post by teodosio on 2017-06-29
Dear speartip:
I installed the correct version for 16.10 and it worked, at least so far it didn't crash anymore.
Thanks again for you suggestions, which were quite helpful.
All the best.

---

