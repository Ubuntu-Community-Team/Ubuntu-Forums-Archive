---
title: "(Tutorial) How I fixed my firefox sound and freezing issues"
date: 2006-10-08
forum: General Help
---

### Post by wilsonisme on 2006-10-08
This thread is intended to show some easy fixes I applied to firefox to solve some of the following issues:

-Sound not playing on youtube/google video/etc
-Firefox freezing up when visiting flash sites (pretty common) and who knows what else (pretty rare)
-Firefox acting sluggish loading sites, expecially digg.

First off I do not claim to be an expert in anything and I am only showing what I did to make firefox work a lot better for **me**. With that said.... This is what I did:

Step one:
Open Synaptic and make sure you have "alsa-oss" installed. If not, install it

Step two:
Right click on your panel (where applications, places, etc is) and click "Add to panel" Now select "Custom Application Launcher"

Step three:
In the box that pops up, put "Firefox" (or whatever you want to name it) in the name. Now for the important part: In the command section, type "aoss firefox"

Step four: In the icon section, you can select the standard firefox globe icon, which by default is located at: "/usr/share/pixmaps/mozilla-firefox.png"

Step five: Go ahead and click close. *What you have just done is made a shortcut to open firefox using oss to alsa conversion. I do not know the ins and outs of this wrapper but from my extended testing, it virtually removed all sound related problems with firefox. I would assume this is because, well, Alsa>OSS :)* You may want to delete your old firefox shortcut if you have one. And also note that you will need to close any exsisting firefox windows (that were not opened using this shortcut) before using your new shortcut.

Step six: Alright you now have the annoying sound issues fixed! Now we are going to fix sluggishness, freezing, etc. Open firefox and in the URL field type "about:config"

Step seven: Scroll to the following entries:
> network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests

Step eight: Double click on network.http.pipelining in order to set the value to **true**

Step nine: Do the same for "network.http.proxy.pipelining"

Step ten: Double click on "network.http.pipelining.maxrequests" and set this value to 8.

Step eleven: Right click anywhere in the window and select **new > integer**. Name it nglayout.initialpaint.delay and set its value to 0 (zero). This value is the amount of time the browser waits before it acts on information it recieves.

Step twelve: Close firefox and open it (with your newly made link, of course) and enjoy web surfing bliss!

I hope this helps some people,
Wilson

---

### Post by gborzi on 2006-10-08
Thanks for this Howto. It is also possible to use aoss as a wrapper by changing > FIREFOX_DSP="" to > FIREFOX_DSP="aoss" in /etc/firefox/firefoxrc .

---

