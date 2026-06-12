---
title: "Multiple problems, please help"
date: 2008-01-06
forum: General Help
---

### Post by matthewrdamon on 2008-01-06
I hope this thread is posted in the right area.  There are a few different problems at work here.  Last weekend my sister called me saying her laptop won't boot.  She runs windows, and there is a corrupted file that windows needs.  I have verified the problem, and thought that the quickest fix would be to pop the windows disc that came with the computer into it, boot, restore, and done.  The problem is that her optical drive is also non functioning.  She has no floppy dirve on the computer, and BIOS doesn't support USB boot devices.  

My next thought was to setup DCHP and TFTP servers on my (ubuntu) computer and run a network installation, then take the day to explain why she needs to now run linux exclusively.  She says that her data currently on the dirve is too important to just replace.  So I am stuck again.  

I wanted to just pull the HDD, image it on my computer, if i got lucky, replace the ini file that is wrong, and replace the HDD, boot and pray.  This is also cannot be done because of the damage to the laptop already.  Unscrewing and/or fiddleing around with the case is out of the question.  And yes, I checked, the HDD is only accessable by removing the keyboard.

This leaves me only one option: find a network bootable "live" image of linux and get access to her files that way.  I need something like the Ubuntu live install CD that allows an X session to be run off of the CD, but for a network boot.  I tired the ubuntu gutsy network install image, it booted properly, but the session that I could escape to from the installer doesn't have ntfs support, so that was a no go.

Please help me, if there is something that I'm overlooking please let me know.  Also, if anyone knows of a "hardware agnositc" live boot image that has ntfs-3g on it, I would love to hear about it.

Thank You.

---

### Post by HermanAB on 2008-01-06
I have had the same problem long ago: [http://aeronetworks.ca/ris-howto.html](http://aeronetworks.ca/ris-howto.html)

However, the easiest way to fix your problem is to remove the laptop HDD, use a notebook to IDE footprint adaptor to plug it into another chassis, then use a live CD called BartPE to copy all her data off to a server (or another HDD in the chassis) or write it to a DVD or something.

Then install Windows 98 or ME on the HDD - yes, hear me out!

Now, if you plug the HDD back into the laptop, Windows ME will have a minor heart attack since all the hardware changed, but it should work after a while.  At this point you can enable Samba networking and copy a complete Windows XP disk from a server to the HDD in the laptop.  Then you can run the XP installer off the HDD and upgrade the laptop from WinME to XP.

Of course, the best solution is to go and buy a new CD drive for the laptop...

Cheers,

Herman

---

### Post by matthewrdamon on 2008-01-09
Will try this weekend, when I hove some time.  That is great news, she will love her Windows.  I have tried many times, but she just doesn't want to switch "yet"

Thanks!

---

### Post by vanitopooh on 2008-01-09
Sorry for my english i just want to clear up something i was just wondering why ubuntu is giving me a headache regarding on installation. Many forums that ive read a while ago and the other day no one is like mine... here ist it... i try to install ubuntu to my intel p4 pc 2.66 ghz 512 mb of ram the problem is when it boots it hangs??? keeps on the orange bar loading until 2.5 hours and finally i decided to re start my pc and do the same thing again and thesame thing happens.......... im a computer technician of my own computer only i'm very much sure that there are no hardware problems error on my pc bcoz i came out to windows planning to install linux bcoz i like only not the 3d graphics interface but the way it communicates imagine software and programs for free im new to linux going back to my problem... i installed ubuntu on my pc guess what??? i remove my nvidia ge force fx5500 video card and finally it worked.... but how about my video card can't i used to ubuntu??? any idea how this works??? i have windows xp on my pc i used vcard for my 3d modeling of my autocad its hustle when i plan to use my windows bcoz of my cad im gonna have to put back my video card again and then when i plan to use ubuntu i have to remove my video card pls emai me for your answers i want to know about linux and i want to no more about it...  is there any solution for this ??? pls help......

---

### Post by chewearn on 2008-01-09
> **vanitopooh said:**
> Sorry for my english 

I'm not so good at English, too, but I do learn to use capital letters and paragraphs.  Simple changes, and it will improve a lot.

Then, the people in the forum might know what exactly you are asking.
:(

---

