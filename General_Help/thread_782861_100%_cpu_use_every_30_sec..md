---
title: "100% cpu use every 30 sec."
date: 2008-05-05
forum: General Help
---

### Post by spudratic on 2008-05-05
ok here is what I found.my cpu doing nothing and I mean nothing every 30 seconds spikes to 100 percent for 10 seconds.this is what is causing lag and I don't know why 0r what is doing it any ideas.the system monitor is not showing the cpu use as far as what is doing it.It shows the system monitor and during the spike of cpu use the monitor is only between 50 and 60 percent in the process list and that is all it shows where is the other 40% comming from for the ten seconds every 30 seconds.I think it the kernel.any ideas any one thank you.

Edit: hardy w/intel p4 2ghz 2 gigs of ram and the 845g chipset.

---

### Post by warp99 on 2008-05-05
Open a terminal, maximize your window and type 'top'. Watch the processes to see were the spike is. Press 'q' then try killing it with 'killall <name_of_process>'.

---

### Post by spudratic on 2008-05-05
Thanks Wrap99 for the reply I just checked it with the command you gave and it reads the same shows the same programs running but I did get up dates this mourning after posting and in stalled them and rebooted and left to get some work done, something changed because now if I touch the mouse wheel in ff3.5 it flies to end of the page. its very hard to control so I have to fix this first so I can have some control over scrolling.Right now I only can get the bottom or the top of a page lol.Ounce I take care of this I'll check it like i did before kill everything that is not needed to run the os and see what is going on and post here if there still is a trouble.One last question is there an ubuntu rehab section in the forums lol I have to get away for this for a while and take a break I'm hooked bad.I keep fiddling and  fiddling when I should be doing other things roflmao.

---

### Post by spudratic on 2008-05-06
Alright the updates helped I still get a spike every 30 seconds or so but it's between 90 and 95 percent.Turns out its the system monitor. It shows 90 to 95 percent every 30 seconds.I'm just going to wait and see.they seem to be doing a good job of correcting things.ed;Thanks

---

### Post by warp99 on 2008-05-06
> **spudratic said:**
> Alright the updates helped I still get a spike every 30 seconds or so but it's between 90 and 95 percent.Turns out its the system monitor. It shows 90 to 95 percent every 30 seconds.I'm just going to wait and see.they seem to be doing a good job of correcting things.ed;Thanks
Best thing is just don't run the application until there is an update. You may want to check to see if there is a bug report and/or put in a report if needed:

[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

Just make sure you give them some detailed information before submitting: This page will show you how:

[https://help.ubuntu.com/community/reportbug?highlight=%28bugs%29%7C%28submit%29](https://help.ubuntu.com/community/reportbug?highlight=%28bugs%29%7C%28submit%29)

---

### Post by spudratic on 2008-05-07
Ok this was solved with updates.My cpu use is back to normal.the cube still lags when I switch it with the mouse wheel but hey nothing is perfect and I'm sure they will get to it.


I try not to file bug reports at this time.I really need to know more before I start putting in bug reports.I need to be sure it is the os and not me.I don't want to send it in and then have it be me lol.they have better things to do I would think.This will change I want to start beta testing when I,m ready.Thanks again.

---

