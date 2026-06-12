---
title: "most facebook photos dont show up"
date: 2013-05-11
forum: General Help
---

### Post by abdorefky on 2013-05-11
i have problem viewing the facebook photos on  Mozila firefox , chrome and chromium 
most of the photos and videos don't show up 
the problem sometimes effect most of the photos and sometimes some of the photos . even sometimes all photos and videos and working fine . 
this a photo for firefox and chrome . as u can see the chat photos appear on mozila while its hidden on chrome ! 

[IMG][[IMG]http://imageshack.us/a/img41/9109/facebookpicw.th.png[/IMG]]("http://imageshack.us/photo/my-images/41/facebookpicw.png/")[/IMG]

[B]edit : added video 
 [http://youtu.be/2pgsYwZn-Y8](http://youtu.be/2pgsYwZn-Y8)[/B]
i think the video explain much
this bug not really effective is the middle of the day . but from 1 am to 6 am u can't see most of photos and profile pictures , better not to log on facebook at that time :( 
after 6 am the effect vary from time to time

---

### Post by lisati on 2013-05-11
I've seen similar before when picutre seem to be missing but the browser hasn't actually loaded them yet. What's your internet connection speed like?

---

### Post by abdorefky on 2013-05-11
1 mb

---

### Post by abdorefky on 2013-05-19
i have 3 computers at home and Facebook work fine on all of them . 
its work on the virtual windows in my computer . 

what is that strange bug .  every day i suffer for some hours (90% from photos not visible  )and the other hours its working perfect or some photo's not displayed !! . 
this error come and go depend on what ?

---

### Post by abdorefky on 2013-05-22
up

---

### Post by jairoh_ on 2013-05-22
also experiencing this one in 13.04. but if i switch to windows, everything's fine w/ still the same connection.

---

### Post by abdorefky on 2013-05-22
look . its working on the Virtual windows and not working the Host which is ubuntu 
[IMG][[IMG]http://imageshack.us/a/img27/6766/facebookwv.th.png[/IMG]]("http://imageshack.us/photo/my-images/27/facebookwv.png/")[/IMG]
jairoh where do you live

---

### Post by meenfreem on 2013-05-23
I'm having the same issue for the past few days. Has there been an update of some kind? I'm also having issues with the fb notifications drop down, it shows, some links work and the red alert doesn't count down (only up for new notifications). Also games don't load... 

could it be a flash thing?

---

### Post by lisati on 2013-05-23
> **lisati said:**
> I've seen similar before when picutre seem to be missing but the browser hasn't actually loaded them yet. What's your internet connection speed like?

The reason I asked this earlier is that I have seen a similar effect on a machine at work running Windows and a flaky WiFi connection. Sometimes it takes a while for photos to load on that machine. Some sites aren't particularly good with "slower" connection speeds. Suggestions from others on how to check this out would be appreciated by myself as well.

---

### Post by HiImTye on 2013-05-23
are you using any local or web proxies?
any ad blockers?

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by meenfreem on 2013-05-23
in my case, I'm on good connections (8 to 150mb), last week everything worked just fine and now fb chat is out, clicking on the post link doesn't work and a range of other things (besides not being able to open images).
Also my youtube video pages are blank besides the video...

---

### Post by abdorefky on 2013-05-23
i dont use proxy . and no ad blocker . 
the problem on chrome chromuim and firefox .

---

### Post by abdorefky on 2013-05-25
the problems occurs in the same times every day . 
i think from 12 -- 3 AM i can't see anything . 
should i use proxy ?

---

### Post by abdorefky on 2013-05-26
now all profile photos are gone ...
what's wrong in my ubuntu !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by abdorefky on 2013-05-29
[http://youtu.be/2pgsYwZn-Y8](http://youtu.be/2pgsYwZn-Y8) 
i think this video explain much

---

### Post by abdorefky on 2013-05-30
SOLVED 
i wonder that people here doesn't have the knowledge to solve such an easy problem :(
---------------------------------------------------------------------------------------------------
a member of  Egyption facebook group which has only 5000 member , solved this problem on spot :O 
**this is the fix he told me **

send me :sudo gedit /etc/hosts
i sended :
he said add : 46.33.70.144 fbcdn-profile-a.akamaihd.net

here is the file after edit :
```
127.0.0.1    localhost
127.0.1.1    abdo-Inspiron-5520

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

46.33.70.144 fbcdn-profile-a.akamaihd.net
```

guess what ? problem solved !!!!
[B]he said its DNS problem 
but he told me this :[/B]
[B]to make this parmanent change your dns settings to google dns or your isp dns

[/B]**[http://ubuntuforums.org/showthread.php?t=2078398](http://ubuntuforums.org/showthread.php?t=2078398)**
[B]google is good enoug nameserver [8.8.8.8]("http://8.8.8.8")
nameserver [8.8.4.4 ]("http://8.8.4.4")
[/B]


but i still dont know what is this, is there a good link with photos that explain DNS or some network basics ? 
ty

---

### Post by abdorefky on 2013-05-30
[B]request to move the topic to networking and wireless 

[/B]

---

### Post by abdorefky on 2013-05-31
**request to move the topic to networking and wireless **

---

### Post by strejcr on 2014-04-18
I had this same problem last spring on Windows, but Ubuntu was working fine back then (I was using them both on the same computer). Now I'm having this issue on Ubuntu as well. I've tried your solution and it got better, but still there are some pictures that doesn't show and I have some troubles with other pages too (e.g. youtube's not working). Have you had any simillar troubles recently, or does your Ubuntu work fine now?

---

### Post by bapoumba on 2014-04-18
Any extension or plugin that would be blocking akamaihd.net ? Notscripts comes to mind.

---

### Post by strejcr on 2014-04-18
Well... I don't use any plugins or extensions... I've tried re-install chromium and this happened. (It's only with facebook and youtube, other pages works fine now).

---

### Post by bapoumba on 2014-04-18
lisati had a point earlier re: slow internet speed.
Does it also happen if you make a new user either on Chromium or Firefox ?

---

### Post by jennifer_pinto on 2014-04-18
This problem persist in two cases:
1) If internet is not fast enough to load the photos for the time, as you are saying that many times it shows it all clear.
2) Second case is of the graphics, many times graphic user interface fails to work, in our system but we couldnt notice it because it is for fraction of seconds. in your case it could be for a longer raining time thats why probably error occured.

---

