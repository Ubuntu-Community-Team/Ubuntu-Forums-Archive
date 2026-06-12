---
title: "upgrade to 15.04 now cant install Brother DCP-J4110DW printer"
date: 2015-05-12
forum: General Help
---

### Post by MickM on 2015-05-12
I upgraded from 14.04 to 14.10 then to 15.04 yesterday and I have been trying to install my Brother DCP - J4110DW printer, without any luck. It was installed and working both by usb and WiFi, before the 2 upgrades.
I also tried through  [http://127.0.0.1:631/](http://127.0.0.1:631/) still no luck. The driver and cups show up in Synaptic Package Manager as installed.

---

### Post by sandyd on 2015-05-12
Does
```

sudo systemctl restart cups
```
return any errors?

---

### Post by MickM on 2015-05-12
no it does not.

---

### Post by MickM on 2015-05-12
When I go through the process of installing, the printer is visible and everything seems fine. However it will not print.

---

### Post by MickM on 2015-05-13
Although I cannot print from my computer, I have found by working from my Printer touch screen I can print a PDF , jpgs and photos  using Google Drive/Cloud or One drive etc.
So I may stop worrying about printing from my PC.  
Oh! I can also scan documents from my printer to Google Drive/Cloud.  :p  Using my Brother Printer touch screen.
Oh! again,that's using WiFi  connection.:cool::P

---

### Post by plucky on 2015-05-13
Have you re-installed the drivers since the upgrade?

From a terminal ```
dpkg -l | grep -i brother
``` and post output.

I have found in the past that things change with upgrades and it is best to re-install the Brother drivers.

Good Luck

---

### Post by MickM on 2015-05-13
Hi plucky,
I did re install the drivers, however I did what you asked , thank you, I shall go and check again.

---

### Post by MickM on 2015-05-13
It seems that the drivers from Brother do not suit Lubuntu 15.05.
Due to having had to send my notebook back for repairs under guarantee, it came back with windows 8.1 re installed. So after putting up with windows for 3 weeks I re installed Lubuntu 14.04 and with little trouble I also re installed my Brother Printer. It was only after upgrading to 14.10 then 15,04 that I have had the Printer problem.
Right now I am happy that I can print via the Printer screen.

---

