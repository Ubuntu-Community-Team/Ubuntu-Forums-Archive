---
title: "cups how do i find my printer driver, uninstall and re-install  14.04"
date: 2014-08-28
forum: General Help
---

### Post by btodd012 on 2014-08-28
Hi 
from the cmd line:
How do I see what version  printer driver is installed?

How do I uninstall that driver?

How do I re-install the same **or another driver?**

I was happily running 12.04 with a cups driver for my Kodak ESP 5250 Aio printer. The cups driver was c2esp16 and it worked fine. When I upgraded to 14.04 the printer looks OK, it seems to print but nothing gets sent to the printer. Network printer debugging produced results that look good. Routing is good, printer is found, print job looked like it works ... but it sits in the queue.

Some ubuntu tips say to un-install the old driver and re-install (either the old one or the new one again!).

I don't know how to do that. 

I think I need to query what's there.
Remove it.
Intsall the latest and test.
Maybe uninstall and go back to the old one.

I don't know what cmd line cmds to use.

thanks for any help

---

### Post by btodd012 on 2014-08-29
Hi,
I am surprised by the lack of response on this forum. Perhaps I posted in the wrong place or the wrong questions.... anyway I thought I'd provide my solution in case it helps anybody - painful as it was....

I finally figured out that I needed to learn more about cups.

From the cups web interface [http://localhost:631](http://localhost:631) I found I could somewhat manage and change my printer/drivers etc.

In 12.04 where printing worked, I had downloaded c2esp16 from sourceforge.  I followed the instructions in the "INSTALL" file and everything worked perfectly.

When I upgraded to 14.04, I think the upgrade loaded the latest esp driver but I couldn't really find what version it was or how to do do much with it.

From cups, I could detect printers and it found my printer. When I went to select driver, I picked the Kodak 5200 Aio but nothing worked. Filters failed was the message from cups I believe.

Tried lots of different drivers/settings - no luck.

Finally - I searched and found the latest c2esp that I could get... c2esp-27. I downloaded it - followed the instructions in the in the INSTALL file and it still didn't work. From the cups web interface, I modified the printer and picked the esp5200 Aio again but when I went to select the driver there was no 5200 series... There is another option to browse for PPD files. I selected that and then I found a ppd directory in the archive (c2esp-27). Now I could see esp5200 and when I selected it everything finally started to work.

I am sure there are easier ways and better instructions, but I wasn't sharp enough to find it.

I hope this helps somebody.
:-)

---

### Post by paulnewall on 2014-08-29
Hi,
I think the general problem with this forum is, there are plenty of people who will want to ask for help, but the replies depend on someone who might know the answer reading the question, and generally there are not too many of those people and not much incentive for them to read questions on the forum.
I'm the developer of c2esp, and I might look at this forum once every 3 days or so and search for posts with kodak in the title.
It sounds like you did a good job of solving the problem. I can't think of an obvious cause myself. I have an ESP5250 and xubuntu 14.04. But I might have a slightly different version of c2esp because I always have the latest.
I guess the problem was that c2esp and maybe cups too was updated. When that happens the "printers" that you set up in cups may need to be told where to find the ppd files again. For some upgrades that happens automatically but not always. You can do that in the cups web interface as you did, or in xubuntu (maybe also in ubuntu) from the menu system using "settings manager", "printers". And the most certain method is to delete your printers and create them again.
One possible cause for the "missing" ppd files is that cups now prefers to have *.drv files installed instead of *.ppd files. They are smaller and a lot of similar ppds are generated from one *.drv file. The *.drv file for your printer should have got installed to /usr/share/cups/drv/c2esp/Kodak_ESP16.drv. Cups is supposed to automatically look in the *.drv files for your printer and generate the right ppd file from the drv file. I think it then stores it in etc/cups/ppd. I might not have understood this correctly since I am just an expert in c2esp not in cups.
If I can find a dvd with ubuntu 14.04 on I will try and set up my printer using that, just to check that a clean install of 14.04 can find and set up the printer.

---

### Post by btodd012 on 2014-08-29
Hi Paul,

Thanks for the reply. You are probably right - maybe I was looking for too much too quickly. I was really stumped and wasn't sure how or where to start debugging. I was ala a bit frustrated with the 14.04 upgrade that came with my regular update channel. I waited for a while and finally plunged but I didn't do any research.

After the upgrade - my system was dead - old nvidea driver. Apache doesn't work. Printer stopped work and who knows what else. I figured I better get my printer up before I look at apache.

Anyway FYI - re: cups. I actually did deleted the printer and start over but I don't really think the printer got deleted until I went into the c2esp16 archive that I download and ran a make uninstall and followed that process.

 This did not get installed as you suggested (or maybe it got deleted when I uninstalled the printer?? /usr/share/cups/drv/c2esp/Kodak_ESP16.drv. Here is todd@todd-GX270:/usr/share/cups$ ls drv
c2esp       c2esp.drv        hpcups.drv           sample.drv      splix-lexmark.drv  splix-toshiba.drv
c2espC.drv  cupsfilters.drv  rastertosag-gdi.drv  splix-dell.drv  splix-samsung.drv  splix-xerox.drv

It did store the following
todd@todd-GX270:/usr/share/cups$ ls /etc/cups/ppd
Eastman_Kodak_Company_KODAK_ESP_5200_Series_AiO.ppd

I am not psoitive that this is the right/best driver, but it works. It seems really slow to complete printing and sits in the queue for a long time. But, it works.

Thanks again for replying - and, of course - the support you provide.

Bob

---

### Post by paulnewall on 2014-08-31
Yes, I completely understand the fustration. An extra difficulty with printers / scanners is that it's quite difficult as a user to discover if it's the overall system (cups or sane) that is causing the problerm or if it's the driver just for your printer (c2esp or kodakaio). Then it's difficult to decide what forum is the best to ask questions on.

I think c2esp.drv might be leftover from your c2esp16 installation. But I'm not absolutely sure about that. In any case, now that you have it working, I would leave it alone.

I think everyone using c2esp to print thinks it is slow! I don't have a solution. I don't think it's just the processing in c2esp being slow, though for the ESP5250 it does have quite a lot of work to do.

I don't seem to have a live dvd of ubuntu 14.04 so I can't confirm that the default installation does work with kodak printers. But I guess it probably does or I would expect to be seeing a lot more complaints.

---

