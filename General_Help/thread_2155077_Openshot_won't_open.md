---
title: "Openshot won't open"
date: 2013-06-17
forum: General Help
---

### Post by psykatog on 2013-06-17
No idea.  Tried apt-get purge and reinstalling though the package manager, but here's what I get : 

```
jrmy@kskdn:~$ openshot

------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.3)
--------------------------------
Fatal: cannot create /home/jrmy/.openshot/queue
```

The only clue is that I attempted to load a video from a flash drive, then thought better of it and closed openshot without saving.  Then I copied the file to my hard drive and tried again, but openshot refuses to open for me.  Any thoughts?

(Kubuntu 13.04)

EDIT - tried the following on a blind guess.  Program opened, but is unresponsive.

```
jrmy@kskdn:~$ sudo openshot[sudo] password for jrmy: 


------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.3)
--------------------------------
Process no longer exists: 3646.  Creating new pid lock file.
No LADSPA plugins were found!


Check your LADSPA_PATH environment variable.


Detecting formats, codecs, and filters...

```

-after which it went on to list all the codecs it works with (presumably).

---

### Post by ajgreeny on 2013-06-17
It must be worth removing (or renaming) the openshot configuration folder or file in your /home and trying again to open openshot.

I have never used openshot so have no idea where the config folder/files may be but you should be able to find some clues with ```
locate -i openshot | grep $USER
```

---

### Post by psykatog on 2013-06-17
I'm not familiar with that process of troubleshooting - what is th purpose of deleting the config file?  

I ran my file manager (had to use admin rights) and entered home/.openshot/ , under which there are a few foldes and a file titled config.xml, the entirety of which is this : 
```
370True775536345900450None260FalseYouTubeFalseFalseNosdlfresher17melt20
asciiFalseblenderYesDV/DVD NTSCmediumFalse
```

I assume the command you posted was to help me find the config file?

Anyway, here's what I did, which is working for now - I removed the folder /.openshot/ from my home directory, then ran openshot through the terminal.  I still got the same "error" message as above, but it appears to be importing and exporting videos okay.  I'm glad I had the trouble though, because I actually found that kdenlive has a few features openshot doesn't which are helpful, although I still need openshot to open the specific format my tablet records into.

---

