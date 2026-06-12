---
title: "Dapper packages in edgy"
date: 2006-10-28
forum: General Help
---

### Post by gorded on 2006-10-28
Is it possible to download a .deb from the dapper universe and install it on a edgy installation.

---

### Post by PriceChild on 2006-10-28
packages.ubuntu.com

Its not reccomended and may break your system :)

---

### Post by ~LoKe on 2006-10-28
Maybe I'm mistaken, but isn't that what the backports are for?

---

### Post by PriceChild on 2006-10-28
Backports are the other way around...

Its where new packages with exciting features may come from edgy to dapper if it won't cause breakage.

---

### Post by gorded on 2006-10-28
Well, right now this seems like my only hope to get banshee runing.

---

### Post by beerfan on 2006-10-28
> **PriceChild said:**
> packages.ubuntu.com

Its not reccomended and may break your system :)

If gdebi reports that all dependencies are met, then what is the risk?

---

### Post by PriceChild on 2006-10-28
> **gorded said:**
> Well, right now this seems like my only hope to get banshee runing.Whoa whoa whoa....

Explain what error you're getting running banshee in edgy.
> **beerfan said:**
> If gdebi reports that all dependencies are met, then what is the risk?Because the packages are built for dapper... not edgy... they're not meant to run in edgy and so may have odd effects.

---

### Post by tool462rules on 2006-10-28
> **gorded said:**
> Well, right now this seems like my only hope to get banshee runing.
Banshee 11.1, while not the latest version, is the version available for Edgy, I'm running it right now with very little problems. Ok well not really very little problems, but if you check my previous threads you'll see how I fixed some problems with it on Edgy.

---

### Post by gorded on 2006-10-28
Well my problem with Banshee is a bit different, when ever i start it up, it hangs on Initailizing audio

---

### Post by beerfan on 2006-10-28
> **PriceChild said:**
> Because the packages are built for dapper... not edgy... they're not meant to run in edgy and so may have odd effects.

I'm far from an expert (which is why I'm asking) but aren't packages built against other packages (not distro releases)? If the package depends on xyz.lib v1.0+ and Edgy has xyzlib v1.5 then we should be fine no? This of course assumes that the package creator accurately set the dependency to the correct range of versions (e.g., if the api in xyz.lib changed in v1.2).

I'm not trying to make things unduly complicated but I just want to be sure I understand.

---

### Post by gorded on 2006-10-28
> **PriceChild said:**
> Whoa whoa whoa....

Explain what error you're getting running banshee in edgy.


this is the problem i am having when i start banshee. I used the following command to install banshee and its plugins.

```
sudo aptitude install banshee banshee-official-plugins
```

i asked to dowload these other packages

```
banshee banshee-official-plugins binfmt-support cli-common 
  gnome-volume-manager gstreamer0.10-gnomevfs gstreamer0.10-plugins-ugly 
  gthumb liba52-0.7.4 libdvdread3 libgconf2.0-cil libglade2.0-cil 
  libglib2.0-cil libgnome2.0-cil libgphoto2-2 libgphoto2-port0 
  libgtk2.0-cil libgtkhtml3.8-15 libid3tag0 libipoddevice0 libmad0 
  libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil 
  libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil 
  libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil 
  libmono-system-data2.0-cil libmono-system-web1.0-cil 
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil 
  libmono0 libmono1.0-cil libmono2.0-cil libmpeg2-4 libmusicbrainz4c2a 
  libnjb5 libsgutils1 libsidplay1 libsqlite3-0 mono-common mono-gac 
  mono-jit mono-runtime sg3-utils totem totem-gstreamer totem-mozilla 
```

I said yes, and it went about and did its thing, then i come back and run

```
banshee
```

and the splash screen starts up all nice and the half way through at initializing audio it stops, the massage i got in the terminal is as follows

```
Warning: [28/10/2006 2:28:12 PM] (Cannot connect to NetworkManager) - An available working network connection will be assumed
Creating track table
Creating playlists table
Creating playlistentries table

```

Thanks

Edit: here is a screen shot  

[http://smg.photobucket.com/albums/v244/gorded/?action=view&current=Screenshot.png&refPage=&imgAnch=imgAnch1](http://smg.photobucket.com/albums/v244/gorded/?action=view&current=Screenshot.png&refPage=&imgAnch=imgAnch1)

---

### Post by LxP on 2006-11-12
> **beerfan said:**
> I'm far from an expert (which is why I'm asking) but aren't packages built against other packages (not distro releases)? If the package depends on xyz.lib v1.0+ and Edgy has xyzlib v1.5 then we should be fine no? This of course assumes that the package creator accurately set the dependency to the correct range of versions (e.g., if the api in xyz.lib changed in v1.2).

I'm not trying to make things unduly complicated but I just want to be sure I understand.

I would also be interested in knowing the answer to this.

---

### Post by PriceChild on 2006-11-12
> **beerfan said:**
> I'm far from an expert (which is why I'm asking) but aren't packages built against other packages (not distro releases)? If the package depends on xyz.lib v1.0+ and Edgy has xyzlib v1.5 then we should be fine no? This of course assumes that the package creator accurately set the dependency to the correct range of versions (e.g., if the api in xyz.lib changed in v1.2).

I'm not trying to make things unduly complicated but I just want to be sure I understand.But the way the packages are built is different in each distro also. Using different versions of building tools with different quirks.

9 times out of 10 you won't notice anything bad... but do you want that 1 to be you?

---

### Post by loell on 2006-11-12
i think if dapper packages work in edgy or the other way around, then good, install it.
if something is not right,then the user can always uninstall it.

---

