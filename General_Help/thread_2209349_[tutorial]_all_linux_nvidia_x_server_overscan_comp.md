---
title: "[tutorial] all linux nvidia x server overscan compensation setting"
date: 2014-03-05
forum: General Help
---

### Post by milkboy007 on 2014-03-05
Since Nvidia app version 302 for linux AFAIK, overscan compensation setting has been disabled.
Today when i want to use my old screen laying around as and extra work space, there is an overscan on the screen (i'm using a hdmi-av signal converter)
i cant seems to find to find a solution using the GUI "Nvdia X Server Setting" by searching this forum or googling. only console based solutions, with no explanations
so, after i found a [console based solution]("http://www.pclinuxos.com/forum/index.php/topic,106650.msg911319.html?PHPSESSID=agh6he7mqe364n5a2hnac3nmc4#msg911319") and understanding what those in put meant, i tried experimenting it on the GUI.
with a few trial and error, it was a sucess. :popcorn:
This tutorial may work on other linux, os or`  platform

**Without further ado, here is the step:**
in this step I'll use 720X480 resolution as an example. Change to your desired value

[LIST]
[*]Open Nvdia X Server Setting 
[*]On the right side of the window click "X sever display configuration" 
[*]On the left bottom click on "advance" button 
[*]Choose which display (1) you are using / compensating 
[*]Choose the Resolution (2) if needed 
[*]Change the "View port out" value (3) with this formula "**(720-left-right)x(480-top-bottom)+X+Y**" to compensate 
[/LIST]
the formula means "(Screen Pixel Width)x(Screen Pixel Height)+ offset X  (move the display to the right) + offset Y (move the display to the  bottom)"


[LIST]
[*]Click "apply", if there is still border/overscan change the above value (3) 
[/LIST]
 [ATTACH=CONFIG]250873[/ATTACH]

EXAMPLE. in my case, (based on trial and error) using value of "**720x480+0+0**" on my tv, i _guesstimate_ it has an overscan about 30 pixel on left, 30p right, 15p top and 15p bottom screen. see pic showng a maximized window.
[ATTACH=CONFIG]250876[/ATTACH]

using the guesstimate, and using the formula formula (720-30-30)x(480-15-15), gives me a value of "**660x450+0+0**". 
now when i apply the changes now it has black border of 30p on the right and 15p bellow.see pic.
[ATTACH=CONFIG]250875[/ATTACH]

soo, to move it, to the right by 30p and bottom by 15p, i change X to 30 and Y to 15, now the value is "**660x450+30+15**"
when i apply i still see a small black border of 5p on the right so i change it again to "**660x450+35+15**"
and the final result is this.
[ATTACH=CONFIG]250874[/ATTACH]

display that fit the screen just about right.

this is a trial and error, since most people cant count the displayed  pixel, you have to guess/estimate and fine tune the number until the display  has the exceptable amout of overscan/border. 
**DON'T FORGET TO CHANGE THE RESOLUTION** **AND CORESPONDING VIEW PORT OUT VALUE** [B]TO FIT YOUR TV OR SCREEN
[/B]
[COLOR=#ff0000]**IF YOU HAVE CONSTANT FREEZE AFTER YOU CHANGE THE VALUE, READ BELLOW.**[/COLOR]
For some reason, whenever i use "_665x449_+35+15" or some other number that doesnt end with zero for the resolution, my pc freezes alot before reverting to previous state.
soo, if you guys are also expiriencing such problem use numbers that ends with 0 like "_660x460_+35+15".
Since i dont know whether this is a software bug (X or nvidia) or hardware limitations, so, i did not report it to any bug tracker.

hope you guys understand my instructions and help you with your problem.
cheers

PS as usual i dont know weather im posting in the right section. if i dont, i apologize and pls move it to the right section. :P

---

