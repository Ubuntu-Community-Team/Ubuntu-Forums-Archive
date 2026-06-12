---
title: "MagicJack USB voip phone, does it work for ubuntu?"
date: 2007-07-28
forum: General Help
---

### Post by sdowney717 on 2007-07-28
[http://www.magicjack.com/site/index.html](http://www.magicjack.com/site/index.html)

curious if anyone knows if it works

---

### Post by Griffin3 on 2007-08-01
It does not work with linux, yet.  I saw reports where one person on the magicjack forums has gotten it working (He said "remoting" was the key, but I haven't had the opportunity to follw-up).  Also, another report says that the USB device itself is recognized ... as a modem and a CD player.  So, all the bits are there, we just have to wait for some sharp cookie to reverse-engineer the software.

But, no, it does not work with Linux (or Ubuntu) as of right now.

---

### Post by GoneWithTheWind on 2007-08-01
I got the magicjack in the mail today but haven't tried it yet as I'd have to reboot.

The house wiring is all set up as I used it that way with sunrocket previously and I'm looking forward to using the magicjack later tonight.

The $40 first year free long distance in the U.S. and Canada is a very good deal, and $20 the second.

When someone comes up with a way to run it in Linux, even better.

---

### Post by sdowney717 on 2007-08-03
net2phone is offering to pick up sunrocket customers who paid ahead and will honor the months that we lost. So I had sunrocket for 5 months and net2phone will give me 7 months free plus 3 months free for signing up. After that I can renew a contract with them for 19.95 per month.

So I signed up and got my innomedia gizmo and it works great.

I think the magicjack is neat, but of course you have to have your computer running to use the phone. And then for now,  you got to run windows.

[http://web.net2phone.com/sunrocket/](http://web.net2phone.com/sunrocket/)

---

### Post by sdowney717 on 2007-08-03
I installed virtualbox. And installed XP Pro.
So far it is working fine. I downloaded the .deb from virtualbox.org.
You also should setup the additions for seemless mouse action and file sharing.  And I have the USB working.
I would like to figure out printing to my HP Laser 4000 networked printer that is plugged into my LAN.

What I was wondering was if the majicjack would work in a virtual machine of XP.

[http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices](http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices)

---

### Post by GoneWithTheWind on 2007-08-07
> **sdowney717 said:**
> I installed virtualbox. And installed XP Pro.
So far it is working fine. I downloaded the .deb from virtualbox.org.
You also should setup the additions for seemless mouse action and file sharing.  And I have the USB working.
I would like to figure out printing to my HP Laser 4000 networked printer that is plugged into my LAN.

What I was wondering was if the majicjack would work in a virtual machine of XP.

[http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices](http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices)

Does that work through Linux?  If so, that's cool.

Net2Phone doesn't have any free months.

> **You will be enrolled in our $19.95 unlimited calling plan**. You can also select any additional features that you want on your account, such as a virtual number.

What will you be charged:

    * $29.95 activation fee, if you require a new telephone adapter
    * $10.00 shipping and handling, if you require a new telephone adapter
    *** Applicable monthly taxes and surcharges. These include a $1 Enhanced Service Fee and a Federal Universal Service Fund surcharge.**
[B]
We will automatically credit your account for first three months of service.[/B]

Please keep in mind that you are enrolling in Net2Phone VoiceLine service. **If you cancel anytime within the first twelve months following activation of your account, you will be charged a deactivation fee of $39.99**.

You are charged $19.95 a month, the first 3 months charged immediately.  Then if you cancel in the 1st year it's another $39.95 hit.  That comes out to $279.35 for the year, a rate of $23.79 per month all charged in advance, the first three months charged three months in advance.

On another note, the MagicJack arrived in 2 days.  I've been using it and it's great!

The sound quality is excellent.  Total cost for the 1st year $40 and $20 for the 2nd, which comes out to a $2.50 average per month, with free long distance anywhere in the U.S. and Canada.

---

### Post by LaneLester on 2007-12-13
> **John Rupp said:**
> On another note, the MagicJack arrived in 2 days.  I've been using it and it's great!

The sound quality is excellent.  Total cost for the 1st year $40 and $20 for the 2nd, which comes out to a $2.50 average per month, with free long distance anywhere in the U.S. and Canada.

I presume you're using it through Windows, right?

Lane

---

### Post by bone2006 on 2008-01-25
If somebody can figure out how to get it to work in Linux, then it would probably work on my router that has USB support and a third party firmware flash that's using Linux.

I think it would be the best thing just to plug this device into the router I already have for 50 dollars and not have to worry about a computer even being on.  DD-wrt and Tomato firmware has support for USB, in which cameras and print servers work.  If there was a linux driver for this device that would really be awesome.

---

### Post by dman777 on 2008-04-16
SDOWNY717,
I am running virtualbox-bin on linux with windows xp as my guest. MagicJack registers on the USB device but it's software doesn't install/show up in the windows xp guest. How did you get it to work?

---

### Post by macrohard on 2008-04-19
Been awhile since I last posted here, but I saw info about this in the Klikit Linux forum from a user in the Phillipines. So I decided to give it a try to see what I could do about this to get it up and running in Linux

So I ordered one and give it a whirl on my work Windows XP laptop. It didnt work initially so I went out to download a the Magicfix form the MagicJack website and got it working.

When I initially tried this on Gutsy, it saw it only as a USB flash device.

What I discovered is that this is more than a USB flash device, it also runs inside of it a virtual USB CDROM drive.

So when you plug it into Windows, it sees it that if you run your hard drive as C: and cd/dvdrom drive as D:, it runs the USB flash drive as E: and the Virtual CD Rom drive as F:

So I didnt little thinking and found a site that complained about MagicJack and how to remove it from your Windows system. (It seemed to work just fine for me in Windows so not sure of the complaints)

Here was the site:

[http://www.ooine.com/index.cfm/2008/3/15/How-to-uninstall-Magic-Jack]("http://www.ooine.com/index.cfm/2008/3/15/How-to-uninstall-Magic-Jack")

So I actually went in and checked out what drivers the both the USB flash and Virtual CDROM drive, verified their locations in Windows and copied them out.

Then went in and checked locations of said files in Document and Settings and copied those out.

Next I exported a copy out of the Windows Registry of the Talk4Free key and all its subkeys out of Windows.

Since I run Crossover Office. I initially created a Windows XP bottle for MagicJack  I went into the .cxoffice directory (this is hidden in your Home folder) and browsed down in the Virtual C: drive to the regedit.exe and ran it, it will open up the WINE version of the Windows Registry Editor.

I then went in and manually entered the settings of the Talk4Free key into the HKEY_CURRENT_KEY (that took awhile, if anyone knows how to export a key out of Windows and drop it in to the Crossover Registry, that would be great.) 

I copied all the appropriate files, .sys and .dll files to their equivalent into the virtual c: drive in Crossover.

After I completed the registry settings in Crossover, I shutdown the box, plugged in the Magicjack into the USB drive and booted into Ubuntu. Now Ubu sees both the Virtual CDROM drive and the Flash Drive.

If I try to run the autorun.exe file from withing the virtual CDROM drive Crossover attemptes to run it. A Magicjack graphic of a USB drive comes on and states I need to plug this drive in. (It is in), then it kicks in my Firefox browser over to the Magicjack website.

I am so close....I can feel it....does anyone have an idea, or something else that might come to mind?

I'll check back later....

---

### Post by Tsukino Kyuuketsuki on 2008-04-23
I was about to get magicjack but I wanted to do a little research first to see if anyone could actually use it with ubuntu (yeah, learned to do research after getting a canon pixma mp470... looks nice but it's useless with linux, lol)
So yeah, anyone tried to run the magicjack setup software with wine? Just wondering :confused:

---

### Post by greenghost77 on 2008-06-14
Has anyone tried virtualbox? (sudo apt-get install virtualbox-ose )

APP:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Install HOWTO:
[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)

It's a free VM system, similar to VMware... Seems that it could be a good option... I'm having a bit of trouble getting an XP VM installed with it, but I guess that's a different thread...

I would love to get this MagicJack working on my kubuntu 8.0.4 desktop machine, as it is stationary in the back room(like my phone ;-)... this little device kicks *** and was a simple "plug it in" operation on my cheapy Vista Home Basic laptop, which, of couse, is mobile... I imagine that (once I get it working) it shouldn't be any different with a virtual machine... 

I'm hoping that someone out there can get this working and help a brother out ;-)

Best wishes all, ~~J

---

### Post by Tsukino Kyuuketsuki on 2008-06-14
After several weeks thinking about it, I just orderer the magicjack just to see if I could make it run on Ubuntu. I was thinking about the virtualbox, thanks for the links. I'll try it and let you know if it works. 

I found this a few days ago: [link]("http://blog.laptopmag.com/magicjack-inventor-plans-linux-support-improved-customer-service-and-more")

If I'm lucky, by the time I get my magicjack there will be a driver for linux already. :KS

---

### Post by Paul86fxr on 2008-07-15
Cant wait to get started, its a dual mode device. I had all these problem with the franklin cdu 680 and got that working fine. as soon as I get my MJ I will crack it and post here, I already know most of what does not work so I have a good starting point.

---

### Post by xe1ufo on 2008-07-18
> **Paul86fxr said:**
> Cant wait to get started, its a dual mode device. I had all these problem with the franklin cdu 680 and got that working fine. as soon as I get my MJ I will crack it and post here, I already know most of what does not work so I have a good starting point.

Paul: I also have the Franklin CDU 680. I cannot get it recognized in Ubuntu 8.04.  Please tell me how you did it. Thanks in advance!

---

### Post by Paul86fxr on 2008-07-18
Its not hard, its done manually, I will post details tomorrow AM on the CDU680, its late here.

Paul

---

### Post by Paul86fxr on 2008-07-19
Ok, plug in the cdu680.
make sure all the ubuntu files for the cdu680 files are on your desktop just like you ran it before.
the important ones are 
1>itfchg
2>execute.sh


3. open a terminal and enter:
 
 $ cd Desktop

$ sudo ./itfchg /dev/sdb

 enter password

$ sudo ./execute.sh 




That should do it, let me know if you have any trouble
Paul



Just got my Magicjack today, will post when I know something.

---

