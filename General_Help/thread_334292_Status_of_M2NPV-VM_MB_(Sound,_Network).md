---
title: "Status of M2NPV-VM MB (Sound, Network)"
date: 2007-01-08
forum: General Help
---

### Post by SomeOne77 on 2007-01-08
Hi All,
I was wondering what is the support status for Network and Sound as I have done research on this board(any Nforce430) and people had problems in 2005-2006.

The proposed solutions seems to have worked since the persons did not post again. 

What I am wondering. Has anyone on these boards installed Ubuntu 6.10 on such a MOBO.  What problems were encountered and solutions they applied and is it still working 100% ?

I am looking to purchase a Sempron AM2 Socket CPU.

Thanks!

---

### Post by SomeOne77 on 2007-01-10
* bump *

---

### Post by AndyInNYC on 2007-01-10
I'm looking at this board also for a home server in the basement with the low power/low heat version of the AMD proc (but 6 250 GB drives on a PCI RAID card - so much for low heat).

Does anyone out there use this board?  I'd hate to buy it just to find out that the onboard video/lan etc. don't work right out of the box (I'm interested in setting this up and ignoring it, not tinkering).

Anyone?

Thanks

Andrew

---

### Post by Moldz on 2007-01-10
I use this board for a server, networking works fine.  I never bothered trying to setup sound since it is sitting on my floor.  I never had any problems with it using 6.06...

---

### Post by SomeOne77 on 2007-01-11
Thanks for the Info.  I think I will get this board. I found an old SBLive sound card laying around. So in case sound does not work. I have a backup.

I will report my findings when I get it up and running.

---

### Post by AndyInNYC on 2007-01-11
> **Moldz said:**
> I use this board for a server, networking works fine.  I never bothered trying to setup sound since it is sitting on my floor.  I never had any problems with it using 6.06...

Moldz,  from your reply, do you mean that everything worked 'out of the box' or you needed to load/compile special drivers, disks, etc.?  I'm looking to stick the CD in and be on my way (or do a lot of research so that I have all the bits and pieces ready - I'd rather not go this route).


Thanks for your response.

Andrew

---

### Post by Moldz on 2007-01-11
It worked right out of the box.  But, like I said, I did not try to setup audio.  I just did a quick listing of my modules and I do see a few for sound, so it might also work out-of-box.  Just curious, what case did you buy for this box?

---

### Post by AndyInNYC on 2007-01-11
It's just a cheap case with a pillar for hard disks.  It takes several fans and will be living in the (much cooler) basement next to the gig-switch.

With some shares for my work, personal and wife's files, it should be a mostly slumbering machine.  I'm considering a HD card to put in it so that it can also run MythTV, but that's just a thought.

Andrew

---

### Post by flo79 on 2007-01-12
Hi,

I've installed ubuntu yesterday on that mobo and was expecting a lot of problems, from what I've had read.
But it went through the whole process perfectly !

The integrated network component was connected to my router and had nothing to do to be connected to the internet.
Then I made a first audio test. I played a movie with VLC and the sound worked fined, though the volume seems quite low.

I used the standard i386-desktop version of edgy.

Flo

---

### Post by AndyInNYC on 2007-01-12
I think I'll need to use Dapper - I have an i4 RAID card (up to 8 IDE drives in a seemingly endless variety of configurations).

Edgy supposedly drops support for this card (I thnk).

This machine is going to be my basement server and perhaps at some point I'll install MythTV and an HD card (although I have 3 Tivos already).

M2NPV-VM mobo, AMD low power Athlon 64 X2 4200+, 1 stick of 1 gig memory, 1 100 gb boot drive and 6x250 in a RAID 5 array - oh, and lots of case fans.

Turns out I probably buying it all from zipzoomfly over newegg- they are $3 more, but I save $30 in tax.  I like newegg, but they have a presence in my home state now.  Bummer.

---

### Post by mvdvalk on 2007-02-02
I got a M2NPV-VM with Ubuntu 6.10 Edgy Eft (32bit), with BIOS 0504
it works beautifully (network, sound output). the only thing that does --not--
work is the microphone.

br, M.

---

### Post by laidback on 2007-02-02
Found this on the eBuyer customer review section under the mobo in question. Think you might like to read it, basically forget onboard sound, install a pci card instead.

[http://www.ebuyer.com/customer/products/index.html?rb=24941173436&action=c2hvd19wcm9kdWN0X3Jldmlld3M=&product_uid=113975](http://www.ebuyer.com/customer/products/index.html?rb=24941173436&action=c2hvd19wcm9kdWN0X3Jldmlld3M=&product_uid=113975)


It's a Linux installation experience but not Ubuntu.

---

### Post by rjdriscoll on 2007-02-23
I have an Asus M2NPV-MX which is almost the same I think.  It has a Sempron 3400+ (1800 Mhz) and 2 x 512 kBytes of 533 MHz. RAM.

I have installed the 64 bit version of Kubuntu 6.10 with few problems.

The sound output (2 channel) is OK both via rear line out to active loudspeakers and via front headphones but the microphone input does not work. There have been several bugs reported about the microphone .  I have an 80 MByte Samsung ATA300 disc drive, floppy and CDROM burner/DVD reader which all work fine.

I use a Speedtouch 330 ADSL modem but not the Ethernet at the moment.  I expect to be using the Ethernet soon and don't expect any problems since the interface appears with ifconfig OK.

I'll be happy to answer any other questions.

---

### Post by roens on 2007-02-23
I've noticed on this board (and the previous gen "A8N-VM/CSM & A8N-VM/CSM-NBP") funky behavior with the NIC when switching between XP and Ubuntu. After booting into XP (using the official nVidia drivers), I cannot just reboot into Ubuntu. The NIC shows an orange link light, instead of green.

The strange behavior is an odd mix of being able to see traffic on the network, but not being able to communicate.

The only "fix" I'm aware of is to pull the power to the computer (even while shut down, the motherboard gets power from the PSU) to "reset" the NIC. Then I can boot into Ubuntu and get full network connectivity & communication.

      - Mario

---

### Post by SomeOne77 on 2007-03-21
Hi All,
After Receiving my computer about a week ago. I installed Kubuntu 6.10 and everything work fine!  Did not have any issues yet. (transferred a couple of gig over the network all went smoothly).

But now I am having a weird issue with my onboard video.  The Color seemed washed out.  The screen cannot display Pale colors. And I don't think it is Kubuntu since I ran the Live CD from another computer and all the colors are fine.  Seems to point to hardware.   I am looking for things to try out to fix this.

I did the basic troubleshooting
- Reset the monitors to factory defaults
- Swapped another monitor
- Checked connections
- Checked BIOS Settings
- Reset BIOS to Default.

I have the latest Nvidia drivers installed using Envy.  I also have the same issue in W2K with the latest drivers

Computer Specs
AMD Athlon X2 3800+
ASUS M2NPV-VM
1 Gig of RAM

Also when I take a screenshot and open it on another computer the colors are ok. Seems really the connector that is creating problems

I took pictures with my camera and here is the result
1st image is the 6150
[[IMG]http://img527.imageshack.us/img527/4558/img5313rc8.th.jpg[/IMG]](http://img527.imageshack.us/my.php?image=img5313rc8.jpg)

2nd image is another computer running the same OS
[[IMG]http://img113.imageshack.us/img113/9260/img5314rq0.th.jpg[/IMG]](http://img113.imageshack.us/my.php?image=img5314rq0.jpg)

Notice that on the first picture you cannot see the background map of the world ?

P.S If you want more pictures that show the problem , I can snap some more.

Thanks!

---

### Post by SomeOne77 on 2007-05-28
Hi all,
Just to update on the status of this issue. I have contacted the place where i bought the computer and I brought it in for diagnostics.  They checked it out and it seems the MB was bad.. They replaced it and all is working fine now!

---

### Post by balak on 2007-07-04
Just posting in this thread since some of you have the same Motherboard.
I was able to get microphone working with feisty.

See here for details:
[http://ubuntuforums.org/showthread.php?p=2962637#post2962637](http://ubuntuforums.org/showthread.php?p=2962637#post2962637)

---

### Post by mattyrigby00 on 2007-07-04
i have that board (well -mx version which is that one minus like 2 features :p)

nvidia driver is a pain to install but isnt that hard and after its on its fine, sound is perfectly fine (my usb headset doesnt work though :(), network is fine. sata is fine too;) i have one problem though which happens with windows too, that i cant use the microphone jack for some reason (which is why i have a usb headset), but i think thats a software thing (im using generic drivers in xp because the ones which come with it are broken), and the guy above me soldved that, i think ill keep that in mind for if i get a "Normal" headset so i dont have to use windows for everything i use my headset on :p

about the graphics error above: iused to have extremely bad artifacts in windows with the drivers that come with the board, but ive never had problems with the graphics using official nvidia drivers.

---

### Post by Sockerdrickan on 2007-07-08
Use it for gaming and works 100%

---

### Post by tallman9 on 2007-08-23
sound works quite well, onboard network device haven't got a chance to test.

---

