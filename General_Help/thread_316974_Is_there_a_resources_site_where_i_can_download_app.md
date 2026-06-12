---
title: "Is there a resources site where i can download applications manually?"
date: 2006-12-11
forum: General Help
---

### Post by abh83 on 2006-12-11
Is there a resources site where i can download applications such as wpa-supplicant, automatix2 or ndiswrapper, manually? So instead of "sudo apt-get install ..."

I'd like to have a backups so that in the future if i ever have to reinstall i can do it manually WITHOUT an internet connection.

Due to the fact that i use a direct connection and a wpa-encrypted wifi point i can only reinstall and upgrade/update via Ethernet cable which is a hassle for me at this point in time!

thx
ABH

---

### Post by raul_ on 2006-12-11
[http://sourceforge.net]("http://sourceforge.net")

i guess

---

### Post by mcduck on 2006-12-11
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

But keep in mind that packages often depend on other packages, so keeping track which ones you need may become fairly impossible..

Also, if you have already installed those packages you'll find all the .deb files in /var/cache/apt/archives so you can just copy them from there instead of downloading from the web.

---

### Post by abh83 on 2006-12-11
thx guys! exactly what i was looking for!

cheers

---

