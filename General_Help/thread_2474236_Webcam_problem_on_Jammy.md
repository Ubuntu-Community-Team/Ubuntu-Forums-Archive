---
title: "Webcam problem on Jammy"
date: 2022-04-24
forum: General Help
---

### Post by Tom_Carr on 2022-04-24
I have a webcam that works fine on my 20.04 machine but not on my new install of Jammy.  When I use the cheese ap  on Jammy I can see myself in black and white with lots of lines through it, and no movement, like a bad photo.  When I use the cheese ap on 20.04 I see a vivid colorful motion picture of myself.

I ran this in terminal but it doesn't help me solve the problem:

> 
ls -ltrh /dev/video*
crw-rw----+ 1 root video 81, 1 Apr 24 13:52 /dev/video1
crw-rw----+ 1 root video 81, 0 Apr 24 13:52 /dev/video0




---

### Post by Seb71 on 2022-04-24
Seems to be a Cheese bug.

Either use something else, or lower the resolution (from Cheese).

---

### Post by Tom_Carr on 2022-04-24
What else can I use to test the webcam?

---

### Post by Seb71 on 2022-04-25
Cheese alternatives or software like Discord, Skype, etc.

---

### Post by Tom_Carr on 2022-04-26
I have 2 desktops, one running 20.04, the other 22.04.

On the 22.04 box I tested with both cheese and zoom and neither works.
On the 20.04 box I tested with cheese and it works so I know the webcam is OK.

I used an old memory stick version of 20.04 to run that on the box that was running 22.04.  Cheese worked fine so I  know there is no hardware problem.

There must be some problem in the 22.04 software.  How do I find the problem and fix it?

One other clue.  When I run   >  [COLOR=#000000]*ls -ltrh /dev/video**[/COLOR]
 on the 20.04 box where the webcam works fine I get:

> tom@tom-OptiPlex-990:~$ ls -ltrh /dev/video*
crw-rw----+ 1 root video 81, 1 Apr 26 12:04 /dev/video1



when I run it on the 22.04 box that  does not work I get 

> tom@tom-OptiPlex-3040:~$[COLOR=#000000]*ls -ltrh /dev/video**[/COLOR]
[COLOR=#000000]*crw-rw----+ 1 root video 81, 1 Apr 26 11:45 /dev/video1*[/COLOR]
[COLOR=#000000]*crw-rw----+ 1 root video 81, 0 Apr 26 11:45 /dev/video0*[/COLOR]

could the 2 root videos on the box that doesn't work be a problem?

---

### Post by Rex Bouwense on 2022-04-27
I just installed Ubuntu 22.04.  Cheese is misbehaving because I too have a black and white preview with colored lines running through it.  However, when I take a picture it comes out fine.  ZOOM and Big Blue Button are also working fine .  I suspect it is a Cheese problem

---

### Post by ajgreeny on 2022-04-27
Try ***guvcview*** which has always been a great deal better for me than cheese which always seemed to give me problems.

---

### Post by Rex Bouwense on 2022-04-27
Guvcview works like a champ.  Thanks ajgreeny.  I should have remembered that from my lxde days.  Tom_Carr try it.

---

### Post by him610 on 2022-04-27
This errant behavior has been reported to Gnome and launchpad. It happened to me too - green and purple vertical stripes.
More 'me too' entries may add to the urgency of repair.

Added: I just reread the suggestion by ajgreeny about *guvcview*. Downloaded it and tried it. It works great. I have begun removing cheese, installing *guvcview*, and defining an easy to remember alias on all of my machines equipped with cameras.

Thanks ajgreeny.

---

### Post by Tom_Carr on 2022-04-30
I tried  guvcview and the webcam works fine with it.  Thanks.

I had another problem which I  thought was related to the webcam, but now I'm not so sure.   Zoom was not working on the box with the new install of Jammy.  After testing the webcam using guvcview, Zoom is now working.  I wonder if guvcview initialized something?  Anyway, everything seems to be working now.  Thanks for your help.

---

