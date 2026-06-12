---
title: "ink levels? how do you do that?"
date: 2008-05-29
forum: General Help
---

### Post by kureyamu on 2008-05-29
hello

i am running ubuntu hardy heron 8.04 and i have an Epson D92 printer, which has 4 colour cartridges.

when a cartridge runs out, the printer stops working until that cartridge is replaced; usually i have no idea which cartridge has gone and i end up replacing cartridges which do not need replacing - so printing is an expensive business on linux! it is not possible to see how much ink is left in a cartridge by taking it out and holding it up to the light - cartridges are opaque and there is a sponge inside which holds the ink anyway. 

i have 2 questions:

(1) until linux distributions sort out a practical policy for ink utilities, are there any chinese users on this forum who can tell me how it's done in mainland china? - i believe many companies and city councils there use linux, and in their offices they will regularly check the ink levels in their cartridges before changing cartridges. so how do the chinese do it? (we in the west can't. it's time for some chinese imports, i think ...)

(2) at some time in the not too distant future, can the programmers for preferably Open Office or if not Ubuntu write a printing ink utilities program? i think many users of linux keep xp, 2000 or vista just so they can use printing utilities - that's sad :(

More details:

(a) there is a .exe file called ssc ([http://www.ssclg.com/epsone.shtml](http://www.ssclg.com/epsone.shtml)) which i have been told has a graphic user interface and can be opened with Wine, but i have looked at the web site and see that it does not support my printer and anyway, i do not like the idea of downloading .exe files from Russia made for Microsoft

(b) i tried Mtink and it did not work;

(c) i tried Inkblot although it does not support my printer, but all i ever received was an Error message from it, saying that it could not open the printer;

(d) i currently use an application called Escputil in a printing terminal although the code used for cleaning the printing heads did not work (sudo escputil -c -u -r /dev/usblp0). i believe work on making a graphic user interface was started but never finished. the only command that works to some extent in Escputil is the very command i need: 
sudo escputil -i -u -r /dev/usblp0
this command line as root in a terminal gives the printing ink levels of the 4 cartridges as long as they have ink in them. i don't know if it also works with 6-cartridge printers ...

unfortunately, i am forgetful and also i don't like to change an ink cartridge until it runs out.

when a cartridge runs out of ink, the printer stops working and will not do anything until that cartridge is replaced - so when escputil tries to link to the printer, the printer says it is busy (it is busy waiting for a replacement) and escputil answers my request for ink level data with: *printer temporarily busy* :-k

it's a catch 22 situation.

how do you other linux users know when to change your printing inks? do you do it on linux or on a microsoft-run machine? i should like to hear your experiences.

regards

kureyamu

[CENTER]*microsoft was a popular 20th century software company*[/CENTER]

---

### Post by todak on 2008-05-29
Here is the link to a graphical front end interface for escputil called Stylus-Toolbox. It is what I use and it works great for me. :)

[http://sourceforge.net/project/showfiles.php?group_id=179430&package_id=207211&release_id=457652](http://sourceforge.net/project/showfiles.php?group_id=179430&package_id=207211&release_id=457652)

---

### Post by kureyamu on 2008-05-29
hello todak

thanks for your response

i tried that gui recently and it didn't work for me, but i think it was on another operating system, perhaps fedora or debian

i shall try it now on my ubuntu (rather tomorrow ... it's the small hours of the morning and yawning time)

are you able to check ink levels when one of the cartridges has no ink left? if you can, then the problem lies with my printer model (epson are always changing things) and not with escputil ... that's the main problem i have

regards

kureyamu

*[CENTER]microsoft was a popular 20th century software company[/CENTER]*

---

### Post by todak on 2008-05-29
Hello kureyamu.

Yes, I can check my ink levels even when one of them is empty. If you still have problems, Stylus-toolbox is going to be upgraded to version 1.0 soon. It will support newer 8-ink printers. Stylus-toolbox is the only program I have found that will work correctly with my Epson printers. There is also a proprietary program called turboprint. You must pay for a full copy. A demo copy can be had for testing purposes for free, but it prints a big nasty watermark across your documents, however for testing to see if it will work for your printer it is good enough. It can be found at [http://www.turboprint.info/](http://www.turboprint.info/) Hope this helps.

---

### Post by kureyamu on 2008-05-30
Hi todak

I downloaded stylus-toolbox (on the webpage called stylus-toolpage-0.2.7-1_all.deb) from that webpage at that link you gave me, installed it with GDebi Package Installer and rebooted.

It isn't in my menu.

Synaptic Package Manager tells me it is installed.

In a terminal I have tried using:

sudo locate stylus-toolbox
sudo locate stylus_toolbox
sudo locate stylus-toolbox-0.2.7-1
sudo locate stylus-toolbox-0.2.7-1_all

nothing shows up ... I will need to find its path  so that I can try to put it in the menu ...

-------------------------------------------

ah, I just tried to list all in bin with the command:

ls -a /usr/bin/

stylus-toolbox is in there

so the path is /usr/bin/stylus-toolbox

------------------------------------------

I have put it in my menu and I think I will keep it there, even though it doesn't work ... maybe some time in the future my epson printer will be added to the list of supported printers, at the moment D92 is not on the list and for the 4 cartridges, printing ink levels show as 0% and stylus-toolbox will not print out a test page.

In stylus toolbox preferences, the settings are:

Device port: /dev/usb/lp0
(I had tried usb#1 and stylus-toolbox said: no such place);

The box “printer is a new usb printer, 740 or newer” is ticked;

Model Settings: atomatically detect;

Location of escputil: /usr/bin/escputil

-------------------------------------------------

As D92 is not on the list of supported printers, in Model Settings I have tried D68 and D88 but no luck – stylus toolbox will not display my printing ink levels nor will it print out a test page.

And yet strangely escputil works in a terminal to show ink levels, but not when a cartridge has run out of ink.

So I am still waiting for Ubuntu or Open Office to provide printing utilities, which are an essential part of any office set-up.

thanks for your help, todak

regards

kureyamu


*[CENTER]microsoft was a popular 20th century software company[/CENTER]*

---

### Post by Bearly Able on 2009-06-10
I found this thread and used it to install Stylus Toolbox in Hardy and it worked fine.  I recently upgraded to Jaunty, but following problems ended up doing a fresh install of Intrepid, and re-installed Stylus Toolbox, only this time I can't get it to work.

When I try to use it, I get an error message saying
```
Cannot open /dev/usb/lp0 read/write: Permission denied
```

I looked for help on the Stylus Toolbox Web site, and found ```
chmod 666 /dev/usb/lp0
```but that just gives me ```
chmod: changing permissions of `/dev/usb/lp0': Operation not permitted
```

Please can anybody help?  Thanks.

---

### Post by michy99 on 2009-06-10
Try the chmod command with sudo.```
sudo chmod 666 /dev/usb/lp0
```

---

### Post by ellgor on 2009-06-10
Hi,

If your still having problems I can recommend Qink, once installed start it from a terminal, "sudo qink" which will run it straight out of the box.

Regards, Ellgor.

---

### Post by Bearly Able on 2009-06-10
michy99 - thanks, that did it.  Sorry, I should really have thought of that myself.

ellgor - thanks for the tip.  I'll bear it in mind for future reference, but I really needed something with a GUI - my husband has a palpatoorie at the thought of having to open a terminal to do anything!

Thanks again guys.

---

### Post by Bearly Able on 2009-06-21
Sorry to keep asking dumb questions, but I'm bewildered - again.  I get the ```
Cannot open /dev/usb/lp0 read/write: Permission denied
```message every time I turn on the printer.  I can fix it using chmod, but I have to do this every time.  Is there some way I can solve the problem permanently?  I didn't have this problem before and I don't understand why it's arisen now.  Thanks.

---

### Post by ellgor on 2009-06-21
Hi,

Just to re-iterate, Qink IS a graphical tool (actually nice looking), the only reason its started from the terminal is to overcome the permission annoyances, hope this of use.

Regards, Ellgor.

---

### Post by Bearly Able on 2009-06-22
Hi Ellgor,

Thanks for that.  I've tried it, and it's certainly easier than changing permissions to use Stylus Toolbox every time.  I might even be able to train my husband to use it!

Lesley

---

