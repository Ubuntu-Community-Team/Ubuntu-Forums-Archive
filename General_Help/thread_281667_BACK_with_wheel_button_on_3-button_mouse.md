---
title: "BACK with wheel button on 3-button mouse"
date: 2006-10-21
forum: General Help
---

### Post by cage cat donnie on 2006-10-21
Hi,  I am trying to make the wheel button of my MS optical intellimouse to execute a "back" function, esp while in a web browser.  It is a three button w/ wheel and click (5 commands).  I have seen a lot of discussion about 5-button mice, (7 commands) but only passing reference to 3-button.  I saw this from 'oars' in the message board...

*I switched from a 5 button mouse to a 3 button (2 buttons and scroll wheel). I used IMwheel to make it so that clicking the scroll wheel goes back for me.*

I have installed imwheel, but I am a total Linux virgin and don't know my way around.  The tutorals for 5 button mice gives clues, but they tend to be recipes and don't talk about HOW it works, and with my limited knowlege I can't it figure out well enough to make it work.  The imwheel manpage seems cryptic to me.  Any advice to put me in the right direction?

Linux feels like a foreign land, but I like the scenery.  Ubuntu seems like the kind of place I could put down roots, and I am really tired of living in Stinkville, MS.  

Don

---

### Post by cage cat donnie on 2006-10-24
I finally figured it out.  I'll post for posterity  (mostly so I can look it up when I need to reinstall and I have forgotten how)

There are a million pages for making 5-button mice work, so I will only hit the highlights. 

The overview:  The main difficulty is imwheel won't let you directly alter the wheel button, so you have to do the following.  You need to tell your config you have 7 buttons, even though you only have 5. I did this by placing these two lines in the mouse section of my xorg.conf.  Now that I look at it, I don't know what the second line is doing there.  Maybe I could delete it, but it works now so I won't mess with it.

	Option "Buttons" "7"
 	Option "ButtonMapping" "1 2 3 6 7"

As I said, IMwheel doesn't let you do anything with the middle wheel button, so you have to remap it to one of the imaginary buttons we created.   You need to make a startup script for IMwheel anyway, so I used xmodmap to do the job.  For some reason, it thinks I need 11 buttons, so I added the extra buttons.  the "2" is needed to show that is the button imwheel is to work on.  This script is set to start at boot

#!/bin/sh
exec xmodmap -e "pointer = 1 6 3 4 5 2 7 8 9 10 11" &
exec imwheel -k -b "2" &
exec $REALSTARTUP
 
Now you need to tell imwheel what to do via the imwheelrc configuration file.  I copied one for another page.  I know there is extra junk, but again, it works so I didn't mess with it.  

".*"
None, Left, Alt_L|Left
None, Right, Alt_L|Right

"(null)"
None, Left, Alt_L|Left
None, Right, Alt_L|Right

So the wheel button is fooled into thinking it is a left thumb button, which is set to perform the "back" function.  This is a lousy writeup, I will try to do a proper one after I clean it up and get some of my other newbie problems straightened out.

---

### Post by darrinfunk on 2007-02-19
> **cage cat donnie said:**
> This is a lousy writeup, I will try to do a proper one after I clean it up and get some of my other newbie problems straightened out.

I also like the wheel click to perform a back function.  If you could spare the time to help me out with this I would be most pleased.   You're right... your write-up is a little hard to follow and it is based on procedures documented elsewhere.

Could you post a complete description of your solution?

---

