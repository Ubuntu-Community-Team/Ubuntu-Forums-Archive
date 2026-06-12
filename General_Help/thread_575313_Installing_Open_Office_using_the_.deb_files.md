---
title: "Installing Open Office using the .deb files"
date: 2007-10-13
forum: General Help
---

### Post by PmDematagoda on 2007-10-13
Ok, now I am trying to install OO on my teacher's Xubuntu computer, but the thing is when I click one .deb file it keeps on telling me about dependencies, I know what this means, but I don't know how to fix this, so how do I install OO on this computer? 

By the way, the apt-get is not an option as the computer is totally offline.

---

### Post by expatCM on 2007-10-13
The .deb file you have may be missing some required files (or found that the machine you are installing to is missing these files) which is why you get the message about dependencies.  Dependencies are the other files which the system requires in order to let the program run.  In the case of Open Office, having JRE on the machine can be quite important.  This however can be included in the initial Open Office .deb file download as long as you leave the check box marked ... 

Is this .deb file 135mb in size?    If not, you may want to download again from the OpenOffice.org site.

---

### Post by PmDematagoda on 2007-10-13
Yes, I have all the .deb files, now the thing is that when I try and install open office core1, it tells me it needs core2, but when I try core2 it tells me it needs core1, very confusing, I tried to get apt-get to recognise the .debs by specifying their location on the drive in the sources file, but I am not sure of the address.

---

### Post by expatCM on 2007-10-13
you say that you "have all the .deb files".    How many have you got and where did you get them from (since the Open Office download is just a single file)?

---

### Post by PmDematagoda on 2007-10-13
Directly from the OO website. And I have a 135Mb's of them.

---

### Post by expatCM on 2007-10-14
hmm ... this is a bit curious ...  what I have seen when installing OO is a single file for installation which contains a number of other files.   I have never had the occasion to look at individual files as part of the installation process.

---

### Post by PmDematagoda on 2007-10-14
Could you tell me how you installed OO?

---

### Post by expatCM on 2007-10-14
I installed the latest version as soon as it was released, I think there was no .deb at the time so what I did was the following from the CLI having unpacked the downloaded file first - 

./configure
make
sudo make install

If this route is to be followed, there is normally a Read Me file included with the downloaded files which you would see when unpacked.  This file normally spells out how to install (so that the dependencies are not an issue).

However ....  in downloading a .deb you should be able to get it to install by double clicking it and then clicking on Install from the window which then opens.

It does sound that you are having a lot of trouble with what should be a straight forward process.  Can you not use APTonCD to help you out here?

Please also note that you may find expert advice on the Open Office forum ....  :)

---

### Post by PmDematagoda on 2007-10-14
> Please also note that you may find expert advice on the Open Office forum .... 

Now why didn't I think of that?

> Can you not use APTonCD to help you out here?

Hmm, I have to try that.

Thank you for all your help and advice expatCM.:)

---

### Post by jocko on 2007-10-14
Instead of intalling the files one by one, try to install them all at the same time:
```
cd /path/to/files/
sudo dpkg -i *.deb
```

---

### Post by PmDematagoda on 2007-10-14
That seems like a good option, thank you jocko, I will try that and post what happens.

---

### Post by yosef on 2007-10-17
I just tried it and it seemed to work fine for me.  Thanx.

---

### Post by ReenenLaurie on 2008-03-04
I am having the exact same problem... but I want to upgrade from 2.2.0 to 2.3.1.

I downloaded the 135mb file from OOo, but then I could not install it in any way.

But AFTER UNINSTALLING 2.2.0, and I typed your command
sudo dpkg -i *.deb

It worked very well.  Thanks!  I am having trouble getting my OpenOffice.org-java-common installed though... :-/

---

