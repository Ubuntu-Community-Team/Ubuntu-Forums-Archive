---
title: "Browsing &amp; dowload problems with chromium browsers only"
date: 2023-05-11
forum: General Help
---

### Post by mamillerpa on 2023-05-11
I recently developed intermittent network instability problems on a Ubuntu 20.4 workstation when using any  chromium-based browser (I've tried Chrome, Chromium and Brave). For example 

[LIST]
[*]"Your connection was interrupted. A  network change was detected.ERR_NETWORK_CHANGED". Those messages resolve  themselves after ~ 2 seconds, with the desired page refreshing. 
[*]Or  browser-based file downloads that fail. 
[/LIST]

**Neither** the "connection was  interrupted" message **or** failed downloads occur on any other computer on  my home network or on the Ubuntu workstation when using Firefox.

I have uninstalled all of those chromium based browsers, followed advice like [https://itsfoss.com/uninstall-chrome-from-ubuntu/](https://itsfoss.com/uninstall-chrome-from-ubuntu/) to tidy up, and tried reinstalling. That's doesn't resolve the problems I described.

Other network/hardware details:
[LIST]
[*]Visiting [https://www.google.com/search?channel=fs&client=ubuntu-sn&q=speedtest](https://www.google.com/search?channel=fs&client=ubuntu-sn&q=speedtest) in chrome reports ~ 270 Mbps down, ~ 11.5 Mbps up and ~ 10 ms latency. 
[*]Comcast reports my plan as "Download speed: up to 400 Mbps, Upload speed: up to 10 Mbps" 
[*]My cable modem: [https://content.abt.com/documents/48624/SB6141-US-EN.pdf](https://content.abt.com/documents/48624/SB6141-US-EN.pdf). I believe that is the limiting fact in my data rate, and I'm fine with that for now. 
[*]My router: [https://www.tp-link.com/us/home-networking/wifi-router/archer-c7/](https://www.tp-link.com/us/home-networking/wifi-router/archer-c7/) 
[*]My workstation hardware: [https://ark.intel.com/content/www/us/en/ark/products/188811/intel-nuc-10-performance-kit-nuc10i7fnh.html](https://ark.intel.com/content/www/us/en/ark/products/188811/intel-nuc-10-performance-kit-nuc10i7fnh.html) 
[*]Docking station: [https://www.cablematters.com/pc-887-133-aluminum-thunderbolt-3-dock-with-dual-4k-60hz-video-and-60w-power-delivery.aspx](https://www.cablematters.com/pc-887-133-aluminum-thunderbolt-3-dock-with-dual-4k-60hz-video-and-60w-power-delivery.aspx) 
[*]The network connection I have been using most consistently with the NUC over the past two years is via USB-C to my docking station, with an Ethernet cable to the router. 
[*]I have also tried WiFi from the NUC to the router and WiFi from the NUC to my cell phone's hotspot. The chromium browsing/downloading problems occur in all of those configurations. 
[*]I am not experiencing the "connection was interrupted" message on any of my other devices, which are all on WiFi from the same router 
[/LIST]

---

### Post by mamillerpa on 2023-05-11
I don't have any problem browsing or downloading with Chromium when I boot from a Ubuntu 22.04 USB drive

---

