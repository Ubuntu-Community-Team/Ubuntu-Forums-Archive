---
title: "Uninstalling Software and Its Addons"
date: 2012-11-29
forum: General Help
---

### Post by jakfish on 2012-11-29
Lubuntu 12.04 installed on Lenovo S10-3t

Happy with my setup, I installed remastersys and made a custom iso.

The rub is, when I installed remastersys through Synaptic Package Manager, Synaptic said I needed a lot of other libs and software (KDE stuff, for example) to make the remastersys installation work.

It's about 300mbs and now that the custom iso is done, I'd like to get rid of these 300mbs.  But in Synaptic, when I try to uninstall remastersys, Synaptic says it'll only uninstall remastersys and not all the other stuff.

Is there a solution to this?  For example, can Synaptic uninstall anything installed on a certain date?

Any help would be much apppreciated,
Jake

---

### Post by dino99 on 2012-11-29
synaptic will find the orphan packages after the main soft removed; but you also can use deborphan to do more cleanings.

but remember the usual way:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

thats it :P

---

### Post by jakfish on 2012-11-29
Thank you for your quick reply.  Those commands will only do a partial uninstall, perhaps b/c remastersys demanded so many extra packages.

Per these instructions,

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-completely-uninstallremove-a-packagesoftwareprogram](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-completely-uninstallremove-a-packagesoftwareprogram)

I ended up opening /var/log/apt/history.log, looking for the packages installed at the time of remastersys's installation, and then:

sudo apt-get remove --auto-remove <file names>

Tedious, but it was the only thing I've found so far that worked.

Jake

---

