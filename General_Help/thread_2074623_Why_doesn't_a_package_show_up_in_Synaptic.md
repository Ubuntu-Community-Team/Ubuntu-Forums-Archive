---
title: "Why doesn't a package show up in Synaptic?"
date: 2012-10-22
forum: General Help
---

### Post by oxf on 2012-10-22
I'm trying to install QGIS. (but this could apply to other applications I think)

On my other PC which has Maverick running on it Synaptic shows QGIS and all associated packages.

ON this one which is running Precise QGIS does not list. I can find it under apt-get in the terminal but not on Synaptic, Why??
I would prefer to install it via Synaptic so I can use the "force version" option.

I have the repositories and key updated so its not that.

Thanks 
Veronica

---

### Post by Hairy_Palms on 2012-10-22
very strange, looking at [http://packages.ubuntu.com/search?keywords=qgis](http://packages.ubuntu.com/search?keywords=qgis)
it seems qgis isnt there in precise at all, but its there in quantal and oneiric
id guess there was an oversite in precise, qgis do maintain there own PPA for precise though it seems, if you add the repository line
> deb [http://qgis.org/debian](http://qgis.org/debian) precise main

---

### Post by 2F4U on 2012-10-22
Seems as if it has been moved to a PPA:

[https://wiki.ubuntu.com/UbuntuGIS](https://wiki.ubuntu.com/UbuntuGIS)

---

### Post by buckyaustin on 2012-10-22
You will have to add the repo. This is done in terminal by using "sudo add-apt-repository ppa:user/ppa-name" , instead of ppa:user/ppa-name you will have to use QGIS ppa. Then run "sudo apt-get update".

---

