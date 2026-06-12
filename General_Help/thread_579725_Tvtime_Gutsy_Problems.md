---
title: "Tvtime Gutsy Problems"
date: 2007-10-18
forum: General Help
---

### Post by Merry on 2007-10-18
I upgraded to Gutsy today and for some reason TVtime, which was previously working in Feisty has stopped doing so. I thought it could be a problem with compiz however turning this off has no effect, nor does uninstalling and re-installing tvtime.

Tvtime starts briefly then closes by itself within a second or so. I'm using the restricted Nvidia driver if thats helpful.

*edit* I would like to add that this problem is occurring on my laptop too, which runs entirely different hardware (it has an Ati x700gpu for a start) and has compiz turned off

---

### Post by jchollet on 2007-10-21
I've been trying to get my Pinnacle Studio PCTV Pro card to work under Gutsy with no luck so far. The same thing happens to me when I try to open tvtime. It closes in less than a second. I've been trying to get xawtv working but it only detects my webcam. Does anybody have any suggestions as to what I should try to do?

Thank you very much in advance.

Edit: I tried reinstalling tvtime and it still closes in less than a second. I am not using any restricted drivers as far as I know.

---

### Post by DagMan on 2007-10-21
Maybe kaffeine supports this in a point and click interface.  It does for dvb but I don't know about analoge.

---

### Post by 8 Ball on 2007-10-21
I also have the exact same problem as Merry. Ati restricted driver for X550.  Starting from terminal gives   :~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/checkerspa/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

Any help greatly appreciated!

---

### Post by 8 Ball on 2007-10-21
Problem fixed here.  See this link [http://www.ubuntuforums.org/showthread.php?t=191763&highlight=tvtime](http://www.ubuntuforums.org/showthread.php?t=191763&highlight=tvtime)

---

### Post by Merry on 2007-10-23
> **8 Ball said:**
> Problem fixed here.  See this link [http://www.ubuntuforums.org/showthread.php?t=191763&highlight=tvtime](http://www.ubuntuforums.org/showthread.php?t=191763&highlight=tvtime)


that doesnt really help if you have an NVIDIA graphics card. Thanks for your help though.

---

### Post by monomeric on 2007-11-08
I had the same problem after recently upgrading to 7.10. It seems to be related to some squirk in the settings defined in ~/.tvtime/tvtime.xml. In case you do not use XMLTV, you could simply try to delete this settings file (make a backup first):
```

cp ~/.tvtime/tvtime.xml ~/.tvtime/tvtime.xml.bak
rm ~/.tvtime/tvtime.xml

```
Upon the next run, tvtime will recreate this file with standard values. In case you make use of XMLTV, it might be a good idea to keep all entries concerning the program informations. Thus edit the settings file and remove all options which do not concern XMLTV, e.g.
```

nano ~/.tvtime/tvtime.xml

```
to make the file resemble this:
[HTML]
<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="XMLTVFile" value="/home/monomeric/.xmltv/tv_grab_se_swedb.xml"/>
  <option name="XMLTVLanguage" value="none"/>
</tvtime>
[/HTML]

Does it help?

---

