---
title: "Firefox Issues!"
date: 2013-05-01
forum: General Help
---

### Post by tycoon35 on 2013-05-01
Hello all,

I installed Ubuntu with my new 7750 GPU at last. The primary things went almost smooth for a newbie like me. Now when I am trying to make things as it would suit my requirements some little things making it harder. I must seek help about firefox here before I get mad about the issues my favourite browser causing.

1. It won't simply load some components of a site. I have tried disabling the adblock plus and once totally removed it. I have no other blocking extension/s. I have javascript enabled. Example site - [http://www.dotnxt.com](http://www.dotnxt.com), [http://www.mybloggertricks.com/](http://www.mybloggertricks.com/)

I must say that the pages are actually trying to load. But the componenents like images from Youtube(ytimg.com), Google codes(jquery, google-analytics), Twitter share image(javascript to generate the button), Disqus widgets etc. i.e. smaller components of web-pages not loading by any means. Well I have tried with fresh new profile too & yes they load flawlessly with the same profile in my windows system with same broadband connection. The fact is when I enable adblock plus and whitelist those small part sites they become visible! But the complete webpage never works as it should! Moreover I keep getting install missing plugins notification, while I can watch all flash videos and the sites I am talking about has no other video conent or java(I won't be installing java anyway). I can't even see the blogspot edit links for my posts in my own blog among other things.

2. I am habituated with using 2 instances of Firefox for many years now. So I followed atutorial and tried to make the launcher with my second profile. When I tried to initiate the 2nd firefox with the terminal(with no-follow command) it just replaced the default firefox and didn't make any separate instance! I had to use the profile manager & terminal again to get my default firefix version 20 back. Is there any full tutorial I could follow to make it work?

---

### Post by dino99 on 2013-05-01
are you using ppa(s) ?
do you do some cleaning ? (clean/autoclean/autoremove/gtkorphan/bleachbit)
do you glance at your logs ? (xsession-errors, /var/log/)

---

### Post by tycoon35 on 2013-05-01
I assume you are asking if I am using additional PPA/s. Yes I am using 2, 1 for Variety and other for VLC I guess.

Clean/Autoclean couldn't find anything to clean from my system when I ran them after reading your post.

Do you want me to look into "xsession-errors" file? It is empty and there are no such file inside /var/log/

Btw, flareget.com site don't even open partially with the current problem.

Edit: If anyone interested, I tried changing my DNS of ADSL & cleared cookies, cache several times.

---

### Post by ppjdee on 2013-05-01
> **tycoon35 said:**
> I assume you are asking if I am using additional PPA/s. Yes I am using 2, 1 for Variety and other for VLC I guess.

Clean/Autoclean couldn't find anything to clean from my system when I ran them after reading your post.

[COLOR=#ff8c00]**Do you want me to look into "xsession-errors" file? It is empty and there are no such file inside /var/log/**[/COLOR]

Btw, flareget.com site don't even open partially with the current problem.

Edit: If anyone interested, I tried changing my DNS of ADSL & cleared cookies, cache several times.

Home folder then Ctrl + H to show hidden files. It should be in there.
Have you tried running a different browser?

---

### Post by tycoon35 on 2013-05-01
> **ppjdee said:**
> Home folder then Ctrl + H to show hidden files. It should be in there.
Have you tried running a different browser?

Ahh...found it. What exactly should I look for in that error file? Seems pretty long with informations. I couldn't find anything starting with firefox inside the texts.

I haven't tried any other browser yet. Will post that info within few minutes.

---

### Post by tycoon35 on 2013-05-01
Update: Opera having the same issue. Same site/s showing same problem :/ Any suggestion about what I should do?

My hosts file -

> 127.0.0.1    localhost
127.0.1.1    User-UB13

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by tycoon35 on 2013-05-01
Update Agin: If I use pppoeconf every time, then the pages work flawlessly! But that ruins the chances of on-demand connectivity and I must keep my system connected always :/

---

