---
title: "file case / capitalization problem"
date: 2008-05-18
forum: General Help
---

### Post by virgil_disgr4ce on 2008-05-18
Hi all!  Happy Ubuntu user here, was on v.7 and just upgraded to 8.  I've had this problem from the beginning, however.

My ubuntu install is a fileserver with both mac and pc clients.  I set up a mirrored raid main drive (ext3) and everything works great, except for one odd and frustrating behavior.  I mostly use my mac and when I browse my ubuntu filesystem, it acts unpredictably with regards to filename case/capitalization.  If I move/copy files to the ubuntu drive(s) from any of my clients (regardless of OS, though I don't have another linux install to test from), all file capitalization is stripped.  Any mv or cp operations I do within ubuntu (either in a terminal or in gnome) work normally.

My research so far [indicates it's a samba problem]("http://ubuntuforums.org/showthread.php?t=692467"), but I haven't figured out how to tell if I'm using smbfs or cifs and how I would change it for future use, or if I'm on the wrong track.  I've looked through my smb.conf but didn't spot anything obvious.  Would this be more of a question of how the client (OS X or Windows) connects to the smb share?  Thanks so much for your help!

---

### Post by ryanhaigh on 2008-05-19
From here: [http://www.faqs.org/docs/Linux-HOWTO/SMB-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/SMB-HOWTO.html)

> 
    ; Mangle case = yes seems to give the correct filenames 
    ; for Win95/98/NT.
    mangle case = yes

    ; If samba is case sensitive when looking for files
    case sensitive = no

    ; Default case of files that are created
    default case = lower

    ; Preserve case for all filenames
    preserve case = yes

    ; Preserve case for dos (8.3) filenames
    short preserve case = no


You could try adding those options to your samba configuration.

---

