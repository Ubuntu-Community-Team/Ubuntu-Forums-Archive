---
title: "Restarting X-server or logging out freezes computer..."
date: 2008-01-24
forum: General Help
---

### Post by whashnez on 2008-01-24
Greetings Ubuntu forums....Thanks for you help...You rock![http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
I' using ubuntu for the past 2 years and I have a problem since then with all the versions.It's a little annoying sometimes...Here goes:When I try to log out from gnome's(or KDE's) shutdown menu OR  
when I try to simply restart X-server by pressing Ctrl+Alt+Bcksp the the monitor shuts down most times and system freezes.It goes black, then shuts down and there's no respond when I press several buttons except of course the reset button.I would be glad if you could help me,this is really annoying.

I'm running ubuntu guttsy with ATI radeon 9600 pro,and using the fglrx drivers at an xgl session having the compiz fusion enabled.I have a qdi superb 4fx(I think) motherboard.

                                                                                                                                  Thank You

---

### Post by kuja on 2008-01-24
It's a fairly well known problem with the fglrx driver. With that particular card however you may be able to achieve similar performance with the ati or radeon drivers. I do know for a fact that they aren't subject to that bug, and if the performance is acceptable with the open source drivers you should be set. Give it a try.

---

### Post by whashnez on 2008-01-25
First of all thanks for replying...As I remember the open source drivers performance was much poorer than the fglrx drivers...I used them before..(You mean the mesa-project drivers...)...Also there were several issues with the xgl,the composite etc and as I remember I couldn't enable compiz...Is there any other solution for this problem?...Anyway thank you very much for replying...

---

### Post by kuja on 2008-01-26
awww :( 

Maybe it was the Radeon 9500 and down that performed well with the OSS drivers. I'd have to check to be sure though.

I know this is probably not what you want to hear, but the most ideal solution to the problem is probably the simplest, and is also what I did to my Radeon 9700 way back when. Simply replace the card with another ... preferably one with better drivers/support/ available. I think I put a GeForce 4 MX  420 in mine. Another option could be an older Radeon, seeing as they're said to work rather well with the OSS drivers (I mention this idea also seeing as that way you wouldn't need any binary blob drivers)

---

### Post by whashnez on 2008-01-28
Well...I don't think tha it's my graphics card because friends with later ATI radeon models than mine don't have any problems restarting X.Could it be a motherboard problem or a BIOS setting that corrects the problem?

---

