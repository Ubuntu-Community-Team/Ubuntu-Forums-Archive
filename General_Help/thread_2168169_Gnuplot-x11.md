---
title: "Gnuplot-x11"
date: 2013-08-16
forum: General Help
---

### Post by warsame on 2013-08-16
Hi everyone

New to the forum, apology if this is breaking any forum rules.

I have Ubuntu 12.04 LTS on VMware player. I'm writing some scripts on python where I have set of data where ideally I want to use gnuplot to output the data. I'm having a real problem getting gnuplot to work.

The python file when I run it comes back with a error message:
set terminal x11
                      ^
         line 0: unknown or ambiguous terminal type; type just 'set terminal' for a list




So I did some looking around, I have gnuplot installed. I searched the forum and google, most suggest gnuplot-x11 is not installed.

So I did do 'apt-get update' and then 'apt-get install gnuplot-x11' but when its done most says no files added or updated.

I would greatly appreciate any advise. I'm using gnuplot because I have been suggested as I'm trying to use it with data and want to output it with graph which will later on be put on a website. This will be automated on daily, weekly and monthly.

If you guys even suggest a better option to gnuplot, I would take it into consideration. 

Thank you.

---

### Post by tgalati4 on 2013-08-16
x11 is not in the list!

Terminal type set to 'unknown'
gnuplot> set terminal

Available terminal types:
       cairolatex  LaTeX picture environment using graphicx package and Cairo backend
           canvas  HTML Canvas object
              cgm  Computer Graphics Metafile
          context  ConTeXt with MetaFun (for PDF documents)
            corel  EPS format for CorelDRAW
             dumb  ascii art for anything that prints text
              dxf  dxf-file for AutoCad (default size 120x80)
            eepic  EEPIC -- extended LaTeX picture environment
              emf  Enhanced Metafile format
            emtex  LaTeX picture environment with emTeX specials
         epscairo  eps terminal based on cairo
         epslatex  LaTeX picture environment using graphicx package
              fig  FIG graphics language for XFIG graphics editor
              gif  GIF images using libgd and TrueType fonts
             gpic  GPIC -- Produce graphs in groff using the gpic preprocessor
          hp2623A  HP2623A and maybe others
           hp2648  HP2648 and HP2647
             hpgl  HP7475 and relatives [number of pens] [eject]
           imagen  Imagen laser printer
             jpeg  JPEG images using libgd and TrueType fonts
            latex  LaTeX picture environment
Press return for more:  
              lua  Lua generic terminal driver
               mf  Metafont plotting standard
              mif  Frame maker MIF 3.00 format
               mp  MetaPost plotting standard
             pcl5  HP Designjet 750C, HP Laserjet III/IV, etc. (many options)
         pdfcairo  pdf terminal based on cairo
              png  PNG images using libgd and TrueType fonts
         pngcairo  png terminal based on cairo
       postscript  PostScript graphics, including EPSF embedded files (*.eps)
          pslatex  LaTeX picture environment with PostScript \specials
            pstex  plain TeX with PostScript \specials
         pstricks  LaTeX picture environment with PSTricks macros
              qms  QMS/QUIC Laser printer (also Talaris 1200 and others)
            regis  REGIS graphics language
              svg  W3C Scalable Vector Graphics driver
          tek40xx  Tektronix 4010 and others; most TEK emulators
          tek410x  Tektronix 4106, 4107, 4109 and 420X terminals
          texdraw  LaTeX texdraw environment
             tgif  TGIF X11 [mode] [x,y] [dashed] ["font" [fontsize]]
             tikz  TeX TikZ graphics macros via the lua script driver
         tkcanvas  Tk/Tcl canvas widget [perltk] [interactive]
             tpic  TPIC -- LaTeX picture environment with tpic \specials
Press return for more: 
          unknown  Unknown terminal type - not a plotting device
            vttek  VT-like tek40xx terminal emulator
            xterm  Xterm Tektronix 4014 Mode

Typically you would use *xterm* to give you a vector (thin line) plot.

---

### Post by steeldriver on 2013-08-16
AFAIK the default 'graphical' terminal type for gnuplot is wxt

```
set term wxt
```

however both that and the x11 term are provided by gnuplot-x11 as you have already found out - maybe try UNinstalling gnuplot-nox and then reinstalling gnuplot-x11?

```

sudo apt-get uninstall gnuplot-nox

sudo apt-get install --reinstall gnuplot-x11

```

Sorry I am guessing here but that's about all I can think to try

---

### Post by warsame on 2013-08-16
Thanks for the reply

I typed in 'gnuplot' and then typed 'set terminal' which gave me the following list:

Available terminal types:
canvas  HTML Canvas object
cgm  Computer Graphics Metafile
context  ConTeXt with MetaFun (for PDF documents)
corel  EPS format for CorelDRAW
dumb  ascii art for anything that prints text
dxf  dxf-file for AutoCad (default size 120x80)
eepic  EEPIC -- extended LaTeX picture environment
emf  Enhanced Metafile format
emtex  LaTeX picture environment with emTeX specials
epslatex  LaTeX picture environment using graphicx package
fig  FIG graphics language for XFIG graphics editor
  gpic  GPIC -- Produce graphs in groff using the gpic preprocessor
hp2623A  HP2623A and maybe others
hp2648  HP2648 and HP2647
hpgl  HP7475 and relatives [number of pens] [eject]
imagen  Imagen laser printer
latex  LaTeX picture environment
mf  Metafont plotting standard
mif  Frame maker MIF 3.00 format
mp  MetaPost plotting standard
pcl5  HP Designjet 750C, HP Laserjet III/IV, etc. (many options)
pdf  PDF (Portable Document File) file driver
postscript  PostScript graphics, including EPSF embedded files (*.eps)
pslatex  LaTeX picture environment with PostScript \specials
pstex  plain TeX with PostScript \specials
pstricks  LaTeX picture environment with PSTricks macros
qms  QMS/QUIC Laser printer (also Talaris 1200 and others)
regis  REGIS graphics language
svg  W3C Scalable Vector Graphics driver
tek40xx  Tektronix 4010 and others; most TEK emulators
tek410x  Tektronix 4106, 4107, 4109 and 420X terminals
 texdraw  LaTeX texdraw environment
tgif  TGIF X11 [mode] [x,y] [dashed] ["font" [fontsize]]
tkcanvas  Tk/Tcl canvas widget [perltk] [interactive]
tpic  TPIC -- LaTeX picture environment with tpic \specials
unknown  Unknown terminal type - not a plotting device
vttek  VT-like tek40xx terminal emulator
xterm  Xterm Tektronix 4014 Mode



So I tried 'set terminal tpic' svg and even xterm.

I still got the error. Everytime I exit gnuplot and enter it again it it always has this message below:
Terminal type set to 'unknown'

Does this mean, it is forgetting each time I have set it as 'xterm' 'tpic' or 'svg' or something.

If I want to show different type of graphs do I have to alternate between these terminals?

Any suggestions? I have tried installing various packages and still with no success.

I have also checked this thread but with success :(
[http://askubuntu.com/questions/171778/not-able-to-get-graphs-on-screen-with-gnuplot](http://askubuntu.com/questions/171778/not-able-to-get-graphs-on-screen-with-gnuplot)
[http://ubuntuforums.org/showthread.php?t=940140](http://ubuntuforums.org/showthread.php?t=940140)

---

### Post by warsame on 2013-08-16
Thank you very much for replying.

I have removed and reinstalled gnuplot-x11 again as you advised. I have try to set the terminal as 'wxt' but it gave me
> gnuplot> set term wxtTerminal type set to 'unknown'
                  ^
         unknown or ambiguous terminal type; type just 'set terminal' for a list


Still unable to run my python file
> gnuplot> set terminal x11                      ^
         line 0: unknown or ambiguous terminal type; type just 'set terminal' for a list

This is very frustrating, sorry if I'm asking silly question about this.


gnuplot> set data style line
             ^
         line 0: Unrecognized option.  See 'help set'.




---

### Post by tgalati4 on 2013-08-16
*gnuplot* has it's own scripting language.  Perhaps set up your plot and save the command file then use python to call *gnuplot myspecificplot.txt*.  Without seeing the python code, I would guess you have a parsing problem or a delimiter problem, because the gnuplot commands are not being sent properly.

It looks like terminal type x11 is default if certain conditions are met:

X11 OPTIONS
       Gnuplot provides the x11 terminal type for use with X servers. This terminal type is set automatically at startup if the DISPLAY environment vari&#8208;
       able is set, if the TERM environment variable is set to xterm, or if the -display command line option is used.  For  terminal  type  x11,  gnuplot
       accepts  the  standard  X  Toolkit  options  and  resources such as geometry, font, and background. See the X(1) man page for a description of the
       options.  In addition to the X Toolkit options:

---

### Post by maurococco34 on 2013-11-20
Hey, I had the same problem using Ubuntu 13.10 and Gnuplot 4.6.4. I've reading a while and solved the problem just installing gnuplot-x11. This automatically uninstalls gnuplot-nox and replace it by gnuplot-x11 allowing you to run wxt terminals.

> sudo apt-get install gnuplot-x11

Hope this help you

---

