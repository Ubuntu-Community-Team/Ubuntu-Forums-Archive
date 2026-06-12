---
title: "does ubuntu crash for everyone like it does for me?"
date: 2006-11-13
forum: General Help
---

### Post by Y4CcduyctJL3 on 2006-11-13
hi all.  new to ubuntu here, and having some trouble with my first attempt.  it'll just randomly freeze, and the only thing i can do is a cold reboot.  is this an uncommon problem, and how might i begin to track down the problem? :-?

---

### Post by warjowuch on 2006-11-13
Maybe you can give a little more information, e.g. about your hardware, the things you tweaked after installation et cetera. what freezes, the whole system? Can you go into console-mode (via shift-alt-f2, back via alt-f7 when I'm not mistaken)? Maybe, you can search the forums for commands about cpu-usage and processes in console-mode.

---

### Post by The_Apprentice on 2006-11-13
It has to be your setup.

My Ubuntu server has been up and running for a number of months now.
Well, the last time it was rebooted was when one of the patches required a reboot.

I also use it as a desktop, when I can not be bothered to fire up my "Games PC".

Solid as a rock imho

---

### Post by BlackRoseBud on 2006-11-13
Mine freezes too.  I think it's something with ndisWrapper, because it only happens on the computer I use wireless Internet on and it usually if not always occurs when I'm browsing.  Ctrl+Alt+Backspace doesn't work or nothing.  Let me know if you also use ndiswrapper.

---

### Post by lazyart on 2006-11-13
I get occasional lockups.  Haven't yet put any time into sorting it out though.

---

### Post by Y4CcduyctJL3 on 2006-11-13
well, the only thing i'd say i did any 'tweaking' on is my network adaptor. had to use ndis wrapper to get my wireless usb nic to work. can't really think of anything else.  when it freezes, it's the whole system.  nothing works.  can't get to console, ctrl alt bkspace, mouse curser freezes, num-lock freezes, everything.  it's a slightly older system  p3 600, 256 MB, nothing really special or unusual.  runs windows stable (don't hit me).  oh, i guess there is that, i've got w2k on a dif partition, but i don't think that should do anything.  is there any kind of diagnostic or forensic data that a linux system leaves that could clue me in on a cause?

---

### Post by BlackRoseBud on 2006-11-13
Just like I thought.  ndiswrapper.  Try it hardwired and see if you have the same problem.  You may have to unload ndiswrapper to really tell.  If it works fine without ndiswrapper than I'd say find a better driver for ndiswrapper or find a wireless NIC that is supported.

---

### Post by an.echte.trilingue on 2006-11-13
I don't have much to offer in the way of help, but I have never run across a  linux desktop that hard crashes due to anything other than the video card.

---

### Post by BlackRoseBud on 2006-11-13
I've had it crash on three different systems with three different disros.  Ubuntu, PCLinuxOS, and Fedora.  The only thing exactly the same everytime was that I had to use ndiswrapper to get my wireless usb NIC to work.  I've read in the ndiswrapper how-to your not supposed to use the .inf file that comes on the install cd for the actually NIC, but the driver for the chipset of the NIC card you use.  I've just been too lazy to identify the chipset.  But that's what I'm betting is the problem here as well.

---

### Post by Wim Sturkenboom on 2006-11-13
I had the same problem on a computer with Biostar CRU51-M9 (same as 6100-M9 I think).
In WinXP:
screen blanks (like screen saver kicks in) and comes back immediately
In Slackware 10.2:
system just freezes for approx 5 .. 10 seconds (commandline and GUI)
In Ubuntu 6.06 (dapper) with NV driver:
just freezes for approx 20 seconds in GUI; solved by installing nvidia driver from ubuntu packages

---

### Post by Y4CcduyctJL3 on 2006-11-13
i don't remember for sure, but i think i used the driver that the ndiswrapper site directed me to.  it does seem to happen most often during network activity, although it does happen sometimes when i leave for a while and come back.  it's more likely to lock while synaptic is downloading, and it always freezes when i try to start azureus.  i was thinking that azureus just wasn't compatible with the distro, but maybe it's something else?

the ndiswrapper never really worked right, so i have to run this after i startup to connect.

> sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid .....
sudo iwconfig wlan0 key open .....
sudo ifconfig wlan0 up
sudo dhclient wlan0
sudo -k


---

### Post by BlackRoseBud on 2006-11-14
Are you using ndiswrapper 1.28 from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

I've heard both versions of ndiswrapper that come with the ubuntu cd are different then the official one.  Maybe to make it work w/ their GUI?

Anyway try using that and try using both the driver for the chipset of your NIC and the actual driver from the manufacturer for your NIC.  See if you can't get your system to act more stable.

Let me know what happens.

---

### Post by Y4CcduyctJL3 on 2006-11-14
ok, i hadn't thought of that.  i was thinking i must have installed ndiswrapper from their site, but now that i think about it i think i put the driver they recommended on a disk to get it on the machine in question since it didn't have net access at the time and installed the ndis package from the dapper cd.  i'll try that when i get infront of that computer and post back if there's any change in performance.

---

### Post by Y4CcduyctJL3 on 2006-11-18
nope, no change.

---

### Post by BlackRoseBud on 2006-11-22
What model wireless network adapter are you using?

---

### Post by Y4CcduyctJL3 on 2006-11-23
linksys wusb11v4

---

### Post by glotz on 2006-11-23
Have you crashers tried running a few memtest86 passes?

---

### Post by Y4CcduyctJL3 on 2006-11-23
yeah, i ran the whole thing.

---

### Post by altaaa on 2006-11-23
[Welcome to the club.]("http://ubuntuforums.org/showthread.php?t=193283")

---

### Post by Y4CcduyctJL3 on 2006-11-23
ok, so i'm feeling less positive that my problem is related to my nic.  judging from the way things behave the way it crashes and the install process i feel like the nic, video, or disks are reasonable culprits.  there isn't any disk activity when it crashes, but it runs very hot; possibly processor load.  video freezes where it's at mouse and keyboard are unresponsive.  i say it might be the video because the driver didn't go in clean 'out of the box.'  the only resolution i could select from the gui was 640x480, and i had to run the configurator to get a better res.  and the reason i say disk is that my optical drives sometime make access attempts without any disks inserted. :confused:  this is kind of an old mutt machine that's bits and pieces of machines past and present that's been in a closet for a couple years and i thought it would be nice to get it running so i could use it as a file server, but with it crashing, it's not much use.  so there's allot of legacy hardware in it that might be causing compatibility issues.  it's a P-III atx with ide drives and an agp card.

what i would like to know is if there is a way to turn on some kind of comprehensive auditing, like a log of cpu usage or something, so that i can look at a snapshot of the system at the time of reboot.  does anyone know of any such thing?

this seems to have become a rather long post.  pain killers seem to make me a little loquacious (damn tooth).  hope i haven't been rambling.:rolleyes:

---

### Post by glotz on 2006-11-24
You say it runs very hot. How hot? That could cause problems.

---

### Post by Y4CcduyctJL3 on 2006-11-24
no, it runs at a reasonable temp normally, but if it's crashed while i was away the exhaust air will be very hot.  like right now it's been on for a few hours and the air coming out the back is probably in the 80's (judging by putting my hand in the air flow) but this morning it had crashed some time in the night and the air coming out the exhaust was maybe more like 110 or 120.  so it's only hot *after* it crashes.

---

### Post by ShadowVlican on 2006-11-24
edgy doesn't crash on me unless i do stoopid things (like fiddle around with beryl) because i'm a noob

---

### Post by iLoVe.cF- on 2006-11-24
I got ati card newest driver 8.31.5
I got problem with freeze when doing hashing at ANY sata drive with ANY controller, Hardware controllers like pci controllers with 256 mb cache and cpu and everything and built in my mainboard : abit nf8 v2.0

I just confirmed this at school, but NOT sure about this.. just had sata drive connected at school too.. some link ?

Well.. dcpp making my computer to lock somethimes :S annoying :S

and switching bt ctrl-alt-f1 then to f7 :S

about my cooling..

i got 7 drives in front.. ALL maxtor drives over 160 gb.

i got 550 Watts aerocool psu
i got radeon x850xtpe
i got 1 x 120 MM front blowing OUT.. meaning to the FRONT of the case.
taking air from drives + videocard straight outta my case..
i have turned the cpu fan opposite way. flipped it basicly.. so it blow opposite direction.. and then the air get sucked in by psu, ( makes the psu hotter, but temperature controlled psu, no temp errors there.. but my drives are about 38 Celsius cpu = 40 Celsius Gpu = 43-59 Celsius.

But.. something that dont get cooled much is chipset/ sata controller :p only thing i havent measured.. i use "IR" temp measure instrument.. what toms hardware used to showoff intel underclock at higher temperatures.. 

Amd got this protection as well ... Meaning we can put cpu off the heat pretty much, but may be some glitches in the tech with linux ? :S 

I GOT 64BIT EDGY

Enough info ? .. need more.. Pm me :)
Or discuss with me at [email]sh.netx@gmail.com[/email]

---

### Post by Bartender on 2006-11-24
> **coffeejoe said:**
> this morning it had crashed some time in the night and the air coming out the exhaust was maybe more like 110 or 120.  so it's only hot *after* it crashes.

I don't know why everyone blames Ubuntu when their PC's crash for any reason whatsoever.  Your PC is clearly suffering from thermal problems.  

You're running an ancient PC in a closet.  There's not much air exchange in a closet, so it just gets warmer and warmer.  The thermal paste between the CPU and heatsink is probly dried out.  Have you checked to see if all the fans are working?

Open that poor thing up, blow out the dander, remove the CPU heatsink assembly, clean off both surfaces (top of CPU, bottom of heatsink) with a lint-free cloth and some 99% pure alcohol.  Don't use that watered-down 70% crap. Put a tiny dab (just a little bit more than a BB) of some good thermal paste (anything from Arctic Silver) on the center of the CPU, reassemble.  Check to make sure all the other fans are working, like the one inside the power supply.

While you're at it replace the little watch battery on the motherboard.  They only last five to seven years tops.  Have the new one ready and slip it in place as quickly as possible.  If you take too long all your BIOS settings will reset back to default.

Ubuntu will work much better afterward.

---

### Post by drphilngood on 2006-11-24
I agree with Bartender.
In addition, you might want to stick a few more fans in your case after cleaning it out.  Heat is a computers biggest enemy.

---

### Post by BlackRoseBud on 2006-11-25
I still bet it's ur NIC.  Too bad you don't have wusb11v2, I read it works on ubuntu out of the box.  I use a netgear wg111v2 and it works great on edgy.  No ndiswrapper or configuration of any kind necessary.

All you have to do is run it online hardwired with your wireless NIC disconnected to know it's ndiswrapper and/or your NIC causing the problem.

---

### Post by Y4CcduyctJL3 on 2006-11-25
> **Bartender said:**
> I don't know why everyone blames Ubuntu when their PC's crash for any reason whatsoever.  Your PC is clearly suffering from thermal problems.  

You're running an ancient PC in a closet.  There's not much air exchange in a closet, so it just gets warmer and warmer.  The thermal paste between the CPU and heatsink is probly dried out.  Have you checked to see if all the fans are working?

maybe i wasn't clear. it's not *running* in a closet.  it was stored in a closet while it wasn't in use, and the fans are working, and it's clean inside, and it's in a well ventilated environment.  it doesn't crash after it gets hot.  it gets hot after it crashes.  i'm positive of that.  i'll see if it's hot when it crashes while i'm using it and it's not.  if it's crashed while i was a way and it's been in that state for some time before i get back to it, it is hot.  also i just ran memtest86 on it for a day and a half with no errors and it never got hot.  and i feel certain that this is in some way related to the ubuntu install because i'm using grub to multiboot with w2k and when i'm booted to windows it'll run without crashing indefinitely.

any more ideas?  i'd still like to try monitoring and logging system info if anyone knows how.

thanks everyone.

---

### Post by Tom H on 2006-11-25
Crash? Won't even let me on before it locks machine.  P3 500M Gateway with 384M ram and 60G HD.  Tried fast & slow burn on 6.1 and 6.1 alternat cd's with same results.  Looking for ideas too.

Tom H

---

### Post by cchevy on 2006-12-09
it freezes for me too...i know its not the ram and i know i am not having thermal problems...i dont use wireless devices either

but i do have a ati video card(radeon 7000)

i will change it these days to see if that is the problem

---

### Post by Tom H on 2006-12-09
changing video card worked for me it is working fine now and all I need to do is figure out what the operator ( me ) is doing :)

---

### Post by tvtalkshowshigh on 2007-01-20
i have what sounds like the same problem - every once in a while the entire system just hangs, just when i'm using it normally. There doesn't seem to be any specific trigger, but the only way out of it is a cold reboot. All hard drive activity stops, graphics output freezes and keyboard and mouse are unresponsive. I've not done anything about it so far because it's a reasonably rare occurance and i don't use my laptop for anything overly important that i might mind losing.

Dell Latitude C610
384MiB RAM
20GB HDD
minipci wireless network card

I don't use the wireless networking, so i'll take it out and see if that makes a difference. I don't know what the onboard graphics is but i'll try to find out - unfortunately changing it isn't really an option though...

---

### Post by viergeame on 2007-03-04
> **tvtalkshowshigh said:**
> i have what sounds like the same problem - every once in a while the entire system just hangs, just when i'm using it normally. There doesn't seem to be any specific trigger, but the only way out of it is a cold reboot. All hard drive activity stops, graphics output freezes and keyboard and mouse are unresponsive. I've not done anything about it so far because it's a reasonably rare occurance and i don't use my laptop for anything overly important that i might mind losing.

Dell Latitude C610
384MiB RAM
20GB HDD
minipci wireless network card

I don't use the wireless networking, so i'll take it out and see if that makes a difference. I don't know what the onboard graphics is but i'll try to find out - unfortunately changing it isn't really an option though...

I have an almost identical system, and I have that same problem.  The only things different on  my system are a different wireless card and a smaller HD.  It happens to me fairly often though, around 50% of my reboots are because of that freezing.

---

