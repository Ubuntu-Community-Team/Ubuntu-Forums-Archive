---
title: "geogebra on 14.04"
date: 2015-06-17
forum: General Help
---

### Post by elim-qiu on 2015-06-17
I have geogebra 4.4.45.0 (java 1.7.0_45-64bit, 910MB, CAS Initializing) 17 Septermber 2014 on my ubuntu 14.04 system.

Today I got update prompt when opening geogebra. I donwloaded GeoGebra-Linux-Protable-5.0.127.0. Trying to use Ubuntu Software Center to uninstall the current version but found it doesn't aware  of my geogebra 4.4.45 and prompts for a installation. And the downloaded pkg is a portable one which, to my understanding, does not require installation.

So what should I do? Manually uninstall the current version (but how)? Install new version via software center or just using the portable one without installing it?

Thanks for your advise.

---

### Post by CantankRus on 2015-06-18
How did you install geogebra in the first place?
You can:
[LIST=1]
[*]download in a tar.bz2 file (includes java)...can be run from folder once extracted....**geogebra44** or the latest **geogebra5** with java (portable linux)
[*]install an older version using the software centre...**geogebra** (requires java to be installed)....is installed in your applications.
[*]install latest version using a deb file from [**_[COLOR="#B22222"]geogebra.org[/COLOR]_**]("http://wiki.geogebra.org/en/Reference:GeoGebra_Installation")...**geogebra5**....is installed in your applications.
[/LIST]

Using the deb file option installs geogebra5 and also adds the official GeoGebra repository 
to your sources and will update geogebra5 with your normal updates.

Software centre search isn't that good.
eg I installed geogebra5 using the deb file and didn't show up till I added the 5. 
When searching in software centre try using the term **geogebra44** or **geogebra5**
I prefer using synaptic.
```
sudo apt-get install synaptic
```

---

### Post by elim-qiu on 2015-06-18
Thanks a lot cantankrus[COLOR=#000000] for the help.
[/COLOR]
I found that my old geogebra was installed via [COLOR=#000000][FONT=Ubuntu Mono]synaptic, so uninstalled it and installed geogebra 5 by synaptic. It turns out the newer version runs very slow. So I uninstalled it and downloaded the newest geogebra portable for linux from geogebra.org.

I was able to create an launcher buttom for geogebra portable, but don't know how to add .ggb file association to the system. Any ideas?[/FONT][/COLOR]

---

### Post by CantankRus on 2015-06-19
The easiest way to fix file associations is to install the default geogebra via synaptic as this adds icons and file associations.
What you can then do is edit it's .desktop file to execute the portable version.
**.desktop** files placed in **~/.local/share/applications** will override .desktop files in **/usr/share/applications**

Firstly you may want to disable the geogebra ppa if it was added...
```
software-properties-gtk --open-tab=1
```
[ATTACH=CONFIG]262698[/ATTACH]

Install the default geogebra via terminal...
```
sudo apt-get update && sudo apt-get install geogebra
```

After installation, copy the geogebra.desktop file to ~/.local/share/applications....
```
cp /usr/share/applications/geogebra.desktop ~/.local/share/applications
```

Edit the new file to execute your portable version.
```
gedit ~/.local/share/applications/geogebra.desktop
```
eg I edited the "Exec" line  to point to my downloaded portable version execute script.
from...
```
Exec=[COLOR="#0000CD"]geogebra[/COLOR] %F
```
to ([COLOR="#0000CD"]use your full path[/COLOR])
```
Exec=[COLOR="#0000CD"]/home/glen/Downloads/GeoGebra-Linux-Portable-5.0.127.0/geogebra-portable[/COLOR] %F
```

Leave geogebra installed in synaptic to maintain icons and file associations.
You'll be running the portable version from your folder when you search and run "geogebra" from the dash.
Drag the dash icon to the launcher.
May need to log out for associations to work.
[ATTACH=CONFIG]262697[/ATTACH]


PS: the slowness you observed may be due to the system java you have installed.
The deb or synaptic install uses your installed java.
```
java -version
```

The portable version comes bundled with java.
If you're happy using the portable version don't worry about your system java version.

Here's a link to install oracle's java8 if you want ...
[**_[COLOR="#B22222"]Install oracle-java-8 in ubuntu[/COLOR]_**]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")

---

### Post by elim-qiu on 2015-06-22
Thanks a lot CantankRus! Your advise was Very helpful, all the issues I got were resolved!

---

