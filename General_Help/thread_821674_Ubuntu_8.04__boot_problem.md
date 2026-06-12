---
title: "Ubuntu 8.04  boot problem"
date: 2008-06-07
forum: General Help
---

### Post by Avenger1432 on 2008-06-07
I have been wondering why my computer has not been booting into ubuntu for quite a while and I just figured out why by resetting my bios...   whenever i disable USB support, Ubuntu starts... whenever it is enabled it never starts.  I have not tried just unplugging all usb devices instead of disabling in BIOS  but it is still a problem...  

anyone else with this issue? does anyone have a solution?, i have searched for it, perhaps not hard enough and i did find some people with the same problem but no solution.  This has happened to me since 7.04....  


thankyou in advance


my specs..

Intel Core 2 Duo 2.66 ghz E6750
Intel IP35-E Motherboard
Nvidia Geforce 8800 GT
500 gig Western Digital HD SATA
2 gigs ram

---

### Post by Th3Professor on 2008-06-07
> **Avenger1432 said:**
> I have been wondering why my computer has not been booting into ubuntu for quite a while and I just figured out why by resetting my bios...   whenever i disable USB support, Ubuntu starts... whenever it is enabled it never starts.  I have not tried just unplugging all usb devices instead of disabling in BIOS  but it is still a problem...  

anyone else with this issue? does anyone have a solution?, i have searched for it, perhaps not hard enough and i did find some people with the same problem but no solution.  This has happened to me since 7.04....  


Have you double-checked the settings in grub? (/boot/grub/menu.lst is one place)

Have you double-checked the boot order in the bios set-up?

You mentioned you have not unplugged all USBs (instead of disabling in bios) though mentioned that it is still a problem. Or I think that's what you were saying, it was a little confusing.

If you unplug all USBs, is it still a problem?

The grub settings probably won't solve this but it wouldn't hurt to double-check the config file.

It is possible the the bios "boot order" is set-up to boot from usb before hard drive or other device. You might need to rearrange the boot order in bios set-up.

If the boot order is set up right in bios, that should prevent the computer from using usb devices as bootables (assuming you have a bootable usb device connected).

---

### Post by Naatan on 2008-06-07
Try booting in recovery mode, this should output all the debug data so you can see where the error occurs

---

### Post by Avenger1432 on 2008-06-08
The thing is it says    usb something and   retries forever.    i did however try unplugging anything USB but it still didnt boot, i have to disable usb in the bios for it to boot.

I will try to copy down what it says exactly in recovery mode..  but it doesnt say anything useful really just  usb retry or smth.


And the only things i have connected to USB are my keyboard and mouse.. and webcam..

---

### Post by Avenger1432 on 2008-06-08
ok, so i copied as much as i could from what i saw in recovery mode and her goes (I know there probably a log file somewhere and i didnt have to do this...  but anyways i already copied it down on paper so i will copy it down again on keyboard....


 /build/buildd/linux-2.6.24/drivers/HID/usbHID/HID-Core.c: v2.6: USB HID Core Driver
[48.752700] ata3.00: qc timeout (cmd 0x27)
ata3.00: failed to read native max address (err_mask= 0x4)
ata3: failed to recover some devices, retrying in 5 secs
ata3.00: qc timeout (cmd 0x27)
revalidation failed (errno= -5)
ata3.00: disabled
ata3: soft resetting link
ata3: EH complete
ata_piix 0000:00:1f.5: MAP [ PO --P1 --]
ACPI : PCI interrupt
0000:00:1f.5 [A] ->
G5I 19 (level, low) ->
IRQ 20
SCSI4: Ata_piix
SCSI5: Ata_piix
ata5: Sata max UDMA
cmd 0xf200 ct1 0xf100
bmdma oxee00 irq 20

Alert! /dev/disk/by - uuid/f5707e76-6e26-4522-808d-9bdac3efdd37 does not exist. Dropping to shell!


then it brings up built-in shell 


P.S. this is missing a few things since it was very tedious to copy everything... but its mostly all there..

---

### Post by Naatan on 2008-06-08
Hmm I don't see anything helpfull in there, check the log at /var/log/messages or /var/log/syslog

---

### Post by Th3Professor on 2008-06-08
There is likely still a convenient step out there, somewhere, that will solve all of this... but have you also considered (and I hate having to say this because it seems to be a pretty generic fall-back in cases like this (though for good reason))... a fresh install?

If you do go for a fresh install...

If you have important data on the hard drive you need to back-up, you might try a recovery disk first or something similar.

Actually, you might just try a recovery disc anyway, it might solve the current issue.

(By the way, why do people spell it "disc" *and* "disk"?) hmmm....

---

### Post by doninsa on 2008-06-08
Hope you don't mind me jumping in here with another boot problem.  I'm trying to boot from a CD just to see what ubuntu looks like on my newest machine.

Can't boot from ISO image of unbutu 8.04.  
CD works fine on another machine so I think this problem is system specific.

During the boot process the ubuntu progress bar is replaced with a screen dump:
error messages are:
[454.150463] ata2.0:cmd a0/01:00:00:60:00/00:00:00:00:00:/a0 tag 0 dma 96 in
[454:150510] ata 2.00:status{DRDY}
.... - There are a number of other reports just like the ones above.  

After many tries the screen text ends with
(initramfs)

I've tried all the boot options with no success.  Any help would be appreciated.



System:
ASUS M2NPV-VM motherboard
AMD Athlon 64X2 3800+
2GB Kingston PC2-6400 (500MB x 4)
Seasonic S12-380 RT PSU
Seagate 80GB SATA300 HD
Samsung DVD+R 8X DVD+RW 

Windows XP SP2
ZoneAlarm Pro 7.0.470.000
Symantec AV Corp Ed. 10.1.5.5000
Linksys WRT54G Wireless Router

---

### Post by Avenger1432 on 2008-06-08
> **Naatan said:**
> Hmm I don't see anything helpfull in there, check the log at /var/log/messages or /var/log/syslog



well... if i could boot into ubuntu and use my mouse or keyboard... that would be possible. 

unfortunately, i do have a generic keyboard thats not USB... but im still lacking a mouse.  I know there is a program for windows somewhere where i can have windows see the ubuntu files...  



P.S. this has happened to me since 7.10...  i have done multiple fresh installs

---

### Post by Th3Professor on 2008-06-08
You mentioned some specs but what about:

What brand and model computer is it?

---

### Post by Avenger1432 on 2008-06-09
I built it myself...     I also missed one more spec...   Abit Intel motherboard... i missed the Abit part.

---

### Post by Avenger1432 on 2008-06-09
Bump.

---

### Post by gsanroma on 2008-06-10
I experience exactly the same problem (with a fresh install).
  I have a Dell inspiron 530 desktop computer with core 2 duo processor E6550.
  I only wanted to add that despite this problem, live cd boots correctly.
  Effectively there musb be something wrong in USB because, as Avenger1432 said, the problem disappears USB is disabled in the bios.
  
  Thanks,

Gerard.

---

### Post by Avenger1432 on 2008-06-12
Sry for the late reply.. but i thought i replied before....  but anyways.


I built my computer.. it doesnt have a brand name...  just my specs... as i  had put in my first post..

Intel Core 2 Duo 2.66 ghz E6750
Intel IP35-E Motherboard
Nvidia Geforce 8800 GT
500 gig Western Digital HD SATA
2 gigs ram



   As far as the logs... i have posted to you both  logs...  hope they help.  thankyou for all the help you can give.


P.S. I have been able to boot into ubuntu but only if i disable USB support in BIOS and use my   non-usb mouse and keyboard.  But I still want to be able to boot with my usb support on.. especially since i want to use my webcam.

---

### Post by Avenger1432 on 2008-06-12
bump..



just checking that people got this post cuz it keeps falling behind to the second page.  most people don't look at the second page i don't think.

---

### Post by Avenger1432 on 2008-06-12
2nd bump???

---

### Post by Avenger1432 on 2008-06-13
Bump.

---

### Post by Th3Professor on 2008-06-13
You can always ask on another forum/message board (on another linux - or even unix - website). ;)

---

### Post by Avenger1432 on 2008-06-15
no one knows anything?

I do not want to go to another forum this is the UBUNTU forums... this has happened to me since 7.04. This is some sort of USB bug thing problem in ubuntu... if it were purely my system other operating systems would do the same and not load when usb is enabled.





Help???

---

### Post by Th3Professor on 2008-06-15
> **Avenger1432 said:**
> no one knows anything? I do not want to go to another forum this is the UBUNTU forums... this has happened to me since 7.04. This is some sort of USB bug thing problem in ubuntu... if it were purely my system other operating systems would do the same and not load when usb is enabled. Help???

The point in stating, "you can always ask on another forum/message board (on another linux - or even unix - website)"... was this...

1. You won't always find all of your answers within one source alone, such as the ubuntuforums.org website.

2. Allowing for multiple sources of information increases the chances of coming across alternate external solutions, which you would not receive from interacting with only one source.

3. Within this thread, 11 of the first 19 messages are from you, including 5 bumps. After that 5th bump, I informed you that you could consider checking other sources. With that many bumps, it would be a positive step to look elsewhere.

4. The issues you are experiencing with booting are not restrictive to just Ubuntu, which is *still* Linux, henceforth the potential of receiving beneficial information from another Linux source - including, yet definitely not limited to, Debian.

5. If you are unable to find resolution from an alternate Linux source, note that Ubuntu is also *still* a Unix-based system, henceforth the potential of receiving beneficial information from a Unix source - there are plenty of Unix users who would gladly help.

6. There are other message boards and forums, other than ubuntuforums.org, that provide helpful discussions and assistance on Ubuntu-specific topics, including your booting issue.

7. While you are experiencing the booting issues with Ubuntu, specifically, the details you provided in your original post (USB-related, BIOS-related, and booting into a system) are not *strictly* Ubuntu problems.

8. Your booting issues (and/or USB issues, and/or BIOS issues) can potentially be resolved quicker if you look elsewhere (in addition to here); these issues arise in other systems too, and it will help you if you consider other options of assistance.

9. If someone on another website has never touched Ubuntu but has the answer to your booting problem, would you still accept it? That is rhetorical.

10. The bottom line is: don't limit yourself just to one source, especially when you don't receive the help you were hoping for from it. Don't omit that source, ubuntuforums.org is a very helpful website; though, don't restrict yourself to just the one source.

Beyond that, I hope you reconsider how you respond to someone who is trying to help you. I informed you that you can always ask on another website and you responded with an uncompromising, dogmatic, and uncivil message like, "no one knows anything? I do not want to go to another forum this is the UBUNTU forums..." How you stated your message served as an unwarranted and offending response to someone's attempt at helping you. Being callous will get you nowhere, so please be kind in your responses. Even if you do feel adamant about where you go to seek assistance on such matters, at least do the individual (who is offering help) a favor and respond politely. Thank you.

---

### Post by Quickshot on 2008-06-17
I had the same problem on my ip-35 motherboard. The solution was to add irqpoll to the boot parameters and after that ubuntu started to work fine.

---

### Post by Erlander on 2008-06-17
> **Quickshot said:**
> I had the same problem on my ip-35 motherboard. The solution was to add irqpoll to the boot parameters and after that ubuntu started to work fine.

Pardon my ignorance but how does one add irqpoll to the boot parameters?

Just wanting to learn.

Rob

---

### Post by ikkem on 2008-06-17
hi Erlander

I had the same problem I added the irqpoll option to /boot/grub/menu.lst

```
 title		Debian GNU/Linux, kernel 2.6.25.7-ne0nxq
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.25.7-ne0nxq root=/dev/sda1 ro [COLOR="Red"]**[SIZE="3"]irqpoll[/SIZE]**  [/COLOR]
```

hope it helps....:)

---

### Post by Erlander on 2008-06-17
Thank you for that.

I had hoped to cure a problem with my DVB USB2 TV tuner.  If it is connected at bootup under 8.04 I get a continually reoccurring line in dmesg that is:

```
 72.688798] dvb-usb: bulk message failed: -110 (1/1) 
```

If I connect the tuner after bootup there are no problems.

Rob

---

### Post by Avenger1432 on 2008-06-18
> **Th3Professor said:**
> The point in stating, "you can always ask on another forum/message board (on another linux - or even unix - website)"... was this...

1. You won't always find all of your answers within one source alone, such as the ubuntuforums.org website.

2. Allowing for multiple sources of information increases the chances of coming across alternate external solutions, which you would not receive from interacting with only one source.

3. Within this thread, 11 of the first 19 messages are from you, including 5 bumps. After that 5th bump, I informed you that you could consider checking other sources. With that many bumps, it would be a positive step to look elsewhere.

4. The issues you are experiencing with booting are not restrictive to just Ubuntu, which is *still* Linux, henceforth the potential of receiving beneficial information from another Linux source - including, yet definitely not limited to, Debian.

5. If you are unable to find resolution from an alternate Linux source, note that Ubuntu is also *still* a Unix-based system, henceforth the potential of receiving beneficial information from a Unix source - there are plenty of Unix users who would gladly help.

6. There are other message boards and forums, other than ubuntuforums.org, that provide helpful discussions and assistance on Ubuntu-specific topics, including your booting issue.

7. While you are experiencing the booting issues with Ubuntu, specifically, the details you provided in your original post (USB-related, BIOS-related, and booting into a system) are not *strictly* Ubuntu problems.

8. Your booting issues (and/or USB issues, and/or BIOS issues) can potentially be resolved quicker if you look elsewhere (in addition to here); these issues arise in other systems too, and it will help you if you consider other options of assistance.

9. If someone on another website has never touched Ubuntu but has the answer to your booting problem, would you still accept it? That is rhetorical.

10. The bottom line is: don't limit yourself just to one source, especially when you don't receive the help you were hoping for from it. Don't omit that source, ubuntuforums.org is a very helpful website; though, don't restrict yourself to just the one source.

Beyond that, I hope you reconsider how you respond to someone who is trying to help you. I informed you that you can always ask on another website and you responded with an uncompromising, dogmatic, and uncivil message like, "no one knows anything? I do not want to go to another forum this is the UBUNTU forums..." How you stated your message served as an unwarranted and offending response to someone's attempt at helping you. Being callous will get you nowhere, so please be kind in your responses. Even if you do feel adamant about where you go to seek assistance on such matters, at least do the individual (who is offering help) a favor and respond politely. Thank you.


Sorry, I was frusturated because ive already made 3 topics about it... and it feels as tho noone really cares. ^^^ until now...    I was just confused because as Linux has the BIGGEST support group  and these forums are linked right on the Ubuntu main site, I got frusturated and I think I Should find answers here considering most Ubuntu users go here... that is just my thought and seems like common sense to me that everyone would be coming here to look for answers since these forums are linked at the ubuntu site.     Anyways, I am sry if i appeared unpolite, I am not trying to offend or anything.

 

  Anyways... another thing, I do not think this is an issue with the IP 35 motherboard.. this happened to me with my other Abit motherboard (not IP-35) except it would actually boot after about 8 restarts. (did not realize it was a usb issue back then)

---

### Post by anibalrojas on 2008-06-22
Edit the kernel entry in the grub starup menu and add the pci=nomsi parameter to the end of it.

--
Aníbal Rojas
[http://laracaraoscura.com](http://laracaraoscura.com)
[http://anibal.rojas.com.ve](http://anibal.rojas.com.ve)

---

### Post by Th3Professor on 2008-06-22
> **Avenger1432 said:**
> Sorry, I was frusturated because ive already made 3 topics about it... and it feels as tho noone really cares. ^^^ until now...    I was just confused because as Linux has the BIGGEST support group  and these forums are linked right on the Ubuntu main site, I got frusturated and I think I Should find answers here considering most Ubuntu users go here... that is just my thought and seems like common sense to me that everyone would be coming here to look for answers since these forums are linked at the ubuntu site.     Anyways, I am sry if i appeared unpolite, I am not trying to offend or anything.
I appreciate that. I understand the frustration that comes along with issues like these. Well, best of luck in resolving it... I hope that, despite how long it's taken to figure it out, that it turns out with a fairly easy solution.

---

