---
title: "A what if I have no access to wired internet?"
date: 2016-10-03
forum: General Help
---

### Post by ardouronerous on 2016-10-03
A what if scenario, what if I have no access to wired internet?

Reason why I am asking this? I might experience the same problem in the future.

Scenario: I move into a new house, my landlord lives next to me and grants me access to his internet with the use of his wireless WIFI modem, I agree, provided that I pay half the monthly internet bill.

The problem: I have to upgrade my Ubuntu distro, however, I have no access to wired internet. And of course, I cannot inconvenience my landlord by setting up my desktop computer in his house just to have access to wired internet to upgrade my Ubuntu distro.

Questions: does Ubuntu need internet access to do a full installation? Can I install Ubuntu without internet, then install the deb files ```
b43-fwcutter
``` and ```
firmware-b43-installer
``` which I downloaded from ```
http://packages.ubuntu.com/
``` using another computer, then when I get internet access, update the packages using the package manager? Or is there a way to set up my wireless router in the LiveCD environment without wired internet available?

---

### Post by kurt18947 on 2016-10-04
Here's an option I've used in the past, don't know if it's practical for you.

[http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/](http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/)

---

### Post by ardouronerous on 2016-10-04
> **kurt18947 said:**
> Here's an option I've used in the past, don't know if it's practical for you.

[http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/](http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/)

Unfortunately this doesn't help me though, because in the scenario that I've posted, there is no way for my desktop PC to communicate with any wired or wireless internet networks because by default the wireless driver isn't installed in LiveCD and in order for me to install the wireless driver or install Ubuntu at all, I need access to wired internet, which I do not have.

Which leads me to another question, why isn't the wireless drivers pre-installed on Ubuntu LiveCDs?

---

### Post by Bucky Ball on 2016-10-04
> **ardouronerous said:**
> Which leads me to another question, why isn't the wireless drivers pre-installed on Ubuntu LiveCDs?

There's *tons* of wireless drivers in the kernel, perhaps just not yours. Suggest you buy a wireless dongle that will work 'out of the box' with Ubuntu, live or otherwise, and you'll be prepared for any scenario. 

The reason the driver for every known wireless device is not in the kernel has little to do with Canonical. Suggest you contact the manufacturer of your device and ask them why they have not made an open-source linux driver available for your device. If it is a proprietary driver owned by a third-party Ubuntu can't legally include it in the kernel. You need to agree to that manufacturer's TOS to install their driver. Nothing to do with Ubuntu. :)

PS: Ubuntu doesn't need internet* at all* to install. Don't tick 'install third-party drivers' and 'update system' during the installation.

---

### Post by T2uiYKb7 on 2016-10-04
**[B][SIZE=2]@ardouronerous[/SIZE]**[/B][SIZE=2] I feel ya bro I have an x86 tablet that doesn't have a ethernet port and does require a non-kernel WIFI driver.[/SIZE]

Those packages you listed also require wget and bzip2 which off course have there own dependencies. I think that's all installed by default tho so you can simply install those packages like you said.

firmware-b43-installer is dependent on b43-fwcutter so install b43-fwcutter first.

Eg:

Browse to files, open terminal. Elevate to root/sudo however you want then,
[I]
dpkg -i b43-fwcutter

dpkg -i firmware-b43-installer

[/I]You can buy a USB WIFI dongle for literally a few dollars  (worldwide postage included) from shops like AliExpress and they have common new WIFI chips that are most likely in the kernel (on the live CD/USB.)

**Edit: If it asks for a bunch of other packages you can link your sources list (the thing that tells Ubuntu where to download applications) to a local folder where you can have everything necessary. Let me know if that happens.**

---

### Post by ardouronerous on 2016-10-04
> **Bucky Ball said:**
> There's *tons* of wireless drivers in the kernel, perhaps just not yours. Suggest you buy a wireless dongle that will work 'out of the box' with Ubuntu, live or otherwise, and you'll be prepared for any scenario. 

The reason the driver for every known wireless device is not in the kernel has little to do with Canonical. Suggest you contact the manufacturer of your device and ask them why they have not made an open-source linux driver available for your device. If it is a proprietary driver owned by a third-party Ubuntu can't legally include it in the kernel. You need to agree to that manufacturer's TOS to install their driver. Nothing to do with Ubuntu. :)

Okay thanks for that clarification Bucky, but isn't  firmware-b43-installer open source? If not, then I understand why it  isn't included in the kernel, but if it is open source, shouldn't it  come pre-installed?

> **Bucky Ball said:**
> PS: Ubuntu doesn't need internet* at all* to install. Don't tick 'install third-party drivers' and 'update system' during the installation.

Okay, just for clarification, I can install Ubuntu without the Internet by not clicking on 'install third-party drivers' and 'update system', okay, after installation, I can manually install the deb files 'b43-fwcutter' and 'firmware-b43-installer' and reboot, then Ubuntu would be able to detect my wireless card, then perform system updates afterwards, right?

> **andrew.nz said:**
> **[B][SIZE=2]@ardouronerous[/SIZE]**[/B][SIZE=2] I feel ya bro I have an x86 table that doesn't have a ethernet port and does require a non-kernel WIFI driver.[/SIZE]


Those packages you listed also require wget and bzip2 which off course have there own dependencies. I think that's all installed by default tho so you can simply install those packages like you said.


firmware-b43-installer is dependent on b43-fwcutter so install b43-fwcutter first.

Eg:

Browse to files, open terminal. Elevate to root/sudo however you want then,
[I]
dpkg -i b43-fwcutter

dpkg -i firmware-b43-installer

[/I]You can buy a USB WIFI dongles for literally a few dollars from shops like AliExpress and they have common new WIFI chips that are most likely in the kernel (on the live CD/USB.)

**Edit: If it asks for a bunch of other packages you can link your sources list (the thing that tell Ubuntu where to download applications) to a local folder where you can have everything necessary. Let me know if that happens.**

Thanks for the clarification, install 'b43-fwcutter' first, then 'firmware-b43-installer', thanks. :)

> **andrew.nz said:**
> You can buy a USB WIFI dongle for literally a few dollars  (worldwide postage included) from shops like AliExpress and they have common new WIFI chips that are most likely in the kernel (on the live CD/USB.)

**Edit: If it asks for a bunch of other packages you can link your sources list (the thing that tells Ubuntu where to download applications) to a local folder where you can have everything necessary. Let me know if that happens.**

Thanks for the suggestion, but AliExpress is owned by Alibaba China, which I had a bad experience with lol.

---

### Post by T2uiYKb7 on 2016-10-04
Yeah AliExpress and AliBaba are in the same boat as eBay when it comes to bad experiences. It's hundreds of different businesses under one umbrella.

I rarely get the cheapest option, I always make sure the seller has thousands of sales and above 97% positive feedback. It's normally roughly 10% - 20% more money than the cheapest seller. But still way less than buying at a local store.

---

### Post by kurt18947 on 2016-10-04
> **ardouronerous said:**
> Unfortunately this doesn't help me though, because in the scenario that I've posted, there is no way for my desktop PC to communicate with any wired or wireless internet networks because by default the wireless driver isn't installed in LiveCD and in order for me to install the wireless driver or install Ubuntu at all, I need access to wired internet, which I do not have.

Which leads me to another question, why isn't the wireless drivers pre-installed on Ubuntu LiveCDs?

The useful thing about wireless bridges is that the PC doesn't need any sort of wireless networking, only wired/ethernet. It's like plugging into a wall mounted ethernet jack. The router running dd-wrt provides the wireless networking connectivity. It works, I've used it in the past.

---

### Post by T2uiYKb7 on 2016-10-04
> **kurt18947 said:**
> The useful thing about wireless bridges is  that the PC doesn't need any sort of wireless networking, only  wired/ethernet. It's like plugging into a wall mounted ethernet jack.  The router running dd-wrt provides the wireless networking connectivity.  It works, I've used it in the past.


Wireless bridges are a good option if someone already has a spare modem (that doesn't have it's settings locked down by an ISP) I've used one as WIFI for an old desktop I let a flat mate use for a couple months.

If you're going to have to buy one a USB dongle with a common WIFI chip is a cheaper option.

Another option that uses things you may already have is use the USB tethering on a smart phone. Plug it in and find the tethering option on the phone it's self and it should just work.

---

### Post by ardouronerous on 2016-10-04
> **kurt18947 said:**
> The useful thing about wireless bridges is that the PC doesn't need any sort of wireless networking, only wired/ethernet. It's like plugging into a wall mounted ethernet jack. The router running dd-wrt provides the wireless networking connectivity. It works, I've used it in the past.

I've re-read your link again, and yes, I can see the usefulness of it, sorry it took me a while to figure it out, IT isn't my major lol :)

However, doesn't that mean I need physical access to the main router, my landlord's wireless modem,  while some people might be okay with it, but some might not be as accepting of someone touching their $50-75 modem, giving your WIFI password is fine, but having someone going through your modem's setup page is a different matter.

Thanks for the info, I'll save it for future reference!

---

### Post by QLee on 2016-10-04
> **ardouronerous said:**
> 
Scenario: I move into a new house, my landlord lives next to me and grants me access to his internet with the use of his wireless WIFI modem, I agree, provided that I pay half the monthly internet bill.

This wasn't part of your scenario but have you considered that all your Internet usage will be going through a router that someone else controls ?  If it were me, I would only do so if I was sure I could trust that other person.  They could throttle your bandwidth and that would only be a minor inconvenience.  At worst it would be trivial to monitor everything you do and/or restrict your access to things. 

I don't see why anyone would provide you with access to their Internet address if they don't know you very well already because they are accountable for anything done through that address.

I'm not trying to be scary,  just suggesting something that you may not have thought about. Personally, in the scenario you posed, I wouldn't do it.

---

### Post by T2uiYKb7 on 2016-10-04
> **QLee said:**
> This wasn't part of your scenario but have you considered that all your Internet usage will be going through a router that someone else controls ?  If it were me, I would only do so if I was sure I could trust that other person.  They could throttle your bandwidth and that would only be a minor inconvenience.  At worst it would be trivial to monitor everything you do and/or restrict your access to things. 

I don't see why anyone would provide you with access to their Internet address if they don't know you very well already because they are accountable for anything done through that address.

I'm not trying to be scary,  just suggesting something that you may not have thought about. Personally, in the scenario you posed, I wouldn't do it.

It's not as unlikely as you think. I've been in an apartment building that had that situation. I've also used a commercial WIFI (a well known company) when I lived down town where users created an account and paid per GB via credit card.

**Edit: Also all tablets and some laptops don't have Ethernet ports.**

---

### Post by QLee on 2016-10-04
> **andrew.nz said:**
> It's not as unlikely as you think. .

I don't think it unlikely at all, that's why I mentioned it. Pretty much the same for Internet in a coffee shop or elsewhere. You are in the LAN which may be configured as the owner sees fit.

---

### Post by T2uiYKb7 on 2016-10-04
It means buying an adapter whether you have access to the modem or not if you have an x86 tablet or certain ultra thin laptops. I just felt you were being a bit defensive, as if this situation shouldn't be one people put themselves in.

---

### Post by kurt18947 on 2016-10-05
> **ardouronerous said:**
> I've re-read your link again, and yes, I can see the usefulness of it, sorry it took me a while to figure it out, IT isn't my major lol :)

However, doesn't that mean I need physical access to the main router, my landlord's wireless modem,  while some people might be okay with it, but some might not be as accepting of someone touching their $50-75 modem, giving your WIFI password is fine, but having someone going through your modem's setup page is a different matter.

Thanks for the info, I'll save it for future reference!

No, the wireless bridge appears as a wifi adapter to the wifi host. You don't have to do anything to the host wireless access point. The magic happens in your router where the network data carried over the wifi stream is translated to ethernet available on your modified router's LAN ports. I thought I'd pasted a link but it doesn't appear so. If you have a supported router it's a cost-free option:

[http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/](http://www.makeuseof.com/tag/how-to-turn-an-old-router-into-a-wireless-bridge/)

Another option I've used in the past when confronted with a wifi card that requires a network connection to install is to use an [old hoary wifi network adapter]("http://www.trendnet.com/products/proddetail?prod=265_TEW-424UB") I keep in the back of an odds-n-ends drawer. It's slow and it's homely but it works with every linux distro I've tried for the past 6 yrs+. Use that to install the drivers/firmware for the faster sleeker sexier wifi adapter . Once the newer adapter's software/firmware is installed, shut down and remove old faithful USB adapter. Place it back in it's den where it waits until the next young sleek sexy wifi adapter fails :D.

---

### Post by jeremy31 on 2016-10-05
Something else that should work, copy the files you have in /lib/firmware/b43 and save them on a CD/DVD or whatever and then you could just make the b43 directory in the new install and copy the files after installing

---

### Post by Bucky Ball on 2016-10-05
> **jeremy31 said:**
> Something else that should work, copy the files you have in /lib/firmware/b43 and save them on a CD/DVD or whatever and then you could just make the b43 directory in the new install and copy the files after installing

Indeed it should, and has, and how to do that is [documented here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access"). :)

They're older instructions but will probably still work fine. You may like to have a look, jeremy31, as you know more about all things wireless than me.

---

### Post by jeremy31 on 2016-10-05
Thanks for posting that link Bucky Ball as Larry Finger has an archive that will do the same [http://www.lwfinger.com/b43-firmware/no_net_install_bcm43xx_firmware.tar.bz2](http://www.lwfinger.com/b43-firmware/no_net_install_bcm43xx_firmware.tar.bz2)

And see the post by [Hadaka](https://ubuntuforums.org/showthread.php?t=2316978) as I was going to search earlier as I knew somebody posted a b43.zip file

---

### Post by kurt18947 on 2016-10-05
> **QLee said:**
> This wasn't part of your scenario but have you considered that all your Internet usage will be going through a router that someone else controls ?  If it were me, I would only do so if I was sure I could trust that other person.  They could throttle your bandwidth and that would only be a minor inconvenience.  At worst it would be trivial to monitor everything you do and/or restrict your access to things. 

I don't see why anyone would provide you with access to their Internet address if they don't know you very well already because they are accountable for anything done through that address.

I'm not trying to be scary,  just suggesting something that you may not have thought about. Personally, in the scenario you posed, I wouldn't do it.

This seems a valid concern to me as well. Would a commercial VPN connection address it? Most of what I do (like surfing and posting here) I wouldn't be unduly concerned if someone were able to view it. Personal and financial communications are another matter.

---

### Post by T2uiYKb7 on 2016-10-05
^ It's not ideal, I remember being uncomfrtable about it at first. A VPN would stop info being stolen if you had reason not to trust it. HTTPS everywhere would be better than nothing. And keep an eye on your firewall.

[https://addons.mozilla.org/en-US/firefox/addon/https-everywhere/](https://addons.mozilla.org/en-US/firefox/addon/https-everywhere/)

[https://chrome.google.com/webstore/detail/https-everywhere/gcbommkclmclpchllfjekcdonpmejbdp?hl=en](https://chrome.google.com/webstore/detail/https-everywhere/gcbommkclmclpchllfjekcdonpmejbdp?hl=en)

---

### Post by QLee on 2016-10-06
> **kurt18947 said:**
> This seems a valid concern to me as well. Would a commercial VPN connection address it? Most of what I do (like surfing and posting here) I wouldn't be unduly concerned if someone were able to view it. Personal and financial communications are another matter.

Something like openVPN might be all that you need and wouldn't have monthly fees. As andrewNZ suggested, connection through the landlord's router would be encrypted. Do consider that there could be some performance hit (slowdown) involved but it might be negligible in your specific situation.

You are probably already using encryption between your system and your financial institution. If you aren't, then I suggest getting a new financial institution for online access.

---

### Post by monkeybrain20122 on 2016-10-06
I am in the situation you describe. In fact come to think of it I have never had access to wired internet at home. For the very reason you described I have a cheap usb wifi adapter in case I need to use the internet to get computer's wifi card to work. The usb dongle costs less than 10 bucks. Isn't great, but good enough to download wifi driver and such.

---

### Post by leunam12 on 2016-10-07
I always have a cheap Linksys WRT54G router with DD-WRT flashed on it and configured as a client bridge to have internet connection in order to download drivers and updates on new installs. It also works for printers, Bluray players, set top boxes and pretty much any device that has an ethernet port. Very useful. They cost 1 to 5 dollars at garage sales and thrift stores. Check the DD-WRT website for a list of flashable routers.

---

### Post by kurt18947 on 2016-10-07
> **leunam12 said:**
> I always have a cheap Linksys WRT54G router with DD-WRT flashed on it and configured as a client bridge to have internet connection in order to download drivers and updates on new installs. It also works for printers, Bluray players, set top boxes and pretty much any device that has an ethernet port. Very useful. They cost 1 to 5 dollars at garage sales and thrift stores. Check the DD-WRT website for a list of flashable routers.

I have the same. One thing to be aware of is that WRT54G are all G speed (54 mb./sec) AFAIK. They won't work with routers that are set to N speed only, the host router would have to be G & N speed. Something else that bit me re Linksys routers & DD-WRT. Some Linksys routers that support 5 Ghz. wifi don't support 5 Ghz. in DD-WRT. The 5 Ghz. radio is on the USB bus on the Linksys I have (E2500 V3).  DD-WRT doesn't have a driver that supports that configuration so 2.4 Ghz wifi only.

---

### Post by HermanAB on 2016-10-07
BTW, Edimax USB dongles work without hassles and cost almost nothing.  They even come with a friendly penguin picture on the package.

---

