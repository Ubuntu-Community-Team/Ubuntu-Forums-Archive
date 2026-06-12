---
title: "Freezes up"
date: 2013-03-24
forum: General Help
---

### Post by JimS on 2013-03-24
Ubuntu 12.04, Gnome Classic, Home built pc, AMD 2-core, 16GB RAM.

When I start Firefox and then Software Manager,
one of the CPUs goes to 100%, then settles down.
But, if I type a letter in the Software Mgr's Search box,
one of the CPUs will go back up to 100%,
and stays around 98, 99, and 100%.
The pc freezes up.
Then I can't type a 2nd letter.
I can't quit Software Manager normally.
If I'm running full screen, I have to cut power.
I have tested this several times with the same bad results.

My conky shows the above CPU figures.
But Task Manager gives no clue and shows minimal CPU useage.

I never had this issue running Ubuntu 10.04 LST.
But I had this happened with Zorin OS 6.1 and Mint 13 xfce also.
So I think this is a basic Ubuntu issue and not my hardware.

Suggestions.
...

---

### Post by JimS on 2013-03-29
...
Strange that noone seems to be able to comment!

I will not use Software Mgr when I'm using Firefox.
I don't like that solution.
Avoiding the problem, doesn't fix the problem.
...

---

### Post by maglinu on 2013-03-29
I can only comment that it doesn't happen here on a much lower spec machine. I'n running Unity desktop though.

(I've assumed you meant Ubuntu Software Centre by 'Software Mgr'?)

---

### Post by Jay_E on 2013-03-29
Hi Jim,
I'm just another user...
When the freeze happens, give it 3 or more minutes before resetting/unplugging. (see if kernel detect timeout.)
Note the time.
After restart take a look in the logs for a telltale

like:
cd /var/log
sudo  more syslog

have you used 'more'? there is a search command. use it to get near (slightly before)
your time of crash/hang

a suspicious entry is like:
syslog:Mar 29 08:43:59     ((( name of your pc )))   : [47688.853517] INFO: task Xorg:1211 blocked for more than 120 seconds.

what all was going on?

go from there.

Have fun,
Jay

---

### Post by JimS on 2013-04-03
...
Jay  Thanks for the reply.
I had another hang up yesterday
No Software Mgr involvement this time.
All I was doing was running TorGuard and Firefox.
On FF I was watching a video of a TV show from another country, (normally blocked to outsiders like me).
I was running the video show full screen, so I didn't see my conky display CPU readings.
I forgot to follow your advise.
Hopefully next time I'll remember.
This old dog's memory has never been the best.
Thanks again.
...

---

