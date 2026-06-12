---
title: "Wireless Cards GUARANTEED  to work with Ubuntu"
date: 2006-09-04
forum: General Help
---

### Post by Mazza558 on 2006-09-04
Hi, 

I've given up hope with getting my Broadcom wireless card to work with ubuntu. Ndiswrapper, exact drivers, etc, to no avail. So for now, I've gone back to XP until Edgy Eft becomes a release version (much better support). Instead, is there a wireless card that is GUARANTEED to work out of the box with ubuntu, with no fiddling other than setting up WEP?

---

### Post by mbeierl on 2006-09-05
Fiddling - well minimal fiddling.  I bought a Trendnet TEW-424UB (wireless .11g usb network dongle - $29 CAD) and used ndiswrapper to install the .inf file from the install cd and it worked perfectly.  Not bad considering the price.

Just my $0.02...

---

### Post by Bagnaj97 on 2006-09-05
I've got a card with a RaLink chipset and it works perfectly out of the box with Ubuntu. I think cards with Atheros chipsets work as well. I also have a usb wifi adapter with a Zydas chipset, this is recognised by Ubuntu but it's driver didn't work for me. The driver from the zydas site compiled and worked easily however.

---

### Post by masterplumber on 2006-09-05
Agree.  I bought an Edimax wireless card (uses RaLink chipset) from ebay for 14 quid.  Worked a treat.

---

### Post by PriceChild on 2006-09-05
Yeah i got 3 RaLink PCI cards for £10 each and they work absolutely perfectly, even better than in windows where they lose connection sometimes on a fresh instillation :s

Pricey

---

### Post by xaos5 on 2006-09-05
I know one of intel's a/b/g works awesome on linux, just not ubuntu. Atheros works to a point but anything newer is going to probably have problems. look up madwifi for atheros drivers. I have the 5005g internal but I believe they make usb for the same thing. I'd recommend getting a 5004 for better support, even though I get better speed vs windows, I believe it reports signal lower and drops every once in a while.

---

### Post by PapaWiskas on 2006-09-05
D-Link Air Plus G Wireless DWl-G630 PC Card 
works fine for me both in Breezy and Dapper.

---

### Post by lupine_nickt on 2006-09-05
Anything Ralink works like a charm - they even have their own configuration utility. For maximum ease of use, look [here](http://www.ubuntuforums.org/showthread.php?t=240669)

xF,

...Nick

---

### Post by Cuppa-Chino on 2006-09-05
> **Bagnaj97 said:**
> I've got a card with a RaLink chipset and it works perfectly out of the box with Ubuntu. I think cards with Atheros chipsets work as well. I also have a usb wifi adapter with a Zydas chipset, this is recognised by Ubuntu but it's driver didn't work for me. The driver from the zydas site compiled and worked easily however.

Second the RaLink chipset! Had problems with ACX-100 chipset and also with Broadcom - although with a bit of patience and NDISWRAPPER they did work with WPA.

RaLink worked pretty much right off the mark, got an EDIMAX card on ebay for 14GBP or 24U$ delivered and after 30mins was up and running with WPA - this thread is useful : [RaLink RT61 Wireless Solved - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=132980")

---

### Post by ewl1217 on 2006-09-05
If you don't mind trying to get your current card to work, we might be able to help you. If you want to try with that, insert the card into your computer and run the following two commands:
```
lspci
```
```
lspci -n
```
Just post the output of those two here and we might be able to get somewhere.

---

### Post by almrking on 2006-09-05
I bought a TrendNet TEW-443PI from newegg.com for $28.00 and it was plug and play, no ndiswrapper, nothing. I was running in less than 2 minutes. I had struggled with a D-Link usb for 2 weeks before I gave up. This card is so good it even picks up wireless networks down the street.

---

### Post by wordsmythe on 2006-09-06
Can anyone think of a network card that's got a wireless antenna and a cat5 jack?  I'm thinking of turning my ubuntu box into a wired/less router.

---

### Post by wbeck85 on 2006-09-06
If you are planning on using the ubuntu machine as a wireless router, I recommend using seperate wlan and ethernet NICs. There is no need to have both on the same card, in fact it would probably be beneficial to NOT have them on the same card. Keep in mind that they need to have different addresses anyway to bridge the wireless with the wired.

I strongly recommend a powerful wifi card with an atheros chip that supports the madwifi-ng driver. Basically any standard ethernet card will do. Unless the reason you need the dual capable card is because you have are referring to an older laptop that is lacking both wifi and ethernet capabilities and only has one PCMCIA slot. In which case, good luck, because I doubt there are any wifi/wired pcmcia cards around.

---

### Post by muggins on 2006-09-06
> **mbeierl said:**
> Fiddling - well minimal fiddling.  I bought a Trendnet TEW-424UB (wireless .11g usb network dongle - $29 CAD) and used ndiswrapper to install the .inf file from the install cd and it worked perfectly.  Not bad considering the price.

Just my $0.02...

I have the same adapter TEW-424UB and would like to know how you used ndiswrapper to install the .inf file. Have not any luck so far with ndisgtk. Am new user with ubuntu.

---

### Post by mbeierl on 2006-09-07
I actually went to the terminal (Accessories -> Terminal).

First mount the cdrom (insert and if it does not mount automatically, run mount /media/cdrom or sudo mount /media/cdrom in the terminal window)

I don't have the CD near me right now, but there was a directory something like drivers/WinXP on the CD.  Look for that directory and you'll find the .inf file in there.

Once you've found it, use the following to install it:

sudo ndiswrapper -i /media/cdrom/path-to-inf/file.inf

(replacing the path-to-inf/file.inf with the real path, of course)

Next,

sudo ndiswrapper -m

That writes the module line for next reboot.  The module itself I cannot recall, but you do need to do a 

sudo modprobe <name of module> 

to get it to load.  After that, it was straightforward network configuration using the GUI.

Hope this helps.  I'll try to get more info later today when I get home and back to the machine that I did this on.

---

### Post by Gaijin on 2006-09-07
A good Pcmcia adaptor with a Ralink chipset and low price seems to be the SWEEX LC500070, I've just bought some from Scan for £13.38 ea inc VAT from [http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=219264]("http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=219264")

Look here for other Ralink chipset cards:

[http://ralink.rapla.net/]("http://ralink.rapla.net/")

I've struggled for hours trying to get Broadcom (Belkin)and Incomm (Linksys) chipset cards to work in the past and have decided it's just easier to getsomething that I know will work out of the box!

---

### Post by mabhatter on 2006-09-11
> **Mazza558 said:**
> Hi, 

I've given up hope with getting my Broadcom wireless card to work with ubuntu. Ndiswrapper, exact drivers, etc, to no avail. So for now, I've gone back to XP until Edgy Eft becomes a release version (much better support). Instead, is there a wireless card that is GUARANTEED to work out of the box with ubuntu, with no fiddling other than setting up WEP?

sorry this is long, it's a repost from another thread...

Like you, I'm sick of f***ing around with wireless and was dying to find something that "just worked". I ran to dinner the other day after work bonuses (yea!) and researched BB's website and the Linux compatible website listed on the wiki page. I only found 3 that looked compatible with all "greens" There were two netgear ones listed WG511T and WPN511 Both were labled on the box as Atheos chipsets.. score 1 point. Anyway, I picked the more expensive one the WPN511 (the labeling looked more promising?). It worked out of the box with the live CD of Kubuntu and Ubuntu 6.06 with the only setup being SSID and WEP key.. another note, it didn't seem to like "shared" keys or broadcast disabled SSID.  I live in a quite neighborhood so I didn't fight it, just changed it to work.. but that may be an issue for you.  I was so happy I didn't bother looking at iwlist till just now and it says I'm getting almost the full 54 Mb.

Seriously, I'm on this card right now. The Only downside was that to get it working on my Dell Latitude C610, I had to reinstall Ubuntu but that could have been because I had an upgraded setup from breezy beta thru Dapper... but with the Live CD recognizing it, it was a sure bet to work with a install.

Normally I don't hype products, particularly Best Buy, but in this case they happened to be the only retail with anything from the "green" list.. and it happened to be in stock.

---

### Post by gzenitsky on 2006-09-11
Here's a vote for Linksys WMP54G. Worked out of the box in 6.06 LTS. Signal strength better than my Netgear WG111T USB which of course will never work in Linux. The WMP54G cost me $49 at a local Office Depot. It's more than I would have liked to pay but it was handy and I was in a hurry!

---

### Post by junior aspirin on 2006-09-11
yup Linksys WMP54G for me too. has to be a V4 though i understand.

plug it in and go go go.... :p

---

### Post by NeoGreen on 2006-09-11
I am installing one right now, hope I dont run into any problems.:confused:

---

### Post by NeoGreen on 2006-09-11
Okay, what Ubuntu version did you use Breezy or Dapper?  I am using Breezy, will I run into problems if I am Breezy?:confused:

---

### Post by NeoGreen on 2006-09-11
Man, I installed a fresh copy of Breezy on this computer and I got an Error 18 message.  I replaced the old harddrive (10GB) with a new Seagate (200GB) and it seems that my Bios can't handle it.  :mad:

---

### Post by Cynical on 2006-09-11
Here is a list of wireless cards supported in linux for anyone interested.

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

---

### Post by Bokonon on 2006-09-12
While I can't guarantee anything, I have gotten the following cards/chipsets to work.

Intel 2200 B/G
Intel 3945 B/G
Atheros 5006XS B/G

---

### Post by eldaria on 2006-10-28
Well, while looking for how to get my Netgear WG511T card working on my Edgy, I came across this thread.

The card works perfectly in Kubuntu 6.06 Dapper, no reinstall, nothing, I just plugged it in and it worked, to get WPA support, I installed knetworkmanager, and have been running that for a while.

Upgraded to Edgy, and card is no longer working, a reinstall also does not get the card working.

---

