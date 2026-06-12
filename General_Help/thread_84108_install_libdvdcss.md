---
title: "install libdvdcss"
date: 2005-10-30
forum: General Help
---

### Post by eyebrowman92 on 2005-10-30
how do i go about getting libdvdcss to play encrypted dvds?

---

### Post by el toro on 2005-10-30
You can get it from marillat I think, or from the project homepage--they've got debs up--just google it.

---

### Post by NewbieNik on 2005-10-30
[QUOTE=eyebrowman92]how do i go about getting libdvdcss to play encrypted dvds?[/QUOTE]

Grab the .deb package from

[http://www.linuxsoft.cz/en/sw_detail.php?id_item=915](http://www.linuxsoft.cz/en/sw_detail.php?id_item=915)

---

### Post by eyebrowman92 on 2005-10-30
ok im sorry but im new to all this so how should i go about downloading it?

---

### Post by NewbieNik on 2005-10-30
No worries,

Just go to the link:-
[http://www.linuxsoft.cz/en/sw_detail.php?id_item=915](http://www.linuxsoft.cz/en/sw_detail.php?id_item=915)

select the .deb package from the list and save it. Tis should save to your desktop. You then need to open Applications/Accessories/Terminal
and type:-

sudo dpkg -i Desktop/libdvdcss2_1.2.8-1_i386.deb

Please notice the capital D in desktop!!!
This should then ask you to enter your password. Hey presto and Voila! libdvdcss2 should now be installed. You can delete the .deb file from the desktop after that!

---

### Post by NewbieNik on 2005-10-30
[QUOTE=NewbieNik]

sudo dpkg -i Desktop/libdvdcss2_1.2.8-1_i386.deb

that![/QUOTE]


I should add that this command is basically telling Ubuntu:- Super User DO (sudo) debian package install (dpkg -i) then the package name.

This is one of the easiest and stable way to install packages not available in Synaptic.

Hope this is of some help

---

### Post by eyebrowman92 on 2005-11-10
alright i got it from synaptic. thanks though.

---

### Post by rapha on 2005-11-11
linuxsoft.cz appears to be down right now :-/
Does anybody know where else to get libdvdcss2 from? The restricted/universe/multiverse/backports repositories do not appear to have it either.

Edit: is some governmental organization out to kill DVD usage on Linux?
/usr/share/doc/libdvdread3/examples/install-css.sh, which tries to download libdvdcss from [www.dtek.chalmers.se](www.dtek.chalmers.se) fails as well. The [https://wiki.ubuntu.com/LibdvdcssInstallationMethods](https://wiki.ubuntu.com/LibdvdcssInstallationMethods) page does not exist. What is it?

---

### Post by jamesford on 2005-11-11
u can grab them from the plf repositories
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by rapha on 2005-11-11
[QUOTE=jamesford]u can grab them from the plf repositories
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)[/QUOTE]

404 Not Found
The requested URL '/mirrors/ubuntu/plf/' was not found on this server.

(421 for the ftp server)

Thanks tho :-)

---

### Post by eyebrowman92 on 2005-11-11
isnt there a package in synaptic when you alter your repos?

---

### Post by etc on 2005-11-11
The plf repos are down :(
You can grab libdvdcss on the vlc developer's site, I don't know if it's kosher to link to it or what.

---

### Post by eyebrowman92 on 2005-11-11
oh they are? when will they be back up?

---

