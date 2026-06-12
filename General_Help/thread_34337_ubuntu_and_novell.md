---
title: "ubuntu and novell???"
date: 2005-05-14
forum: General Help
---

### Post by skuzzy on 2005-05-14
Hello,
As you can see i have just discovered ubuntu - i have tried all the other distros but thi s one is the best :D:D

At my school we use laptops and novell to log into the network - is there any clients that will allow me to login to the novell server  :neutral: 

Thanks
Scott

---

### Post by Kurai on 2005-05-14
Real VNC works for me form linux to novell or windows or apple or ...
you get the point
Edit:  ultra VNC works too real is easier but get the free version it works just fine

---

### Post by brannolte on 2005-05-14
[QUOTE=skuzzy]Hello,
As you can see i have just discovered ubuntu - i have tried all the other distros but thi s one is the best :D:D

At my school we use laptops and novell to log into the network - is there any clients that will allow me to login to the novell server  :neutral: 

Thanks
Scott[/QUOTE]


Hi Scott

I have used two different ways: 
- there ist a "novel client" (with one l) on the coolsolutions side from novell 
- or you can use the ncpfs - tools 



```

#!/bin/sh
NWCLIENT_PREFERRED_TREE=##place your tree here##
NWCLIENT_DEFAULT_NAME_CONTEXT=home
NWCLIENT_DEFAULT_USER=$USER

export NWCLIENT_PREFERRED_TREE
export NWCLIENT_DEFAULT_NAME_CONTEXT
export NWCLIENT_DEFAULT_USER


ncplogin -S ##SERVERNAME## -A ##SERVERNAME## -P ##PASSWORD## -E -l
ncpmap -A ##SERVER-NAME## -X  ##SERVER-KONTEXT## -V ##SERVER_VOLUME## -l
ncpmap -A ##SERVERNAME## -X ##SERVER-KONTEXT## -V ##SERVER-VOLUME -R ##PATH_ON_THE_SERVER -A ##SERVER-NAME  -f 0664 -d 0775 ##PATH-WHERE-TO-MONT-ON-LINUX-SIDE##

``` 

Check this sides for more Information
[one](http://now-well.sourceforge.net/linux/now-well/) 
[two](http://prope.insa-lyon.fr/~ppollet/netware/linux.ssi)

---

