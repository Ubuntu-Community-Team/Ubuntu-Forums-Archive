---
title: "input field box: arrows input weird numbers- help!"
date: 2014-07-18
forum: General Help
---

### Post by mrsfixit on 2014-07-18
This is affecting multiple applications- it's up to 6 at this writing. It is difficult to explain, I am having trouble describing it. It also seems to be getting worse. I'm getting desperate.

This is a fairly fresh install of Xubuntu 14.04 LTS, and this seems to  have happened since the last kernel upgrade. Things were working ok  before that. 

Affected so far: GIMP, Inkscape, XFCE Screenshot, GPRename, AviDemux, and PyRenamer.

Symptoms: if a program has an "input" field box for entering a number, and up/down arrow icons to increase/decrease that number, the arrow icons next to the input field box should increase/decrease in increments of "1". They do NOT.

When pressing the up/down arrow icon instead of increments of "1" as it should be- the programs display a bizarre range of numbers. Instead of going to "2, 3, 4, 5..." etc, it may go to 13,285 or something. It keeps changing. The numbers only stay the same with GPRename.

GPRename when using "insert/delete" goes to a specific number: when I press the up arrow it goes to "256" each and every time. If I press the down arrow it goes to "-256" every time. The other programs are hit and miss, and the numbers when the up/down arrows are pressed are literally all over the place

I CAN enter a number in the input box manually, but doing it this way in every program is a real pain.

This is so bad it is rendering this OS unusable. I had none of these problems with Xubuntu 12.04, 12.10, 13.04 and I used all the same programs.

Can anyone help???

---

### Post by mooreted on 2014-07-18
Well, that is a weird one. Did you check the keyboard settings for things like delay before a key press repeats? If you open something like a spreadsheet and move the cell reference around using the arrow keys, does it work normally?

---

### Post by mrsfixit on 2014-07-18
> **mooreted said:**
> Well, that is a weird one. Did you check the keyboard settings for things like delay before a key press repeats? If you open something like a spreadsheet and move the cell reference around using the arrow keys, does it work normally?

I don't really use spreadsheets, by cell "reference" do you mean selecting a cell? Seems to work ok in Gnumeric and Calc. I only tried it briefly though.

The keyboard repeat was on, set to the default settings- repeat delay 500, repeat speed 20. I disabled it, but it didn't make a difference, so I re-enabled it.

Thanks for your input. I'll try any and all suggestions at this point rather than having to face a complete install of some other distro to get around these bugs.

---

