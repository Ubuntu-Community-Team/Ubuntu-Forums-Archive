---
title: "google chrome just died on me"
date: 2012-12-29
forum: General Help
---

### Post by sdowney717 on 2012-12-29
then when running in terminal,  says this
```
scott@scott-P5QC:~$ google-chrome
Segmentation fault (core dumped)
scott@scott-P5QC:~$ 

```

so why is this?

---

### Post by The Spectre on 2012-12-29
What version of Chrome are you using?

Is it a Beta or is it the Stable release?

---

### Post by sdowney717 on 2012-12-29
chrome 64 bit the stable release

---

### Post by dino99 on 2012-12-29
dont you get more usefull warnings/errors logged to help you ? maybe some conflicts with ppa's installed packages

---

### Post by sdowney717 on 2012-12-29
I was using it fine this am, then it just closed all the windows as I was using it.
I did not install anything. I will reboot later.
I am using firefox at the moment.

---

### Post by sdowney717 on 2012-12-29
Is there a chrome log to view what happened?

---

### Post by The Spectre on 2012-12-30
Did you try Re-installing Chrome?

[https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)

---

### Post by sdowney717 on 2012-12-30
I found out what happened. I had replaced memory a few days prior.
And the memory timing was not set to auto in the bios. When I reset to auto, then chrome started. However, dont know why it worked at all with it not on auto. What keyed me into bios setting was everything started to act weird and crash. Synapic apt-gtk firefox and others started to spontaneously error.

---

### Post by The Spectre on 2012-12-30
Glad to hear that you got it straitened out.

---

### Post by Magalaan on 2013-10-04
i have the same problem, google chrome today refuses to start. It was okay a couple of days ago and it never crashed. I get the same segmentation error, when starting from terminal. 

Purging and reinstalling does not help. I did
   
> sudo apt-get purge google-chrome-stable
[COLOR=#000000]sudo apt-get autoremove[/COLOR]

I reinstalled the stable from software centre, but the same problem remains. I rebooted in between, it makes no diff. 
I did nothing to the hardware, so that can not be the problem. Not did I install anything lately, except for updates. It simply refuses to run. 

I hope someone has a clue

---

### Post by Magalaan on 2013-10-04
Update:

The problem seems to be only in the 64 bit version. I installed the 32 bit version from the web and this one runs fine!
It seems to be memory related.

---

### Post by Magalaan on 2013-10-04
Update: I cheered to soon. After a good one time start, it did not want to restart. But it is giving more information now in the terminal:

> user@ubuntu:~$ google-chrome
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "atk-bridge"
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
`menu_proxy_module_load': /opt/google/chrome/chrome: undefined symbol: menu_proxy_module_load
[6160:6160:1004/141828:ERROR:browser_main_loop.cc(226)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /opt/google/chrome/chrome: undefined symbol: menu_proxy_module_load
[6160:6160:1004/141828:ERROR:browser_main_loop.cc(226)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /opt/google/chrome/chrome: undefined symbol: menu_proxy_module_load
[6160:6160:1004/141828:ERROR:browser_main_loop.cc(226)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /opt/google/chrome/chrome: undefined symbol: menu_proxy_module_load
[6160:6160:1004/141828:ERROR:browser_main_loop.cc(226)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /opt/google/chrome/chrome: undefined symbol: menu_proxy_module_load
[6160:6160:1004/141828:ERROR:browser_main_loop.cc(226)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /opt/google/chrome/chrome: undefined symbol: menu_proxy_module_load
[6160:6160:1004/141828:ERROR:browser_main_loop.cc(226)] Gtk: Failed to load type module: (null)

`menu_proxy_module_load': /opt/google/chrome/chrome: undefined symbol: menu_proxy_module_load
[6160:6160:1004/141828:ERROR:browser_main_loop.cc(226)] Gtk: Failed to load type module: (null)

--2013-10-04 14:18:28--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Herleiden van clients2.google.com (clients2.google.com)... 74.125.136.100, 74.125.136.139, 74.125.136.138, ...
Verbinding maken met clients2.google.com (clients2.google.com)|74.125.136.100|:443... verbonden.
HTTP-verzoek is verzonden; wachten op antwoord... 200 OK
Lengte: niet-opgegeven [text/html]
Wordt opgeslagen als: &#8216;/dev/fd/3&#8217;

    [<=>                                                        ] 0           --.-K/s              
Crash dump id:     [ <=>                                                       ] 16          --.-K/s   in 0s      f0ac605ea0f1e903


2013-10-04 14:18:30 (2,65 MB/s) - '&#8216;/dev/fd/3&#8217;' opgeslagen [16]

Segmentatiefout (geheugendump gemaakt)

---

### Post by tgalati4 on 2013-10-04
Is your disk drive failing?  What is the SMART status of the drive?

Normally when you get crashes without useful error messages I spend time verifying that the hardware is 100% OK.

---

### Post by Frogs Hair on 2013-10-04
My Chrome (64#)  browser updated from 29 to 30 on Tuesday. but I have noticed no changes  . Was this update installed on your system ?

---

### Post by enterdavertex on 2013-10-04
Try chromium , If it still crashed try re-installing all the library that Chrome is using.
sudo apt-get install chromium-browser

---

### Post by Magalaan on 2013-10-19
Thanks for the suggestions. My diskdrive (SSD) is fine. I use specifically chrome for a few things Firefox can not do and because it has built in flash that always works as a fallback. I have been having some problems with 13.04 maybe a result of apps I installed. I have read that fist versions of Chrome 30 had issues. I am going to do a fresh install of Ubuntu 3.10 anyway, so I am not going to bother about it for now. I reacted because I thought I had found a way around it, but thanks very much for the support. :-)

---

