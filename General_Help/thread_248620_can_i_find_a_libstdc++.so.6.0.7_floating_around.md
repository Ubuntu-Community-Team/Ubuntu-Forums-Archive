---
title: "can i find a libstdc++.so.6.0.7 floating around"
date: 2006-09-01
forum: General Help
---

### Post by tuariviel on 2006-09-01
hi all,

like a completely dolt i managed to do a

ln -sf something libstdc++.so.6.0.7
instead of 
ln -sf libstdc++.so.6.0.7 something

which of course destroyed my libstdc++.so.6.0.7, as i tried not to panic over that sily mistake, i tried to run apt-get to install the library back...

but apt-get (and hence synaptic), depends on the library.... so basically, i have a botched system :/

any ray of hope of where can one find a compiled version of that file floating around? or can someone mail me their libstdc++.so.6.0.7?

i have an amd64 athlon, but i dont believe ive set anything for it to really use the 64 bit versions of the libraries, unless ubuntu autmatically does so

---

### Post by slugkilla on 2006-09-01
can't you extract it from the .deb that is resides in, and then copy it to that directory?

---

### Post by tuariviel on 2006-09-01
thanks for the answer but,
how exactly can I extract it from the deb (without using dpkg which also depends on the library) ?
(oh and, where can one find the deb which contains the said library? :/)

---

### Post by tuariviel on 2006-09-01
well, nevermind :)
thanks a lot for your answer, it turns out that while apt-get, `dselect' and aptitude all need libstdc++.so.6.0.7, dpkg itself does NOT,

so after downloading the libstdc deb from the ubuntu site i just did a 
dpkg -i libstdc++6_4.0.3-1ubuntu5_i386.deb

and im all set again, 
thanks a lot

---

### Post by slugkilla on 2006-09-01
I'm not too sure that I helped any, but i'm glad you now have your system working well again.

---

