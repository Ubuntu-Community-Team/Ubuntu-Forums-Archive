---
title: "Wifi Problem"
date: 2012-11-27
forum: General Help
---

### Post by Robbobden on 2012-11-27
Ubuntu 12.04 - Dell Mini9 running from a thumb drive...

I autoconnect to the Internet at startup, but I like to disable my wifi connection to conserve battery when I'm working on the PC offline.  When I go to disable, often I don't get the SSID list when I click the connection icon so I can't do this.  What shows up is just the bottom of the drop-down.  See the 1st attachment.  What I want to see displayed (and what is normal) is shown in the 2nd attachment.  Disabling/enabling networking or the wireless doesn't work.  Sometimes I can wait a bit and it'll appear or sometimes never.  I have to restart and it happens again often.  Is there a file or script I could run in terminal to get the WiFi list of SSIDs to display when this happens? Maybe a delay is needed in some script ?  I know I had to insert delays in my Conky scripts to get them to run at startup.

Thanks !
RDL

---

### Post by Y^2om&amp;#7sgP on 2012-11-27
I get a similar issue with Xub 12.04.  Sometimes the wifi just doesn't seem to connect, check connections and find there are none.  If I disable the wifi, count to 5 then re-enable, it works fine.

In fact I also get the same problem on my desktop, which is connected directly to my router, so not sure that this is a wifi error as such.

---

### Post by NikTh on 2012-11-27
Hey @Robbobden , nice conky :) 

This is a delay (I think) , can happen due to network-manager. Happens to me also sometimes, but after few seconds works as it should. If you want to disable WiFi I believe your best option is from hardware switch (at my Laptop is Fn+F3) and WiFi is "dead" in seconds.

As for the command you asked (about scan ESSID) try this 
```
iwlist scanning
``` this will return you SSID and some additional info.
If you want the full range results use the same command with "sudo" prefix.

Thanks

---

### Post by Robbobden on 2012-11-27
Ok, disabling networking, waiting a few seconds, then re-enabling works.   Thanks ! hattpa.  I'll mark this [solved] but I'll keep digging for a better way and post here if I find something.

RDL

---

