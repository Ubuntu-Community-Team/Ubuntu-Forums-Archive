---
title: "Every FTP on linux crashes"
date: 2006-10-25
forum: General Help
---

### Post by NiksaVel on 2006-10-25
](*,) 

hey all,

I am trying to upload my php-nuke site via ftp and every ftp prog I tried under linux crashed:

gftp, kftp, ftp extension for firefox and krusader (which doesn't crash but gives an error about too many connections from my internet address)...

the rest just crash with no error - they simply disappear for no apparent reason, the process as well...


the site has many directories and a gazillion small files (could that be a prob)...


everything works okay from win, using filezilla.


thanks for all help in advance

---

### Post by matthewstory on 2006-10-25
did you try tarring it up and using the command line?

tar yourfolder.tar.gz yourfolder
ftp <server>
put yourfolder.tar.gz

If this doesn't work then maybe try sftp, perhaps only sftp is working.

---

### Post by NiksaVel on 2006-10-25
I'm sure I could upload it as a single file, but that's not what I want to do...   to complicated...

I DID upload it all, but I went piece by piece...     it works okay with a few files/directories, but when I try to upload it all at once or even some of the bigger directories it crashes...

---

### Post by matthewstory on 2006-10-25
the GUI-based recursive FTP upload is a relatively new phenomenon, so it's not surprising if it's buggy, i guess i'm just old school with my .tar.gz ways.

---

