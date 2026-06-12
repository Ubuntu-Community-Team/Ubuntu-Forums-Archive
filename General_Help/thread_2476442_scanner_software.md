---
title: "scanner software"
date: 2022-06-26
forum: General Help
---

### Post by jgw on 2022-06-26
I need to install printer scanner spoftware.  Its been a while since I used my scanner.  I had vuescan but its gone and I have driven the author crazy before when I lost the software so I thought I would just install another.  From what I have read I should install 'sane' and then install 'xsane' and that should do it but thought I had better ask here to make sure that is what I should do.  

Thank you.............

---

### Post by yancek on 2022-06-26
xsane is a gu for sane, other options discussed at the link below.

[https://en.wikipedia.org/wiki/Scanner_Access_Now_Easy](https://en.wikipedia.org/wiki/Scanner_Access_Now_Easy)

---

### Post by mIk3_08 on 2022-06-27
> **jgw said:**
> I need to install printer scanner spoftware. Its been a while since I used my scanner. I had vuescan but its gone and I have driven the author crazy before when I lost the software so I thought I would just install another. From what I have read I should install 'sane' and then install 'xsane' and that should do it but thought I had better ask here to make sure that is what I should do.
Thank you.............
Here also it might help you on the installation of xsane.
Below are what you need to install xsane.
```

sane 
sane-utils 
libsane-extras 
xsane
```



If you want to install simple-scan also:
```
apt install simple-scan
```
or install it from snap
```

apt install snapd
snap install simple-scan
```

Regards and cheers.

---

### Post by TheFu on 2022-06-27
I use gscan2pdf.  It will optionally perform OCR and place the text underneath the image inside the PDF file.  There are times when this is handy.
If the scanner is supported by SANE, you are lucky.

Printing and scanning are completely different and use different libraries/tools.

If it were me, I'd avoid using any snap package, since I often want to place scanned files in places that snap constraints won't allow.

---

### Post by Holger_Gehrke on 2022-06-27
Before trying to use SANE, you might want to take a look at the [list of supported devices]("http://www.sane-project.org/sane-mfgs.html"). VueScan supports more than 6000 different devices, SANE about 1700. Granted, the Vuescan number might be somewhat inflated by counting identical devices sold under different names multiple times, but there are devices for which VueScan has support and SANE does not. I remember owning a cheap HP branded consumer grade flatbed scanner with a Genesys chipset back in the early to mid  2000's which wasn't supported by SANE (details on the chipset only available under NDA ...) which worked with VueScan (still didn't buy it, I was dual booting back than and used Windows when I needed to scan something).

Holger

---

### Post by TheFu on 2022-06-27
Newer scanners will work without any computer connection. Just connect an SDHC or USB storage device and choose "Scan to .... " button.  When my brother MFC finally dies, I'll get a cheap replacement that scans to USB storage and never worry about Linux compatibility again.

I have an old Brother MFC 240C ($65) from 2008. It is USB only. When the tiny demo-ink ran out, I never replaced it.  I use a Laser printer for printing, but wanted an ADF (automatic document feeder) for the scanning and faxing side of the MFC.  I'm not interested in using any network connection, since many of these devices mandate phoning home to work.  I have a hard time spending money on proprietary scanning software that costs almost as much as the hardware.

My LUG email list has been discussing different scanners recently.  "Maddog" Hall says he uses a Brother MFC-J6945DW Color Printer/Scanner over wifi and it just works with simplescan.  He's using Linux Mint 19.3 and a 5.4 kernel.  That's an expensive device.


The lesson here is to buy hardware that follows standards so funky drivers aren't needed.

---

### Post by jgw on 2022-06-27
Thank you for all the replies!  I will mark this one done.

---

### Post by jgw on 2022-06-29
Thanks again for all the replies.  

I took a chance that I could use vuescan emailed ed hamrick.  He told me how to recover stuff from him.  The problem there is that he wanted to know the last four from my credit card I used in 2001 <G>  Then I rooted around some more and downloaded vuescan from his site and am now in the process of registering it.  It worked for me but I still haven't gotten it registered but have faith.

Thanks again!

---

