---
title: "Making/Unmaking a Selection"
date: 2007-05-15
forum: General Help
---

### Post by A*p on 2007-05-15
O.K first off, apologies if this is me just being a total tool, but how do I de-select a single item?   

For example...

Say you have a bunch of files and you want to delete all but one in nautilus, I would press Ctrl + A to select all files,then hold Ctrl and select the file I wanted to keep to de-select it and then press delete... Simple and quick


The same goes with spreadsheets rows and cell's which is what I am trying to do at the moment.  Now I have been using Linux as my desktop for years now and know that I do this I am sure, :confused: but I am on my laptop atm and not able to check this against my other machines.

The Ctrl key works fine for everything else, am I going mad? is my laptop trying to make me go mad? and am I doomed to individually delete hundreds of rows out of a spreadsheet one at a time? or will I wakeup from this nightmare when I hit the submit button?

Please Help:-({|=

---

### Post by celticbhoy on 2007-05-15
hold down the CTRL key and press the left mouse button when over whatever you want to de-select.

---

### Post by celticbhoy on 2007-05-15
By the way, I take it you are using OpenOffice

---

### Post by A*p on 2007-05-15
Yep, that is what I am doing, holding the Ctrl key and selecting/deselecting with the mouse....or rather trying too. It does the same in Openoffice and Gnumeric

---

### Post by celticbhoy on 2007-05-15
I know this might sound daft but you are clicking on the number bar for the row/colum you want ??

its just that it works fine for me so it is meant to do it.

---

### Post by celticbhoy on 2007-05-15
are you saying that this function does not work in any app?
if so the problem is probably to do with the hardware setup - especially if it is a non standard keyboard on the laptop.

---

### Post by A*p on 2007-05-15
Yeah not any, I noticed it first the other week, though the Ctrl key does work.  I have had Linux on this Laptop since dapper and I would have noticed it before now, I upgraded to feisty then went back to edgy when feisty did not work out, so I am assuming that it started when I did that fresh install, although I noticed it the other week, it is not till now that it has become a real pain.  Must be a setting somewhere but everywhere I have looked seems fine.

---

### Post by celticbhoy on 2007-05-15
Might be possible to fix with

sudo dpkg-reconfigure xserver-xorg

and then seeing what you get in keyboard section ???

---

### Post by A*p on 2007-05-20
sudo dpkg-reconfigure xserver-xorg   worked, though it did screw up my video settings, though  it was a painless process to get it back in order.

Thanks for the help :)

---

