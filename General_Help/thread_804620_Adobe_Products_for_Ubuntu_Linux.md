---
title: "Adobe Products for Ubuntu Linux"
date: 2008-05-23
forum: General Help
---

### Post by Avinash.Rao on 2008-05-23
Hello all,

I am new here. I am planning to replace windows computers with Ubuntu. But, i am in need of Adobe Products like Adobe Pagemaker, Indesign, Illustrator, Photoshop etc for Linux. I searched the Adobe site but didn't find anything concrete. I am wondering if Adobe products runs on Linux. I am writing to find out if there are any software similar to these products that runs on Linux? 

Thanks
Avinash

---

### Post by Randall Flagg on 2008-05-23
> **Avinash.Rao said:**
> Hello all,

I am new here. I am planning to replace windows computers with Ubuntu. But, i am in need of Adobe Products like Adobe Pagemaker, Indesign, Illustrator, Photoshop etc for Linux. I searched the Adobe site but didn't find anything concrete. I am wondering if Adobe products runs on Linux. I am writing to find out if there are any software similar to these products that runs on Linux? 

Thanks
Avinash

hello!..
well, there are several softwares like those you said...
Illustartor, is inkscape..
Photoshop, Gimp
in desing and pagemaker.. neve used them, so I cant say which is a replace for that... :S

Now, for inkscape and gimp.. well, they are NOT adobe products, so don't wait this will be the same, and there'll be several differences.. At the beggining you'll say: danm! in photoshop i could do this in no time...

with time you'll understand gimp and inkscape...
In any case, for example, in my ubuntu, I can't seem to find a program like Dreamweaver, so I use the Macromedia Dreamweaver on my ubuntu with Wine... and goes perfect :D

Find out more about wine ===> [**HERE**](http://winehq.org/)


:popcorn:

---

### Post by cherva on 2008-05-23
Why don't you install WINE and see how do they run with it or check them in the Wine Application Database [http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by Avinash.Rao on 2008-05-23
Thank you for your response.

I am new to wine, so let me read and get back

Avinash

---

### Post by Zorael on 2008-05-23
Adobe doesn't develop linux versions of those applications. We're "lucky" to get Flash, which at many points comes across as a poor port.

As above posters mentioned, there are linux-native alternatives (Inkscape, Gimp) which will likely be enough for standard home use. If you need Photoshop for professional work, you'll find Gimp lacking, and as such you'd either need to run Photoshop under Wine, or under a virtual machine running Windows.

See [http://www.osalt.com](http://www.osalt.com) for a small database of open source alternatives to common proprietary locked-to-windows/mac applications.

---

### Post by Avinash.Rao on 2008-05-23
Thanks for providing the link.

---

### Post by DJ_Peng on 2008-05-23
For desktop publishing I recommend [Scribus]("http://www.scribus.net/"). I believe Indesign is a web publishing program and I have yet to find an open source program that makes me happy. Hopefully you can find that it runs well under Wine.

---

### Post by maonet on 2008-05-23
Yes I need to run all adobe master collection CS3 as well for work, it is my life, Gimp is very nice and powerful, but Photoshop CS3 is so much more... I guess I steel needs windows but i will not give up Ubuntu Rocks \\:D/

---

### Post by Avinash.Rao on 2008-05-24
Yeah, Ubuntu is really cool but we are dependent on Adobe products! And if i am able to find any open source, i can replace all windows computers with Linux.

---

### Post by DJ_Peng on 2008-05-24
I thought I saw CS3 works pretty well under the current WINE (included with Ubuntu, not necessarily the current version from winehq.com), but I just checked the [WINE AppDB]("http://appdb.winehq.org/") and saw I was wrong. You may be able to copy a Windows install of CS3 and get it working under WINE, but I didn't check that deeply.

GIMP is nice, but nothing is quite as nice, or as easy, as Photoshop unfortunately. And for web development nothing meets the level of DW for easy of use or features.

---

### Post by eldragon on 2008-05-24
if you actually bought the adobe products you mention, you could always mail support @ adobe and ask them for the linux-native versions of their products. make them notice :D
they will probably not care, but they could see the trend if many do the same.

---

### Post by Avinash.Rao on 2008-05-26
Guys,

I installed Wine and Adobe Photoshop 7. It works pretty well.

I would request people who are using windows applications under wine to write if you have found any problems.

Also, i am planning to implement Samba so that users will be storing all data on the server. Now, how does Wine store data, will i be able configure wine or any Windows application to store data on the server automatically. 

Or i think its as simple as using the File - save as option and select the network drive to store data.

Thanks a ton
Avinash

---

### Post by Avinash.Rao on 2008-05-26
> **eldragon said:**
> if you actually bought the adobe products you mention, you could always mail support @ adobe and ask them for the linux-native versions of their products. make them notice :D
they will probably not care, but they could see the trend if many do the same.


I will write to them right away.

Avinash

---

### Post by Avinash.Rao on 2008-05-26
Hi Guys,

I have tested Photoshop and it seems to be working fine.

I have also tested LTS and the clients can boot through the network and works really cool. Now, will just one install of Adobe on the linux server suffice for 30 clients?  I will be installing multiple Adobe products using wine. The requirement is 30 users booting through the LAN and using Linux and Adobe products. I have no doubts on Linux, will the Windows Application work when multiple users access the same exe file? 

Thanks
Avinash

---

### Post by melenor on 2008-05-26
Alright quick question if i have both Adobe CS3 and Mircosoft Office 2007 will any of these work under wine? i know of the open source alternatives but i have to use these. thanks

---

### Post by Avinash.Rao on 2008-05-27
I checked the Wine Configuration tool and saw all the windows Operating Systems are supported. So, i guess it supports application for these operating systems. 

The best way is to install it and check

Avinash

---

### Post by randytan on 2008-12-02
Hi Guys and Gals! :KS

Any updates regarding this?

Will be running Ubuntu by this week and need to know if I should make a small partition for windows xp just to run the Adobe stuff.

Thanks! :guitar:

---

### Post by DJ_Peng on 2008-12-02
The best place to check is the WINE [AppDB]("http://appdb.winehq.org/"), which is their database of how various programs work with WINE. It looks like some parts of Adobe CS3 work better than others so you'll have to search for the particular components to see how they'd work under WINE. As for [Microsoft Office 2007]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3514") it looks like the installer has worked under Hardy but nobody's given results for Intrepid yet. Again, different components have different success rates so you'll want to check for the specific component you need to run.

When you're checking programs on the AppDB look at not only the results provided but all of the information provided. You may need to follow a specific set of instructions to get the best results.

---

### Post by randytan on 2008-12-02
Thanks DJ Peng,

I'll check it out. Actually, I only need to run the CS2 stuff for now. ;)

---

### Post by azenquor on 2010-06-09
feel free to check out [http://www.osalt.com/](http://www.osalt.com/) it give a list of commercial/windows programs and there open source alternatives.

---

