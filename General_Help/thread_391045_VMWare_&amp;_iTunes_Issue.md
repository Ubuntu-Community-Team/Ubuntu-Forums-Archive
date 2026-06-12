---
title: "VMWare &amp; iTunes Issue"
date: 2007-03-22
forum: General Help
---

### Post by spgreenberg on 2007-03-22
I am running an Ubuntu 6.10 host running a Windows XP guest on VM Server 1.02. I am trying to burn a CD from within ITunes.

The following always happens: Itunes asked me to insert a blank cd (even if one is already in the drive). I do so, and ITunes says: "The disc burner is in use by an application other than ITunes".

I have tried this with an IDE drive and SCSI drive. I have tried by starting with the drives connected and disconnected. I have also tried setting ide/scsi*.exclusive = "TRUE" in the .vmx file as the "Use exclusively" checkbox is not available in the linux version of the server for the VM config.

Interestingly, I can "Back up to dics" from within Itunes with no problem. 

I disabled CD Writing in XP and the same issue happens. I also set the autoplay function to not run, but to no avail.

My hunch is there are 2 issues:

1) For some reason, when a blank disc is in the drive, iTunes doesn't recognize it as such even though the drive spins up when I first select "burn" (and yes, I have tried multiple blank discs).

2) When I re-insert a blank disc, I think that maybe the 'ide*.exclusive = "TRUE"' setting in the vmx config isn't working. I think its possible that Ubuntu is mounting the drive while iTunes is trying to access it.

Any ideas on what may be happening or how to fix it?  I am unsure of what else to try.

---

### Post by spgreenberg on 2007-03-27
Any ideas?

---

