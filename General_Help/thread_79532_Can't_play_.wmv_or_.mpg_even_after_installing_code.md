---
title: "Can't play .wmv or .mpg even after installing codecs"
date: 2005-10-20
forum: General Help
---

### Post by Jiganto on 2005-10-20
I just just installed ubuntu on my Inspiron 8600 laptop
the specs are
 
1.4ghz centrin
Radeon mobility 9600pro turbo
768mb ram

anyway 

I've installed the multimedia codecs using the guide in unofficial Ubuntu5.04 guide I also used Easy Ubuntu to do the say thing. mp3 audio files play fine, however with .wmv there is only sound no video, and mpg I was only able to play one file once and the video and audio were real choppy. I also tried VLC and  it's exactly the same problem as in Totem.

I've searched the forums and I've seen a couple of posts with similar issues but I haven't found a solution to the problem.

I also installed the ATI drivers from Easy Ubuntu, I'm just wondering if this is commong at all.

---

### Post by Dolphin on 2005-10-20
```
sudo gedit /etc/X11/xorg.conf
```

Look under Section "Device" and make sure it has the following entry:

```
Option 		"VideoOverlay"		"on"
```

---

### Post by ymmotrojam on 2005-10-20
install vlc media player ;) it can do anything...

EDIT: I was being weird and only read the first part of his post... oopsy... disregard

---

### Post by Malphas on 2005-10-20
[QUOTE=ymmotrojam]install vlc media player ;) it can do anything...[/QUOTE]
What's the matter with you?  Try reading his post.

---

### Post by Jiganto on 2005-10-20
[QUOTE=Dolphin]```
sudo gedit /etc/X11/xorg.conf
```

Look under Section "Device" and make sure it has the following entry:

```
Option 		"VideoOverlay"		"on"
```[/QUOTE]

this is what appears under the "Device" section

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
```

---

### Post by Dolphin on 2005-10-20
Add that entry then


PS: And Driver should read "fglrx" if you installed your ATI drivers correctly.

---

### Post by objorkum on 2005-10-20
You can see if it is a overlay problem, by typing "xvinfo" in a terminal. If you get "no adaptors present", or something like that, it's a overlay problem.

ATI-drivers from Easy Ubuntu?

Why not the "xorg-driver-fglrx"-package from Synaptic?

Then just create your xorg.conf [here]("http://www.objorkum.com/scripts/fglrxconfig/"), and voila.

---

### Post by Jiganto on 2005-10-20
[QUOTE=objorkum]You can see if it is a overlay problem, by typing "xvinfo" in a terminal. If you get "no adaptors present", or something like that, it's a overlay problem.

ATI-drivers from Easy Ubuntu?

Why not the "xorg-driver-fglrx"-package from Synaptic?

Then just create your xorg.conf [here]("http://www.objorkum.com/scripts/fglrxconfig/"), and voila.[/QUOTE]

xorg-driver-fglrx were the drivers installed by Easy Ubuntu, just in case I reinstalled them through Synaptic too. I used that link to create another xorg.conf file. When i type xvinfo into terminal it just outputs a whole bunch of information, no errors.

I just checked, .mpg play fine now but .wmv still have no video just audio

---

### Post by Jiganto on 2005-10-20
Nothing? .wvm with no video?

---

