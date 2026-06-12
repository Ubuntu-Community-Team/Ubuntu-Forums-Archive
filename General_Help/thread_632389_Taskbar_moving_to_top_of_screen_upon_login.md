---
title: "Taskbar moving to top of screen upon login"
date: 2007-12-05
forum: General Help
---

### Post by darkstr2o4 on 2007-12-05
The taskbar on the bottom of my screen consisting of quick launch icons keeps moving to the top of the screen upon startup or login.  In order to return it to the bottom i have to go into the properties -> recheck the expand button -> change the orientation to bottom.  If i do not recheck the expand button it will not stay on the bottom, however re-orient itself onto the top.

I do not want to have to do this every time I start up or log in. I just upgraded to Gusty from Dapper and never experienced anything like this before. Any suggestions would be greatly appreciated. 

](*,)

---

### Post by drs305 on 2007-12-05
Open up gconf-editor and check "apps/panel/toplevels/top_panel_screen0" is listed as "bottom". I don't know if that is a sticky or not but it should be. I don't know what is changing your settings.

An inelegant way (since it may be only temproary) to get the panel to the bottom at boot-up would be to put the following in Syst, Preferences, Sessions, Startup. You could also make a shortcut on your panel with the following command so moving the panel is just a single click away:

gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation "bottom"

---

### Post by darkstr2o4 on 2007-12-05
The first solution did not work but i decided to expand the bar and make it completely transparent and now it does not skip to the top.  It also is more visually appealing in my opinion so i think i will just keep it this way. Thanks for the help.

:)

---

### Post by gauravm on 2007-12-18
SOLUTION IN GUTSY: 
you can expand the panel when it's on the top of the screen, change the orientation to Bottom and unexpand it once it's at the bottom....

alternatively, you can follow the steps below to automate what i said above and be done w/ it...

1)cut and paste the code below into a text document:
```
gconftool-2 --type bool --set /apps/panel/toplevels/panel_0/expand true;
gconftool-2 --type string --set /apps/panel/toplevels/panel_0/orientation "bottom";
gconftool-2 --type bool --set /apps/panel/toplevels/panel_0/expand false;
gconftool-2 --type int --set /apps/panel/toplevels/panel_0/y_bottom 0;
```

NOTE: remember to change "panel_0" in the lines above w/ the name of your panel....obtainable by launching gconf-editor and going down into: ->apps->panel->toplevels->(one of the panels here is the panel that keeps moving around)

2)after the text document is saved...right click on it in the file browser (ie. nautilus) and under Properties->Permissions check on the "Allow executing file as program" Then click close.

3)Now go to System->Preferences->Sessions->Startup Programs and  +Add your newly created script to run every time your computer starts...

enjoy!

---

