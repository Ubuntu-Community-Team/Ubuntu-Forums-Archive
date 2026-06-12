---
title: "Lexmark Z-series wireless printer on recent distros"
date: 2013-08-01
forum: General Help
---

### Post by Sleepy-zz-John on 2013-08-01
Hi,     I'm looking for a driver that will work on my neighbour's Precise for his Lexmark Z2420 wireless printer.

I converted my neighbour from Windows to Precise last year and he is very happy with it except that he can't print on his Lexmark,  which he could do on Windows.

Here are some details of things I've already tried,  but which have so far failed:    

I read and tried to follow the out-of-date instructions at  [http://mikebeach.org/2010/04/22/how-to-install-lexmark-z2400-3600-4600-5600-6600-4900-5000-lucid/](http://mikebeach.org/2010/04/22/how-to-install-lexmark-z2400-3600-4600-5600-6600-4900-5000-lucid/) using the suggested lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz driver,  and also the slightly more recent  lexmark-inkjet-09-driver-1.5-1.i386.deb.sh.tar.gz,  but the installations fail with 

ERROR:  parsing file '/var/lib/dpkg/tmp.ci/control' near line 8 
package 'lexmark-inkjet-09-driver:
blank line in value of field 'Description"

A fix for this problem is nicely described at [http://archbird.blogspot.co.uk/2012/04/fix-error-blank-line-installing-lexmark.html](http://archbird.blogspot.co.uk/2012/04/fix-error-blank-line-installing-lexmark.html), (modifying the 'control' file in the .deb) and I've tried following that for both the above-mentioned drivers,  but for reasons I haven't understood,  the same ERROR persists.

I've also tried using CUPS by specifying the file /usr/lexinkjet/08zero/etc/lxZ2400.ppd and have managed to complete the installation,  but printing shows stopped when I try a test print with printer config error,  and 'There is a missing print filter for Lexmark Z2400'.      I obtained that .ppd file from my own Oneric netbook on which I'd also tried to install the above-mentioned two Lexmark drivers,  and whose installations had somehow managed to complete although printing failed with "printer cannot communicate with computer"  and "Server Not Exporting Printers:  Enable Publish shared printers using printing admin tool in System -> Admin -> Printing" which I couldn't find on Oneric.  

I obtained another ray of hope for getting this Lexmark working from: 

[https://answers.launchpad.net/ubuntu/+source/cups/+question/180045](https://answers.launchpad.net/ubuntu/+source/cups/+question/180045)  which suggests that wireless can work even though USB doesn't.   Unfortunately I couldn't understand this old answer,  and posted a request for clarification there last week,  but no answer so far.

Meanwhile I got the following discouraging reply from Lexmark:
> Date: 1 Aug 2013 02:17:21 +0100
From: Lexmark Support<support1@lexmark.com>
Subject: Lexmark Technical Support 1-13551682015

Dear John,

Thank you for contacting Lexmark e-Support regarding your Lexmark Z2420.

I understand that you are trying to find the Ubuntu 12.04 Linux printer driver that will work with Lexmark Z2420. I really apologize but we don't have the Linux printer driver that will work with Ubuntu 12.04 system. I'll pass on your concern to our development team who makes decisions about which printers to support with Linux drivers. We do spend considerable effort understanding market opportunities and, if market demand shifts to a point that would make your proposal worthwhile, I'm sure we would consider it.

If you have any more questions or concerns, please reply and reference Lexmark Service Request Number 1-13551682015 and we will be happy to assist you.

You may also call our technical support at 1-800-395-4039 or 1-800-332-4120, Mondays through Fridays, 9am-9pm EST and Saturday 12pm-6pm EST; Chat support ([www.lexmark.com](www.lexmark.com)), Monday through Friday, 9am-9pm EST and Saturday, 12pm-6pm EST.

Thank you again for contacting Lexmark e-Support.

Sincerely,

Lexmark e-Support Team
[http://support.lexmark.com](http://support.lexmark.com)


**********Original Message**********
Hi,  Can you help me to find the right driver for my friend's model Z2420 working on Ubuntu v12.04 (Precise)? Your operating system search box for this model only goes up to v10.10 and the -08z-series-driver I have tried from there does not work correctly.   I am initially trying to get it going via USB with the ultimate aim of converting to wireless as soon as it prints OK on USB.  This Z2420 works fine via USB on Windows;  it's only on Linux Ubuntu that I'm having difficulty.     Hope you can help.  Thanks.
If I understand correctly,  Lexmark's two above-mentioned drivers used to work on distros up to Lucid,  but something must have changed after that and they no longer worked.  Lexmark didn't subsequently update their drivers.

I've seen a few sceptical posts around that suggest Lexmark and Ubuntu are simply incompatible,  but I'm reluctant to abandon my attempts to make this work.  If I do,  my neighbour would have no alternative but to revert to dear old Windows for his printing!!  

Any suggestions?  bright ideas?  leads worth following on this one,  anyone?

---

### Post by Sleepy-zz-John on 2013-08-26
I'm still looking for a way to get this Lexmark Z2420 printing from Ubuntu,  and wondering whether installing Wine and trying to use Lexmark's Windows installation disc might be a possible way forward.    

I'm not familiar with Wine and what it can and can't do,   so would welcome advice from any Wine user here about whether this is the sort of task it might be able to handle. Would it be worth a try?

---

### Post by kurt18947 on 2013-08-26
Lexmark is going to discontinue their inkjet printers if they haven't already done so and are closing the inkjet supplies factory in 2015.  I know that isn't for a couple years yet but would your neighbor be amenable to buying a machine that is happy with Ubuntu?  HP & Brother I know from experience are linux friendly  and I believe Epson is as well.  A relative has a Lexmark inkjet printer and spent close to $50 on ink recently and I think that was just one cartridge.  I see Brother's  MFC-430W on sale for $59 frequently and it comes with (I think full sized)ink.:)  And I KNOW that works, SWMBO has one.

---

### Post by cparke on 2013-08-26
> **Sleepy-zz-John said:**
> I'm still looking for a way to get this Lexmark Z2420 printing from Ubuntu,  and wondering whether installing Wine and trying to use Lexmark's Windows installation disc might be a possible way forward.    

I'm not familiar with Wine and what it can and can't do,   so would welcome advice from any Wine user here about whether this is the sort of task it might be able to handle. Would it be worth a try?
As I told you before, the printer works just fine (USB and wireless) with the Lexmark-provided drivers on Ubuntu 10.10 (Maverick).  They broke it beginning with 11.04 (Natty).   You can still download Maverick in the archives, and you can update it to the final updates by revising the package repositories.

In the recent versions of Ubuntu, you can only get it to print wirelessly.  For wireless setup, after installing the Lexmark drivers, I used either CUPS or the Add Printer dialog.  In my wireless setup, I have configured the LAN setup to give the printer a fixed IP address.  Then I simply add it as a AppSocket/HP jet Direct network print residing at socket://192.168.1.201:9100.  It works pretty good too!

As far as using WINE to run the Windows version of the Network Configuration Utility, that might work but I never tried it since I have dual boot to Windows for certain things like that.  Sometimes there are basic configuration things for WINE that it works well for.  For example, I read that a new effort is under way to get Microsoft Windows Silverlight to run in the Firefox browser by a project called 'Pipelight' that is using WINE to connect the Linux browser with the Windows applet.  Configuring the simulated Windows environment is sometimes confusing, however.  

Good luck!
CP

---

### Post by Sleepy-zz-John on 2013-08-27
> **kurt18947 said:**
> ..... would your neighbor be amenable to buying a machine that is happy with Ubuntu?   Thanks Kurt,  but in this case no,  I doubt it.  My neighbour is a very light none-too-cyber-savvy user and the Lexmark came free with a laptop and dongle package a few years ago.  He's really happy with Precise in place of his old Win Vista except that neither his printer nor webcam work and he has to keep going back to that barely-working Vista whenever he needs to print.

---

### Post by Sleepy-zz-John on 2013-08-27
Thanks for your suggestions CP.   I'll give Maverick a try myself,  but I dunno about downgrading my neighbour to MAV and I doubt if he's cyber-savvy enough to manage a multiple boot setup with both.    I had tried the old Lexmark drivers and CUPS on wireless with Precise after setting up the printer to work OK wirelessly on Win Vista,  but no luck on Precise.  Haven't tried with a fixed IP address though yet.  

Wonder if anyone else here has experience of using Wine in this sort of setup?

---

### Post by cparke on 2013-08-27
> **Sleepy-zz-John said:**
> Thanks for your suggestions CP.   I'll give Maverick a try myself,  but I dunno about downgrading my neighbour to MAV and I doubt if he's cyber-savvy enough to manage a multiple boot setup with both.    I had tried the old Lexmark drivers and CUPS on wireless with Precise after setting up the printer to work OK wirelessly on Win Vista,  but no luck on Precise.  Haven't tried with a fixed IP address though yet.  

Wonder if anyone else here has experience of using Wine in this sort of setup?

It will work wirelessly even with the recent versions, so long as you completed the Network Setup wizard in Windows and have installed the Linux driver.  The problem is just with the USB driver in my experience.  If the webcam is also USB (as opposed to IP), wouldn't be surprised if it is the same problem.  Canonical really messed up with Ubuntu when going to 11.04, quite a disappointment for me.

---

### Post by Sleepy-zz-John on 2013-08-28
> **cparke said:**
> It will work wirelessly even with the recent versions, so long as you completed the Network Setup wizard in Windows and have installed the Linux driver.   Appreciate your encouraging remarks, CP.     I thought I had done all that because I got it to print wirelessly in Windows quite easily,  but maybe not;  I know I  didn't set a fixed IP there.    I'll have to go back and revisit this with my neighbour.  >  If the webcam is also USB (as opposed to IP), wouldn't be surprised if it is the same problem.  Yes,  the webcam is USB and I've ID'd its vendor  and found a driver that's listed as supposedly supporting it,  but it's not working.  Will have to do more research and experimenting on this one too. >    Canonical really messed up with Ubuntu when going to 11.04, quite a disappointment for me.I agree.  I've had another similar issue with a USB 3G dongle that ceased working properly around that time.  Backward compatibility does seem to have been somewhat neglected in order to get these new flashy distros out on time.

---

### Post by cparke on 2013-08-28
> **Sleepy-zz-John said:**
> Appreciate your encouraging remarks, CP.     I thought I had done all that because I got it to print wirelessly in Windows quite easily,  but maybe not;  I know I  didn't set a fixed IP there.    I'll have to go back and revisit this with my neighbour.   Yes,  the webcam is USB and I've ID'd its vendor  and found a driver that's listed as supposedly supporting it,  but it's not working.  Will have to do more research and experimenting on this one too. I agree.  I've had another similar issue with a USB 3G dongle that ceased working properly around that time.  Backward compatibility does seem to have been somewhat neglected in order to get these new flashy distros out on time.

I set the fixed IP by going into the router config and 'reserving' the IP address for the printer's IP address.  It still uses DHCP, but thd router always gives it the same address, so it is like a static IP but configured differently.

---

