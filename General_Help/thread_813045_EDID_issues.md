---
title: "EDID issues"
date: 2008-05-30
forum: General Help
---

### Post by reiki on 2008-05-30
EDID issues

First off I have no idea where would be the "proper" place to post this so it's here...

MANY MANY people are having issues with their monitors not being properly detected. This is not confined to Ubuntu. It's happening in other distros too. I am writing this as an nvidia user, but this does not appear to be strictly confined to nvidia either. 

I have researched this all over the net for several days. In summary, the scenario goes something like this:

"I can't get my monitor above 640x480. The higher resolutions aren't available in screens and resolution."

"Try using read-edid. I bet you have bad EDID data from your monitor"

"Ok I got read-edid installed. I ran get-edid |parse-edid and it tells me the data is corrupt!"

"Yup... your monitor is outputting bad EDID. You need to do *this* to work around it."

OK, stop scenario. *this* usually equates to using a hex editor on your EDID data because it apparently has a bad checksum after somehow extracting it with phoenix edid editor running under wine or.... it goes on and on.

I did all of these things. Using ddcprobe the final line is "edidfail:". I checked into DVI cabling and what pins are carrying the DDC between graphics card and monitor... all kinds of stuff. I had the *gasp!* corrupt EDID on my monitor too!

Ok so this isn't confined to one monitor, one manufacturer, nothing. Does anyone else have a problem with the assumption that ALL OF THESE monitors from a variety of manufacturers have bad EDID data?

Guess what. They DON'T.  Last night I started nvidia-settings and used the "Acquire EDID" button it provides. Well... it retrieved EDID from my monitor just fine. Did it really?  So I ran parse-edid on that file the nvidia-settings retrieved and created.

parse-edid<edid.bin

Lo and behold it parses absolutely fine! There's nothing wrong with my monitor's EDID data after all. Huzzah!

It seems get-edid doesn't handle the newer EDID version 1.3 data sets correctly. My monitor is using EDID 1.3. It says so in the EDID data. 

What I **DON'T** know is what mechanism is being used to read EDID from the monitor when it's being detected. I am assuming it's not get-edid because that's not included with a default installation. 

This issue has also been blamed on the nvidia restricted drivers. I don't know yet if they play a part in this. This weekend I'm going to do another clean install and test if EDID retrieval works on a default install. In other words... can xorg properly detect my monitor in the default install without restricted drivers being there to take the blame?

My guess is that whatever mechanism is reading EDID for monitor detection, has not been updated to handle EDID 1.3 data. this would explain the LARGE number of different monitors having this issue.

The lack of official help on this is astounding. I paged through many bug reports and almost all of them blame the drivers, blame the monitor for having corrupt EDID data responses, suggest that the user has bad cabling... and more.

EDID 1.3 has different header bytes than EDID 1.2 and previous. I am REALLY beginning to suspect the problem lies in the detection tools, and not the data.

---

### Post by mtbdrew on 2009-08-25
Hello,

I believe you are on to the heart of the issue here. I am seeing the same issue with two different manufactures (Samsung and Vizio) LCD TVs. BTW no the default driver doesn't work either.
Also interestingly the new Nvidia driver that comes with 9.04 (180.44) fixes the issue over RGB connections but the issue is still there with HDMI/DVI connections. 
Many work around this issue by using the CustomEDID option in the xorg.conf to assign a EDID file which has been captured from the TV using Phoenix or Viewsonic's EDID tools.

It sure would be nice to see this correct but as you say, can't seem to get any support on this even though there are loads of post on the web regarding this issue.

---

### Post by P4man on 2009-08-25
FWIW, i just tried get-edid on my monitor. It ends with "Your EDID is probably invalid.". The restricted nvidia driver recognizes it just fine. As does the "nv" driver btw. At least they both set the correct 1440x900 resolution.

---

### Post by rayj on 2009-08-25
I'm wrestling with this as well. It doesn't help that I'm basically a linux newbie...

Upon a fresh install, I tried to install the latest stable drivers. Nvidia-xconfig doesn't seem to be able to grab my EDIDs. I'm still learning, and still playing with it, but even editing xorg.conf doesn't seem to take. The software prompts me to 'fix my issues', and I end up not being able to get a refresh rate above 60hz. This wasn't the case in my earlier setup, with all the same hardware.

---

### Post by raoulmaher on 2011-07-05
Funnily enough I personally would have to possibly agree, as I have a fairly new LG TV connected to my laptop with a HDMI cable HDMI to HDMI only

1. On install ( Natty )  both laptop and TV echo identical screens, so it can be done with this configuration but on reboot just laptop screen works !

After using many Edid readers / editors and log reading indicates lost cause ( bad edid ) - 
I duplicated and renamed the edid created from laptop and pointed to it from conf and both work again so edid would appear to be the way to go. ( I obviously need to do this correctly !  soon - I promise ! )

Should Linux have an edid repository ? for each screen with a howto , although I still have audio problems - but that's another story ...........................

Raoul

---

