---
title: "Assitance with modelines xrandr and GUI display setup."
date: 2020-10-15
forum: General Help
---

### Post by adrian-h on 2020-10-15
Introduction:-  I have been working with old valved/tube equipment recently including a TV from 1954 which was a 405 line black and white standard, and wanted to find a way to drive a modulator to generate pictures for this vintage tech off the PC.

Partial solution :-  I found what was called mode lines for Windows and that it was also available under xrandr in Linux, so people have been using configuration lines in shell to set a display mode and then select it from display settings, at least in 'Mint'.

So this is taken from several posts I have read on vintage equipment forums.
xrandr
would tell me initially what modes were supported such as :-

```
~$ xrandr
DVI-0 connected primary 1600x900+0+15 (normal left inverted right x axis y axis) 434mm x 236mm
   1600x900      60.00*+
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
DVI-1 connected 1024x768+1600+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94
```


Then using the following:-

```
~$ xrandr --newmode "405" 8.10 664 680 752 800 377 378 385 405 -hsync -vsync interlace
~$ xrandr --addmode DVI-1 405
```

It would add the mode to DVI-1
xrand would now report this extra mode

```
DVI-1 connected 1024x768+1600+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
   405           50.00
```

But my issue is that the normal display settings under the gui would still never recognise the mode.

I can force the mode to be selected for DVI-1 by using.

```
xrandr --output DVI-1 --mode 405
```
in shell, but any venture into display settings after this point will revert the display back to normal.  Is there a way to make the standard display settings package recognise the new mode so that it can be set and stay permanently?

I have put 
```
xrandr --newmode "405" 8.10 664 680 752 800 377 378 385 405 -hsync -vsync interlace
xrandr --addmode DVI-1 405
```
into the hidden file .profile, but it will not force the selection if the last line is also in there.

For interest the DVI-1 video connector is wired through some resistors and capacitor to provide composite video out from the PC in 405 line format.

Adrian

---

