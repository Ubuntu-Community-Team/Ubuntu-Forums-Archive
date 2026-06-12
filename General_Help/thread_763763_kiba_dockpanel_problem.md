---
title: "kiba dock/panel problem"
date: 2008-04-23
forum: General Help
---

### Post by n00d1ek1ng on 2008-04-23
hey guys so i installed the kiba dock and deleted my panels and came across some problems

followed this tutorial to install the dock
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)


and i did this tutorial to delete my panels
1. Goto System -> Preferences -> Sessions
2. Click on Current Session tab. Find gnome-panel there and set it's style to
"Trash" and click Apply button. DO NOT close the Sessions Window
3. Now open a terminal and type:
$killall gnome-panel

4. Now close the terminal window and go back to the sessions window.
5. Click on the Session Options tab and check (tick) the "Automatically remember running applications when logging out" check-box.
6. Click on the "Remember currently running applications" button.
7. Close the sessions window.




my problem is is that after i restart or boot up, my computer displays the panels still.

i also get these white boxes instead of the icon for wireless connection. my dock also duplicates certain apps. for example say i have amarok or pidgin open, it will show up twice in my dock. 

finally, where can i get themes or buttons/akamaru to customize my dock? 
[http://www.youtube.com/watch?v=kVXgSBLCbLQ](http://www.youtube.com/watch?v=kVXgSBLCbLQ)


when i boot up i always have to open up a terminal and type:
gconftool-2 --recursive-unset /apps/panel

afer i do this, my panels disappear......

finally switched over to linux after being sick of vista and xp, however there are certain problems like this that really bug me > <

pls help!!! xD
here are some screenshots
[IMG]http://i34.photobucket.com/albums/d111/divinerice/linux/Screenshot-Desktop-1.png[/IMG]

[IMG]http://i34.photobucket.com/albums/d111/divinerice/linux/Screenshot-Desktop.png[/IMG]

---

### Post by Ub1476 on 2008-04-23
It appear to me that you have a "notification" plugin enabled in kiba-dock. That's why there's duplicates of already opened panels when the gnome-panel is killed, and only white squares when it's open (because the notification area in the gnome-panel has it "reserved"). If you remove that plugin it your problem is fixed, I guess:)


So, the reason you have to **kill the gnome-panel** in Sessions **before saving** your session is that when you "save the session", the next time you log into Gnome/Ubuntu is that it will only start the apps which were running at the time you saved.

Either you missed a step here, or there's some restrictions for it to happen (if is, you can always set gnome-panel opacity to 0 in Compiz).

I don't know if you can find already made themes for kiba-dock, but you should be able to edit your current theme in kiba-dock manager.

If you can't find any "kiba-dock manager", hit alt+f2 and start writing kiba-dock manager/preferences, and see if anything comes up.

You should also be aware of that mostly all the docs for Linux is in pretty heavy development stage, which means they are not 100% or guaranteed to work.

Good luck with Linux:)

---

### Post by n00d1ek1ng on 2008-04-23
thnx for the help. as of now i am reinstalling ubuntu with the 64bit 8.04 rc den i guess imma try this again xD

tyty!!

however, how can i put the wireless button and bluetooth button on the dock?
awn or kiba...

here's an example of what i wanted to do....it's outlined in yellow...

[IMG]http://i34.photobucket.com/albums/d111/divinerice/linux/glassdesk.png[/IMG]

---

### Post by Ub1476 on 2008-04-24
That would be using the notification area in kiba-dock (which you already had on your previous install), but you have to tell Amarok and Pidgin to not minimize to the notification area. I'm using the Hardy Heron x86_64 myself, but I'm using Avant-Window-Navigator (AWN). Tell me if you find a guide for kiba-dock for 64-bit:)

---

### Post by n00d1ek1ng on 2008-04-24
now using awn but still can't get the network manager and bluetooth manager onto the dock. ideas?

---

### Post by Ub1476 on 2008-04-24
If you're using AWN, you need to install the AWN extras/plugins. I'm running the trunk build (unstable) but there should be an AWN guide around here in this forum.

When AWN extras is installed, simply open AWn-manager>Applets>add notification area.

---

