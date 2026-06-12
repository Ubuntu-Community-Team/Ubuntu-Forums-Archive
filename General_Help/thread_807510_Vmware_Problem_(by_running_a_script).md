---
title: "Vmware Problem (by running a script)"
date: 2008-05-25
forum: General Help
---

### Post by reyhan on 2008-05-25
Hello i just read this tutorial [http://ubuntuforums.org/showthread.php?t=788169]("http://ubuntuforums.org/showthread.php?t=788169")

and i got this problem

> root@reyhan-desktop:/home/reyhan# ./install_vmware.sh
 -- Updating Ubuntu, continuing...
 -- Upgrading Ubuntu, continuing...
 -- Installing essential libraries for 32-bit architecture, continuing...
 -- Checking for essential GUI libraries, continuing...
 -- Essential GUI libraries already installed, continuing...
 -- VMware already present. Skipping download, continuing...
 -- Extracting VMware server, continuing...

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
 !! Could not extract VMware-server-1.0.5-80187.tar.gz. Does it exist or is it corrupt?, exiting...
 -- Removing downloaded and extracted files, continuing...


---

### Post by pointone on 2008-05-26
Try removing VMware-server-1.0.5-80187.tar.gz and let the script download again. Possibly could be a corrupt download.

---

