---
title: "New file association with an unlisted program"
date: 2013-02-06
forum: General Help
---

### Post by Heinrich_Evers on 2013-02-06
Hi there,

So I've migrated back to Ubuntu since I recently built a new desktop.
The older machine had compatibility issues with 12.04 and 12.10 so I went to pure debian squeeze for about a year or so.

Okay, so here's my issue.

I'm a Cisco Networking Academy student and we use a program called Packet Tracer for creating network simulations and whatnot.

Our project files are *.pkt extension based files.

The problem is that when I us "open with" or "properties / Open  with" packet tracer isn't listed as an available program to associate the file extension with.

With debian I had field at the bottom where I could just enter in the terminal command of the program and there was a browse for program feature in this open with section.

Is there a way I can modify my ubuntu so that it will have these same two features?

And yes I check Ubuntu tweak and under unlisted extensions it's still not listed.

I have Packet Tracer installed, and I can use it and open my pkt files with it but I'd like to be able to have the ability to execute them from their respective folders like I can with my other regular files.

Any suggestions?

---

### Post by dino99 on 2013-02-06
there is no easy way sadly. Open a terminal to run the command with the full path; then hopefully the association might be listed.

---

### Post by stinkeye on 2013-02-06
Try the answer in this thread.
[**_[COLOR="DarkRed"]How to open a file of an unknown type with a specific application?[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2109395")

---

### Post by Morbius1 on 2013-02-06
> With debian I had field at the bottom where I could just enter in the  terminal command of the program and there was a browse for program  feature in this open with section.Gnome took that ability away since it was declared a feature and therefore a bug that must be removed. Install the file manager from XFCE that still has this ... um ... bug:
```
sudo apt-get install thunar
```Then open thunar, right click a *.pkt file > Open with other application > Use a Custom Command, and you will get a dialog box that looks something like the attachment below. 

Once you set it in Thunar it will set the association everywhere else.

---

