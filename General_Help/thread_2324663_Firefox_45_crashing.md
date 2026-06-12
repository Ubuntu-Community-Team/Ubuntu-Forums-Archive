---
title: "Firefox 45 crashing"
date: 2016-05-15
forum: General Help
---

### Post by fbird3 on 2016-05-15
Hi, everybody
Long story short: ff45 esr crashes even with all add-ons disabled...
When it happened first, I restarted it on safe mode; followed the procedure, but if I had so much as one add-on enabled, ff 45 esr would crash; so I disabled them all and after a while it crashed nevertheless...
I paste below the error message received during my last try [all add-ons disabled, but with ff 20 running with a different profile]:

./firefox -P FF45-ESR
firefox: ../../src/xcb_io.c:386: _XAllocID: Assertion `ret != inval_id' failed.


It does not crash straightaway, but it does it in a matter of minutes, and even if I was not interested in running it without my add-ons enabled, much less so would I be if it is to crash like this.
Do let me know if you would like me to try something else.
I hope for good news, but I will take what I can get.

---

### Post by nanotube on 2016-05-16
Background info on this thread: [http://ubuntuforums.org/showthread.php?t=2324146](http://ubuntuforums.org/showthread.php?t=2324146)

well... it seems to be some issue with the Xorg libraries. There's a bug report about it here: [https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/507062](https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/507062)
Unfortunately.... in that thread nobody seems to know what fixed it eventually, just "well some new updates have been made to that library, with the latest release and problem went away"
so... you might be out of luck on running an updated firefox on your ubuntu10, after all... unless someone else comes up with some magic for you. :)

---

### Post by fbird3 on 2016-05-16
Thank you, nanotube.
I will give ff38-esr a try. What do you think?
My ff20 is still very useful. I am glad I still have it.
Thanks to you, I now know how to install and run the firefox binary.
First, I will remove ff45-esr and the profile I created for it; then, I will deal with ff38-esr.
Let's see what is in store for me now!  :D

---

### Post by fbird3 on 2016-05-17
Hi, nanotube!
I have installed ff38-esr yesterday; it was consuming a  lot of cpu and memory [at the time, I also had ff20 running on a  different profile]; so, once I had all the add-ons installed and the  browser customized to my liking, I chose to close it.
Today, I have  been running it for a few hours [solely, ff20 is taking a well deserved  break] and so far I am pleased with the results: no crashes, freezes...,  nothing I can attribute to it; cpu and memory consumption are an all  time low -- and I have 75 tabs open: it's hard to believe it is a ff  browser...! I do not want to sing praise to it too loudly yet, but I am  hopeful that it'll continue like this.
However, there is still  something I do not understand well: I tried to start it from the cli  with firefox -P, so I could choose its profile, instead of navigating to  where the binary file is located  [N.B.: there were no other instances  of ff running then, to my knowledge] and the Profile Manager opened; I  chose ff38's profile but it opened ff20! And it was consuming a lot of  cpu, rendering it practically useless; so I closed it, flushed the swap  memory, did other bits needed and then went again to the cli, but this  time I entered the command from the right directory and I even used the  option "--no-remote" for good measure! And it's been working fine since  then! I now remember what you mentioned, about having to include ff45 [at the time] in my $PATH [I think]...
Another  'however': I would like to be able to start it like other programs,  from the applications menu, instead of having a dedicated shell spewing  all sorts of [error?] messages I am not too interested in reading about  [or understanding it, it would be more honest to state]. Since ff38-esr  is doing well until now [it has been more than 3 hours...], I would like  to take the next step and get it started from the applications menu  [like I did with Ubuntuzilla's Firefox] -- but for that I need your  assistance.
Thanking you in advance.

---

### Post by fbird3 on 2016-05-19
Hi, there!
It has been over 2 days and ff38-esr keeps going fine!
True, I have gone off-line many times, but the browser remained open and continues to require minimal cpu and memory from my system.
I have never seen Firefox being so efficient.
Maybe by the end of the week I will seriously consider given ff20 its well deserved RIP banner for all the years of good service [if on the gluttonous side].
By then, I hope, I will have found another way to start it other than from the cli.

---

### Post by fbird3 on 2016-05-29
Hello, all
I have been using ff38-esr for a week or so now, and I think only once I had to terminate it because it started using too much cpu [and doing nothing!]: but it had neither frozen nor crashed during that time; so I am satisfied with it as it is.
There is only a snag regarding a particular website, but I doubt ff38-esr it is to blame [unfortunately, with no solution in sight, I have to run ff20 to the rescue to do it instead...].
I have managed to include ff38-esr in the applications menu and can now launch it like any other program there included.
May thanks to all who assisted me, em particular for nanotube's tireless patience.
All the best.

---

