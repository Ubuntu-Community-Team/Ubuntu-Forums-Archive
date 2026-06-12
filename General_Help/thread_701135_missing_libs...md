---
title: "missing libs.."
date: 2008-02-19
forum: General Help
---

### Post by jorik42 on 2008-02-19
Not sure if this is the best place to post this, but, as the title said, i seem to be missing several "lib" files.  These ones, to be exact:

libstdc++5 (>= 1:3.3.4-1)
libqt3-mt (>= 3:3.3.8really3.3.7)
libaudio2
libsmpeg0

any ideas on how to fix this little problem?

thanks,
     jorik

---

### Post by meindian523 on 2008-02-19
Search for them in System>>Administration>>Synaptic and install them.

---

### Post by jorik42 on 2008-02-19
thanks for the suggestion.  regrettably, it did not work.  as suggested, i went into synaptic and searched out the libs that I was missing.  

i began with libstdc++5 (>= 1:3.3.4-1).  However, there is no libstdc++5; however, there is a libstdc++6, which is allready installed (with version number 4.2.1-5ubuntu4.  Presumably this is a higher version number, and should cover whatever libstdc++5 did.  unless im missing something.  

as for libqt3-mt, there is no lib with that exact name.  there are four similarly named libs however (libqt3-mt-mysql, -obdc, -psql, -sqlite).  when trying to install one of these libs (for instance, libqt3-mt-mysql), i recieved the following error:

libqt3-mt-mysql:
 Depends: libmysqlclient15off (>=5.0.27-1) but it is not installable
 Depends: libqt3-mt (>=3:3.3.8really3.3.7) but it is not installable

this also seems to depend on libqt3-mt, but i dont see that here to install.  

i then searched for libaudio2, but once more found no lib by that name.  there was a libaubio2 file, but that was not installable with the following errors:

libaubio2:
 Depends: fftw3  but it is not installable
 Depends: libsamplerate0  but it is not installable

neither fftw3 or libsamplerate0 exist.  there is an fftw2, however.  

libsmpeg0:  this lib doesnt exist.  

what does this mean/should i do?


thanks
     jorik42

---

### Post by jorik42 on 2008-02-21
i did some more probing, and realized that somehow, in the software sources, i did not have ubuntu set to update the main repositories and so forth.  this seems to have been my problem; i have only tried a few things thus far but no glitches yet!

jorik

---

### Post by meindian523 on 2008-02-22
So are you now able to install those libs?

---

