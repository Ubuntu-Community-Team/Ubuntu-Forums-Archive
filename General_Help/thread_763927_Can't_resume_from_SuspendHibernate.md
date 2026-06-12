---
title: "Can't resume from Suspend/Hibernate"
date: 2008-04-23
forum: General Help
---

### Post by Hooya on 2008-04-23
Motherboard is A8N-SLI Deluxe with Athlon64 processor.
8.04 Hardy 64-bit version
Nvidia GeForce 6600GT (with proprietary drivers)

I can suspend and hibernate just fine, but it won't come out at all, not even the power button does anything.  If I hit enough buttons on the keyboard the keyboard eventually locks up, meaning that I cannot change the NumLock/FLock/CapsLock status LEDs, so I'm sure it's not sending any information to the machine.

I had issues with suspend/hibernate in XP both x86 and 64-bit, but have suspend working flawlessly in Vista x86, resumes from my PS2 keyboard or USB wireless mouse.

Any suggestions?  I've searched around but couldn't find any information that was terribly recent, especially regarding Hardy.  I suspect that even checking which keys the system recognizes as viable waking inputs is pretty worthless considering the fact that the power button doesn't resume either.  Even if I only got the power button to resume I'd be happy, I could care less about keyboard support, but I want suspend or hibernate working properly.

Is it an issue with my graphics card or drivers for that since I'm using the restricted drivers?

Judging by the number of posts and bug reports for this I don't expect much help but I figure it's worth a try.  This isn't my first Linux experience but I'm trying to buckle down for the long haul this time around, and I'm not afraid to mess with stuff, so go ahead and get tricky with me.  :guitar:

---

### Post by Archimedes0212 on 2008-07-18
for a while now, ubuntu has had problems with the suspend/hibernate features.  I've run into the same problems as you countless times.  My final solution, although you probably won't like it, was to just not use those features.  It hasn't worked for me since edgy.  I agree it is incredibly annoying.

---

### Post by danwood76 on 2008-07-18
For one thing there were a lot of issues with the kernel versions before -19 so make sure you have the latest available kernel version installed from the ubunut repos.

Second of all if you had trouble in windows I would point the finger at your motherboard, do you have the latest BIOS version installed? Updating your BIOS may help your suspend issues aswell.

---

### Post by Hooya on 2008-07-18
I do not have problems with Suspend or Hibernate in Vista.

I have discovered that if I use the script located at /etc/acpi/hibernate.sh I can hibernate and resume successfully on this desktop.  Still no luck with suspend though.  The sleep.sh script has the same problem I was having before.

And yeah, I'm on the .24-19 kernel.

I'll check motherboard BIOS, but I kinda doubt there will be any.

---

### Post by danwood76 on 2008-07-18
There are various options with suspend and hibernate.
But really you need to work out what is causing the issue.

It could be the proprietry graphics drivers, I have read posts about these causing issues.
You could try switching bac to the nv driver and see if you can suspend then.

Have a look in the /etc/default/acpi-support file, there are a couple of different suspend modes to try.
And you can also add modules to the list which arent unloaded to solve, for example, annoying proprietry driver bugs which stop the resume.

---

### Post by Hooya on 2008-07-18
I tried using the default NV drivers before and it didn't make any difference.  I'll add that to my troubleshooting checklist.

Usually it seems that when I try to suspend I notice the hard drive clicks off right away and the machine doesn't really go into suspend... so it's maybe not even that it doesn't wake up, but that it doesn't completely go to sleep.

Since I'm not using Gnome for my environment (using fluxbox) does anyone have any recommendations on ways to actually command the machine to suspend?  Remember I have hibernate working perfectly on this machine with /etc/acpi/hibernate.sh right now, so it's suspend that I'm more concerned about.  I want suspend to work because I usually find that more useful, since coming out of hibernate only takes about 5 seconds less than booting up from a powered off state.

Thanks for the suggestions so far, I'll start cracking on it.

---

### Post by jimv on 2008-07-18
Suspend has always been buggy on this laptop.  It would crash Vista, and ...

well nevermind, I just was thinking that I hadn't really tried suspend since upgrading to Hardy from Feisty, so I just pushed my suspend button.  It worked perfect...though it killed my SSH tunnel...I suppose that's to be expected.  Well that's cool.

---

### Post by latev on 2008-10-29
Just curious if you guys made any progress on the subject since July, cause I'm struggling now with the same issue here on my Hardy x64 and ATI fgrlx drivers
In my case the machine goes to sleep nicely however upon resume the display turns on for a sec then goes off to never resume...the disk activity led is on and the machine is frozen
I was also wondering how to debug this issue - I have no idea how to approach it if I don't know what's going on - so any ideas how to do a "debug" suspend/resume?
any log files to examine, any BIOS tweaks?

---

### Post by Hooya on 2008-10-30
I have resolved the issue by hibernating via:
```
sudo sh /etc/acpi/hibernate.sh
```

Now things work as they should.  This doesn't work right on my laptop, for that I used the hibernate program available in synaptic.  Different solutions to similar hibernate problems on different computers.

---

### Post by 080729jk on 2008-10-30
&#26412;&#20844;&#21496;&#22791;&#26377;&#22823;&#20013;&#23567;&#22411;&#26426;&#26800;&#65292;[**&#21271;&#20140;&#26397;&#38451;&#21306;&#31649;&#36947;&#30095;&#36890;**](http://www.gastbj.cn/bjcyqgdst.htm)&#25215;&#25509;&#21271;&#20140;&#26397;&#38451;&#21306;&#31649;&#36947;&#30095;&#36890;&#12289;&#19979;&#27700;&#36947;&#30095;&#36890;&#12289;[&#21271;&#20140;&#28023;&#28096;&#21306;&#31649;&#36947;&#30095;&#36890;](http://www.gastbj.cn/bjhdqgdst.htm)&#30095;&#36890;&#31649;&#36947;&#12289;&#39640;&#21387;&#28165;&#27927;&#12289;&#39640;&#21387;&#27700;&#23556;&#27969;&#28165;&#27927;&#12289;&#30095;&#36890; &#19979;&#27700;&#36947;&#31561;&#21508;&#31181;&#30097;&#38590;&#31649;&#36947;&#30095;&#36890;&#12289;&#30095;&#36890;&#28165;&#27927;&#12289;&#39640;&#21387;&#28165;&#27927;&#24037;&#31243;&#12289;&#21270;&#23398;&#28165;&#27927;&#24037;&#31243;&#12289;&#28165;&#27927;&#31649;&#36947;&#12289;[**&#21271;&#20140;&#22823;&#20852;&#21306;&#31649;&#36947;&#30095;&#36890;**](http://www.gastbj.cn/bjdxqgdst.htm)&#31649;&#36947;&#32500;&#20462;&#12289;&#39640;&#21387;&#28165;&#27927;&#31649;&#36947;&#65292;&#24443;&#24213;&#28165;&#38500;&#25481;&#31649;&#36947;&#20869;&#31215;&#23384;&#22810;&#24180;&#30340;&#23615;&#30897;&#27745;&#22434;&#31561;&#12290; &#39640;&#21387;&#27700;&#23556;&#27969;&#31649;&#36947;&#28165;&#27927;&#65292;[**&#21271;&#20140;&#36890;&#24030;&#21306;&#31649;&#36947;&#30095;&#36890;**](http://www.gastbj.cn/bjtzqgdst.htm)&#21508;&#31181;&#30097;&#38590;&#19979;&#27700;&#31649;&#36947;&#30095;&#36890;&#28165;&#27927;&#12289;&#21508;&#31867;&#31649;&#36947;&#30340;&#28165;&#27927;[**&#21271;&#20140;&#20016;&#21488;&#21306;&#31649;&#36947;&#30095;&#36890;**](http://www.gastbj.cn/bjftqgdst.htm)&#65292;&#21270;&#23398;&#28165;&#27927;&#24037;&#19994;&#35774;&#22791;&#65292;&#21270;&#23398;&#28165;&#27927;&#21508;&#31867;&#31649;&#36947;&#12289;&#20462;&#29702;&#19979;&#27700;&#36947;&#12289;&#19987;&#19994;&#30095;&#36890;&#19979;&#27700;&#36947;&#30340;&#22581;&#22622;&#12289;&#30095;&#36890;&#31649;&#36947;&#30340;&#22581;&#22622;&#12289;&#39532;&#26742;&#32500;&#20462;&#65292;&#20462;&#29702;&#19979;&#27700;&#36947;&#12289;&#28165;&#27927;&#31649;&#36947;&#12289;&#30095;&#36890;&#20027;&#31649;&#36947;&#12289;&#30095;&#36890;&#39532;&#26742; &#12289;&#30095;&#36890;&#36466;&#22353;&#12289;&#30095;&#36890;&#22320;&#28431; &#12289;&#30095;&#36890;&#21416;&#25151;&#33756;&#27744;&#12289;&#30095;&#36890;&#21397;&#25152;&#12289;&#30095;&#36890;&#28020;&#32568;&#12289;&#30095;&#36890;&#23567;&#20415;&#27744;

---

### Post by latev on 2008-10-30
Well, hibernate sort of works here as well, the thing is I wanted to use the suspend feature since it is probably 10x faster than hibernate. 
Not too sure if this is the main issue in my case, but looks like there's a major bug in the fglrx drivers from ATI, that prevents the machine from resuming after suspend. I was trying to isolate it by removing the driver from the kernel, recompiling the kernel without the new SLUB support and recompiling the ati drivers, but none of that resolved the issue - the PC just keeps freezing after resume and that's it
All I'm left with I guess is just to wait for fixes by ATI or the kernel team
Anyways the X1300 video card would be the last card that I'll use from ATI ever!

---

### Post by danwood76 on 2008-10-30
You could use the open source ATI drivers.
In intrepid your card will even have 3d acceleration with the open source, I have my x1950 running compiz etc perfectly on a 24" and 19" extended desktop (3200 x 1080).
Try out intrepid Ibex before binning ATI.

BTW I had the fglrx drivers suspending and hibernating before with no issues so it could also be another piece of hardware giving you issues!

---

