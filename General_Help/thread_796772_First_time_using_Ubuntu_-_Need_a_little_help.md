---
title: "First time using Ubuntu - Need a little help"
date: 2008-05-16
forum: General Help
---

### Post by jras20 on 2008-05-16
Ok, I'm tired of Vista.  I wanted to try something new, I got Ubuntu.  I downloaded the 64bit version.  Everything works, but the wireless lan driver and the sound card driver.  the plug-in wired network works for broadband.  I havnt tried the modem yet.  But I hardly use the modem.  If I could get the sound drivers and the wireless lan working that would be great.  What will I need to send out to get it working?
Thanks

---

### Post by Bakon Jarser on 2008-05-16
> **jras20 said:**
> Ok, I'm tired of Vista.  I wanted to try something new, I got Ubuntu.  I downloaded the 64bit version.  Everything works, but the wireless lan driver and the sound card driver.  the plug-in wired network works for broadband.  I havnt tried the modem yet.  But I hardly use the modem.  If I could get the sound drivers and the wireless lan working that would be great.  What will I need to send out to get it working?
Thanks

We'll need to know what wireless card and what sound card you are using.

---

### Post by Exsecrabilus on 2008-05-16
Do you have a Broadcom wireless card?

---

### Post by jras20 on 2008-05-16
Atheros AR5007EG Wireless network adaptor (built in the laptop)
realtec high def audio drivers FOR VISTA (R170)

I'd like the easiest way to get it working.
Thanks!
J

---

### Post by ugm6hr on 2008-05-16
Try one thing at a time.

Wifi:

Post back with results from (case sensitive):
```
lspci
lshw -C network
```

---

### Post by Bakon Jarser on 2008-05-16
> **jras20 said:**
> Atheros AR5007EG Wireless network adaptor (built in the laptop)
realtec high def audio drivers FOR VISTA (R170)

I'd like the easiest way to get it working.
Thanks!
J

For your wireless card start here.

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by ugm6hr on 2008-05-16
> **jras20 said:**
> Atheros AR5007EG Wireless network adaptor (built in the laptop)
realtec high def audio drivers FOR VISTA (R170)

I'd like the easiest way to get it working.
Thanks!
J

Wifi:
64-bit trickier than 32-bit: [http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

---

### Post by jras20 on 2008-05-16
> **ugm6hr said:**
> Try one thing at a time.

Wifi:

Post back with results from (case sensitive):
```
lspci
lshw -C network
```

Where do I type that at? sorry I'm new at this...

---

### Post by Bakon Jarser on 2008-05-16
> **jras20 said:**
> Where do I type that at? sorry I'm new at this...

In the terminal. (Don't type, copy and paste, run one line at a time)

Applications > Accessories > Terminal

---

### Post by jras20 on 2008-05-16
> **Bakon Jarser said:**
> In the terminal. (Don't type, copy and paste, run one line at a time)

Applications > Accessories > Terminal

Thanks - Will I half to do this every time to load the driver if it works?  I'll do it asap.

---

### Post by strabes on 2008-05-16
You can "copy" and paste things using the standard Ctrl+C, Ctrl+V way (In gnome-terminal you must also hold down shift because ctrl+c and ctrl+v do different things.) OR you can simply highlight some text and then middle click somewhere else to paste the highlighted text. I find the latter to be much easier because it doesn't require any keyboard strokes.

> Will I half to do this every time to load the driver if it works? I'll do it asap.

No. If you actually get it working it should work every time you reboot. By the way, the correct word would be "have" not "half."

---

### Post by jras20 on 2008-05-16
Heres another thing, I went to the device drivers, it had that driver listed, and it said it was enabled.  but, I cant get anything to connect over on the connection manager.  I dont know this is hard...  I'd like to learn how to use this.  When I go to edit wireless networks, nothing shows up.

---

### Post by jras20 on 2008-05-16
I dont know I am stuck on this I'll half to get back when I get a chance..

---

### Post by ugm6hr on 2008-05-17
> **jras20 said:**
> I dont know I am stuck on this I'll half to get back when I get a chance..

Unfortunately, you seem to be lost on step 1.

The Terminal is explained in the Code in Terminal link below.  Read it, and perhaps browse the rest of that site - it deals with the basics of Ubuntu well.

Once that makes sense, you can move on to solving the problem.

You are using 64-bit Ubuntu.  I use it too.  Unfortunately, your wifi card is easier to get working with 32-bit (due to no current 64-bit driver).

The 32-bit and 64-bit solutions are linked to in posts 6 & 7.

So - take a break - learn about Terminal - then connect with a wired ethernet cable, and decide which route you are going to take.

It would be helpful to confirm what wifi card you have with *lspci* anyway.

---

### Post by jras20 on 2008-05-20
Hello,
I'll try the codes again, it seems that my wireless card doesnt even turn on when it boots into Ubuntu.  When Vista boots it turns on, and the sound card works.  A friend of mine thought that everything should work fine, I wish it did.  I wish there was a simple way to install these drivers.  I just downloaded the 32bit version now, and have it installed.

---

### Post by jras20 on 2008-05-20
This is what the terminal tells me when I tried to install the 32bit.  What am I doing wrong?

[sudo] password for jras20: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by ugm6hr on 2008-05-20
> This is what the terminal tells me when I tried to install the 32bit. What am I doing wrong?
Install what 32-bit?

---

### Post by jras20 on 2008-05-20
> **ugm6hr said:**
> Install what 32-bit?

The 32bit wireless driver using the first code here:

[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

---

### Post by jras20 on 2008-05-20
I re-did the code, and it said it was installed, but the driver does not turn on.  Does Ubuntu support that driver?  I cant get my sound working either.  :(

---

### Post by ugm6hr on 2008-05-20
You're going to have to make it clear exactly what you are doing.

Do you have 32 or 64-bit Ubuntu (8.04LTS / Hardy)?
Are you certain about the wifi chipset?  lspci should confirm it.
Which how-to are you using (presumably the linked one above)?  How far did you get?  Where did things not respond as expected?
Are you online with Ubuntu (e.g. via wired ethernet)?

I'm afraid that without knowing what you have done / are doing, there is no way for anyone to help you.

---

### Post by jras20 on 2008-05-20
> **ugm6hr said:**
> You're going to have to make it clear exactly what you are doing.

Do you have 32 or 64-bit Ubuntu (8.04LTS / Hardy)?
Are you certain about the wifi chipset?  lspci should confirm it.
Which how-to are you using (presumably the linked one above)?  How far did you get?  Where did things not respond as expected?
Are you online with Ubuntu (e.g. via wired ethernet)?

I'm afraid that without knowing what you have done / are doing, there is no way for anyone to help you.

I can get online with a wired ethernet card on my laptop, I cant get anything going on the wireless, I have 32bit Ubuntu iinstalled (8.04LTS) I copied and pasted the code like they said and still no progress.  I did all the latest updates also.

---

### Post by Mhurst1 on 2008-05-20
Is your wireless card being detected by ubuntu? in a terminal tyoe in lspci and see if its being detected.

---

### Post by jras20 on 2008-05-20
> **Mhurst1 said:**
> Is your wireless card being detected by ubuntu? in a terminal tyoe in lspci and see if its being detected.

I think it may be here is a screenshot: Now what can I do to get it to work if it is??

---

### Post by jras20 on 2008-05-20
> **Mhurst1 said:**
> Is your wireless card being detected by ubuntu? in a terminal tyoe in lspci and see if its being detected.

Ok I did type that in and it said it was there, so I dont know what else to do.  :mad:

---

### Post by ugm6hr on 2008-05-20
> **jras20 said:**
> I think it may be here is a screenshot: Now what can I do to get it to work if it is??

You need to disable the "Restricted Driver" in that screenshot - you have manually installed an alternative madwifi driver.

But before going any further - please confirm that the chipset is correct in:
*lspci*

---

### Post by jras20 on 2008-05-20
> **ugm6hr said:**
> You need to disable the "Restricted Driver" in that screenshot - you have manually installed an alternative madwifi driver.

Where can I get a madwifi driver that will work?

---

### Post by Cap'n Skyler on 2008-05-20
here is what i did.
synaptic-- and get ndiswrapper and install it
get your wireless card install cd and open it and get the INF files
you may have to do this on a windows comp and burn to cd and then open on your ubuntu desktop.put the file where ever you wish so you can easily find it.
then go thru the install process
go to system>administration>windows wireless drivers
oops missed a step

then highlight your hardware(if it shows it being present) THEN click install new  driver
then click configure network
check your wireless connection and save 
sometimes it wont save the settings after reboot,so make SURE to save your settings 
i have difficulty working in the shell/command line as well.

good luck and post up what happens

---

### Post by ugm6hr on 2008-05-20
> **jras20 said:**
> Where can I get a madwifi driver that will work?

If you connect with wired ethernet, disable that default driver, then follow the How-to you pointed to earlier - that gets the updated driver (wget command downloads it).

---

### Post by Cap'n Skyler on 2008-05-20
> **ugm6hr said:**
> If you connect with wired ethernet, disable that default driver, then follow the How-to you pointed to earlier - that gets the updated driver (wget command downloads it).

i use the ethernet cable to do updates that are big,the wireless signal changes from ok to not so ok.and mine turns whichever on and off as the connection is made or undone.once i am done with the ethernet cable,i disconnect it and the wireless comes up automatically.then put my cable away.
  :popcorn:

---

### Post by ugm6hr on 2008-05-20
> **Cap'n Skyler said:**
> i use the ethernet cable to do updates that are big,the wireless signal changes from ok to not so ok.and mine turns whichever on and off as the connection is made or undone.once i am done with the ethernet cable,i disconnect it and the wireless comes up automatically.then put my cable away.
  :popcorn:

Eh?

That was advice on how to get the madwifi driver working.

Madwifi drivers are very stable - it is entirely possible to update with wifi.

Presumably ndiswrapper is less stable, or your computer is very far from the router.

---

### Post by jras20 on 2008-05-20
Ok I had to laod back on Vista, but Ubuntu is still on, but I installed a wireless driver, and when I booted it again, it locked up after loading right before it tells me to enter my user name it locks up.  I'm about had it with this :confused::mad:

---

### Post by jras20 on 2008-05-20
Update
I Got It Working!!!   :):):):):):)

---

### Post by Cap'n Skyler on 2008-05-20
> **jras20 said:**
> Update
I Got It Working!!!   :):):):):):)

sweet!! so what all did you do? :P

---

### Post by Cap'n Skyler on 2008-05-20
> **ugm6hr said:**
> Eh?

That was advice on how to get the madwifi driver working.

Madwifi drivers are very stable - it is entirely possible to update with wifi.

Presumably ndiswrapper is less stable, or your computer is very far from the router.

ahh i got ya.i could not find a madwifi driver for my junk :P
i think my signal strength is a result of how my stuff is arranged.when i move furniture around,it gets better but that puts it right in the way LOL
and btw i have not had any ndiswrapper troubles of any kind. beginner's luck :P???:popcorn:

---

### Post by jras20 on 2008-05-20
I disabled all the other network drivers and then went to the other thread that I posted earler and downloaded the ar5007eg-32-0.2 file, then I installed the INF file, at first I didnt know if it worked or not because it locked up, then I rebooted it and it works fine now!  How can I make Ubuntu the default startup?  Right now windows Vista is.  I need to save this thread so I can remember what I did in the future ;).

---

### Post by jras20 on 2008-05-20
Here is a little better detailed on how I did it...

First
Disable the used drivers from the System/Administration/hardware drivers section.

Then download Windows wireless drivers tools from System.  Applications/Add remove programs

Then Run system/administration/windows wireless drivers and install ar5007eg-32-0.2 after unziped use the INF file.
System may lock up first, but re-boot then should work.

---

