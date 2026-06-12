---
title: "Need Help with Missing “public Key”"
date: 2008-05-26
forum: General Help
---

### Post by davidkyn on 2008-05-26
Need Help with Missing “public Key”

Hi, I'm still at it as a newbie:).....anyways I am following this excellent guide:
Comprehensive Multimedia & Video How-to
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

My main issue is with errors about NON EXISTANT PACKAGES so I checked to see if I have enabled Medibuntu, Universe and Multiverse repositories by going to Software sources:
Is this correct?
[IMG]http://i181.photobucket.com/albums/x30/davekyn/SoftwareSourcesUbuntuSoftware.png[/IMG]So while I was there I checked "Third Party Sofatware and say that I had three unticked..SO I TICKED THEM thinking it would be the right thing to do:[IMG]http://i181.photobucket.com/albums/x30/davekyn/ThirdPartySoftware.png[/IMG]
after I reloaded this is the error I got:
[IMG]http://i181.photobucket.com/albums/x30/davekyn/TheCopy.png[/IMG]
Also is there where I fix the error..public key??? I am also having trouble trying to update win32 codec support is this also where I am to fix that problem????:
[IMG]http://i181.photobucket.com/albums/x30/davekyn/Authentication.png[/IMG]

---

### Post by p_quarles on 2008-05-26
You need to download Medibuntu's GPG key (instructions are on their web site) and import it. You can use either the "Import Key File" button in Synaptic there, or the apt-key command line application.

---

### Post by noynac on 2008-05-26
I'm having the same problem as the OP. I suspect the medibuntu servers are down or otherwise unavailable.

---

