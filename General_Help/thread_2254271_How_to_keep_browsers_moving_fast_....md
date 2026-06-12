---
title: "How to keep browsers moving fast ..."
date: 2014-11-26
forum: General Help
---

### Post by shantiq on 2014-11-26
...    once you have had an install for a while


having used Ubuntu since 2009 on different versions i have noticed that when you have a fresh install   all the browsers perform very fast loading time of pages is minimal
but after a while it all slows down a lot



So my question is:    how can one retain the earlier page load-up times.    is is possible/?     what slows it all down/?

I use chromium-browser as my main so i am looking for advice with this one;    but i also have firefox installed and same issue there


so far i have done this:


flushed the chromium cache


and now opening it with this line


```
chromium-browser --disk-cache-dir=/tmp/cache

```


as it then does not keep the cache for the next time

what else can one do?      it seems to be system wide anyway



all clever suggestions welcome   thanx

---

### Post by ajgreeny on 2014-11-26
Have you added some extensions that may be causing delays?

Is it just the first cold load of the browser that is slow, or does it remain slow to start even after a previous opening during a session?

---

### Post by shantiq on 2014-11-26
no nothing new aj  

i have" Instant Translate "   and ""SingleFile"  as my only 2 add-ons   i shall disable them and test

Ok   no that does not seem to impact

---

### Post by pqwoerituytrueiwoq on 2014-11-26
there is another browser you can try
[http://www.phoronix.com/scan.php?page=news_item&px=MTg0MDk](http://www.phoronix.com/scan.php?page=news_item&px=MTg0MDk)

---

### Post by shantiq on 2014-11-26
thanx pq and will take a look .     really my quest here is to return chromium to the pristine state :}   if possible and also to understand why it does  perform less well as time goes by regarding page-loading time


edit     ok so tried [otter-browser]("http://sourceforge.net/projects/otter-browser/files/otter-browser-weekly43/")   all brand new and the speed of load-up s sharp and fast like chromium was on first install

why does it lose that with time;   there must be reasons here and elements which can be retuned.   anyone knows?    thanx

---

### Post by pqwoerituytrueiwoq on 2014-11-26
cookies, history, cache, etc. (memory leeks)

you could delete chrome's data ~/.config/chromium

---

### Post by shantiq on 2014-11-27
ok pq and thanx    starting to understand that the reason it is fast when pristine is the fact that there is no history no bookmarks no cache no stored data whatsoever    as installing otter-chromium proved    AS FAST AS chromium was when it first was installed on new OS
so there is a built-in situation here where it WILL slow down as one starts to use the browser  and that is UNAVOIDABLE it seems
i do no wish to delete all my history and bookmarks;    so the solution is to use new browsers from time to time for fast load-up time and use the main one for things which are not urgent   ie when i am not impatient   ::]]    will mark this as solved

---

### Post by Impavidus on 2014-11-27
So there is a built-in situation where household waste will accumulate as one starts living in the house and that is unavoidable it seems. I don't want to throw away my furniture, so the solution is to rent an additional home and change that from time to time, so I can use it if I don't want to spend a long time searching for my houshold items, and return to my original home when I'm not in a hurry and want to use my furniture.

Bookmarks don't accumulate automatically, cache can be limited and cleared, cookies can be removed (I set firefox to automatically remove cookies, with a few exceptions, when I close the session), history can be deleted. Move the things from your history that you want to keep to your bookmarks, but don't overdo it. Remove bookmarks you no longer need. I've never seen any significant slowdown over the course of a few years.

---

### Post by shantiq on 2014-11-27
ok interesting    so basically clutter

although   i have removed **ALL my chromium cache AND all data for chromium**  [just kept preferences and bookmarks]    and still not the pristine state    i get in say this otter browser i installed yesterday
it is still in comparison much slower from say 1 second to load my gmail on this newly installed browser to 20 seconds on "cleaned" chromium

[ATTACH=CONFIG]258237[/ATTACH]


so i still do not see how this is rigged up

adding to the fact that now i open with  ```
[COLOR=#000000][FONT=Ubuntu Mono]chromium-browser --disk-cache-dir=/tmp/cache[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono] so NO cache ever kept from now on   but not back to pristine and slower than it once was



ps   on otter-browser

cache not being kept can also be done



[/FONT][/COLOR]```
otter-browser --cache /tmp/cache
```
[COLOR=#000000][FONT=Ubuntu Mono]

[B]probably worth doing on all browsers
[/B]


[/FONT][/COLOR]

---

### Post by dragonfly41 on 2014-11-27
I'm not too familiar with Chrome although I do have it installed.

But in Firefox 33 under Help > Firefox Health Report > Vital Stats I can see a timeline of crashes etc. 

Also I have a session manager add-on which allows me to go to stripped back session (sans add-ons, bookmarks etc.).

---

### Post by vasa1 on 2014-11-27
Chrome, and I'm assuming Chromium as well, allows you to create a new user with a new profile very easily under Settings, People. That should be the equivalent of a clean slate. No bookmarks, no preferences. If that gives you improved performance, you'll know the slowdown is due to your bookmarks or preferences.

---

### Post by shantiq on 2014-11-28
Thank you Vasa   it seems it shaves a second or two.    Did not know this was there :]

---

### Post by pqwoerituytrueiwoq on 2014-11-28
so is op using wifi and a 5400 rpm 2.5" HDD

op why not go into your browser settings and disable 3ed party cookies, install adblock, and install no script
that is what i do in ff and have been using the same ff profile for years
yes browser startup time can be slow, but i have over 100 tabs

---

### Post by Mike_Walsh on 2014-11-28
> **shantiq said:**
>  i have noticed that when you have a fresh install   all the browsers perform very fast loading time of pages is minimal
but after a while it all slows down a lot



So my question is:    how can one retain the earlier page load-up times.    is is possible/?     what slows it all down/?

I use chromium-browser as my main so i am looking for advice with this one;    but i also have firefox installed and same issue there




Hi, shantiq.

If you like Chrome, and snappy response times.....and don't mind a bit of experimenting; why not try what I've done?

I use Ubuntu 14.04 as my main OS on my old Compaq Presario desktop. However, I'm also running the latest version of Puppy Linux ('Tahrpup' 6.0) from a USB flash drive. Chrome is very easy to install from Puppy's own 'Quickpet' repos; and it FLIES...seriously.

The main reason for all this speed is that Puppy is so small it doesn't take up very much space at all. The whole thing decompresses into RAM at bootup, and occupies maybe 250 MB, tops. The entire OS and all its apps sit in RAM all the time it's up and running.....and you must know how fast RAM itself is compared to a spinner; it's on a par with an SSD. So you have a very responsive system.

The only downside to this is that you're not getting the very latest version of Chrome. Puppy uses version 32, which was just on the way out when I first switched to Linux back in May. But by some arrangement with the powers-that-be, it's still supported, and gets regular updates, just like the current versions.

This is because the Puppy devs always look for the most lightweight apps they can find, to keep the footprint as small as possible. Chrome, as you know, has included 'sandboxing' for quite a while now.....and this adds a LOT of 'bulk' to the browser.

Just a suggestion, that's all!

Regards,

Mike. ;)

---

### Post by shantiq on 2014-11-28
thanx guys    all excellent info will try as many of those suggestions as feasible ::]]    love the community for this reason  ...   Teach a Man to Fish Attitude

---

### Post by Mike_Walsh on 2014-11-28
@shantiq:-

UPDATE: Have now discovered that Chromium 38 (with pepperflash included) is available as a download for Tahrpup from here:-

[http://sourceforge.net/projects/lxpup/files/Other/chromium_38.0.2125.111%2Bpepper_15.0.0.189_lx.sfs/download](http://sourceforge.net/projects/lxpup/files/Other/chromium_38.0.2125.111%2Bpepper_15.0.0.189_lx.sfs/download)

Just as fast, since the Puppy devs always look at packages they've selected (more so with Chromium than Google Chrome, because Chromium IS open-source), in order to see where they can 'trim the fat' from the coding.

Regards,

Mike.

---

### Post by shantiq on 2014-11-30
hilarious fact about using [Otter]("http://sourceforge.net/projects/otter-browser/files/otter-browser-weekly43/")  which has been **insane fast so far** [thank you pqwoerituytrueiwoq] is that it gives this message when using gmail      it thinks i am on a mac :]

[IMG]http://s20.postimg.org/a3gh1lgnx/safari.png[/IMG]

otter has also got this amazing function to save even more time    enter u   in your url box    and you are in the forum in a second or less    niiiiice

[IMG]http://s20.postimg.org/gtafxp1ul/shortcut.png[/IMG]

---

### Post by Bucky Ball on 2014-11-30
> **pqwoerituytrueiwoq said:**
> ... go into your browser settings and disable 3ed party cookies, install adblock, and install no script
that is what i do in ff and have been using the same ff profile for years ...

+1. Me too. 

@op: Also, use a search engine that is not going to slow things down too much, something like [duckduckgo]("https://duckduckgo.com/"), for instance, "The search engine that doesn't track you."

You can configure a duckduckgo settings profile and save it 'in the cloud' which allows you to use your profile with that browser on any computer. Neat. ;)

---

### Post by mörgæs on 2014-11-30
Here are some ideas to speed up a system. Browsers including plugins are some of the heaviest applications and they often trigger a lot of hard disk activity.

[http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289](http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289)

---

### Post by shantiq on 2014-11-30
> [COLOR=#000000]Browsers including plugins are some of the heaviest applications and they often trigger a lot of hard disk activity.[/COLOR]


interesting!

---

