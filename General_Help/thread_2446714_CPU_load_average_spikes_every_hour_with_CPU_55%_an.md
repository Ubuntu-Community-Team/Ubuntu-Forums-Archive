---
title: "CPU load average spikes every hour with CPU 55% and memory 82% only"
date: 2020-07-05
forum: General Help
---

### Post by azinity-tom on 2020-07-05
Our Digital Ocean droplet's CPU load average spikes every 1-1.5 hour. Here is the the [performance graph]("https://i.stack.imgur.com/Qgudh.jpg") for the past 24 hours. 

Here are some [MySQL error logs for 1.5 hours (one cycle) as well as syslog for 1.5 hours (one cycle)]("https://pastebin.com/UeRSVBmi").

Some folks commented that "our mysql instance is being killed regularly by Linux&#8217;s OOM (out of memory) killer. You should review the load consumed by the resources running on the server. Based on experience it&#8217;s usually down to a greedy query that causes a resource contention and makes Linux sacrifice the most expensive process."

However, if you look at the [syslog]("https://pastebin.com/3CCqp8Fi"), it is because there were a bunch of apache child processes running which crashed mysql. These apache child processes killed the process! They run every 1-1.5 hours! We don't have any cron jobs.

Besides, if you look at the performance graph, even when the cpu load average (1 min) peaks at 20.71, the cpu hit 46.47% only and the memory hit 53%. The highest cpu and memory have never exceeded 57.5% and 88% respectively.

I found many related threads on Google but they don't seem make any sense in my case including using swap, limiting apache child processes, etc. For instance, limiting apache child processes is just fire fighting. We got to find out the crux of the problem which is why there are so many apache child processes running in the first place which only cropped up about 10 days ago.

Also, here is the [htop log]("https://pastebin.com/vFVfRjmj") when the sites were momentarily down. Both cores shot up to 100% momentarily but the CPU stayed below 50%.

Any idea will be very much appreciated!!

Thanks a lot!

BR, Tom

---

### Post by TheFu on 2020-07-05
i am clueless but looks like something happens every 60 minutes.  Does mysql recreate any views every 60 minutes?
Have you considered taking a backup over to MariaDB and seeing if the problem follows??

---

### Post by QIII on 2020-07-05
Hello!

Please use the default font and color unless there is a pressing need to draw attention to a specific part of our post for clarity.

---

### Post by Doug S on 2020-07-05
Readers, F.Y.I.: also posted on [askubuntu]("https://askubuntu.com/questions/1256548/cpu-load-average-spikes-every-hour-with-cpu-55-and-memory-82-only")

---

### Post by azinity-tom on 2020-07-06
hi there,

thank you for your comment. were you talking about the links which are in orange color or something else? sorry, i'm new here so i don't know much about the forums' rules and regulations. apologies.

br,
tom

---

### Post by azinity-tom on 2020-07-06
hi thefu, 

thanks for your suggestion! 

but it doesn't sound like a very good option at this point because we got 31 websites sitting on this DO droplet and many of the domain names are not even managed by us.

br,
tom

---

### Post by coffeecat on 2020-07-06
Welcome to the forum!

> **azinity-tom said:**
> thank you for your comment. were you talking about the links which are in orange color or something else? sorry, i'm new here so i don't know much about the forums' rules and regulations. apologies.

QIII was not referring to the hyperlinks, but the fact that you added a mass of BBCode rendering your first post in a difficult to read grey colour.

[COLOR=#8B8A8A][font=Arial]This was what it looked like. [/font][/color]

You also changed the font to Arial. That is a lesser problem, but unnecessary as the forum software defaults to a very clear font, and defaults to back text. As QIII says, please do not use non-standard font/colour/size/attribute formatting unless you need to highlight something.

---

### Post by azinity-tom on 2020-07-06
hi doug s,

thanks for your comment. 

first, no one from DO support replied to me even after i had opened two tickets. then i got some [comments from the DO community]("https://www.digitalocean.com/community/questions/why-cpu-load-average-spikes-every-1-1-5-hour") but i still can't figure out why so many apache child processes were running and killing mysql. it's been almost two weeks since this problem first cropped up so i've become so desperate to get this fixed.

any suggestions would be highly appreciated!

br,
tom

---

### Post by azinity-tom on 2020-07-06
hi coffeecat!

thank you so much for pointing me to the right guides.

it was probably because i just cut and pasted the content directly from the DO community website which carried the code forward. i should have hit the "remove format" button. once again, thank you for the reminder. have a good one.

br,
tom

---

### Post by Doug S on 2020-07-06
> **azinity-tom said:**
> hi doug s,

thanks for your comment. 

first, no one from DO support replied to me even after i had opened two tickets. then i got some [comments from the DO community]("https://www.digitalocean.com/community/questions/why-cpu-load-average-spikes-every-1-1-5-hour") but i still can't figure out why so many apache child processes were running and killing mysql. it's been almost two weeks since this problem first cropped up so i've become so desperate to get this fixed.

any suggestions would be highly appreciated!

br,
tomI simply wanted to make readers on both forums aware of the other posting so they wouldn't waste time if one or the other was making progress on your issue.

---

### Post by TheFu on 2020-07-06
> **azinity-tom said:**
> hi thefu, 

thanks for your suggestion! 

but it doesn't sound like a very good option at this point because we got 31 websites sitting on this DO droplet and many of the domain names are not even managed by us.

What do domainnames have to do with this?  Changing 1 line in 31 apache confs (the virtual domain name) wouldn't alter anything.
The point is to simplify and test.  And keep simplifying and testing until the root cause of the issue become clear.  I'd rather not have a 100 guesses game, but it is your system.

---

### Post by azinity-tom on 2020-07-06
hi doug s, thanks for the note.

i got [a tip from someone on unix.com community forum]("https://community.unix.com/t/cpu-load-average-spikes-every-hour-with-cpu-55-and-memory-82-only/379113/7") who suggested some very aggressive, rogue, unidentified bots originating on Chinese networks! however, i don't find anything malicious or anomalous in the second session where the cpu load spiked and mysql was killed. am i missing something?? any idea?

br,
tom

---

### Post by azinity-tom on 2020-07-06
hi thefu,

oh! sorry i misread that! 

migrating from mysql to mariadb takes time! i don't know if this is the route i want to take at this point.

if the spike is due to malicious bots, migration to mariadb won't help, will it?

br
tom

---

### Post by Doug S on 2020-07-06
I looked at the link you provided. All I can say is that this is an excerpt from my iptables rules set:

```
# Enough already. Just disallow the entire 185.0.0.0 sub-net
$IPTABLES -A INPUT -i $EXTIF -s 185.0.0.0/8 -d $UNIVERSE -j DROP
```Which isn't China, by the way. I block all of China using ipset.

And here are my packet/byte counts:

```
   27621  1283626 DROP       all  --  enp4s0 *       185.0.0.0/8          0.0.0.0/0
```So, 27,621 attempts to create a session. My uptime is significant though, probably 1000 tries per day average. (and my site is just a pathetic little thing of no significance to anyone.)

By the way, you got some really good advice over on that other forum. Just so you know, my iptables rules set has evolved over a period of well over a decade.

---

### Post by azinity-tom on 2020-07-09
Hey Doug,

Thanks for sharing your invaluable experience with me. We ran some scripts on the server and came up with a summary of the activities as below.

As far as IPs, we have offices in Norway, UK, HK, and China so some of those IPs are our IPs. Our China office uses VPN which means their IPs vary from time to time. So how can we find out which IPs from China are malicious? Shall we block those IPs?

Any suggestion will be highly appreciated. Thank you so much in advance.

P.S. We have yet to fix the mysterious hourly CPU load spike which cripples our 31 websites for almost a minute every hour!!



Top 20 GET requests:
76   GET  /wp-content/themes/bridge/css/style_dynamic_responsive_callback.php
80   GET  /wp-includes/js/jquery/ui/tabs.min.js
81   GET  /wp-includes/js/comment-reply.min.js
83   GET  /wp-includes/js/jquery/ui/accordion.min.js
83   GET  /wp-includes/js/jquery/ui/sortable.min.js
84   GET  /wp-includes/js/jquery/ui/core.min.js
84   GET  /wp-includes/js/jquery/ui/widget.min.js
85   GET  /wp-includes/js/jquery/ui/mouse.min.js
88   GET  /wp-includes/css/dist/block-library/style.min.css
92   GET  /wp-content/uploads/2014/05/logo_urban.png
93   GET  /wp-includes/js/wp-emoji-release.min.js
107  GET  /wp-content/plugins/contact-form-7/includes/css/styles.css
116  GET  /wp-includes/js/wp-embed.min.js
122  GET  /wp-includes/js/jquery/jquery-migrate.min.js
125  GET  /wp-content/plugins/contact-form-7/includes/js/scripts.js
126  GET  /wp-includes/js/jquery/jquery.js
308  GET  /wp-json/yoast/v1/prominent_words
396  GET  /robots.txt
574  GET  /wp-login.php
663  GET  /

Most Recent top 20 GET requests:
2   GET  /wp-content/plugins/cssigniter-shortcodes/src/fonts/fontawesome-webfont.woff2
2   GET  /wp-content/plugins/cssigniter-shortcodes/src/js/jquery.flexslider.js
2   GET  /wp-content/themes/technico/js/superfish.js
2   GET  /wp-includes/js/jquery/jquery.js
2   GET  /wp-includes/js/jquery/jquery-migrate.min.js
2   GET  /wp-includes/js/wp-embed.min.js
2   GET  /wp-json/oembed/1.0/embed
2   GET  ///wp-json/wp/v2/users/
2   GET  /zh-hant/
2   GET  /zh-hant/%E6%B2%96%E5%A3%93%E6%A9%9F/
3   GET  /contact/
3   GET  /dev/wp-admin/
3   GET  //install/
3   GET  /reborny/about/
4   GET  /&nbsp
4   GET  /website-design-service-blog/&nbsp
12  GET  /southchinastring/
25  GET  /wp-login.php
50  GET  /robots.txt
74  GET  /

Top 20 POST requests for:
4     POST  /wp-json/contact-form-7/v1/contact-forms/5/feedback
4     POST  //wp-login.php
5     POST  //cate/dangdouqiao.ASp
5     POST  //xmlrpc.php
6     POST  /wp-admin/update-core.php
6     POST  /zh-hant/
8     POST  /hotcrafthobby/
16    POST  /wp-admin/post.php
16    POST  /wp-json/wp/v2/posts/4426
18    POST  /wp-json/yoast/v1/prominent_words_link/4426
54    POST  /wp-content/plugins/wp-phpmyadmin-extension/lib/phpMyAdmin_1JjuZITe0KGPznkN9D6l5dX/error_report.php
65    POST  /southchinastring/wp-login.php
77    POST  /
99    POST  /hotcrafthobby/wp-cron.php
163   POST  /hotcrafthobby/wp-admin/admin-ajax.php
227   POST  /wp-json/wp/v2/yst_prominent_words
535   POST  /xmlrpc.php
575   POST  /wp-login.php
1359  POST  /wp-cron.php
1925  POST  /wp-admin/admin-ajax.php

Most Recent top 20 POST requests:
1    POST  /assets/images/blackhat.php
1    POST  /components/com_jce/editor/tiny_mce/plugins/imgmanager_ext/classes/image/imagick.php
1    POST  /contact/
1    POST  /error-logs.php
1    POST  /wp-admin/includes/lock46.php
1    POST  /wp-content/plugins/way2register.php
1    POST  /wp-json/contact-form-7/v1/contact-forms/5/feedback
1    POST  /wp-json/contact-form-7/v1/contact-forms/9/feedback
2    POST  /
2    POST  //cbvvc/mupiaowen.asp
2    POST  /hotcrafthobby/wp-cron.php
2    POST  /zh-hant/
15   POST  /xmlrpc.php
20   POST  /wp-login.php
65   POST  /southchinastring/wp-login.php
109  POST  /wp-cron.php
217  POST  /wp-admin/admin-ajax.php

Top 20 IP addresses that have been accessing your site:
Do you want geo location check for the IPs? [yes/no]
yes
3948    84.202.100.14    Norway
1311    139.59.96.33    Singapore
995    222.79.50.74    China
837    110.167.93.145    China
772    124.235.138.14    China
722    223.166.74.9    China
682    113.128.105.94    China
628    27.211.56.183    China
556    1.30.28.77    China
549    222.94.212.104    China
543    58.244.10.241    China
488    185.69.144.24    United Kingdom
445    222.94.195.46    China
432    121.57.12.85    China
361    121.57.229.55    China
294    113.128.105.226    China
283    114.33.16.191    Taiwan
251    61.238.142.146    Hong Kong
230    210.3.196.182    Hong Kong

Most Recent top 20 IP addresses:
185    84.202.100.14    Norway
104    139.59.96.33    Singapore
87    62.210.143.10    France
73    183.89.212.199    Thailand
69    36.237.55.63    Taiwan
59    180.215.255.141    India
31    110.235.33.135    India
16    77.75.77.101    Czech Republic
13    216.244.66.226    United States
10    34.73.85.242    United States
7    77.88.5.176    Russian Federation
6    199.58.86.211    United States
5    35.231.80.6    United States
5    216.244.66.230    United States
5    193.106.30.99    Ukraine
4    66.249.65.134    United States
4    64.202.185.246    United States
4    62.84.58.177    Kazakhstan
4    46.229.168.163    United States[FONT=Verdana]
[/FONT]

---

### Post by Doug S on 2020-07-09
> **azinity-tom said:**
> So how can we find out which IPs from China are malicious? Shall we block those IPs?My input here is exactly the same as you got from ["Neo" on that other thread]("https://community.unix.com/t/cpu-load-average-spikes-every-hour-with-cpu-55-and-memory-82-only/379113/15"). I get the impression that you are looking for a short cut, but I am not aware of one. This stuff takes a lot of time and effort.

---

### Post by TheFu on 2020-07-09
A few things to consider ...

Why let any non-corporate user access /wp-admin/ on any request?
Client requests to places they shouldn't go shouldn't be allowed. 
if you aren't using WP at all, then any request to /wp-* should immediately be added to a block list.  Tools like fail2ban can do that.
Subnets that aren't for the company or clients shouldn't be allowed at all.

Have you enabled micro-caching at all?  95% of all requests should be for read-only data, so a delay of 2 seconds wouldn't matter at all, but it will drastically reduce the server and DBMS load.

if your droplet is small perhaps spending $10/month more would make this issue go away. That is certainly cheaper than a highly paid developer wasting too much time on the problem.  Or splitting the front-end from the DBMS?

BTW, my 20 or so websites block over 8K subnets due to abuses.  I'm pretty quick to block entire /8 networks from countries we don't do business inside.  I also block a bunch of vps providers because they've become hideouts for illegal activities.  I don't really care if some bot can't scan my sites. Blocking bots is part of what the reverse-proxy does.

---

