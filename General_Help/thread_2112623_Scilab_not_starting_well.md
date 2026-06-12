---
title: "Scilab not starting well"
date: 2013-02-05
forum: General Help
---

### Post by satyamM on 2013-02-05
Hi all,

I tried to install one add-on in scilab, SVIP i.e Scilab Video and Image Processing.

In doing that, I don't know what happened, but now my Scilab Console, whenever started, displays following message:

[HTML]
  ___________________________________________        
                        scilab-5.3.3

                Consortium Scilab (DIGITEO)
              Copyright (c) 1989-2011 (INRIA)
              Copyright (c) 1989-2007 (ENPC)
        ___________________________________________        
 
 
Startup execution:
  loading initial environment
exec('@TOOLBOXDIR@/loader.sce');
                                !--error 241 
File "@TOOLBOXDIR@/loader.sce" does not exist.
at line       2 of exec file called by :    
      exec(startupfiles(i),-1);
at line     156 of exec file called by :    
exec('SCI/etc/scilab.start',-1);;
 
-->

[/HTML]And moreover, my **menu bar in scilab has ceased to work**, (menu bar means bar displaying File Edit Preferences Control etc etc),....I mean when I click on it nothing happens, seems like it is jammed, I guess the Java Applet(probably) is missing/corrupted which makes menus to work......

Plus I have failed in installing SVIP correctly.....!!! Nothing's happening today...A bad day... :(

Somebody can come up with a solution, will be deeply appreciated...

---

### Post by Cajamarcawarrior on 2013-03-12
Hi SatyamM,
I want to ask if you found any solution for your scilab problem? 
I also have  a problem that scilab shuts down as soon is It is opened.

---

### Post by satyamM on 2013-03-12
Hi,

No, I couldn't find the solution to my problem. There were many problems including this in Scilab.
I had to shift to GNU's Octave for my work. So far Octave is doing good work for me.

---

