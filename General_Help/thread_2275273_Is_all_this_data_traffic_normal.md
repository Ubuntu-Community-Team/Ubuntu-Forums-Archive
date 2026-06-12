---
title: "Is all this data traffic normal?"
date: 2015-04-25
forum: General Help
---

### Post by t0p on 2015-04-25
When I turn my computer on, and run Chromium, I seem to get a lot of data traffic going on. As I pay per MB of traffic, this is a concern to me.  I've attached a couple of screenshots, showing System Monitor and netstat.  These are not unusual situations, this goes on all the time.

Do Chromium and Dropbox create this level of data traffic normally?  Is there a way to cut it down (other than uninstalling Dropbox and not running a browser)? I haven't even got a lot of files in Dropbox...

Cheers.

EDIT: After a bit more investigating, it seems that some sites in particular are responsible for the majority of the traffic.  Even though I'm not actually interacting with the site, just sitting there with the site open on my browser creates loads of traffic.  Grrr...

---

### Post by TheFu on 2015-04-25
Well - what does dropbox do? Think about it.  It has to verify that 1 bit hasn't changed in any of the files you have placed into that folder structure. How would that be done?  It has to create and compare signatures between the files - that means transferring data.

Chromium - there's a reason that it feels faster than other browsers. There is a setting that lets it pre-load web pages based on links in the current webpage - EVEN if you NEVER click the link.  That means transferring data.

You might want to start blocking ad networks and 3rd party tracking websites which use your bandwidth to sell you crap you don't want.
[http://blog.jdpfu.com/pages/hosts-for-security](http://blog.jdpfu.com/pages/hosts-for-security) (lifehacker republished this).  I don't use chromium much - but with firefox there are addons to help stop those things 
* [http://blog.jdpfu.com/pages/secure-browser-settings](http://blog.jdpfu.com/pages/secure-browser-settings) has a list

I've added **ghostery** recently in addition to blocking ad networks with an /etc/hosts file.

Plus stock Ubuntu sends queries to 3rd parties every time you enter text into the tap-box. Unless you've turned that off, amazon knows everything you type there.

---

