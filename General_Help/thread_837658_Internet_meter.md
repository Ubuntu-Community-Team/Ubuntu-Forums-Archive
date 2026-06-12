---
title: "Internet meter"
date: 2008-06-22
forum: General Help
---

### Post by codeking on 2008-06-22
Would it be possible to get something that meters internet usage and can tell me how much bandwidth I've used in a certain amount of time?

---

### Post by brian_p on 2008-06-22
> **codeking said:**
> Would it be possible to get something that meters internet usage and can tell me how much bandwidth I've used in a certain amount of time?

mrtg?

---

### Post by windoze87 on 2008-06-22
I use gdesklets. Among many of the apps it has, one measures how much content youve downloaded during your current session. Open a terminal and type ```
sudo apt-get install gdesklets
``` it is a very small, versatile daemon. Give it a try and see how you like it.

---

### Post by ad_267 on 2008-06-22
Also you can use vnstat which works very well and does exactly this. It is command line only but I use conky to display the output.

[http://tombuntu.com/index.php/2007/08/30/traffic-monitoring-with-vnstat/](http://tombuntu.com/index.php/2007/08/30/traffic-monitoring-with-vnstat/)
[https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals](https://help.ubuntu.com/community/HowToMonitorInternetTrafficTotals)

vnstat uses no memory and just runs every 5 minutes to get data from /proc

It can show monthy, weekly, daily and hourly totals and produce graphs of hourly usage

---

### Post by codeking on 2008-06-22
I have screenlets installed, any applications for that?  Or will I have to install an entire nother widget thing?

---

### Post by ad_267 on 2008-06-22
> **codeking said:**
> I have screenlets installed, any applications for that?  Or will I have to install an entire nother widget thing?

There's this one: [http://www.gnome-look.org/content/show.php/Net+Monitor?content=72013](http://www.gnome-look.org/content/show.php/Net+Monitor?content=72013)

---

### Post by windoze87 on 2008-06-22
netmon is probably your best bet. [HTML]http://linux.softpedia.com/get/Desktop-Environment/Screenlets/Netmon-37705.shtml[/HTML] check that and see if it's to your liking.

---

### Post by waapwoop1 on 2008-06-22
I followed the gdesklets install. Now what do i do. It is installed and running, but all i have on there is a clock, calendar and quote of the day... how do i get more? like this

---

### Post by SkonesMickLoud on 2008-06-23
If you use Conky, you can add this line to it:

```
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
```

Change 'eth0' as needed.  This method only measures totals for that particular session though...

---

### Post by ad_267 on 2008-06-23
> **SkonesMickLoud said:**
> If you use Conky, you can add this line to it:

```
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
```

Change 'eth0' as needed.  This method only measures totals for that particular session though...

Yeah I really recommend conky if you want something lightweight. It is extremely versatile and can also show things like unread emails. Like I said before you can also use conky to parse the output of vnstat if you want to record your usage over a long period of time.

---

### Post by SkonesMickLoud on 2008-06-23
> **ad_267 said:**
> Like I said before you can also use conky to parse the output of vnstat if you want to record your usage over a long period of time.

How might someone go about adding that to their conky?  Can you post that line of your .conkyrc?

---

### Post by vishzilla on 2008-06-23
Its not totally necessary to parse vnstat into conky. Conky itself can show the basic info on your internet usage.

---

### Post by ad_267 on 2008-06-23
> **SkonesMickLoud said:**
> How might someone go about adding that to their conky?  Can you post that line of your .conkyrc?

I only show my daily upload and download totals but it would be easy enough to do the same sort of thing for weekly or monthly totals. This is the .conkyrc section:

```
Today:
Down: ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'} ${alignr}Up: ${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}

```

And the output looks like:
> Today:
Down: 192.91MB      Up: 16.55MB

It would be nice if it was integrated better with conky but this works for me.

> **vishzilla said:**
> Its not totally necessary to parse vnstat into conky. Conky itself can show the basic info on your internet usage.

Yeah but the conky total gets reverted to zero if you have to reboot and can only show this for one day. Vnstat lets me keep track of daily and monthly totals as I have a cap on my download limit.

Eg for a monthly total:
```
Down: ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'} ${alignr}Up: ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}

```

For weekly total:
```
This week:
Down: ${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'} ${alignr}Up: ${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}

```

If you want you can get a dump of the whole vnstat database and parse this with a script to get exactly what info you want.

---

### Post by chunchengch on 2008-06-23
I recommend Conky too, it requires much less resources than Screenlets does.

[ATTACH]75046[/ATTACH]

---

### Post by SkonesMickLoud on 2008-06-23
> **ad_267 said:**
> I only show my daily upload and download totals but it would be easy enough to do the same sort of thing for weekly or monthly totals.

<snip>



Thanks, but I think your code might be backwards.  I copypasta'd it and there is no way that I have **uploaded** 1.4Gb's today.  It's also telling me that I've only **downloaded** 41Mb's.  Also not possible.

Flipping it around makes it a bit more accurate.

---

### Post by ad_267 on 2008-06-23
> **SkonesMickLoud said:**
> Thanks, but I think your code might be backwards.  I copypasta'd it and there is no way that I have **uploaded** 1.4Gb's today.  It's also telling me that I've only **downloaded** 41Mb's.  Also not possible.

Flipping it around makes it a bit more accurate.

Whoops yeah it is backwards. Haha sorry about that. I'll edit my post.

Wow I had that wrong on my conky the whole time and I never even noticed! Don't I feel stupid haha.

---

### Post by light50 on 2008-10-24
Great thread, cheers.

---

### Post by dburnett77 on 2008-10-24
Try network monitor.  And, notice if there's interuption from outside.  This affects the total bandwidth.

from cmd line:
sudo ifconfig network_id up monitor, or similar.

In the logs, you should see correct as well as incorrect transfers.
Monitor your productivity...

---

