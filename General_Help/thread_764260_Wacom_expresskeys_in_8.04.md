---
title: "Wacom expresskeys in 8.04?"
date: 2008-04-23
forum: General Help
---

### Post by jessika-kaos on 2008-04-23
I am trying get my Wacom Intuos3 configured in Hardy and am running into a problem with [expresskeys]("http://freshmeat.net/projects/wacomexpresskeys/")

Whenever I try to start the program I get this error:

```
sonne@HIVE:~$ expresskeys 

expresskeys ERROR: Tablet not attached, OR (in case of Cintiq 21UX, Intuos3
and Graphire4) the 'pad' device has not been specified in xorg.conf, OR is
lacking on the command line when using "named devices".

```

I have pressure sensitivity in Gimp, so the tablet it otherwise working properly, but I really need the touchstrips to work. This was all working fine in Gutsy. I even installed the latest linuxwacom drivers (0.7.9-11) but still not working.

---

### Post by activx on 2008-04-24
Hi

I got the same problem, the pad works fine in Gutsy with my intuos3 and today with the release of Hardy Heron only the pen was usable. I finally found the solution : [here]("http://www.nabble.com/ExpressKeys-won't-find-"pad"-anymore-td15739601.html")

You'll need to edit one file before compiling the expresskeys:
```


 Change line 462 of the file src-expresskeys/get_device.c from:

 if (xdevice_list[i].use == IsXExtensionDevice) {

 to these two:

 if (xdevice_list[i].use == IsXExtensionDevice ||
     xdevice_list[i].use == IsXExtensionPointer) { 

```

Works fine for me, i got the pad with GIMP and i'm happy now :KS.

---

### Post by jessika-kaos on 2008-04-24
Thanks! I'll try that and post an update.

---

### Post by ueman on 2008-05-12
@activx

hi, i've try it raplacing that line as you did, but i still have the same problem im using expresskeys-0.4.1 version. none error compiling. i dont know what to do

im in ubuntu hardy, when i was using gutsy every thing works  fine.

---

### Post by bigdee973 on 2008-05-23
thank you that info worked for me, but now that i have installed expresskeys theres a problem with gimp working fine.  Expresskeys works fine in other programs ..the pad buttons do the default settings (alt, space, ctrl. etc) on terminal and firefox but on GIMP I get no effect...could someone explain whats going on...in input settings in gimp i have pad configured for screen and axes numbered from 1 to 6...so its X:1 Y:2 PRESSURE:3 ...and so on...i followed the steps..i have UBUNTU 8.04 HARDY HERON and my xorg.conf seems to be configured just fine, is anybody else having these problems? i have an intuos3 verision.

---

### Post by mallow on 2008-05-25
I have similar problem. Managed the express keys to work, but not with GIMP. I mean they work, but... GIMP just ignores somehow the intuos3.conf1 and ExpressKeys work as default. That`s big issue to me. Beside that, it sometimes stops working and when I try rerun expresskeys deamon, my laptop`s processor starts working 100%. Temperature goes very fast and I have to reboot laptop. What to do? :(

edit:
OK, I`ve found out, that if you start gimp with "gimp" command (NOT gimp-2.4 which is under GIMP`s shortcut at Applications), then expresskeys work with shortcuts I want.
Unfortunatelly there`s still one more issue. Sometimes expresskeys deamon stops working. I think this happens when I try to use pad`s touchstrips. But why? Maybe some sort of conflict with Synaptics touchpad?

---

### Post by jessika-kaos on 2008-10-12
Has anyone figured out how to get expresskeys working? After recompiling  the program with the above mentioned fix, it just gives a segmentation fault whenever I try to use the touchstrips. 

I'd really like to get this working - as it is I have to keep booting back to windows whenever I want to do any artwork (frequently).

---

### Post by Merde on 2008-12-18
> **jessika-kaos said:**
> Has anyone figured out how to get expresskeys working? 

not me, but I found solution here :
[http://www.hightechsister.com/25/ubuntu-hardy-804-gimp-wacom-success/](http://www.hightechsister.com/25/ubuntu-hardy-804-gimp-wacom-success/)
for "tablet not attached" issues

and for touchstrip causing crash :
[http://www.hightechsister.com/153/ubuntu-hardy-804-gimp-wacom-revisited/](http://www.hightechsister.com/153/ubuntu-hardy-804-gimp-wacom-revisited/)

everything is working for me now

---

### Post by fragos on 2008-12-18
Have you defined the "pad" device in xorg.conf? That is required for keys on the pad to work.

---

