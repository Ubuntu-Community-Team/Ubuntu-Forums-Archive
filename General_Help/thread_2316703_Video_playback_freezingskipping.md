---
title: "Video playback freezing/skipping"
date: 2016-03-10
forum: General Help
---

### Post by danny_king on 2016-03-10
I am running Ubuntu 15.10 on my Toshiba L650 laptop which I bought in Dec 2010. The system specs are as follows:

[TABLE]
[TR]
[TD="class: sstitle, colspan: 2"]**Computer**[/TD]
[/TR]
[TR]
[TD="class: field"]Processor[/TD]
[TD="class: value"]4x Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz[/TD]
[/TR]
[TR]
[TD="class: field"]Memory[/TD]
[TD="class: value"]3841MB (1407MB used)[/TD]
[/TR]
[TR]
[TD="class: field"]Operating System[/TD]
[TD="class: value"]Ubuntu 15.10[/TD]
[/TR]
[TR]
[TD="class: field"]User Name[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]Date/Time[/TD]
[TD="class: value"]Thursday 10 March 2016 03:32:45 PM IST[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]**Display**[/TD]
[/TR]
[TR]
[TD="class: field"]Resolution[/TD]
[TD="class: value"]1366x768 pixels[/TD]
[/TR]
[TR]
[TD="class: field"]OpenGL Renderer[/TD]
[TD="class: value"]Unknown[/TD]
[/TR]
[TR]
[TD="class: field"]X11 Vendor[/TD]
[TD="class: value"]The X.Org Foundation[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]**Multimedia**[/TD]
[/TR]
[TR]
[TD="class: field"]Audio Adapter[/TD]
[TD="class: value"]HDA-Intel - HDA Intel MID[/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]**Input Devices**[/TD]
[/TR]
[TR]
[TD="class: field"] Power Button[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"] Lid Switch[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"] Power Button[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"] AT Translated Set 2 keyboard[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"] Video Bus[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"] SynPS/2 Synaptics TouchPad[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]** Toshiba input device**[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"] HDA Intel MID Mic[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"] HDA Intel MID Headphone[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"] CNF9055[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]**Printers**
[/TD]
[/TR]
[TR]
[TD="class: field"]No printers found[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]**SCSI Disks**[/TD]
[/TR]
[TR]
[TD="class: field"]ATA TOSHIBA MK3265GS[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"]TEAC DV-W28S-VT[/TD]
[/TR]
[/TABLE]

The dedicated video memory is 64 MB. 

All video playback freezes or skips frames regardless of the video app I use. I have the default Ubuntu video player 'Videos' and VLC. I had this problem when I was using W7 and W10 in the same laptop. However, when I switched to Ubuntu 14.10 from Windows, all videos played without any issues. No freezing or skipping. The problem returned after I upgraded to Ubuntu 15.10. It was a clean install though, using a live usb stick.

---

### Post by Le3eVolfoni on 2016-03-10
Which graphic card do you have ? Might be a driver problem, the line "openGL renderer unknown" surprises me.

---

### Post by danny_king on 2016-03-11
> **Le3eVolfoni said:**
> Which graphic card do you have ? Might be a driver problem, the line "openGL renderer unknown" surprises me.

My laptop has an Intel HD graphics card integrated.

---

### Post by Le3eVolfoni on 2016-03-11
Is your CPU over the roof while playing a video ? Do you have the same problem when watching videos online ?

---

### Post by danny_king on 2016-03-11
> **Le3eVolfoni said:**
> Is your CPU over the roof while playing a video ? Do you have the same problem when watching videos online ?

I think its just when playing videos in the default player and VLC. Haven't observed anything when playing videos online.
Videos playback uses around 4 to 5% of the CPU as per what is shown in  System Monitor.

Oh! And here is the render info from the hardinfo report:

[TABLE]
[TR]
[TD="class: field"][TABLE]
[TR]
[TD="class: sstitle, colspan: 2"]**Display**
[/TD]
[/TR]
 [TR]
[TD="class: field"]Resolution[/TD]
[TD="class: value"]1366x768 pixels
[/TD]
[/TR]
 [TR]
[TD="class: field"]**OpenGL Renderer**
[/TD]
[TD="class: value"]**Mesa DRI Intel(R) Ironlake Mobile **
[/TD]
[/TR]
 [TR]
[TD="class: field"]X11 Vendor[/TD]
[TD="class: value"]The X.Org Foundation[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by Le3eVolfoni on 2016-03-12
Your problem is different than the one I faced. It seems that you have a driver problem, even though I though intel graphics were natively in ubuntu. My best bet would be to update your drivers

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade
```

Or to go to **software & updates**, **additional drivers**, and change the selected driver.

I found [this page]("https://01.org/linuxgraphics") as well that might be helpful.

Sorry I can't help more, let's hope one of these 2 things will work or that someone with a better knowledge than me will stop by.

---

