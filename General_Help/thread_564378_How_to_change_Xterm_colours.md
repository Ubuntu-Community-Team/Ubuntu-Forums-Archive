---
title: "How to change Xterm colours"
date: 2007-10-01
forum: General Help
---

### Post by satimis on 2007-10-01
Hi folks,


Ubuntu 7.04 server amd64


I want to change the colours on Xterm but I can't find ".Xdefaults" nor ".Xresources"

$ sudo find / -name .Xdefaults/.Xresources/.Xdefault/.Xresource
all w/o printout


Pls advise which file contains the relevant information?  TIA


Whether to change colour: ```

XTerm*background:   white
XTerm*foreground:   black
XTerm*highlightColor:  yellow

```
will display "white background", "black characters" and "yellow on highlight"?

Then run

$ sudor  xrdb ~/.Xresources (.file)
???

Thanks


Edit:
xtermcontrol 2.9
[http://linux.softpedia.com/get/Terminals/xtermcontrol-9484.shtml](http://linux.softpedia.com/get/Terminals/xtermcontrol-9484.shtml)

Does this package work for my purpose ?


B.R.
satimis

---

### Post by kerry_s on 2007-10-01
you create the .Xdefaults file.

here's what mine looks like->
UXTerm*reverseVideo: true <will make black on white

```

! you should run ` xrdb -merge /path/to/.Xdefaults '

xpdf*initialZoom: width
xpdf*geometry: 800x600

xedit*geometry: 800x600
xedit*enableBackups: off
xedit*fontSet: -adobe-helvetica-*-r-normal--*-120-*-*-*-*-iso8859-* 

.xmessage.form.okay.shapeStyle: rectangle
.xmessage.form.okay.background: gray
.xmessage.form.okay.foreground: black
xmessage*message*background: white
xmessage*defaultButton: okay
Xmessage.form.message.Scroll:  WhenNeeded

xcalc*geometry: 200x275                                                         
xcalc.ti.bevel.background: #111111                                              
xcalc.ti.bevel.screen.background: Green                                         
xcalc.ti.bevel.screen.DEG.background: Green                                     
xcalc.ti.bevel.screen.DEG.foreground: Black                                     
xcalc.ti.bevel.screen.GRAD.background: Green                                    
xcalc.ti.bevel.screen.GRAD.foreground: Black                                    
xcalc.ti.bevel.screen.RAD.background: Green                                     
xcalc.ti.bevel.screen.RAD.foreground: Black                                     
xcalc.ti.bevel.screen.INV.background: Green                                     
xcalc.ti.bevel.screen.INV.foreground: Red                                       
xcalc.ti.bevel.screen.LCD.background: Green                                     
xcalc.ti.bevel.screen.LCD.foreground: Black                                     
xcalc.ti.bevel.screen.LCD.shadowWidth: 0                                        
xcalc.ti.bevel.screen.M.background: Green                                       
xcalc.ti.bevel.screen.M.foreground: Black                                       
xcalc.ti.bevel.screen.P.background: Green                                       
xcalc.ti.bevel.screen.P.foreground: Black                                       
xcalc.ti.Command.foreground: White
xcalc.ti.Command.background: black                                              
xcalc.ti.button5.background: orange                                             
xcalc.ti.button20.background: red                                               
xcalc.ti.button25.background: red                                               
xcalc.ti.button30.background: red                                               
xcalc.ti.button35.background: red                                               
xcalc.ti.button40.background: green                                             
xcalc.ti.button22.background: blue                                              
xcalc.ti.button23.background: blue                                              
xcalc.ti.button24.background: blue                                              
xcalc.ti.button27.background: blue                                              
xcalc.ti.button28.background: blue                                              
xcalc.ti.button29.background: blue                                              
xcalc.ti.button32.background: blue                                              
xcalc.ti.button33.background: blue                                              
xcalc.ti.button34.background: blue                                              
xcalc.ti.button37.background: blue                                              
xcalc*Cursor:                 hand2                                             
xcalc*ShapeStyle:             rectangle

XTerm*faceName: Dejavu Sans Mono:size=10
XTerm*boldFont: Dejavu Sans Mono:style=Bold:size=10
XTerm*loginShell: true
XTerm*scrollBar: false
XTerm*eightBitInput:   false
XTerm*colorMode: true
XTerm*utf8: 1 
XTerm*reverseVideo: false
XTerm*color0:  black
XTerm*color1:  red
XTerm*color2:  green
XTerm*color3:  yellow
XTerm*color4:  blue
XTerm*color5:  magenta
XTerm*color6:  cyan
XTerm*color7:  white

UXTerm*faceName: Dejavu Sans Mono:size=10
UXTerm*boldFont: Dejavu Sans Mono:style=Bold:size=10
UXTerm*loginShell: true
UXTerm*scrollBar: false
UXTerm*eightBitInput:   false
UXTerm*colorMode: true
UXTerm*utf8: 1 
UXTerm*reverseVideo: false
UXTerm*color0:  black
UXTerm*color1:  red
UXTerm*color2:  green
UXTerm*color3:  yellow
UXTerm*color4:  blue
UXTerm*color5:  magenta
UXTerm*color6:  cyan
UXTerm*color7:  white


```

---

### Post by satimis on 2007-10-01
> **kerry_s said:**
> you create the .Xdefaults file.

here's what mine looks like->
UXTerm*reverseVideo: true <will make black on white

! you should run ` xrdb -merge /path/to/.Xdefaults '

- snip -
Thanks for your advice.

I found the trick which is on /etc/X11/app-defaults/XTerm-color file.


Performed following steps;

Edited /etc/X11/app-defaults/XTerm-color
- comment out 
*VT100*foreground: gray90"
*VT100*background: black

- uncomment 
!*VT100*foreground: black
!*VT100*background: gray90

$ cat /etc/X11/app-defaults/XTerm-color```

....

! Set the default text foreground and background colors.
!*VT100*foreground: gray90
!*VT100*background: black

! - OR -
! Uncomment this for black text on a "white" background.
*VT100*foreground: black
*VT100*background: gray90

.....

```

Restarted Xterm.  Now I have grey background and black characters.


satimis

---

