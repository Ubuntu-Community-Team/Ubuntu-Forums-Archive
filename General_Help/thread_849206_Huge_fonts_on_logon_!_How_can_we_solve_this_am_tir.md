---
title: "Huge fonts on logon ! How can we solve this am tired.."
date: 2008-07-04
forum: General Help
---

### Post by jesicap on 2008-07-04
Hello everybody,

am using Ububtu since Gutsy, now are some days that i passed to Hardy but one problem for me remains the same .

Lets take it from the start . When i installed in my laptop for first time ubuntu gutsy all was allright just on the log on screen in the box of username/password whatever and if i was writing is was with HUGE letter appearing . 

I was hopping that in this new version Hardy will resolve this problem but as far i can see now the problem remains the same, i still see HUGE fonts there .

Really what i have to do in order to fix this problem ?

Can anyone give some step-by-step order-help over here plz ..???

* +Some extra info..

[I]Resolution: 1280 x 800 @ 60.1
0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/I]


thanks in advance
am waiting for your answers, give s0me plz help ;)

:confused:

---

### Post by Frozsyn on 2008-07-04
I think the problem has been solve in this thread:
[http://ubuntuforums.org/showpost.php?p=4912357&postcount=1](http://ubuntuforums.org/showpost.php?p=4912357&postcount=1)

The keyword for your problem is 'dpi', wich is the value wich convert the number of pixel in real length (centimers, meters or something), so fonts and vector graphics are affected by this value (correct me if it's wrong)

---

### Post by jesicap on 2008-07-04
Thanks mate,
the answer is finally :
	
Add : **Option  "DDC" "No"**

In : Section "**Device**" in the file **/etc/X11/xorg.conf** . 

..i just also tried and works allright ;) :KS:popcorn::)

---

