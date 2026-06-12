---
title: "Lubuntu OS unable to display onto LCD display."
date: 2020-10-07
forum: General Help
---

### Post by edwin4project on 2020-10-07
Hi guys, I have encountered an issue regarding unable to display lubuntu onto my 10.1” LCD when I connect it to the HDMI of my RPi. 

However, when I connect it to the RPi containing Ubuntu mate it is able to display it perfectly.

I have tried configuring the config.txt file of the Lubuntu OS as the same like how I did for my Ubuntu Mate OS but still unable to display.

I suspect it is the different OS that is communicating with the LCD. Does anyone have any solution regarding on how can I make my LCD display Lubuntu OS when connected to the RPi?

RPi Model: 3B
Lubuntu v14
Ubuntu Mate v18
LCD 10.1” 1280*800 multicomp pro  

Data sheet for the LCD: [http://www.farnell.com/datasheets/2866021.pdf?_ga=2.198811887.1509495771.1602064750-1247098779.1602064750](http://www.farnell.com/datasheets/2866021.pdf?_ga=2.198811887.1509495771.1602064750-1247098779.1602064750)

---

### Post by guiverc on 2020-10-07
Lubuntu and Ubuntu-MATE are desktop releases, which use a *year.month* format for their releases.

Ubuntu has since 2016 used *year* (two digit) for specialist *snap* based releases intended for IoT appliances, devices plus use in the cloud. They do not have a desktop (though can run a desktop when installed as a *snap*)

The oldest Lubuntu (*and Ubuntu-MATE as well*) still supported in 18.04 LTS.

Assuming you're talking about Lubuntu 14.04 LTS (which reached EOL in 2017-April), it's got a much older software stack than Ubuntu-MATE 18.04 LTS (*assuming that's what you meant by v18*), so I'd suggest trying a later software stack on your Lubuntu too (eg. Lubuntu 18.04 LTS)

The head of Ubuntu-MATE (*Ubuntu desktop too*) created a [`desktopify` script]("https://github.com/wimpysworld/desktopify") that adds a desktop to an installed pi server image, so if images aren't available with the desktop you want, I'd suggest that.

Whilst the toolkit stacks differ between MATE & LXDE/LXQt, the biggest difference I see from your description is the four year difference in software stack age (*if's a GTK difference (MATE 18.04 is GTK3) you won't be able to fix that due to LXDE using GTK2, and LXQt using Qt5, but I doubt that's your issue*).

---

### Post by ActionParsnip on 2020-10-07
Does Lubuntu 20.04 (The latest LTS) work OK?

---

### Post by GhX6GZMB on 2020-10-07
> **ActionParsnip said:**
> Does Lubuntu 20.04 (The latest LTS) work OK?

Works wonderfully. I've been using it since May. Why?

---

