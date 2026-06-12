---
title: "Quick question on Adobe Flash Player and Java for browsers"
date: 2019-05-07
forum: General Help
---

### Post by radu19842 on 2019-05-07
I want to install the following : 
- Adobe flash player plugin for browsers
and
- Java plugin for browsers 
For Opera  , Firefox & Chromium
I use Xubuntu 18.04 Bionic Beaver
I searched google but are far to many ways and i need a secure , stable plugin both java and flash installed trough terminal , please help me !
Thank you and have a great evening ! :)

---

### Post by TheFu on 2019-05-07
> **radu19842 said:**
>  i need a secure , stable plugin both java and flash installed trough terminal , please help me !
Thank you and have a great evening ! :)

I don't have an answer, just warnings and suggestions for how to setup both insecure technologies should you find versions anywhere. Sorry.

There is no such thing as a _secure , stable plugin both java and flash installed._

Flash is unsupported on Linux and has multiple design flaws in the data files which prevent it from ever being secure to any reasonable level.
[https://krebsonsecurity.com/2017/08/flash-player-is-dead-long-live-flash-player/](https://krebsonsecurity.com/2017/08/flash-player-is-dead-long-live-flash-player/)

Java Applets have similar issues.  [https://krebsonsecurity.com/2016/02/good-riddance-to-oracles-java-plugin/](https://krebsonsecurity.com/2016/02/good-riddance-to-oracles-java-plugin/)

As for mitigation strategies, I would use a different browser, running inside a different, locked down, container, for flash and only flash.  I'd use a different browser for java applets.  Both would have white-lists for where they can visit, limited to only the exact, specific, websites required.  No DNS enabled.  Just the exact locations in the /etc/hosts file used by the container. Nothing else.

And I'd still be very cautious. For me, risking the security of a full system isn't worth it to have flash or java applet support. I understand that inside some businesses, this isn't an option, but both flash and Java-Applets are dead technologies and have been for more than 10 yrs.  [https://www.wired.com/2008/11/adobe-flash-on/](https://www.wired.com/2008/11/adobe-flash-on/)
> 
On Jan. 27, 2016, Oracle took a major step toward reducing the effectiveness of exploit kits and other crimeware when the company announced it was pulling the browser plugin from the next desktop version of Java – Java JRE 9.
and
> “By late 2015, many browser vendors have either removed or announced timelines for the removal of standards based plugin support, eliminating the ability to embed Flash, Silverlight, Java and other plugin based technologies,” wrote Dalibor Topic, principle product manager for Open Java Development Kit (OpenJDK).

---

### Post by radu19842 on 2019-05-08
**TheFu **thank you so much for your answers , as always you are much to kind with beginners like me , i just wanted those two plugins cause there still are Java/Adob Flash applications and games , just like JavaScrispt still runs , but i got your point and will take it in consideration , have a great day ! :)

---

### Post by TheFu on 2019-05-08
Javascript is very different from Java.
But allowing JavaScript to be run by any remote website that asks is fooling, IMHO. I only allow JS to run from places I trust.  I've stopped using some websites completely due to their abuse of JS for tracking.  My default is to block JS everywhere.

---

