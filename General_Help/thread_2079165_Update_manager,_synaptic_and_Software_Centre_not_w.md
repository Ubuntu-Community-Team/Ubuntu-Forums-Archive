---
title: "Update manager, synaptic and Software Centre not working"
date: 2012-11-01
forum: General Help
---

### Post by headflux on 2012-11-01
Hi,

I can no longer open Update Manager, Synaptic Package Manager or the Software Centre.  I get the following error...

'E:Encountered a section with no Package: header, E : Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

I'm running 12.04.

Can anyone help please?

Thanks

---

### Post by dannyboy79 on 2012-11-01
first try
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

if that doesn't fix it, try this

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by headflux on 2012-11-01
Hi DannyBoy79,

Thank you... your second suggestion worked perfectly!

Really appreciate your help.

---

