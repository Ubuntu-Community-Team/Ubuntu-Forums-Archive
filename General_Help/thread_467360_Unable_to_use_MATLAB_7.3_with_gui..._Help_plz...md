---
title: "Unable to use MATLAB 7.3 with gui... Help plz.."
date: 2007-06-07
forum: General Help
---

### Post by canbal on 2007-06-07
I have a problem with using MATLAB 7.3 with gui. :( I am a newb&#305;e in Linux and try to get rid of Windows totally. I installed MATLAB according to the instructions and the MATLAB seems to work perfectly from the console. However when "matlab" is called directly, the gui opens as a blank window after the splash. I searched for this through the net bu I could not find a solution. I would really appreciate if you could help me...

P.S. I don't know if it is any help but, when plot or figure etc. commands are invoked from the console, the windows that handles the axes etc. works fine..

---

### Post by Blayde on 2007-06-07
I'm not sure how MATLAB works, but if it is anything like Maxima or Maple then the GUI starts a background process that does all the thinking. They communicate via localhost so make sure it is setup correctly:

Go to System > Administration > Network
Click on the Hosts tab
Make sure there is an entry with ip address 127.0.0.1 and alias localhost
Make sure there is an entry with ip address 127.0.0.1 and alias <your computer name here>

Hope this helps!

---

### Post by daschmidty on 2007-06-07
Not sure about 7.3 but this was the case for 7.2. You need to tell matlab to run in a terminal because it needs a dumb terminal running in the background to do its real work. Give it a terminal and the gui should work just fine.

---

### Post by canbal on 2007-06-07
I tried this but problem still exists. Nothing has changed...... :(:(

---

### Post by canbal on 2007-06-07
@daschmidty

I could not understand what do you mean by giving it a terminal? I start MATLAB by "matlab -desktop" from the terminal. Is it what you mean?

---

### Post by daschmidty on 2007-06-07
are you using ubuntu or kubuntu?
I have to look up how to do it in GNOME as i am a KDE guy..

---

### Post by canbal on 2007-06-07
Ubuntu 7.04

---

### Post by daschmidty on 2007-06-07
i read that if you add a launcher for it in gnome-menu, you can use this option. Call just matlab and not matlab-desktop and tick the box for run in terminal, and it should hopefully start up.

---

### Post by canbal on 2007-06-07
As I said I am a newbie #-o and I am truly sorry for bothering you so much. Can you be more specific about what to do? I am posting a screenshot of the problem....

---

### Post by daschmidty on 2007-06-07
hmmm..that's not the problem i was having and i don't think i know how to fix this one exactly. You may want to search other posts regarding newer version of MATLAB as i have seen people mentioning versions 7.2r14 and up may have some Java issues :(. sorry i couldn't be of more help there.

---

### Post by Kent84 on 2007-06-07
Do you have the license manager running? To start it, run the following: <matlab install dir>/etc/lmstart

I created a script called matlab-start.sh with the following:

#!/bin/bash
/opt/matlab74/etc/lmstart
/opt/matlab74/etc/matlab
/opt/matlab74/etc/lmdown

Then I create a launcher pointed at this script, making sure that run "run in terminal" was selected. What the script does is start the license manager, then start matlab. Once matlab has quit, shutdown the license manager again. This is just me being anal since I *HATE* license manager so want to stop it whenever I don't need it. Most people have their license manager running in the background all the time (i.e. start it during boot time). See [http://www.caspur.it/risorse/softappl/doc/matlab_help/base/install/unix/chap2_11.html](http://www.caspur.it/risorse/softappl/doc/matlab_help/base/install/unix/chap2_11.html) for how to do this.

---

### Post by cookies on 2007-06-07
You seem to have Desktop Effects on. Disable them, then try to run matlab.

---

### Post by canbal on 2007-06-08
Thanks for all your help.. The problem seems to be because of beryl running on. After disabling beryl, everything worked fine.. BTW I also cannot use Mplayer or VLC Player while beryl is running on.. It seems like I should stick with the original GNOME. Too bad I cannot use beryl, it was fancy!! :( :(

---

### Post by aJayRoo on 2007-06-08
Add the line:
```
export AWT_TOOLKIT="MToolkit"
```
to your /etc/environment file. This seems to resolve problems with java swing widgets (which is what Matlab uses to display its graphical interface). This solved the exact same problem I had with Matlab allowing me to use beryl still. Hope that helps.

---

### Post by Kent84 on 2007-06-11
Yes! That's what you have to do to launch any java swing application on top of beryl.

> **aJayRoo said:**
> Add the line:
```
export AWT_TOOLKIT="MToolkit"
```
to your /etc/environment file. This seems to resolve problems with java swing widgets (which is what Matlab uses to display its graphical interface). This solved the exact same problem I had with Matlab allowing me to use beryl still. Hope that helps.

---

### Post by anaGP on 2008-05-27
HELP ME!!!!!
I have installed matlab 7.0 (r14) on linux. Use the distribution kubuntu (Ubuntu 8,04 kernel 2.6.24 - 16 - generic).
Matlab does not recognize mex - setup (it gives a license error -2). But in line of command of linux yes works well mex -setup.
Also when I want to use guide, it does not work (it gives license error -1).
I followed the installation passages that I found in forums and I do not see differences with which I did  Somebody can give some suggestion me?  Will be that I need some license?
Somebody has the license of the Matlab 7 R14 that can command to me by mail? 
Thank you very much
 AnaGP

---

### Post by anaGP on 2008-06-12
I installed the R2008a without problems, but when I want to use the GUI (guide) appears a screen to activate the license, I indicate the way to him where it is the license file, but when returning to open that or another group GUI it does the same  what can be happening? (simulink works) 
In addition I continue having he himself error (another one) that with other older versions of matlab under linux (in matlab under Windows it does not happen): work with a bookstore, called truetime; I must add lines in matlabrc.m so that it recognizes it, of those lines of code works all safe good by the line: mex - setup; matlab under linux does not recognize that code, by error of license 2. 
////// 
Which I add at the end of matlabrc.m: 

disp(’Bienvenidos. A trabajar con TrueTime.’ 
disp(’Espere por favor …’ 
addpath([getenv('TTKERNEL')]) 
init_truetime; 
disp(’Todo bien hasta aca …’); 

mex -setup 

make_truetime; 


HELP PLEASE. THANK YOU !!!!

---

