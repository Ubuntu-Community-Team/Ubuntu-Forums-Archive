---
title: "Gutsy PVR350 poor colour problem"
date: 2008-04-04
forum: General Help
---

### Post by wollo on 2008-04-04
I'd like to say Hi first. 

I've been struggling to set up my first Mythbuntu box. So far I have been able to Google all the answers I need. However, Since install I have only been able to recieve a grainy near black and white picture the shvs input on my PVR-350 card.
 This happens when I play live TV via the frontend onto either my monitor, or through the svhs out on the 350 to my tv and even through vlc to my monitor. I have not yet tried to pass x through the pvr-350. Altering brightness, color, contrast, hue etc in either channel manager or via OSD doesn't help.

Whilst googling I found someone who had a similar problem [http://www.mythtv.org/pipermail/mythtv-users/2006-January/116027.html](http://www.mythtv.org/pipermail/mythtv-users/2006-January/116027.html)

ivtvctl -j doesn't work for me, I don't even know if I'm barking up the wrong tree here!

I've installed Mythbuntu 7.10 from disk and performed updates, Ive followed this: [https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

for svhs out, I've tried PAL and PALBG both are almost as bad as each other, 
PALBG may be slightly less grainy though.

I really don't know what to try next. from past experience windows pvr's are not reliable enough for me please, can anyone suggest a next move?

P.C. spec: Athlon X6400, MSI K9N SLI, 4GB crucial ddr2 ram, IDE 120GB HDD(testing only) onboard sound and network, GeForce 7600GT 256MB. Using Nvidia drivers.

If I've left anything helpfull out please ask. Unfortunately this is only my second real foray into Linux. I've been using a clark connect firewall for ages but I'm really more used to windows I'm afraid.  Any help would be greatly appreciated.

Bill.

---

### Post by danwood76 on 2008-04-04
So if you play a video which you know is a good video (or a DVD) out through your nvidia card you get this issue?
Or is it just video you play from your PVR-350 or have recorded from this?

---

### Post by wollo on 2008-04-04
Dan, thanks for the quick reply. DVD through the Nvidia card to the monitor works fine, colour is great.

---

### Post by danwood76 on 2008-04-04
I wonder if maybe you are pushing out an NTSC signal to a PAL TV or the other way round depending on where you live. (or capturing in the wrong format)
That would create a grainy black and white colour, but may also create a scrolling picture.

I dont really have any experiance with making PVRs but I am thinking of building one some time soon. Although I have quite a bit of experiance with signal matching and TVs and Monitors.

Do you have an NTSC or PAL TV?

---

### Post by wollo on 2008-04-04
Dan, I'm in the uk, using a Pal TV, PAL PVR 350 and pushing PAL to the set. I've also tried PAL BG.The card also works fine in windows I should add.
Bill.

---

