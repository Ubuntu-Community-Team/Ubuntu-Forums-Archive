---
title: "Canon PIXMA iP4300 printing issues"
date: 2007-04-05
forum: General Help
---

### Post by The Pinny Parlour on 2007-04-05
Hi all,

Have followed the following website on installing the Canon PIXMA iP4300 printer on ubuntu.  
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

It installs ok and the test page prints perfectly, but when I go to print anything else, I get the item wanting to be printed along with the whole page covered in black.  Put another way, the whole page is printed black.

Any ideas?

Thank You

---

### Post by g8m on 2007-04-12
Same printer. Only on debian etch (desktop is ubuntu, server is debian). I followed the guide because printing with the Gimp showed some artifacts. It looked like the blue color was shifted in location. Giving a ghosting like effect. Then I realized that gimp is not using the system drivers. Tried printing the image with image-viewer and a perfect print rolled out of the printer.

---

### Post by g8m on 2007-04-12
At least in feisty, the PIXMA ip4300 drivers are present. Both in system and Gimp. So for my clients its only a matter of time.

---

### Post by pellgarlic on 2007-04-18
@g8m - can i ask if your comment about the pixma ip4300 drivers being present in feisty is drawn from experience? i am currently considering buying this model of printer, as my (vista-using) friend has recently bought it and it seems very good quality. however, i am concerned that it i might not be able to get it to work on linux. i have read the guide at [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview) and the ip4300 is mentioned in the first few lines, but i was hoping to get some feedback from someone who has actually tried the printer and got it working...

---

### Post by Smuve on 2007-04-18
I've had the iP4200 working in Edgy.  I just had to install the latest drivers from Gimp-Print.  The reason it works in Feisty is because Feisty uses the latest drivers, 5.1 I believe.  As long as you have the latest Gimp-Print installed the 4200 should work no matter which release you're using.

That being said, it works but it's not ideal.  It would print, but I couldn't get the color and crispness that I had in Windows.  That's why I ditched it and bought a cheap HP.  HP supports Linux, I'm going to support HP.  Canon's working on it, but they aren't there yet.  

If you've already got the 4200, that's one thing.  But if you're going to buy a new printer, I wouldn't get a Canon for Linux compatibility reasons.  It's unfortunate because they make great printers and I really liked the 4200 for its separate ink cartridges.

If you want my 4200, I'll sell it to you.  I just decommissioned it a couple weeks ago.  I bought an HP D1341.  They are bundled with a lot of computers and have huge rebates, so people are selling them for really cheap on ebay.  I got mine for $35.  It works great with the hplip drivers and hplip configuration tool.

---

### Post by pellgarlic on 2007-04-18
hi smuve, thanks for the reply, and for the offer :) unfortunately, i'm in the uk, so it wuld be a pain to take you up on your offer. besides, i think i'm gonna go down the hp route anyway... 

i'm looking at the d5160. not as high res as the ip4300, but as you say, hp seem to be much better on the linux-compatibility front. i find this very appealling in a company, unlike canon's attitude. their printers might be a bit better, but maybe they need to be taught a lesson :) (by little old me not buying their printer... i'm sure they'll cry over that...)

i also particularly like the principle hp have of making the cartdridge and head in one unit, meaning clogged heads wont kill a printer (as happened to an epson i had previously). as i leave the printer untouched and unused for sometimes months at a time, this is very important for me.

---

### Post by Smuve on 2007-04-18
You're welcome.  Yea, I mostly print documents and maps off the web.  I finally realized that a cheap printer that "just works" is better than a fancy one that doesn't.

I'm slowly learning how important hardware compatibility is with Linux.  Shortly after the printer, I also had to replace the wireless card in my wife's laptop.  

I spent countless hours trying to get an old Linksys PCI card with the Broadcom chipset to work.  Then I stopped and purchased a new DLink with the Atheros chipset.  I booted up and it connected to our network right away.  I couldn't believe how much time I wasted trying to get the Linksys to work.

Good luck with the new printer.

---

### Post by g8m on 2007-04-20
I cant comment on quality differences. I upgraded the printer from an old epson. Currently I dont have a XP to compare it with. Had some problems with my dual booted xp system ... it burned down in febrruary after a failed harddisk upgrade. Not a hardisk problem actually, but a power molar accidently landed on spif output connector of the motherboards soundchip. The motherboard really melted. 

But as far as I can tell, the minimal requirements I have for a printer are met. It prints documents. It prints my covers. Maybe the quality can be better, but I'm not into photo printing quality. It was just an replacement for an old printer, I had problems finding inkt cartridiges for. The printer wasnt really cheap, but I had Canon's in the past and liked the quality, and I wanted a printer with color based cartridges. Not having to replace the whole cartridge when it run out of blue.

Still waiting for a replacement motherboard for my motherboard for the other computer.


Actually, I am considering deleting the Xp install, because, I'm not really missing the microsoft stuff.

---

### Post by The Pinny Parlour on 2007-05-19
Heads-up:  [http://www.canon.com.au/support/wsss.aspx?id=ip4300&m=DR&r=http://www.canon.com.au/products/printers/colour_bj_printers/ip4300.aspx?m=support&h=http://www.canon.com.au/products/printers/colour_bj_printers/ip4300.aspx?m=support](http://www.canon.com.au/support/wsss.aspx?id=ip4300&m=DR&r=http://www.canon.com.au/products/printers/colour_bj_printers/ip4300.aspx?m=support&h=http://www.canon.com.au/products/printers/colour_bj_printers/ip4300.aspx?m=support)

---

