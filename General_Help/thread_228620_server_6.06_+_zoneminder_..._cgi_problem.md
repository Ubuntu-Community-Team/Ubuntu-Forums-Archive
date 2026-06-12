---
title: "server 6.06 + zoneminder ... cgi problem ?"
date: 2006-08-03
forum: General Help
---

### Post by intenseblu on 2006-08-03
hello, i just finished a pretty painful (<-newb) install on ubuntu. it is running on 6.06 ubuntu server and i am using the custom zm_remote_camera.cpp zm_remote_camera.h that was created for the sony SNC-1/3 cameras.

when i log in through firefox into the ZM interface all is working fine except when i click to check my monitor instead of a picture i get a broken link icon displayed (as if its poiting to the wrong place) but i know ZM is capturing images fine cause when i click to go to configure zones for that monitor i see a picture it captured from the camera.

what i thought it is, a problem with executing the zms cgi script ... all my files are stored under /var/www/cgi-bin/ so technically apache should have no problem recognizing them there or letting them run ... i tried to access the cgi-bin directory directly through firefox and it tells me permission denied error (not sure if i should be able to access it?) and when i try to access /cgi-bin/zms/ it tells me the file was not found (it is there ... i just can't get in there). under ZM config i have attempted to use both /cgi-bin/zms and /cgi-bin/nph-zms

i have tried to get apache to access the cgi-bin scripts by editing apache2.conf with the following:

uncommented this line:
AddHandler cgi-script .cgi

and added this line:
ScriptAlias /cgi-bin/ "/var/www/cgi-bin/"

with no results...

can you guys think of anything i may be not doing right ?
other posts on this subject have been no help so far so please if you can think of anything... i am so close i can taste it Razz

---

### Post by intenseblu on 2006-08-03
solved ... the cgi-bin i created in /var/www was not enabled so i just cp'ed the scripts to /usr/lib/cgi-bin and all works well now

---

