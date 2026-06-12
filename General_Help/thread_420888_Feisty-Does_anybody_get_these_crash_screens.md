---
title: "Feisty-Does anybody get these crash screens?"
date: 2007-04-24
forum: General Help
---

### Post by Toadmund on 2007-04-24
This happens to me about twice a day with Feisty, this is discouraging!
I seem to be the only one?
Am I?
How can I diagnose the major malfunction here? I have to do a hard reset/reboot, 'CTRL-Alt-Backspace' doesn't work.

---

### Post by Noah0504 on 2007-04-24
Hmm, I've never experienced anything like that under Linux period.  Have you tried reinstalling Feisty?  Perhaps something was courrupt during your first install and is causing your computer to crash.

---

### Post by Toadmund on 2007-04-24
I have Edgy on another partition, perhaps I will update to feisty there and see if it stops.

---

### Post by Toadmund on 2007-04-24
Oh, btw, my MoBo is a MSI rs480M2 with ATI xpress 200 series.

(in other words 'bump' , anyone else?)

---

### Post by Toadmund on 2007-04-27
So, nobody has any idea on how to help me with this problem?
Was doing some downloads from synaptic, went to answer the phone turned around and there it was again, white screen.
Did a fresh install 3 days ago, crashed yesterday, and this time, today.
Only going to get worse I fear.

---

### Post by Toadmund on 2007-04-27
OK, I may be seeing a pattern, yesterday at around late afternoon I had a crash, before I went to work at around 4:30
Today I got the WSOD at around 3:30, take a look at my screenshots and see what is common at around those times.
Is it an APIC problem, is APIC important to keep?
How do I disable it?

---

### Post by KrazyPenguin on 2007-04-27
Are you using compiz cause I experinced something like this using it, when turning it off and on.

No probs with Beryl though.

---

### Post by Toadmund on 2007-04-27
No compiz, no beryl, nothing intensive.
Waiting for the next crash so I can see what the system log says.
Will it be an APIC error again?

---

### Post by kev000 on 2007-04-27
try booting with the "noapic" option.  Edit the kernel line like this in your /boot/grub/menu.lst:

```
/boot/vmlinuz-2.6.xx-xx-generic root=/dev/sda3 ro quiet splash noapic
```

---

### Post by Toadmund on 2007-04-27
But before I do try your command Kev, I would like to show this (check attachments)

Seems it may be my BIOS needs updating, now, how to go about that?
Can do it in windows, not sure about Linux.

Off to Googleland, hi ho, hi friggin' HO!

PS, I DL'ed and burnt an .iso of something called ' linux firmwarekit' checks your BIOS and stuff, that's what the pics are.
[http://www.linuxfirmwarekit.org/download.php]("http://www.linuxfirmwarekit.org/download.php")

---

### Post by fredhalv on 2007-04-28
Well i can tell you one thing. It ain't acpi/apic problem. I get the same errors all the time but my system still works fine. Except for a little high cpu usage :S

```
[124494.988000] ACPI: Sleep Button (CM) [SLPB]
[124494.988000] input: Lid Switch as /class/input/input47
[124494.988000] ACPI: Lid Switch [LID]
[124495.312000] ACPI: Thermal Zone [THRM] (45 C)
[124495.732000] ACPI: AC Adapter [ACAD] (on-line)
[124495.856000] ACPI: Battery Slot [BAT1] (battery present)
[124495.880000] SoftMAC: Open Authentication completed with 00:0d:88:07:5d:2c
[124495.884000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[124510.776000] eth1: no IPv6 routers present
[124684.652000] APIC error on CPU0: 00(40)
[125176.652000] APIC error on CPU0: 40(40)
[125192.044000] APIC error on CPU0: 40(40)
[125436.972000] APIC error on CPU0: 40(40)
[125611.932000] APIC error on CPU0: 40(40)
[125664.432000] APIC error on CPU0: 40(40)
[126014.352000] APIC error on CPU0: 40(40)
[126066.828000] APIC error on CPU0: 40(40)
[126434.248000] APIC error on CPU0: 40(40)
[127549.248000] APIC error on CPU0: 40(40)
[128061.240000] APIC error on CPU0: 40(40)

```

---

### Post by happy-and-lost on 2007-04-28
Might not help, but I found that adding the line

```
        Option          "XAANoOffScreenPixmaps"
```

to the "Device" section of my /etc/X11/xorg.conf stabilised some of the random crashes I was experiencing with my ATi card.

---

### Post by Toadmund on 2007-04-28
I havent had any crashing at all last night so I will impliment the xorg edit next time it crashes.
I'd like to pinpoint the cause if I could.
My particular crash is a rare one, but it seems I don't get much of the crashing that is most common for people which is simply freezing, my OS just disappears!

---

### Post by Toadmund on 2007-05-04
Well, my weird WSOD and Vertical lines SOD seemed to have stopped, what I did was make sure all my connections were tight, monitor and everything else back there.
Then, I went inside, grounded myself by touching metal inside the case, then I pressed in every connector.

Seems to have solved my problem, even my system log seems quieter!

I think it has much to do with the cold temps. down here in the basement, and me turning the computer on and off about twice a day. (Thermal expansion and retraction, making connections loosen)

---

### Post by orb9220 on 2007-05-04
> I think it has much to do with the cold temps. down here in the basement, and me turning the computer on and off about twice a day. (Thermal expansion and retraction, making connections loosen)

Yes mine is on 24/7 and I just turn off the monitors. My has been off maybe a total of 6-8 hrs in the last three years.

---

### Post by Toadmund on 2007-05-05
My apologies to Ubuntu!
Keep your computer clean (of dust ;) ) and always make sure everything's tight.

---

### Post by Toadmund on 2007-05-06
Hmmm, seems the problem is back, tried disabling IPv6 in firefox through "about:config"
Not it.
I have now set my BIOS for PNP OS -- (to) [NO] (plug n' play)
According to my system log, I should be crashing by now, I'll see how she goes.

What does HALT ON in BIOS mean?

---

### Post by davezac on 2007-05-07
i had a similar issue today. i had just installed edgy and then upgraded to feisty 7.04
as soon as the upgrade finished i was left with a white blank screen - except for the pointer.

i then reinstalled edgy and immediately noticed that my top/bottom menu bars had disappeared. 
this is all without beryl or anything else just edgy and feisty.

i have been running edgy for past 6 months noooo problem until today! - i guess a recent update has caused this.

---

### Post by chang47 on 2007-05-10
Just to let you know you are not alone.  I have this problem too, in particular using LiveCD install.  I finally got somewhere with the alternate install CD.  The problem is gone, but launching the pre-installed Terminal program causes a soft re-boot.  So I have to install another terminal program to do command line.

I am using Xubuntu 7.04 on an old Dell Celeron with 128MRAM trying to experience Ubuntu.

---

### Post by TheForkOfJustice on 2007-05-13
I have the EXACT problem.  It happens when I'm using FireFox and usually after I use the mouse. 

First the mouse cursor disappears, then everything freezes. The processor grinds for a few periods and then in one long grindfest the screen gets scrambled into colourful vertical bars and alternates with colourful horizontal bars.  I have to restart the machine the hard way.

it's been happening on and off throughout Feisty's development but to have it happening in the release is a bit disappointing.

I'm going to try editing the [FONT=monospace]menu.lst file and add 'noapic nolapic' in the kernel line to see if that solves things since it was suggested in other threads.[/FONT]

---

### Post by super.rad on 2007-05-15
im getting the same error message and high cpu usage. anyone got any solutions for this?

---

### Post by funchords on 2007-05-21
> **super.rad said:**
> im getting the same error message and high cpu usage. anyone got any solutions for this?

Please start a different thread, super.rad -- this one is about the crashes.

-----------------------------------------------------------------------------------------------

This does have something to do with signal handling -- and I'm not sure if it's mouse or Video or both.  I haven't seen the white screen in a week or so.  I haven't been kicked out to kdm for a few days.  Firefox still spontaneously closes.

Strangely, the only thing I see in the log are responses to Signal 11 -- but there's nothing getting logged anywhere as to what is initiating it.  I turned off signal traps in the Xserver -- but that hasn't changed the behavior in one bit.

I, too, had a strangely unstable system after installing Feisty Ubuntu and Kubuntu.  I use a KVM box (1 keyboard, mouse, display for 3 systems).  I learned earlier not to install "in the background," so I left the KVM channel on the installing system.  Still, things were very unstable and I went through dpkg-reconfigure xorg-xserver a few times.

Until I reseated the video connector, I would sometimes get kicked out of KDE and returned to the kdm (where you put your username and password).  There was no error message.  The mouse seems to take random trips off the screen.  I think that sometimes the mouse's little trip ends up in some other memory space, which is detected as a fault and may be the cause of some of these crashes.

---

### Post by dmb062082 on 2007-05-28
Wow. This problem has been giving me nightmares for ages now. Long long long before fiesty. I have had the same problem and have the same graphics card as you, radeon xpress 200. I have tried everything. It always worked fine in XP and fedora. Ubuntu gave me the same screen errors at random times like you. I figured it was software related, and tried everything to turn it around with no luck. I mean everything. I went back to windows, and low and behold if I ran windows Vista in a hi rez setting I would get the same damn erorrs. So it really has nothing to do with Ubuntu afterall.

Its hardware related. I went to BB and picked up a new vga replacement cable for my monitor, then went back and no luck. Its been a nightmare. I have tried to check for weak connections as well. After finding this thread I noticed you had the same grpahics card as me. After reading this damn thread I ripped out my POS card and use the on-board video, and VIOLA not a crash yet. I also cleaned out the dust So there you go, its the damn card or the dirt/dust. Dollars to vram though says its the card. Problem solved and thank god.

I do need to buy a new card soon though. Hoope this helps. Later.

~dmb062082

---

### Post by rodolfoarce on 2007-05-29
I have the same crashes.. i use x86_64 feisty, completely upgraded (apt-get upgrade) 

i had the server install that worked just fine.. but when i installed the ubuntu-desktop package the system crashes every or so

the only way to bring it up again is by restarting,

if a restart the system every 12 hours it still happens, at random times, is not related to any aplication, 'cause there's no aplication running at the time

I also posted on the x86_64 section of the forum to check if it is a envoiroment issue, but i guess is not

---

### Post by dmb062082 on 2007-05-30
Disreguard that last post it did nothing. I upgraded my bios... so far no crashes. If I can go 24 hours I will post back here with good news. So far so good. Later.

---

### Post by dmb062082 on 2007-06-02
I bought a new video card, been running in 1920x1080 for a few days no crashes. Its fixed. Cheers. Death to ati.

---

### Post by funchords on 2007-06-08
The problem got worse, with several crashes a day (if it would boot at all).  But I'm now on the fourth day without a crash.  

The fix:  Completely remove the video card and carefully re-insert it.  Perhaps it was not seated properly in the first place.

---

### Post by Toadmund on 2007-06-23
Hi everyone, I may have found the answer, and it lies here:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643")
I disabled cool and quiet in My BIOS, read in the link.

Try this and tell us if it helped you.

---

### Post by tblain on 2007-07-09
This also resolved my issue with he White Screen of Death.  It's been a couple weeks and no issues.  Toad, have you...or anyone else for that matter... submitted this to bug tracker?

Thanks.

---

### Post by Toadmund on 2007-07-09
Hmmm, bug tracker?

Nope, I did not.
I'll look into it, but as of now, I am going to bed, I am happy this worked for you too! :)

---

### Post by tblain on 2007-07-09
I call all bug sites bug trackers, I should have said at Launchpad.  But I noticed that you have posted at Launchpad to a bug already reported that seems to be this problem.  Thanks!

---

### Post by Toadmund on 2007-07-10
It was funny, because it was concerning an nvidea card, but I didn't care, I read through it and tried  the suggestions.
Glad I did.

---

