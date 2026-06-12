---
title: "Can I watch cable TV with a TV tuner in ubuntu?"
date: 2005-10-25
forum: General Help
---

### Post by chimera on 2005-10-25
I was wondering,how supported are TV tuners in ubuntu anyway?And what programs are there?

---

### Post by bradd on 2005-10-25
[QUOTE=chimera]I was wondering,how supported are TV tuners in ubuntu anyway?And what programs are there?[/QUOTE]

 Well I have a leadtek WinFast tv2000XP expert and it seems to be ok..
From what I've heard tho a card with the hauupage chipset are supported the most..

---

### Post by chimera on 2005-10-25
Which programs do I need?

---

### Post by RAOF on 2005-10-25
If you want a fully-featured PVR solution, you could try mythtv.  It'll let you watch tv, schedule recordings, dowload program guides from the internet, whatever.

If you just want to watch stuff, there's tvtime (although that won't work if you've got a digital tv card, I think).

---

### Post by dvejnovic on 2005-10-25
[QUOTE=RAOF]If you want a fully-featured PVR solution, you could try mythtv.  It'll let you watch tv, schedule recordings, dowload program guides from the internet, whatever.

If you just want to watch stuff, there's tvtime (although that won't work if you've got a digital tv card, I think).[/QUOTE]

You may also try kdetv or atitv (for ATI TV cards)...

---

### Post by drummer on 2005-10-25
[QUOTE=bradd]Well I have a leadtek WinFast tv2000XP expert and it seems to be ok..
From what I've heard tho a card with the hauupage chipset are supported the most..[/QUOTE]
I have the same card and it works pretty well for watching tv, although I haven't been able to record. Probably the most well supported/oldest chipset is the Brooktree (bt868 or something).

I've also heard/read that Hauppauge cards work well. I think the mythtv guide reccomends the hauppauge wintv-pvr-150/250/350.

EDIT - <OT>bradd, can you record using your tv card?</OT>

---

### Post by chimera on 2005-10-25
I have a mercury TV-tuner,and it doesn't seem to work in kdetv(it doesn't find any channels),I'll try the rest now.

EDIT:How I scan for channels in tvtime???

---

### Post by chimera on 2005-10-25
Anyone?I really need this badly,because my TV broke(fell about 1,5m down,just enough to mess it up beyond repair:mad: )

---

### Post by JurB on 2005-10-25
Just push the up and down buttons on your keyboard, the channels have already been set but they are scattered.
You can re-number them by right clicking --> channel management ---> re-number channel

---

### Post by chimera on 2005-10-25
[img]http://freeweb.siol.net/klemenf1/Screenshot-1.png[/img]

Please show me the chnnel management button,I can't seem to find it.

---

### Post by JurB on 2005-10-25
Weird , it should be right above " input configuration".
Also the screen should be blue, if not i think there if something wrong with your configuration.
Did you install via Synaptic? Did the configuration screen come up after install?

---

### Post by chimera on 2005-10-25
Yes to both

P.S.:This is what I get when I try to run tvtime-scanner

chimera@ubuntu:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/chimera/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/chimera/.tvtime/stationlist.xml: No existing PAL station list "Custom".

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.

---

### Post by drummer on 2005-10-25
Is your card actually working properly? Do you know what chipset the card has?
type lspci into a terminal and see if there's a line describing the card. if there is then it's detected alright..
Then you need to know the chipset to make sure the right drivers have been loaded by the kernel. If it's the brooktree chipset, type in a terminal "lsmod | grep bttv" (without quotes), if it doesn't come up with anything, try typing "sudo modprobe bttv" and "sudo modprobe tda9887" and "sudo modprobe videodev" then see if tvtime works.

---

### Post by chimera on 2005-10-26
0000:03:0b.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadca st Decoder (rev 01)

this is it right?

I've tried all of those commands drummer,and it STILL doesn't work

---

### Post by RAOF on 2005-10-26
I'd check to see how well supported your card is.  Check out the one of the wikis at [www.linuxtv.org](www.linuxtv.org), either the V4L wiki if the card is an analogue tv card, or the DVB wiki if it's a digital tv card.

---

### Post by fragmental on 2005-10-30
Are you using the mercury tv tuner?  That's what I'm using and it has not been easy to set up.

lspci will have a line about it.  Mine says this:
0000:01:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

For saa7130/7134 cards check this info here [http://tvtime.sourceforge.net/cards.html#saa7134](http://tvtime.sourceforge.net/cards.html#saa7134)
> The saa7134 driver supports newer capture cards based on the Philips SAA7134 chip. This driver is included with Linux 2.6 kernels.

tvtime should work fine with this driver. Known issues:

   1. If you cannot tune to any channels, your card may not be detected by the driver. Please see this discussion on our problems page.
   2. This driver can return I/O errors when there is no signal or a poor signal. These errors are not allowed by the V4L2 standard, and should be fixed in more recent driver versions. These errors will cause tvtime to output warnings to the console, and potentially crash under tvtime 0.9.12. 

My dmesg output told me that the card type was undetected.

I think this happens more on the cheaper cards, because the manufacturer leaves off the eeprom which provides data telling the drivers exactly what kind of chipset and tuner the card has.  So, without that data you must figure it all out for yourself.

[http://howtos.linux.com/howtos/BTTV/mfgr.shtml](http://howtos.linux.com/howtos/BTTV/mfgr.shtml) is a handy link for that.  My card is a kobian mercury, which shows up as lr50 or lr138 via that link.  If I search the rest of the document I can find out that the lr50 is is a Bt8x8 and I know mine is saa7130 and searching for lr138 shows that the same chipset is used in the lifeview flyvideo 2000 and 3000 series cards.

I used the card list from here: [http://www.wlug.org.nz/TvTunerCards](http://www.wlug.org.nz/TvTunerCards) which showed me that flyvideo3000 was number 2 and flyvideo2000 was number 3.  After a little research I found out that the main difference between the two cards is that flyvideo3000 uses the saa7134 chipset which has stereo sound and flyvideo2000 uses the saa7130 chipset which has mono audio.  The output from lspci confirms that I use the saa7130 and if I try to load the saa7134(with the correct tuner, see below) sound doesn't work.

In order to load the card I then unload the "saa7130" module if it's loaded via "sudo rmmod saa7130" and then "sudo modprobe saa7130 card=3".

Problem with that then is that the channels don't come in right.  I checked the dmesg output again and it told me that the tuner was pal, when it should say ntsc or ntsc-m. [http://www.wlug.org.nz/TvTunerCards](http://www.wlug.org.nz/TvTunerCards) has more info on that.  If the card does not have the eeprom info for the card chipset it probably doesn't have info on the tuner chipset either.  If you're not lucky enough to have it guess the right one by chance you've got to find out.  What I did can be found here: [http://gentoo-wiki.com/HARDWARE_saa7134]("http://gentoo-wiki.com/HARDWARE_saa7134").
I unloaded the driver, reloaded the driver with another tuner and then checked a vhf and uhf channel in tvtime to see if it worked.  For me, the tuner number 9 and 39 both worked correctly.  I'm not sure if the fm radio works though.

I can then load my mercury tv tuner with:
"sudo modprobe saa7134 card=3 tuner=39"

If you have the mercury tv tuner and are in a pal location you might try using tuner number 11, 12, or 13.

That's all i've got so far.  I will probably have to add this stuff to /etc/modules.

Oh yeah, interesting side effect of the cheap cards with no eeprom.  If you try to use any drivers besides the ones that came on the cd that came with it(or possibly the brand website), in windows, they won't work because the drivers that came with the card are hardcoded to know the card's chipset and tuner's chipset.  That happened to me because I tried using lifeview's software and drivers for the mercury card because they are very similar(in fact, the software is basically the same besides the branding and lifeview's are newer).  The software basically did the same thing that tvtime did in linux before I set the card and tuner number.

Edit:  I'm still having a problem where, while changing channels, sound will sometimes cut out.  It comes back if I change the channel back and forth though.  I'm not sure why this happens.  Maybe it's tvtime.

---

### Post by btdown on 2005-10-30
man..i hate to be the bearer of bad news. I have a Leadtek Winfast 2000XP, a Hauppauge 150 and 250 and I have *NEVER* been able to get any of them to work with ANY distro. I've done all the tutorials, changed all the settings, loaded all the drivers/firmware/etc...never any success.

You have a better chance of capturing a bigfoot than getting a TV tuner to work with Ubuntu.....

Sorry I couldnt be more helpful, but Im trying to save you a lot of pain and aggravation.
BT

---

### Post by fragmental on 2005-10-30
Most cards are supported.  You just have to find the right driver, card # and tuner #(see above)

---

### Post by fut21 on 2005-10-31
Maybe this thread would give you an idea of what to do:
[http://www.ubuntuforums.org/showthread.php?t=24813&highlight=7134](http://www.ubuntuforums.org/showthread.php?t=24813&highlight=7134)

---

### Post by @jens on 2005-11-01
[QUOTE=btdown]man..i hate to be the bearer of bad news. I have a Leadtek Winfast 2000XP,[..]

Me too. It works fine in Breezy with KDETV and tvtime. What I've done is:

sudo gedit /etc/modprobe.d/tv
options tda9887 pal=x (x= depends on where you stay). E.g. I'm living in GB, so the pal is pal=i

hth
Jens

---

### Post by Caraibes on 2006-09-04
I hate to say it, but the only distro that allow me to watch TV out of the box with my Lifeview Flyvideo 2000 PCI TV-card is Mandriva...

Configuring the TV-card is easily done thru the Control center...

That is why it is may distro for my "Media Center" Box ;) 

8)

---

### Post by Zaid on 2006-09-12
I have a leadtek tv2000 xp expert as well and it works fine though I can't seem to get it to record. And the image doesn't look to crisp.

---

### Post by Caraibes on 2006-12-12
here's an update, for what it's worth :

[http://forums.blagblagblag.org/viewtopic.php?t=2605&highlight=lifeview](http://forums.blagblagblag.org/viewtopic.php?t=2605&highlight=lifeview)

:cool:

---

### Post by fragmental on 2006-12-12
In ubuntu I used to just put "saa7134 card=3 tuner=39" in "/etc/modules" but for some reason that stopped working so now I put a file called "saa7134" in "/etc/modprobe.d/" with "options card=3 tuner=39" inside.

I have a flyvideo 2000 clone made by Kobian Mercury.

Also, I had to install xawtv so I could get the v4lctl command, and then I have to run "v4lctl volume mute off" if I want to use the card with mythtv.

Just thought I would point that out as a sort of follow up to my other post.

Oh, and tuner #37 will probably work well for a card with a similar tuner as mine, a tnf-5835-mff, if you want to use PAL.  I use NTSC

---

### Post by zyxnull on 2007-06-16
> **btdown said:**
> man..i hate to be the bearer of bad news. I have a Leadtek Winfast 2000XP, a Hauppauge 150 and 250 and I have *NEVER* been able to get any of them to work with ANY distro. I've done all the tutorials, changed all the settings, loaded all the drivers/firmware/etc...never any success.

You have a better chance of capturing a bigfoot than getting a TV tuner to work with Ubuntu.....

Sorry I couldnt be more helpful, but Im trying to save you a lot of pain and aggravation.
BT

Hmmmm.... Very negative from you, if you weren't able to do it, it doesn't mean it's not possible, i hava a FlyVideo3000 and previously had a FlyVideo2000, the older one worked out of the box, even in slackware and even there i had to download / compile the TV program

Now in ubuntu was way to easy to set up, it just happens that people (including me) are lazy, and doesn't like to search for the appropriate parameter for their card, in my case with the flyVideo3000 on Ubuntu feisty it was as simple as doing:

sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo rmmod videodev

Because the kernel detected the card, however it didn't set it up in the proper manner, then it was just doing the following:

sudo modprobe saa7134 card=2 tuner=39

There you are! it loads everything else it needs!

---

