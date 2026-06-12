---
title: "Is an Epson Workforce WF-2835 printer compatible with 20.04?"
date: 2021-09-17
forum: General Help
---

### Post by Extreedoc on 2021-09-17
The title says it all - does anybody know?

---

### Post by bcschmerker on 2021-09-17
**The EPSON® WorkForce 2830 Series drivers are available in Red Hat RPM format from [Download.EBZ.Epson.net](https://download.ebz.epson.net/dsc/search/).**  Recommend install the alien package first:
```
sudo apt install alien
```which should mark Depends for co-installation.

---

### Post by Extreedoc on 2021-09-18
Thank you, I'll give it a go and post results later.

---

### Post by Extreedoc on 2021-09-18
Problem!! The link to the drivers doesn't work: I don't have permission...

---

### Post by coffeecat on 2021-09-18
I get the forbidden message too. 

A brief google search came up with this: [https://www.freeprinterdriverdownload.org/epson-workforce-wf-2835-driver-download/](https://www.freeprinterdriverdownload.org/epson-workforce-wf-2835-driver-download/)

The 64-bit Linux and Ubuntu download links appear to be for deb packages, so you won't need alien. That all being said your original question was asking whether the Epson WF-2835 is compatible with Ubuntu 20.04, which to me reads as though you are asking this before committing yourself to purchase of the machine, rather than trying to get an Epson machine set up. Perhaps you could confirm which. I'm afraid I can't help any further as I have no recent experience with Epson printers, but good luck anyway.

---

### Post by Extreedoc on 2021-09-18
> **coffeecat said:**
> I get the forbidden message too. 

A brief google search came up with this: [https://www.freeprinterdriverdownload.org/epson-workforce-wf-2835-driver-download/](https://www.freeprinterdriverdownload.org/epson-workforce-wf-2835-driver-download/)

The 64-bit Linux and Ubuntu download links appear to be for deb packages, so you won't need alien. That all being said your original question was asking whether the Epson WF-2835 is compatible with Ubuntu 20.04, which to me reads as though you are asking this before committing yourself to purchase of the machine, rather than trying to get an Epson machine set up. Perhaps you could confirm which. I'm afraid I can't help any further as I have no recent experience with Epson printers, but good luck anyway.

Thanks Coffeecat, you are right, I am considering buying the Epson. I have had no luck with printers since getting 20.04. I want an ink jet suitable for home use and preferably one which will work 'out-of-the-box' rather than have to search out drivers online. I had an HP deskjet that I rescued from a neighbours bin which worked straight away but has now expired.

If anybody can suggest a printer which will fit my bill... Please do, things are getting desperate here!!

---

### Post by ActionParsnip on 2021-09-18
[https://www.openprinting.org/printers/manufacturer/Epson/](https://www.openprinting.org/printers/manufacturer/Epson/)

Pretty authoritive list here

---

### Post by ActionParsnip on 2021-09-18
[https://www.turboprint.info/printer_Epson_WorkForceWF2830DWF.html](https://www.turboprint.info/printer_Epson_WorkForceWF2830DWF.html)
Maybe TurboPrint can help. It's not free in any way (Not open source and does cost money) but may work. Could be an avenue to explore but the site says the scanner doesn't work. Could send them an email to see if their software will make you able to print at least (costs 40 Euros)

---

### Post by Extreedoc on 2021-09-18
OK, I've took the plunge and bought the Workforce 2835 and downloaded the driver from your website. Problem is that I get something called an image scan bundle containing: 'Core' a folder, 'Plugins', a folder, Install.sh, a shell script and 'Readme'. Now I'm at a loss because I'm instructed to double click the folder and choose: Next/Continue/Install. Nothing I do gives me that option. I've clicked 'Extract' so now I have the bundle on my home page but how do I proceed?

---

### Post by Extreedoc on 2021-09-18
On reading the 'Readme' I see that installation involves entering a line of code in the terminal, this I am reluctant to do as there are warnings that it might not work, that some parts are 'non free' and can be left out of the install and so on... Unless anybody knows of a less complicated driver, not involving Terminal that is available, I am thinking of returning the printer and... well, giving up. All the other distros of Ubuntu I've had have just worked with my old printer, but not 20.04.

---

