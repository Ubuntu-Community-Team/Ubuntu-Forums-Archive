---
title: "Please help me leave Windows!!!!"
date: 2008-05-24
forum: General Help
---

### Post by rakan_dr on 2008-05-24
Hi guys I want your help to let me leave Windows.
Actually 2 things let me stick to Windows which are the Adobe CS3 and my Dial up modem .
1- I'm a Web designer and developer so Adobe CS3 is very important to me especially Photoshop, Dreamweaver, Illustrator, Flash ...etc.

2- My modem is Genius GM56PCI-SA internal.

Please guys I want to leave Windows I hate that system, my computer is full with viruses and Malware.

Anyway Adobe products are the most important to me because I can buy an external serial modem but I hope not!

I hope you find solutions for my problems. If you can't, I have the only expensive choice which is Apple Mac for the Adobe products.

Thanks

---

### Post by yaztromo on 2008-05-24
1. Most adobe apps run okay in WINE. Check the wine app db here [http://appdb.winehq.org/](http://appdb.winehq.org/)

Wine is available as simple download from the synaptic package manager.

2. Internal cards are known to be troublesome on Linux. You may have some look googling but I would recommend buying an external serial modem such as 3com/US Robotics, these are well supported.

edit: Also try the Ubuntu Modem HowTo before looking for a new modem: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by IHATEDLINK on 2008-05-24
I **_REALLY_** don't advise you to completely switch if you need the Adobe products.
But if you still want to switch WINE HQ can rune some of the adobe apps.
And for the modem, first try using a live cd just to check if if it doesn't, start a thread asking for help with it.

---

### Post by latna on 2008-05-24
For the modem you might have a look at [http://www.linmodems.org/]("http://www.linmodems.org/")

---

### Post by geo909 on 2008-05-24
> **IHATEDLINK said:**
> I **_REALLY_** don't advise you to completely switch if you need the Adobe products.


+1 to that.

You can use windows only for the adobe products and have lots of other services stopped so it will be really fast. If you only use them for your work you are not going to get viruses (except if you crack the adobe programs you use ;)).

Another option is to use a virtual machine, like virtualbox to install windows inside your desktop. But this way you will have to spare your ram, so  maybe it's not the perfect solution.

 It's not so bad to have dual boot. That's the way I use cubase for recording purposes. Since I use windows ONLY for that, I've never had a single virus.

---

### Post by rakan_dr on 2008-05-24
Thanks guys a lot for your help, you gave me pretty solutions.

I just want to ask you if the Adobe products that work on Wine work completely perfect or not?
Also does Internet Explorer work on Wine? Because I have to test my websites on it also not only on Firefox.

Actually guys I'm really thinking to make a Virtual Machine for Windows to run Adobe apps, but I have also the same question:
Will Adobe product work perfectly on the Virtual Machine? I mean with the FULL features?? or I'm going to face some problems?

Thanks.

---

### Post by strabes on 2008-05-25
For your purposes I strongly advise that you get a mac. You can get a macbook for < $1100 now, and even cheaper if you're a student. You are not going to enjoy battling linux / wine for support for IE and your adobe products. With your needs you will want stability and reliability and wine is not the route to go for either.

---

### Post by Lantesh on 2008-05-25
Check out Codeweavers.  They make a commercial version of Wine that is a lot more powerful.  I do believe they support Adobe products, and guarantee them to work.  The software will cost you about $40.00 U.S. dollars I believe.

[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by rakan_dr on 2008-05-25
Thanks Lantesh, but I read the compatibility software for codeweavers. It doesn't support Adobe CS3 only very older ones.

I think the mac choice is quite expensive to me!!! maybe the best choice is the virtual machine!

---

### Post by werries on 2008-05-25
another thought is that if you just need the purpose of the program and not the actual filetypes and such for work, you can always use the alternative programs that you can get natively in linux, ie. GIMP=photoshop, Nvu/Kompozer=dreamweaver, and OpenOffice Drawing=illustrator as far as editing/web/vectors goes. flash im not so sure.

vmware may be your best bet if you can't use the alternatives, but try wine first.

---

### Post by prshah on 2008-05-25
> **rakan_dr said:**
> 
2- My modem is Genius GM56PCI-SA internal.


The GM56PCI is available in two types: With a Motorola chipset and an Agere chipset. Both are supported by linmodems, as mentioned in the previous post. However, certain chipsets of Agere are not working properly.

As for Photoshop, have you considered GIMP? It has a learning curve. The following posts by a very talented forum-er show it's capabilities and act as a tutorial.

[http://ubuntuforums.org/showthread.php?t=758678&highlight=showing+power+gimp](http://ubuntuforums.org/showthread.php?t=758678&highlight=showing+power+gimp)
[http://ubuntuforums.org/showthread.php?t=791604&highlight=showing+power+gimp](http://ubuntuforums.org/showthread.php?t=791604&highlight=showing+power+gimp)

---

### Post by SneakyWho_am_i on 2008-05-25
> [quote]I REALLY don't advise you to completely switch if you need the Adobe products.
+1 to that.[/quote]
+1 to that. I rejoice whenever anyone moves to *nix, but if you genuinely need Adobe products then don't move because you will get no satisfaction.

> **werries said:**
> GIMP=photoshop, Nvu/Kompozer=dreamweaver, and OpenOffice Drawing=illustrator
+1 to this too though. I'm a really bad friend, I always seem to talk my friends into trying new things. Firefox, for one. It's easy to move people to Firefox though, especially if you show them how to make it faster.

GIMP is equal to Photoshop (unless you're using LAB colourspace, but I couldn't find any Photoshop users who could tell me what that was, so it's unlikely).
When I say it's equal, I mean:
- The clone tool looks like a rubber stamp in both
- both have scissors
- both have select by colour and both have select by contiguous region (magic wand)
- both do gradient fills
- both have filters like mapping to polar coordinates
The interfaces are nearly identical. For some reason people think otherwise but seriously, although I've never used Photoshop I can identify all the main tools in a screenshot, easy.

GIMP will even import all your PSD files (except those with "Layer Styles", although I read on adobe.com that psd isn't even the native Photoshop format any more... +1 for the GIMP then)

Thanks to Google's work on WINE***, most Adobe products (particularly Photoshop) will run up to version CS2 inclusive. Don't quote me on that, I've never tried. Flash CS2 apparently is a bit patchy (although I have Flash 8 installed that I won in a competition and it works absolutely perfectly)

My favourite Vector graphics editor is Inkscape. The great thing about Inkscape, OpenOffice.org and GIMP is that you can try them in Windows - so you don't even need to burn a LiveCD.

As for Virus Explorer... Oh dear. Dear, dear, dear. See, that's a big part of the reason you have so much malware on your computer ;)
I pity you for having to make sites work in IE :(, I feel your pain.
Luckily, you can run Virus Explorer easily on Linux:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
I can testify to this, I have installed ies4linux myself, as a joke. It's EASY, and you can run multiple versions side by side.


Again though, if you NEED those proprietary products (Adobe's latest), then you should probably just wait and suffer. I can't think why you would need them unless everyone else in your office is sending you files which use the very latest extensions to the proprietary formats, but I have a feeling that that is not an issue so you should be fine with alternatives?)

Either way, when you can come over to the dark side [insert respiration sound effect], you will be embraced with open arms and such.

*** Google has submitted a massive number of Patches to WINE, with the aim of getting a massive number of programs running to a massively high standard. Massive!

PS I always have this fear that I may offend someone when I make forum posts, especially expressing opinions about software. If I have offended anyone, I apologize. Remember that I am only expressing my opinions, nothing more or less.

---

### Post by rakan_dr on 2008-05-25
Thanks guys.
Acutally the best solution I found that from geo909, also I'm thinking about the solution about the vmware.

Please guys can you give me a direct link to download VMWARE for Ubuntu 8.04? I can't use the Synaptic cuz I don't have my Modem installed well! hehehehe don't ask!! I'll go to the Internet Cafe.

---

### Post by liorwohl on 2008-05-25
> **rakan_dr said:**
> Thanks guys.
Acutally the best solution I found that from geo909, also I'm thinking about the solution about the vmware.

Please guys can you give me a direct link to download VMWARE for Ubuntu 8.04? I can't use the Synaptic cuz I don't have my Modem installed well! hehehehe don't ask!! I'll go to the Internet Cafe.

virtualbox is much faster (for me atleast) and you can find it in the repos for free. vmware don't have a DEB and only vmware player and server are free.. so i recommend trying virtualbox first.

and if you have to check your websites in IE, you cant use IE on wine because it's sometimes not exactly the same.. (i'm a web developer) so you have to use virtual machine (i'm using two virtual machines, one for IE6 and the second one for IE7)

photoshop cs/cs2 work perfect on wine, cs3 not but will probably be soon..

---

### Post by rakan_dr on 2008-05-25
Ohhh man (SneakyWho_am_i) thank you very much your opinions has very much liked me!! really man thanks. Actually now also I'm thinking about ur opinions and suggestions.

But please I don't want to buy a new modem. Guys pleeeease give me links to learn how to install my modem from ZERO because I'm new to Linux world. as I said it's GM56PCI with Agere chipset.
(SneakyWho_am_i) can you help me?

---

### Post by rakan_dr on 2008-05-25
> **liorwohl said:**
> virtualbox is much faster (for me atleast) and you can find it in the repos for free. vmware don't have a DEB and only vmware player and server are free.. so i recommend trying virtualbox first.

and if you have to check your websites in IE, you cant use IE on wine because it's sometimes not exactly the same.. (i'm a web developer) so you have to use virtual machine (i'm using two virtual machines, one for IE6 and the second one for IE7)

photoshop cs/cs2 work perfect on wine, cs3 not but will probably be soon..

Man can you tell me your story with Ubuntu??
Are you a real web developer?? What tools and programming languages do you use in Ubuntu??? Pleeease man give me some tips with your trial in Ubuntu for developing websites. Is it better than Windows and Mac???

For me I'm using PHP and Mysql, and now I'm learning JAVA for (JSP) but I haven't installed them till now on Ubuntu.
Please man give me your complete story with developing websites on Ubuntu, the Advantages and Disadvantages.

Thanks.

---

### Post by liorwohl on 2008-05-25
> **rakan_dr said:**
> Man can you tell me your story with Ubuntu??
Are you a real web developer?? What tools and programming languages do you use in Ubuntu??? Pleeease man give me some tips with your trial in Ubuntu for developing websites. Is it better than Windows and Mac???

For me I'm using PHP and Mysql, and now I'm learning JAVA for (JSP) but I haven't installed them till now on Ubuntu.
Please man give me your complete story with developing websites on Ubuntu, the Advantages and Disadvantages.

Thanks.

i'm not a designer so i don't need all the adobe programs, only photoshop cs1 to "cut" the images out of the PSDs.. this works perfect in wine.
(GIMP don't show "layer styles", thats the only reason i need photoshop)

i use the builtin Gedit text editor to write php,html,css,js. I don't need more then gedit for that. but it's a very good and easy to use basic text editor and i didn't found something similar for windows. actually it's the only text editor i know (except for notepad (too basic) and visual studio (too huge)) that don't have problems with Hebrew which is my language..

i test my websites on LAMP (Linux Apache Mysql Php) installed with System->Admin->Synaptic->Edit->Mark Packages By Task->LAMP server (this is much much easier then installing this on windows)
and manage my databases with phpmyadmin installed from synaptic.

---

### Post by rakan_dr on 2008-05-25
> **liorwohl said:**
> i'm not a designer so i don't need all the adobe programs, only photoshop cs1 to "cut" the images out of the PSDs.. this works perfect in wine.
(GIMP don't show "layer styles", thats the only reason i need photoshop)

i use the builtin Gedit text editor to write php,html,css,js. I dont need more then gedit for that. 

i test my websites on LAMP (Linux Apache Mysql Php) installed with System->Admin->Synaptic->Edit->Mark Packages By Task->LAMP server (this is much much easier then installing this on windows)
and manage my databases with phpmyadmin installed from synaptic.

Oh man what you use is very poooor and weak! I would recommend you to use Netbeans from SUN [http://www.netbeans.org]("http://www.netbeans.org")
It's a very helpful IDE for developing websites. It supports PHP too!
Man the Gedit doesn't check for syntax errors! How do you use it??? That's exhausting!

---

### Post by Tom--d on 2008-05-25
If you want to completey move to Linux.. and use Adobe products. 

Virtualbox will do it :)

In the past. I have installed Windows XP and it works really fast :D Probably because I have 2GB ram. >.>
I did install CS3 in there. Works like it does on a normal xp install.

You can set up sharing folders. Share your home folder in Linux into Xp. XP will see it as a network drive.
Internet works in Virtualbox. (For me it worked out of the box).

Once you have xp (thats if its xp..) Install the Guest additions :) and go on seemless mode. 
[http://www.virtualbox.org/attachment/wiki/Screenshots/VirtualBox_OSX_beta_3.png](http://www.virtualbox.org/attachment/wiki/Screenshots/VirtualBox_OSX_beta_3.png)
Thats with mac, but you can do it in Linux :D

---

### Post by rakan_dr on 2008-05-25
> **Tom--d said:**
> If you want to completey move to Linux.. and use Adobe products. 

Virtualbox will do it :)

In the past. I have installed Windows XP and it works really fast :D Probably because I have 2GB ram. >.>
I did install CS3 in there. Works like it does on a normal xp install.

You can set up sharing folders. Share your home folder in Linux into Xp. XP will see it as a network drive.
Internet works in Virtualbox. (For me it worked out of the box).

Once you have xp (thats if its xp..) Install the Guest additions :) and go on seemless mode. 
[http://www.virtualbox.org/attachment/wiki/Screenshots/VirtualBox_OSX_beta_3.png](http://www.virtualbox.org/attachment/wiki/Screenshots/VirtualBox_OSX_beta_3.png)
Thats with mac, but you can do it in Linux :D

These are my hardware specifications:
CPU: INTEL P4 3.60GHz [COLOR="Red"][/COLOR] built in Video Card!! very bad 64 VRAM.
Motherboard: ASUS P5GZ-MX
RAM: 2GB
H.D: 160 WD

but why Virtualbox not VMware?

[COLOR="Red"]And can i use the internet in Ubuntu from the XP using Virtualbox???!!![/COLOR]

---

### Post by Tom--d on 2008-05-25
Your computer will be able to run Virtualbox fine :) 

Virtualbox because.. its Free.. its open source.. and its in the repos :)

You can try both if you like...
I think many people will Virtualbox. 

Is it XP you will install in a virtual machine? (thats if you do)

---

### Post by rakan_dr on 2008-05-25
[COLOR="Red"]Is there any websites designer and developer that can tell me his experience  in Ubuntu and what are the problems that he faced???Disadvantages and advantages please.[/COLOR]

---

### Post by rakan_dr on 2008-05-25
> **Tom--d said:**
> Your computer will be able to run Virtualbox fine :) 

Virtualbox because.. its Free.. its open source.. and its in the repos :)

You can try both if you like...
I think many people will Virtualbox. 

Is it XP you will install in a virtual machine? (thats if you do)

Thanks man, but can i download Virtualbox without using Synaptic? because i don't have my modem installed well (internal modem). I'm going to download it from an internet cafe or from my university, so can you give me a direct link please?

---

### Post by Tom--d on 2008-05-25
Will it be 32bit or 64bit Ubuntu?

You can chose here:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by pixel :-) on 2008-05-25
Don't do the big bang option,start with linux in Virtuallbox under XP,when you are somewhat confortable,go with dual boot.

Virtuallbox[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

For adobes stuff,try out various alternatives ,so that you redious you dependence to adobe stuff.

@Tom--d
Please don't encourage hum to rush it.

---

### Post by rakan_dr on 2008-05-25
> **Tom--d said:**
> Will it be 32bit or 64bit Ubuntu?

You can chose here:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

[COLOR="Red"]It's 32-bit.[/COLOR]

---

### Post by Tom--d on 2008-05-25
> **rakan_dr said:**
> [COLOR="Red"]It's 32-bit.[/COLOR]

Here is the direct download link.

[http://cds-esd.sun.com/ESD42/innotek/virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb?AuthParam=1211739027_af50e29a27eb60d265d54c542ea024d0&TicketId=B%2Fw6kB%2BJSFlOQR1CM1JakQLj&GroupName=CDS&FilePath=/ESD42/innotek/virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb&File=virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb](http://cds-esd.sun.com/ESD42/innotek/virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb?AuthParam=1211739027_af50e29a27eb60d265d54c542ea024d0&TicketId=B%2Fw6kB%2BJSFlOQR1CM1JakQLj&GroupName=CDS&FilePath=/ESD42/innotek/virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb&File=virtualbox_1.6.0-30421_Ubuntu_hardy_i386.deb)

In Ubuntu, just double click the file and install :)

---

### Post by pixel :-) on 2008-05-25
Please don't tell you have already complitly removed windows.Your not very wise if you did.do a dual boot configuration and virtual box.

---

### Post by rakan_dr on 2008-05-25
> **pixel :-) said:**
> Please don't tell you have already complitly removed windows.Your not very wise if you did.do a dual boot configuration and virtual box.

Hehehehhe no man I didn't!:KS I have them dual booted, are you satisfied now:lolflag:??

---

