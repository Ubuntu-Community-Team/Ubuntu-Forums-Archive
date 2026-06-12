---
title: "mythtv-setup on OpenBox and PIII 500MHz - no text in mythtv-setup"
date: 2007-02-12
forum: General Help
---

### Post by nmsmith on 2007-02-12
I've been following [_this_]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend") guide using oldish hardware:

Pentium III 500 MHz
384 Mb RAM
13 Gb disk

It's more of a proof of concept thing in order to justify spending money on a decent mythbox,  but every attempt has given problems. I tried following [_these_]("http://www.parker1.co.uk") instructions, but myth filled so much memory that it couldn't even get to a menu.

So now we're doing OpenBox. I tried this first on my more modern desktop, and it went okay. Move to the P.III and in mythtv-setup I get a light blue border round the screen, a dark blue centre of the screen, and a highlight showing me that a line of text is selected. But there's no text there.

Before I get this menu thing, the whole screen goes funky, and I get interference-stripes, bits of snow storms, and snippets of the GDM theme. Is this something to do with the QT widget engine? Whatever that is.

Here's the tail end of the console output:

```
  Minor opcode:  23
  Resource id:  0xc00660
X Error: RenderBadPicture (invalid Picture parameter) 177
  Major opcode:  151
  Minor opcode:  23
  Resource id:  0xc00660
X Error: RenderBadPicture (invalid Picture parameter) 177
  Major opcode:  151
  Minor opcode:  23
  Resource id:  0xc00660
X Error: RenderBadPicture (invalid Picture parameter) 177
  Major opcode:  151
  Minor opcode:  23
  Resource id:  0xc00660
X Error: RenderBadPicture (invalid Picture parameter) 177
  Major opcode:  151
  Minor opcode:  23
  Resource id:  0xc00660
X Error: RenderBadPicture (invalid Picture parameter) 177
  Major opcode:  151
  Minor opcode:  23
  Resource id:  0xc00660
X Error: RenderBadPicture (invalid Picture parameter) 177
  Major opcode:  151
  Minor opcode:  23
  Resource id:  0xc00660
X Error: RenderBadPicture (invalid Picture parameter) 177
  Major opcode:  151
  Minor opcode:  5
  Resource id:  0xc00660
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  65
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  65
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  65
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x0
X Error of failed request:  RenderBadPicture (invalid Picture parameter)
  Major opcode of failed request:  151 (RENDER)
  Minor opcode of failed request:  7 (RenderFreePicture)
  Picture id in failed request: 0xc00660
  Serial number of failed request:  4632
  Current serial number in output stream:  4650

```

The only difference between this and last time is that I have selected the nv driver in xorg. 

Thoughts?

---

### Post by nmsmith on 2007-02-12
I've checked, and not only is my display horribly sluggish with the vesa driver selected, I also get even worse results with mythtv-setup: a completely garbled screen.

---

### Post by reclusivemonkey on 2007-02-12
> **nmsmith said:**
> 
The only difference between this and last time is that I have selected the nv driver in xorg. 

Thoughts?

If you have a nvidia card, install nvidia-glx and use driver "nvidia" in xorg.conf.

---

### Post by nmsmith on 2007-02-12
> **reclusivemonkey said:**
> If you have a nvidia card, install nvidia-glx and use driver "nvidia" in xorg.conf.
I have a Leadtek Winfast 3D card, something like S3250 I think, but I'm away from home for a couple of days so I can't check.

Thanks though.

---

