---
title: "view USA website in the UK"
date: 2008-04-29
forum: General Help
---

### Post by MozBlue on 2008-04-29
I'm trying to view a website as though I was in the USA but the site has no option to change region.

I know there is a way of getting Firefox to tell the site that you are in a different country then you really are but can't find how to do it!

---

### Post by Rainstride on 2008-04-29
you could use a proxy located in the us... but what ever your doing will go through that proxy server so i wouldn't do anything involving personal info.

---

### Post by rykel on 2011-03-25
Hi, I am also looking for a solution. Some websites "see" the country IP address where I am staying in and switches the homepage to something customised for that country accordingly - without a way to view the USA pages at all! Some other websites, like Hulu and Youtube, prevent me from viewing content meant for the USA when I am in another country.

Is there a solution or software in Ubuntu Software Center that can solve all such problems?

---

### Post by flipper T on 2011-03-25
this works for many us websites, but not hulu.

have used successfully with daily show / south park / abc / cbs...


[http://www.cynicsunlimited.com/2010/03/28/using-firefox-and-modify-headers-plugin-to-view-blocked-video-streams/](http://www.cynicsunlimited.com/2010/03/28/using-firefox-and-modify-headers-plugin-to-view-blocked-video-streams/)

---

### Post by solitaire on 2011-03-25
What's the Website?
There's a few that can be fooled using "Modify Headers" plugin in Firefox
with the following settings (save it to a .json file and import via the plugin.)
```
[{"name":"X-Forwarded-For","value":"12.13.14.15","action":"Add","comment":"US Header","enabled":true}]
```

That fools sites like "Comedy Central"

---

### Post by flipper T on 2011-03-26
> What's the Website?

what ?

click the link / follow the instructions

ps im sure that accessing material in this fashion is not legal...moderators beware

---

### Post by solitaire on 2011-03-26
> **flipper T said:**
> what ?

click the link / follow the instructions

ps im sure that accessing material in this fashion is not legal...moderators beware

ermmmm

my post was directed to MozBlue...
We posted at around the same time.

---

### Post by flipper T on 2011-03-26
you are forgiven :)

---

