---
title: "help with Skydome"
date: 2008-05-03
forum: General Help
---

### Post by bluestargazer on 2008-05-03
I just installed ubuntu, and a friend previously helped me set up my skydome, but i just can't get it working. 

I've checked to make sure that my max was 2048:1024. Done
I've checked to make sure that compiz had jpg and png checked.

but when i try to use the picture it just won't work. i've been searching on the forums but can't find out what to do. 

I found this but i have no clue what this means

I have an ATI card and no matter what I tried, I couldn't get a skydome image to load... the screen would just go white on me, and no matter what the image size or format I tried, I got the same result. I finally gave up and started looking around for a fix for why my custom trueglass theme was going white when I hit the maximize button, and strangely enough... the fix for that fixed my skydome problem too!!

A big thanx to the people at [http://www.bloglines.com/blog/cybernout](http://www.bloglines.com/blog/cybernout) for helping me figure this out!

gksu gedit /etc/drirc


paste :



<driconf>

<device screen="0" driver="radeon">

<application name="all">

<option name="allow_large_textures" value="2" />

</application>

</device>

</driconf>

Now just save the file and you'll be off and running.

Hope this helps somebody out there!

(This is the first time I've ever logged a fix on the Ubuntu forums... I'm so excited!)

I tried coyping  (gksu gedit /etc/drirc) into the terminal still don't know what to do. 

Can anybody explain to me what i'm doing wrong?

---

### Post by darco on 2008-05-03
"the fix for that fixed my skydome problem too!!"

I dont understand. Are you still having a problem w/Skydome?

"I tried coyping (gksu gedit /etc/drirc) into the terminal still don't know what to do."

You then need to hit the enter key, it will then open up a blank text screen where you can add the script that bloglines pointed you to ,hit the save button and "you'll be off and running."

darco

---

### Post by bluestargazer on 2008-05-03
Sorry if my first post was misunderstanding. I took a quote from a post called sco-pro. He had the same problem, i tried using his advice and i wasn't doing it right. 

But thanks to Darco i did what Sco-Pro advised. But my skydome is still white.

Thanks Darco for you advise even if it didn't help, but if you have anymore advise i could use that would be good too. 

Again my problem is: That no matter what i do my skydome is a blank white screen.   

  I've checked my pixel ratio and its 2048 by 2048. (and when i try editing my picture using gimp, gimp won't let me do 2048 by 2048 only a 2:1 ratio. Which i heard is still alright.

  I've checked to make sure compiz is recognizing all the right formats (jpg, and png)

  I now went to my terminal and typed in what Sco-Pro advised and also i was able to the whole pasting and saving thing. but the white screen is still there. (maybe i still did something wrong. but the blank white sheet came up and i copied and pasted what he had, then saved.)

  I also went to gnome look and downloaded a skydome. still didn't work.

Thats all that i've done, is there something i'm doing that is incredibily stupid and obvious? 

Thanks to anyone who can help.

---

### Post by darco on 2008-05-03
Do you see your images for the desktop cube and caps?

darco

---

### Post by darco on 2008-05-03
Heres my screenshot of CCSM...

darco

---

### Post by bluestargazer on 2008-05-03
> **darco said:**
> Heres my screenshot of CCSM...

darco

yeah, i was just able to get my skydome working. but i still don't know what you mean by those other things( background images and cube caps)

I guess i don't understand because my skydome works but i don't know what the background image is going to be the background of. i can guess what the cube caps images will be.

Also thanks for helping me.

---

### Post by darco on 2008-05-03
Here is my desktop w/caps,skydome and desktops images enabled...
good luck
darco

edit..oops you cant see my caps!

---

### Post by bluestargazer on 2008-05-03
yeah i get what they do now. But i can't get my four windows to have four different pictures. I followed your model, but they aren't showing up.

---

### Post by darco on 2008-05-03
type gconf-editor in a terminal,hit enter....the editor will open up, navigate to Apps/Nautilus/preferences and uncheck show desktop...a warning tho, you cannot view anything that you have saved to your desktop. Something the devs or whoever never got around to adressing,,,,
try it and let me know,,,,
darco

---

### Post by bluestargazer on 2008-05-03
Yeah, i did that but i guess i'm getting stuck on not being able to uncheck the show desk top. I clicked on the icon, right clicked and changed the true option to false. I really didn't know what to do with it.

---

### Post by darco on 2008-05-03
maybe you need to re-login...crtl+alt+backspace
darco

---

### Post by bluestargazer on 2008-05-03
> **darco said:**
> type gconf-editor in a terminal,hit enter....the editor will open up, navigate to Apps/Nautilus/preferences and uncheck show desktop...a warning tho, you cannot view anything that you have saved to your desktop. Something the devs or whoever never got around to adressing,,,,
try it and let me know,,,,
darco

yeah i uncheck the "show desktop" the only thing now is that my skydome pic is now a blue screen and my volumne isn't working. wow this is confusing.

---

### Post by bluestargazer on 2008-05-03
actually i figured out the skydome thing, but for some reason the volumne isn't working at all.

---

