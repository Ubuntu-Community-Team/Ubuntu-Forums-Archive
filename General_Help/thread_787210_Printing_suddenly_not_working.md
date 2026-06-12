---
title: "Printing suddenly not working"
date: 2008-05-08
forum: General Help
---

### Post by canadianbaptist on 2008-05-08
I have ubuntu 7.10. I have been printing with my HP Laser Jet 1018 for a long time. I printed a doc.... it printed. On the next doc it goes it goes to the printer than it says it it is done, but nothing happened.

I thought it was my printer so I tried printing from my wifes (usb also) and I get the same thing. I am sort of new to Linux but I think something "broke" It is definitely my system as my wife can print fine.

I have reinstalled the printer a couple of times, but it still does not work.

Can anybody give any suggestions?

[B]Edit:

When I run lpc status in terminal I get HP_LaserJet_1018:
        printer is on device 'usb' speed -1
        queuing is enabled
        printing is enabled
        no entries
        daemon present
HP_LaserJet_P1005:
        printer is on device 'usb' speed -1
        queuing is enabled
        printing is disabled
        no entries
        daemon present

However when I try to print, the icon goes solid for a second then fades.... when I click on it I see there are no docs in the que. This is for any program that tries to print

---

### Post by canadianbaptist on 2008-05-09
> **canadianbaptist said:**
> I have ubuntu 7.10. I have been printing with my HP Laser Jet 1018 for a long time. I printed a doc.... it printed. On the next doc it goes it goes to the printer than it says it it is done, but nothing happened.

I thought it was my printer so I tried printing from my wifes (usb also) and I get the same thing. I am sort of new to Linux but I think something "broke" It is definitely my system as my wife can print fine.

I have reinstalled the printer a couple of times, but it still does not work.

Can anybody give any suggestions?

[B]Edit:

When I run lpc status in terminal I get HP_LaserJet_1018:
        printer is on device 'usb' speed -1
        queuing is enabled
        printing is enabled
        no entries
        daemon present
HP_LaserJet_P1005:
        printer is on device 'usb' speed -1
        queuing is enabled
        printing is disabled
        no entries
        daemon present

However when I try to print, the icon goes solid for a second then fades.... when I click on it I see there are no docs in the que. This is for any program that tries to print




I have singled out the problem. When I plug it into xp with drivers installed it can print fine and when I plug it into Linux WITHOUT turning it off, i can print.

XP sends something to te printer that Linux was but no longer is sending. Any thoughts?

---

### Post by canadianbaptist on 2008-05-10
> **canadianbaptist said:**
> I have singled out the problem. When I plug it into xp with drivers installed it can print fine and when I plug it into Linux WITHOUT turning it off, i can print.

XP sends something to te printer that Linux was but no longer is sending. Any thoughts?



Anybody?????

---

### Post by glennph93 on 2008-05-12
I had the same problem with a HP 1020. The printer needs the firmware loaded and ubuntu default driver doesn't due that. The solution is found here[ http://foo2zjs.rkkda.com/]("http://http://foo2zjs.rkkda.com/")
Follow the directions and works great no more windows.

---

### Post by canadianbaptist on 2008-05-12
> **glennph93 said:**
> I had the same problem with a HP 1020. The printer needs the firmware loaded and ubuntu default driver doesn't due that. The solution is found here[ http://foo2zjs.rkkda.com/]("http://http://foo2zjs.rkkda.com/")
Follow the directions and works great no more windows.

That link doesn't work.... can you repost? Thanks

---

### Post by glennph93 on 2008-05-18
Sorry I'm so late(yahoo tends to put ubuntu in my junk folder). There is an extra http: in that address. This should work [here]("http://foo2zjs.rkkda.com/").

---

