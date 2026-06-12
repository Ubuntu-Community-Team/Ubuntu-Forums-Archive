---
title: "Can't set DPI to 96"
date: 2007-08-08
forum: General Help
---

### Post by 7sudden on 2007-08-08
Just installed Feisty on an old (ancient) Dell desktop. I believe that the video card is a ATI Rage 128, and my monitor is a 19" (1280x1024)

I'm trying to set it to 96dpi. I've edited xorg.conf to reflect 
**DisplaySize 338 270**  -but that didn't work. I then tried **Option "DPI" "96 x 96"** and still no result.

Does anyone have any other ideas?

---

### Post by ThrobbingBrain66 on 2007-08-08
What happens when you set the font to 96dpi in System>Preferences>Font>Details?

---

### Post by 7sudden on 2007-08-08
> **ThrobbingBrain66 said:**
> What happens when you set the font to 96dpi in System>Preferences>Font>Details?

Absolutely no difference. Still reports 85x86 dots per inch

---

### Post by RedSquirrel on 2007-08-08
The DisplaySize setting in xorg.conf doesn't work with the version of Xorg in feisty. It's a bug.

You can safely use the settings in the menu pointed to by ThrobbingBrain66. That will apply to all of your GTK 2.0 applications.

If you absolutely must see 96x96 when you run 'xdpyinfo | grep resolution', then you can add 

```
        Option          "NoDDC"
```to the "Device" section.

I think you are better off just using the settings from the menu mentioned above.


[COLOR=Red]EDIT[/COLOR]

I am using that "NoDDC" setting at the moment, but I also use a Modeline and specify the correct HorizSync and VertRefresh ranges for my monitor. You might need those if you want to use the NoDDC setting.

---

### Post by ThrobbingBrain66 on 2007-08-08
> **7sudden said:**
> Absolutely no difference. Still reports 85x86 dots per inch

Did you restart the X server?

---

### Post by 7sudden on 2007-08-08
> **RedSquirrel said:**
> The DisplaySize setting in xorg.conf doesn't work with the version of Xorg in feisty. It's a bug.

You can safely use the settings in the menu pointed to by ThrobbingBrain66. That will apply to all of your GTK 2.0 applications.

If you absolutely must see 96x96 when you run 'xdpyinfo | grep resolution', then you can add 

```
        Option          "NoDDC"
```to the "Device" section.

I think you are better off just using the settings from the menu mentioned above.


[COLOR=Red]EDIT[/COLOR]

I am using that "NoDDC" setting at the moment, but I also use a Modeline and specify the correct HorizSync and VertRefresh ranges for my monitor. You might need those if you want to use the NoDDC setting.


Thanks for your reply.

I had initially checked my font setting in the menu, and it was (and remains) set to 96, however this does not have an effect on what is displayed when running  'xdpyinfo | grep resolution'

My xorg.conf looks like this
```
Section "Device"
	Identifier	"ATI Technologies Inc Rage 128 Pro Ultra TF"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Option          "NoDDC"
EndSection

Section "Monitor"
	Identifier	"90GX2"
        VendorName   "Monitor Vendor"
        ModelName    "NEC 90GX2"
	HorizSync    31.5 - 67.0
	VertRefresh  50.0 - 75.0
        Option      "dpms"
	Option "DPI" "96 x 96"
EndSection
```

The purpose of this effort is to obtain cleartype-like fonts, as demonstrated here
[http://ubuntuforums.org/showthread.php?t=20976&highlight=firefox+fonts]("http://ubuntuforums.org/showthread.php?t=20976&highlight=firefox+fonts")

---

### Post by RedSquirrel on 2007-08-08
I'm pretty sure that 

```
Option "DPI" "96 x 96" 
```only works with nvidia cards, not ATI.

The font settings in the menu and the xdpyinfo are two different things, so they don't have to match. If you run 

```
xrdb -query  | grep dpi
```I would imagine it will report 96. 

It really shouldn't be necessary to get xdpyinfo to say 96x96, but like I said, if you really want that, you'd have to use a combination of "NoDDC" and your DisplaySize line (with correct values).

EDIT

I just reread my earlier post and it seems I implied that DisplaySize doesn't work AT ALL. That's not what I meant. I meant that it doesn't work without the "NoDDC" option. The bug is that DDC overwrites whatever you specify in DisplaySize, so that's why you have to say "NoDDC".

By the way, your DisplaySize values for 1280x1024 and 96 DPI are just fine. :)

---

