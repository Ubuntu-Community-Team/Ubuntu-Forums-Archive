---
title: "wine-0.9.60 installation problem"
date: 2008-04-20
forum: General Help
---

### Post by drumanart on 2008-04-20
Hello everybody.
I try to install **Wine** on my **UBUNTU GUTSY** using a terminal. After unpacking the **wine-0.9.60.tar.bz2** package with 
**tar -jxvf wine-0.9.60.tar.bz2**
going to the new created directory and typing:
 **sudo ./configure** 
**sudo make depend && maked**
after running for a while I get the error:

[B]/bin/sh: cannot create version-stamp: Permission denied
rm: cannot remove `version-stamp': Permission denied[/B Thks

Any idea Thks

---

### Post by konungursvia on 2008-04-20
You might look at an ls listing of the files extracted, and make sure the configure binary is executable, by its color. Also, try without the sudo if you can. I don't remember doing it as superuser, if you tarred it into a user-executable location. But I'm not entirely sure.

---

