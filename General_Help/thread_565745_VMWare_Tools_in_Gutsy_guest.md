---
title: "VMWare Tools in Gutsy guest?"
date: 2007-10-02
forum: General Help
---

### Post by riddlermarc on 2007-10-02
Hi,

No idea if this is the right place or not.. I have installed Gutsy under VMWare for testing but I can't seem to install VMWare Tools, is there something obvious I'm missing please?

I get the cdrom changed to the relevant iso but it's just a few odd files and I don't know what to do with them?!

Host server is 2003 Server R2 and VMWare Server 1.04, I'm trying to install the VMWare Tools stuff in my Gutsy guest :/

Thanks,
Marc

---

### Post by jocko on 2007-10-02
FIrst of all, you'll need to install two packages: build-essential and linux-headers-generic. FInd them in synaptic, or:
```
sudo apt-get install build-essential linux-headers-generic
```

The vmware-tools cd image contains a .tar.gz file. copy that file to your home folder.
Right-click it and select "unpack here". That will create a new folder ("vmware-tools-distrib") containing a bunch of files.
Open up a terminal and start the install by:
```
cd ~/vmware-tools-distrib
sudo ./vmware-install.pl
```

---

