---
title: "Requesting help on getting software to run"
date: 2018-09-11
forum: General Help
---

### Post by mcristofaro on 2018-09-11
Hi all
My very first post, I have installed Ubuntu 18.04 and the latest version of Wine. Some applications work fine after being installed with Wine but not the application which i would really like running on Ubuntu.
The program im trying to run is Amibroker. There is a 30 trial on thier website if someone would like to try it. It installs fine but when i try to launch the program nothing happens. What are some things that i could try to get it to run? Im a complete newbie to Linux so im pretty much clueless. 
Any advise would be appreciated.
Thanks

---

### Post by rbmorse on 2018-09-12
Ay yi yi.  You've picked a big piece for your first bite. 

I didn't see any information about the latest version of Amibroker running on a Linux host computer using WINE.  The last input is a couple of years, and I assume versions, old and that indicated that the main program can be made to run (it looks like there are some extra steps beyond just installing WINE and the application) but a key auxillary function, AMIQuote (that pulls the latest prices for you holdings into the main program) does not work under Wine and no one has figured out how to make it work. 

You may be lucky. I'm thinking this situation is a perfect candidate for setting up a Windows virtual machine that runs on top of your Linux host.  This is the solution recommended on the Amibroker website.  Setting this up is not difficult, but it looks like the Amibroker software requires a machine with substantial resources, on top the requirements to run the virtual machine hosting software.  I would not try it on a low capability PC or laptop.  

Tell us about your machine...specifically, make model and how much RAM is installed and how much free space is available on your storage disks and how it's arranged.  If you need help with that, let us know.   

Also, check this page: [https://alternativeto.net/software/amibroker/?platform=linux](https://alternativeto.net/software/amibroker/?platform=linux) .  I can't vouch for any of these, but the site claims they are linux applications that do the same thing (more or less) as Amibroker. Give 'em a try.

---

### Post by mcristofaro on 2018-09-12
Thanks for your response, AMIQuote is not important because i import end of day data manually. My laptop is a cheapy brand, i bought it at Aldi. It has an i5 processor, 8gb ram and a 500gb HDD there is more that 250gb free. The reason why i would like to run it on Ubuntu is that Windows is too slow on my laptop, Ubuntu runs much faster. Im just about the check out that link right now. BTW could an old version of WINE fix the issue?
Thanks

---

