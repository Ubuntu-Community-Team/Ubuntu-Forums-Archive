---
title: "Installing Wibu without downloading Ubuntu"
date: 2007-06-11
forum: General Help
---

### Post by Churito on 2007-06-11
**Please help,**I've just downloaded Wibu and when installing it tries to download an Ubuntu7.04-i386- alternative version, well, I've already have in a CD an Ubuntu 7.04 LiveCD desktop-i386 version that I downloaded a weeks ago  in order to try installing in my HD but as I'm zero linux daren't to do because of partitions troubles. I have a HD 200GB, C:=40GB WinXP-Pro and D:=160GB data-music-videos, etc. My question is: should I go on downloading the Ubuntu version that Wibu tries to download and wait for 13 hours to complete? or,  in another way I can install from my LiveCD? or, could I download the same version Wibu wants to from where? In this way I could use a download manager (MassDownloader, for instance) reducing download time. Please, answer with a nice solution, thanks a lot.:)

---

### Post by Nekiruhs on 2007-06-11
Btw the way its wUbI. not wIbU. But wubi's only capable of installing from and Iso. If you were able to find where Wubi looks for the Iso (probably in your temp files). you could place your Iso there.

---

### Post by CrazyGuy123 on 2007-06-11
wubi will accept any ubuntu 7.04 alternate version iso, if the iso file is put in the same place as the wubi.exe installer.  It will automaticly find it and skip the download.

You can't use a LiveCD version, because that contains different data.

You can download the file directly from here:
[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

the version you want is probably:
 ubuntu-7.04-alternate-i386.iso

---

### Post by Churito on 2007-06-11
Yes, sorry, it's **Wubi** and thanks for your answers. I already have an ISO in my HD so I'll try to redirect Wubi to its folder or move to installer folder.;)

---

### Post by Nekiruhs on 2007-06-12
Are you certain its the alternate ISO, Wubi only uses the alternate ISO, not the live CD.

---

### Post by Sushubh on 2007-06-15
wubi works fine with the alternate ISO... just run the installer with the ISO file in the same folder. it copies to the proper location and installs it from there.

---

### Post by ChuroMax on 2007-06-23
**OK, it was really nice!** I installed WUBI and Alternate version of Ubuntu 7.04 and worked fine. Now I dared to format, convert partition to **logic extz.2 + swap file** and install Xubuntu v.7.04 Feisty Fawn in my HD with WXP-Pro installed and had no problems AT ALL!:D Now I'm in Firefox from Xubuntu writing this post and am really pleased! :popcorn:

---

### Post by ChuroMax on 2007-06-23
**I'm very sorry since I posted as Churito and ChuroMax, but I couldn't log with my first nick and had to create a new one. Hope have no problems in the future:D**

---

### Post by Sushubh on 2007-06-23
awesomeness!

---

### Post by MacMhuirich on 2007-07-10
I've tried putting the iso in the same folder as the installer. The The installer moves the iso into the wubi directory then tries to download which overwrites the iso. I've also let the thing download several times and it just starts downloading again. I've uninstalled, I've cleared out the temp folder, I've cleaned with Norton Cleansweep. Any suggestions?

---

### Post by ago on 2007-07-10
> **MacMhuirich said:**
> I've tried putting the iso in the same folder as the installer. The The installer moves the iso into the wubi directory then tries to download which overwrites the iso. I've also let the thing download several times and it just starts downloading again. I've uninstalled, I've cleared out the temp folder, I've cleaned with Norton Cleansweep. Any suggestions?

Hmm that might be because the checksum is not correct. Download the iso manually, do a checksum to veify that there where no transmission errors, then use a copy to install.

---

### Post by KMFDM on 2007-07-13
i downloaded ubuntu-7.04-alternate-amd64.iso

simply because I have an AMD64, I dont want to use i386.

I checked the checksum. match.

I put amd64.iso file in folder with Wubi-7.04.03.exe

I do install. every time it tries downloading the i386.iso

??????:confused:

---

### Post by ago on 2007-07-13
64 bits are not supported at the moment, you can still install 32 bits.

---

### Post by KMFDM on 2007-07-13
> **ago said:**
> 64 bits are not supported at the moment, you can still install 32 bits.

noooo!!! :(
i'm sure there's a reason why but I don't have a idea what it could be. i mean it just installs right? how could 64 or 32 make any difference unless wubi is running all times while running linux?

---

### Post by ago on 2007-07-13
because we would need to compile and maintain a second initrd, and since I (and the other devs) do not have a 64 bit machines that is not going to happen.

Of course if someone wanted to donate a 64 bit machine I would reconsider :D

That said once wubi is included with gutsy it will come to all archs supported by ubuntu.

---

### Post by KMFDM on 2007-07-13
> **ago said:**
> because we would need to compile and maintain a second initrd, and since I (and the other devs) do not have a 64 bit machines that is not going to happen.

Of course if someone wanted to donate a 64 bit machine I would reconsider :D

That said once wubi is included with gutsy it will come to all archs supported by ubuntu.

ok. is it easy to install 64 support on my own after installed i386?

---

### Post by KMFDM on 2007-07-13
> **ago said:**
> because we would need to compile and maintain a second initrd, and since I (and the other devs) do not have a 64 bit machines that is not going to happen.

Of course if someone wanted to donate a 64 bit machine I would reconsider :D

That said once wubi is included with gutsy it will come to all archs supported by ubuntu.

another thing i am curious about...in the 'install' folder under wubi on the target install drive...it has a collection of metalink files, both i386 and amd64 of ubuntu, xubuntu, kubuntu and lupin devel...why are these files there to be used if 64bits isn't supported? was it in the works to do so and then forgot to get removed or something?

---

### Post by ago on 2007-07-13
yep we worked on those, have the metalinks ready thanks to Hampusw (who has a 64bit machine), but did not follow up, as mentioned the required step is to have a second initrd secifically compiled for such machines.

My view is to try wubi32 bit, if you like what you see, do a real 64 bit installation.

---

