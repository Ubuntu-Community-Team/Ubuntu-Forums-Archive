---
title: "Ugly and tiny fonts in X programs"
date: 2007-08-11
forum: General Help
---

### Post by DKnight on 2007-08-11
Hello. I have xubuntu installed, and everything is looking nice except "x" programs, like xterm, xpdf or xzip.
Is there a way to change the font for those programs?
I've attached a screenshot so you can see what I'm talking about:
[[IMG]http://i16.tinypic.com/67sqgzn_th[/IMG]]("http://i16.tinypic.com/67sqgzn")

---

### Post by kerry_s on 2007-08-11
you use a .xdefaults file to change those fonts.
sometings, like xedit, have a bug were the fonts won't change. you'll have to do some googling for the exact wording.
example google:
xterm .xdefaults
xdefaults settings

here's a good example> [http://fluxbox-wiki.org/index.php/Howto_setup_Xdefaults](http://fluxbox-wiki.org/index.php/Howto_setup_Xdefaults)

I like mine big so might adjust mine to your needs->
```

! you should run ` xrdb -merge ~/.Xdefaults '

xpdf*initialZoom: width
Xft.antialias: true
!Xft.dpi: 75

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

XTerm*faceName: Dejavu Sans Mono:size=12
XTerm*boldFont: Dejavu Sans Mono:style=Bold:size=12
XTerm*loginShell: true
XTerm*scrollBar: false
XTerm*eightBitInput:   false
XTerm*colorMode: true
XTerm*utf8: 1 

XTerm*color0:  black                                                            
XTerm*color1:  red                                                              
XTerm*color2:  green                                                            
XTerm*color3:  yellow                                                           
XTerm*color4:  blue                                                             
XTerm*color5:  magenta                                                          
XTerm*color6:  cyan                                                             
XTerm*color7:  white                                                            
 

```

---

### Post by RedSquirrel on 2007-08-11
Don't forget to browse the man page for the terminal you are using to see all of the things you can customize, e.g., 

```
man xterm
```

This is a pretty good 'howto' for changing the colors if you want to play around with that:

[http://gentoo-wiki.com/TIP_Linux_Colors_in_Aterm/rxvt](http://gentoo-wiki.com/TIP_Linux_Colors_in_Aterm/rxvt)

---

