---
title: "fix for internet speeds in 8.04?"
date: 2008-06-25
forum: General Help
---

### Post by dakun on 2008-06-25
every since my switch to 8.04, my browsing speeds have decreased noticably.
i have searched for fixes on this but they dont seems to help the download speeds. such fixes were tweaking firefox and disabling ipv6, both of which dont sound like they would help before i even tried them, still didnt.

is there a fix that actually works and why hasnt this been fixed earlyer as there are many people who have this same problem?

---

### Post by ajgreeny on 2008-06-25
Have you tried different config setup in FF to see if that helps?  Try the following:-

In Addressbar type about:config
In filterbar search for these and set them as shown by double clicking on them and making changes.

browser.tabs.showSingleWindowModePrefs = true

browser.xul.error_pages.enabled = true

network.dns.disableIPv6 = true

network.http.max-connections 48

network.http.max-connections-per-server 24

network.http.max-persistent-connections-per-proxy 12

network.http.max-persistent-connections-per-server 6

network.http.pipelining = true

network.http.pipelining.maxrequests 32

---

### Post by yaknowwat on 2008-06-25
There are a lot of factors that can decrease browsing speed.

Hardware:
Processor Speed
Amount Of RAM
Graphic Procession Unit
Do you have the correct drivers?

Optimization of the internet browser.
What plugins are being used. (Adobes Flash player is horribly optimized.)

What desktop environment setup do you have.

Internet speed.

---

### Post by dakun on 2008-06-26
"browser.tabs.showSingleWindowModePrefs = true" forces single instance of firefox right? also it doesnt exist on mine.
"network.dns.disableIPv6 = true" actually slows it down.

"browser.xul.error_pages.enabled = true" im unsure what this does, could you elaborate?

the rest i dont believe i need to alter because i think its already at its limit, i can only top out at 164KBs(due to both usb1 and wireless d-link)

im comparing all of my speeds to what i had on 7.10
800Mhz intel coppermine
375 ram
Nvidia geForce4

firefox 3.0 5b with noscript, cs lite, and grab and drag.
adobe flash, however doesnt load untill allowed through noscript(what do you suggest for a flash player?)

im using the xubuntu variation of ubuntu as well. im using ndis for the driver that came with the wifi and wcid as the manager because its the only way i know to connect to a wep encrypted modem.

from what ive noticed it might be assosiated with the fact that the power isnt cut off to the usb after shutdown, when i boot up with it still in there is when it has problems but i remember times when it wasnt plugged in and still had problems.

---

### Post by cariboo on 2008-06-26
Have you documented the differences, or is it just a feeling? I find that there isn't much difference between Vista and Ubuntu, if anything Firefox on Vista "**Feels**" slower with exactly the same addons, except for the windows versions of java and flash.

Xp, which is on a totally different computer, "**feels**" way slower, whether using IE7 or Firefox.

My laptop running Linux Mint with wireless "**feels**" like Firefox loads a page faster than either XP or Vista.

I think it is all subjective.

Jim

---

### Post by dakun on 2008-06-26
as much as ide like to say its subjective it isnt. ive used the timer on the extended toolbar(plugin i forgot i was using) for when i went to check my devart messages, 1:24 seconds as opposed to 7 seconds when it works fine.

i read about a guy who switched and it took him 5 min to load google.com

it seems to be fine for now but if anyone can offer a reason, it would be greatly appreciated.

---

### Post by stldirty on 2008-06-26
im having these same problems.  mostly with my broadcom wireless router.  it works fine most of the time but other times it'll just crap out and i have to wait 30 seconds before i can do anything internet-wise...

---

### Post by dakun on 2008-06-28
with further testing, i seem to have to plug in the usb AFTER login(about) for it to get good preformance. still looking for a reason.

---

### Post by Miljet on 2008-06-28
Don't know if this is at all related, but right after I upgraded to Hardy, my browser and mouse seemed really slow. I checked the System Monitor and something was maxing out my CPU. I rebooted and the problem went away. Never did find out what was working the CPU so hard.

---

### Post by maaltan on 2008-06-28
I just fought with this.  try running the following command:

sudo sysctl -w net.ipv4.tcp_{window_scaling,timestamps,sack}=0

It should effect immediately.  if not try reconnecting your network media (remove network cable, disconnect/reconnect to wireless/etc) .
  
If this totally hoses your connection for some reason, it should reset to normal with a reboot.

If this works you can make it permanent by putting that in a startup script or adding this to the end of /etc/sysctl.conf

net.ipv4.tcp_sack = 0
net.ipv4.tcp_window_scaling = 0
net.ipv4.tcp_timestamps = 0

this will fix throughput problems (try your favorite bandwidth test site before/after the change)

handshake/initial connection issues (several seconds before anything happens) is usually related to the IPV6 stuff already mentioned.

---

### Post by dizee on 2008-06-28
it might be a DNS problem.

check the output of
```
cat /etc/resolv.conf
```
if it has nameserver 192.168.1.254 or something similar your DNS servers may not be correctly configured.

---

### Post by Terrycymru on 2008-07-02
> **dizee said:**
> it might be a DNS problem.

check the output of
```
cat /etc/resolv.conf
```
if it has nameserver 192.168.1.254 or something similar your DNS servers may not be correctly configured.

Can you explain this a bit more. I get the output you described above. 192.168.1.254 is the address to my router. What needs to be changed?

---

