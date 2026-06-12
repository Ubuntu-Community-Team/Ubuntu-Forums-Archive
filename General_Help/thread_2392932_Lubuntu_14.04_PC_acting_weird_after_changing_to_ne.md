---
title: "Lubuntu 14.04 PC acting weird after changing to new USB keyboard from PS2"
date: 2018-05-27
forum: General Help
---

### Post by aksam84 on 2018-05-27
Hi,
I'm running Lubuntu LTS 14.04.04 on my old office PC (a Intel Core 2 Quod) for about 2 years now with a PS2 keyboard and USB mouse. 


Today, I bought a new USB keyboard to replace the old PS2 as some keys stopped working and now my PC is acting weird. e.g. When I browse the pages auto reload, auto scrolls, moves pages up and down etc. When I try to scroll using the mouse scroll button it magnifies the web pages. When I type on notepad, the mouse pointer jumps and weird letter combinations get typed without my typing them etc. 


I thought I now had a problem with the mouse, so I got a new mouse but still same issue. So I tried removing the new USB keyboard when the PC is turned on and then tried browsing with only the mouse and it works normal. So I thought its because of the new keyboard. I wonder whether it's because I changed from PS2 to USB? I tried to find solutions for this 2.issue on the Net but couldn't find any. 

Please help me solve this problem? 

(It took me ages to just type this message and post here due to the weirdness.)


Thanks :D

---

### Post by mörgæs on 2018-05-27
Hi, welcome to the fora.

Lubuntu 14.04 is out of support. As a first step I suggest a fresh install of 18.04.

---

### Post by SL0ltMJGyh on 2018-05-27
Before you upgrade, remember that ps/2 devices aren't meant to be hot-swapped (unplugged/plugged in while the device is on). That means you can't just switch to a usb keyboard without rebooting your computer first. With this knowledge, you may want to power off, unplug your ps/2 and usb keyboard, and reboot and plug in the keyboard again.

---

### Post by aksam84 on 2018-05-28
Hi guys,
Thanks for the welcome and replies :)


mörgæs,
When I first installed linux back in 2016, I first installed the 16 LTS but it gave lots of issues. A technical guy I know said to try 14 LTS, because he thought my old pc's hardware might not be supporting newer versions like .16. That's why I installed 14 lts, and it worked with few minor issues in the browser etc. which I was able to fix. Isn't there any ways I can try before trying to upgrade?   


apmarek,
I removed the PS2 and pluged the USB when the pc was off, so it can't be the issue. I've offed and come back to on the pc several times now and still issue persists.


FYI, I've kept the PC updated regularly by installing all the updates the "Software Updater" notifies.

---

### Post by mörgæs on 2018-05-28
A Core 2 Quad is not what I call old. It should be able to run 18.04 without problems.

Best way to find out is trying a live boot.

---

### Post by aksam84 on 2018-05-28
Morgaes,
I live booted (with Lubuntu 18.04 on a usb drive) and checked. The issue still persists. 

Even in the 18.04 live boot, Clicking the close, magnify, minify buttons of any window don't work. In firefox browser, clicking mouse scroll, magnifies the content etc. When I remove the usb keyboard, the mouse click, scroll buttons etc. work normal but when I replug the usb keyboard, I get the weird actions issue again. Any idea what I can do?

---

### Post by #&amp;thj^% on 2018-05-28
This really sounds like a faulty/or incompatible keyboard. (Just my 2 cents worth)

---

### Post by aksam84 on 2018-05-28
1fallen,
 That's a good idea. I didn't know linux required a special keyboard. Don't all keyboards support linux? 

 Anyway, I will try to get another USB keyboard and check with my pc. How can I know the next USB keyboard I buy will support?

 The one I bought was a cheap keyboard called Maxcom brand. In the cover it states it supports Windows XP, 7, 10 etc but no mention of Linux support.

---

### Post by #&amp;thj^% on 2018-05-28
That's a mistake we/ and newer users assume is that they all work right? :)
truth is that keyboards need drivers to work and some manufactures just don't care about Linux or maybe the sellers/ manufacturers never bother to test it?.
Wish I had a list for you to view but I don't. :(
Try googling keyboards that work in Linux.
Good Luck

---

### Post by mörgæs on 2018-05-28
I have never experienced a wired keyboard not working with GNU/Linux, even counting from my first Ubuntu 5.10 install. Of course it might be broken, though.

Regardless of the keyboard you should get away from 14.04 and install a supported release.

---

### Post by aksam84 on 2018-05-28
1fallen,
yeah, we never think. Now I google, I find many questions and forum threads where people asking whether this or that or other keyboard works in linux. I guess I will have to ask around from many shops for linux supported keyboard. Not many shop owners will know it I guess because not many use linux.

morgaes,
I checked the keyboard in my laptop and it is worked normal.  
Agree with you regarding 14.04. I hope to upgrade once I solve this keyboard issue.

---

### Post by #&amp;thj^% on 2018-05-28
Logitech is a good search item I'm using this one now: (Logitech K780 multi device)

---

### Post by aksam84 on 2018-05-29
1fallen,
You were right. 
I just got another new USB keyboard from a shop telling them I'll check and return if it didn't work on linux. Thankfully it worked. I'm now typing this using that new keyboard. No more weird characters getting typed or mouse issues. I think that keyboard didn't support Linux. 

Thank you so much bro :)

---

### Post by aksam84 on 2018-05-29
> **mörgæs said:**
> I have never experienced a wired keyboard not working with GNU/Linux, even counting from my first Ubuntu 5.10 install. Of course it might be broken, though.

Regardless of the keyboard you should get away from 14.04 and install a supported release.

Now the keyboard issue is solved I hope to install Lubuntu 18.04. My concern is about the data. I have lot of documents, files, etc already in the pc. Will I have to take backups of them before installing 18? Is there any easy way to upgrade without taking backups and copying them back after upgrading?

---

### Post by Impavidus on 2018-05-29
Most keyboards work with Linux. Sometimes special features, like multimedia keys or backlighting, don't work.

Maybe a bit late to say this, as you already solved the problem, but anyway. When you use the mouse wheel and see that this changes zoom, that suggests that you web browser thinks you're holding the ctrl key. The numeric keypad can control the mouse cursor when you have enabled mouse emulation. Both may be affected by accessibility settings, so maybe check those.

You can install 18.04 without wiping the data. It's easy if the data are on a separate partition, like a /home or /data partition. Use the "something else" option, don't format the partition with your data and mount it at the same place where it was before. But making a backup of your data never hurts.

---

### Post by aksam84 on 2018-05-29
Impavidus,
Thanks. It's great to hear I can upgrade without data erasing. I must try it.

Regarding my faulty keyboard, how do I check accessiblity settings? I like that keyboard as its a better quality than the new working one, so it'll be great if we can get it to work. Do you think it's possible?
say like changing some keyboard character mapping settings or something?

---

### Post by mörgæs on 2018-05-29
When struggling with hardware support like in this case I would be even less inclined to do an in-place upgrade. You may or may not bring a misconfiguration along to the new install if you keep /home. 

A backup is needed no matter what so a clean install does not add much workload.

---

### Post by aksam84 on 2018-05-31
Morgaes, 
Thanks for your help and advice. I installed Lubuntu 18 and its working ok except for some video issues. I think I will open new thread for that. 

Moderaters please mark this thread as solved. Thanks

---

### Post by mörgæs on 2018-06-02
Congratulations.

Using Thread Tools you can mark the thread solved.

---

