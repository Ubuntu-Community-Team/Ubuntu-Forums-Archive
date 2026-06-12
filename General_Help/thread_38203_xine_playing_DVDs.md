---
title: "xine playing DVDs"
date: 2005-05-30
forum: General Help
---

### Post by astronerd on 2005-05-30
Hello all, I have been trying to play dvds using xine(not burned dvds, normal ones..) and ever time I try I get an error saying someting along the lines of "Dvd seems to be encrypted. ARe you trying to play encrypted dvds without lbs....  ?(I dont remember the exact name of the lbsc thing that it says)  I have tried to look for plugins that have that lbs. thing in them, but I cant find anything....  Does anyone know where/how I can fix this?  

Oh  one more thing, is there a way I can change the prefs in xine so that I can make if go fullscreen by double clicking the mouse instead of ctrl+F?

Thanks, Charles

---

### Post by linuxNewb on 2005-05-30
libdvdcss2

make sure you have the proper sources as per,

[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

---

### Post by astronerd on 2005-05-30
[QUOTE=linuxNewb]libdvdcss2

make sure you have the proper sources as per,

[http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)[/QUOTE]
 I tried to get the libdvdcss2 file from synaptic, but I get this error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted libdvdcss2 1.2.8-1~5.04ubp1
  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/libdvdcss2_1.2.8-1~5.04ubp1_i386.deb](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/libdvdcss2_1.2.8-1~5.04ubp1_i386.deb)  403 Forbidden

I added the repos it said to add as well....  What is wrong?

---

### Post by astronerd on 2005-05-30
Never mind, I got it to work.  I had to turn off the backport repos and then it worked fine.  Thanks!

---

