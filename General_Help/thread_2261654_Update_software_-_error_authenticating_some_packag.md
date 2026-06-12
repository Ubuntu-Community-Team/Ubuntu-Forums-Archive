---
title: "Update software - error authenticating some packages"
date: 2015-01-20
forum: General Help
---

### Post by TheRealJimShady on 2015-01-20
Hi there,

When I run update manager, I am given the below message:
[B]
Not all updates can be installed
Run a partial upgrade to install as many updates as possible.[/B]

So I click partial update button, enter my password, and then after a second or two I am given the message:

**Error authenticating some packages. Continue?**

It then lists packages it is having problems with. They are:

[B]libqgis-analysis2.6.1
libqgis-core2.6.1
libqgis-customwidgets
libqgis-gui2.6.1
libqgis-networkanalysis2.6.1
libqgisgrass2.6.1
libqgispython2.6.1
python-qgis
python-qgis-common
qgis
qgis-common
qgis-plugin-globe
qgis-plugin-globe-common
qgis-plugin-grass
qgis-plugin-grass-common
qgis-providers
qgis-providers-common[/B]

I am not sure how to proceed now. I am just given an option to 'Close' i.e. quit the upgrade process.

My version of Ubuntu is shown below:

james@AnalysisUbuntuDesk01:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

I'd appreciate some help and guidance.

Thanks

James

---

### Post by Holger_Gehrke on 2015-01-20
Have you tried to load quantum gis from a ppa (personal package archive) ? It looks like you have set this up by adding the ppa to the sources, but forgot to add the key for cryptographic verification of the packages. Or you have set it up and the key has changed since you did.

---

### Post by TheRealJimShady on 2015-03-11
Hi [COLOR=#000000]Holger,

That sounds entirely possible. Though I'm not sure how to fix it. The edits I've made to my sources list is here:

[/COLOR][COLOR=#000000]deb [http://qgis.org/debain](http://qgis.org/debain) precise main
deb-src [http://qgis/org/debian](http://qgis/org/debian) precise main

Should I be adding something else here to do with keys please?

Thanks

James


[/COLOR]

---

