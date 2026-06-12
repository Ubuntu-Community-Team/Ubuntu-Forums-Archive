---
title: "openoffice 2.3 with gutsy/compiz not working properly"
date: 2007-10-31
forum: General Help
---

### Post by tjk on 2007-10-31
Ever since I upgraded to 7.10 (and Openoffice upgraded to 2.3) I have had problems with OpenOffice not working properly.  Every time I open any of the components they open in full screen and often the menu bar is not functional.  By "full screen" I mean that there is no titlebar, the taskbar is covered and any of the compiz functions don't work until I close OpenOffice.  I tried reinstalling and it didn't help.  :(

Is anyone else having the same problem (I couldn't find any situation like this when I searched the forums)?  Does anyone have any ideas on how to fix the problem?

BTW, I'm running 64-bit gutsy with KDE desktop.

---

### Post by Speedoo on 2007-10-31
I had the same problem, and couldn't find a solution.  I resolved the problem by installing the 32-bit version of Gutsy.  Now my OO opens normally, and I can create, open, edit documents, but when I try to print, the application freezes.  I filed a bug report with launchpad, but so far no one has offered a solution.  At this point, I'm either looking for a working alternative to Open Office (I downloaded the Gnumeric spreadsheet, but it also freezes when I try to print), or creating a new partition and reinstalling Windows.

---

### Post by aralbald on 2007-11-01
Go to Compiz Config Panel -> Workarounds and the disable Legacy full screen support. That fixed it for me. Haven't noticed any side effects on other applications.

---

### Post by Speedoo on 2007-11-02
Sorry, I'm not following.  By Compiz Config Panel, do you mean "Advanced Desktop Effects Settings"?  Not finding any option called "Workarounds."  Thanks for any further details.

---

### Post by danstah on 2007-11-02
its actually a plugin just search for it in advanced desktop settings

---

### Post by ulefr01 on 2007-11-02
> **Speedoo said:**
> Sorry, I'm not following.  By Compiz Config Panel, do you mean "Advanced Desktop Effects Settings"?  Not finding any option called "Workarounds."  Thanks for any further details.
I have installed the 64-bit version of openoffice.
In the "Advanced Desktop Effects Settings" , go to Utility and disable the" Workarounds".
This works for me

---

### Post by spacegypsy on 2007-11-11
> **aralbald said:**
> Go to Compiz Config Panel -> Workarounds and the disable Legacy full screen support. That fixed it for me. Haven't noticed any side effects on other applications.

did the trick for me

thx aralbald

---

### Post by macbuzz on 2007-11-12
I have had this exact problem but with the 32 bit version of Gutsy.  Thought I would mention this because the solution presented here worked to resolve the issue.

---

### Post by zerobabble on 2007-11-13

agreed... bizarre behavior... 


it appears that when you start openoffice from the menu icon the toolbars are fine... when i click on a document that launches openoffice, my toolbars too disappear and behave  weird... i think that this is the bug... 

launching openoffice documents directly from file association...  




---

### Post by drumsticks on 2007-11-13
Same problem and same workaround here too. I'm using PPC Gutsy (Powermac G5). Just FYI for the rare few running PPC Gutsy ;)

---

### Post by zerobabble on 2007-11-13


so it seems to be more of a launcher thing... i tested with java 1.6 too and the problem persist... if i run from a konsole... 

openoffice.org -calc myfile.ods

the toolbars are fine... its seems to be when you launch from the file association mouse click... i'm using the latest kde, i think today its at 3.5.8... not sure if this exits in gnome... interesting though, actually, annoying more so... 

thoughts?


p.s. - compiz-kde-0.5.2




---

### Post by Blind Tiger on 2007-11-24
I'm running Ubuntu Studio 7.10.  Today I experienced the same menu error -- no title bar, non responsive menus, and reiterated toolbar icon refresh.  I deselected "Legacy Fullscreen Support" in CCSM-->Utilities-->Workarounds, and OpenOffice spreadsheet functions just fine now.

---

### Post by des4ij on 2008-01-12
worked for me as well... just hoping openOffice fixes the few flickering and this in next update... so its automated...

---

### Post by mmadhukarbhat on 2008-02-17
> **aralbald said:**
> Go to Compiz Config Panel -> Workarounds and the disable Legacy full screen support. That fixed it for me. Haven't noticed any side effects on other applications.

Thank you, that worked for me also.
Madhukar

---

### Post by raydar on 2008-03-01
Same problem, same workaround solved it for me, on 32-bit Gutsy.  THANKS!  :)

Here's seconding the motion/hope for a fix in the next release (or sooner) . . . .

---

### Post by bloodorange on 2008-04-02
Awesome.  Disabling Legacy Fullscreen Support has cured more than my OpenOffice problem.  I also had a problem with trying to use Blender in Windowed mode; it would always open in fullscreen instead.  This is now cured...

Thanks very much.
:)

---

### Post by drkjstr on 2008-04-15
> **aralbald said:**
> Go to Compiz Config Panel -> Workarounds and the disable Legacy full screen support. That fixed it for me. Haven't noticed any side effects on other applications.

Thanks for the help. Had to install compizconfig-settings-manager first (don't know how that didn't get installed).

---

