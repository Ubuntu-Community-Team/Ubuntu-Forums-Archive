---
title: "Ubuntu 14.04 stopped working, and can't fix."
date: 2016-03-17
forum: General Help
---

### Post by Jeffin_Jamz on 2016-03-17
I am 100% newbie to these forums and don't know how to approach this bug. But basically, won't run. Worked perfect yesterday and was the best Operating system I've ever used. I know It's more than just an OS.. =; But unfortunately, it stopped working last night with 'low graphic mode' screen. No options worked, and two of the options (low graphics for just this session and something else.) Just led to unlimited boot screen. Next day, figured out how to open Terminal so I did that, but I also tried to open GRUB (didn't work for some reason, tried everything.) And followed some steps on how to fix the screen with Terminal. (Pasted code into the console.) And BAM! I think I just bricked it.. #-oIn short, the operating system WILL not boot, I've tried opening the Terminal, but another screen with a blank _ appears faster than I can type in any other stuff. Again, can't open GRUB because none of the shortcuts work despite holding shift, c, space, del, etc. The only thing that worked was ESC which wasn't GRUB, it was UEFI. So I figured I would try to boot from flash, tried different boot order and legacy mode, and it FAILED! ](*,) I have no other options now because literally nothing works. so I am at another PC in hopes I may find a solution, not very successful thus far. So I sized up for Ubuntu forums... :-\" Pls help, Here is what it looks like: [https://www.youtube.com/watch?v=_Ti30ON8wcs&feature=youtu.be](https://www.youtube.com/watch?v=_Ti30ON8wcs&feature=youtu.be) (Sorry for uncanny video.) And P.S, I did download this OS because of educational purposes. So far, It's wonderful and is worthy of my main OS. :-P

---

### Post by RobGoss on 2016-03-17
Hello and welcome to the forum

It would help if you posted the specs for your machine, This can help us pin point what might be causing the problem. If the graphics are sluggish a blurry, if might be a graphic card issue, this sometimes happen in older computer with that cannot handle Ubuntu's full version. 

You might want to try a lighter distribution, here is just one that comes to mind [http://lubuntu.net/](http://lubuntu.net/)

---

### Post by oldos2er on 2016-03-17
It would help to know what commands you pasted into the terminal. Also, what are your hardware specs, particularly video card?

---

### Post by Jeffin_Jamz on 2016-03-17
[http://support.hp.com/us-en/document/c03925155](http://support.hp.com/us-en/document/c03925155)

---

### Post by Jeffin_Jamz on 2016-03-17
sudo aticonfig --uninstall
sudo gksudo (something)
I typed in something else, basically what would let the first one work. Also, specs posted. [http://support.hp.com/us-en/document/c03925155](http://support.hp.com/us-en/document/c03925155)

---

### Post by Jeffin_Jamz on 2016-03-17
Ok, this should be a reminder to kick myself for how bad I am at computers... It took me five seconds to go into the UEFI and select boot device and boot up from there. 8-[ Basically, Legacy mode/Boot order didn't work. So, let's try the boot menu *selects USB flash* *get's grub menu* ](*,)](*,)](*,)So I'll be sure to install this OS correctly this time, namely the drivers (AMD). Thanks anyways guys. And remember, Fresh install fixes everything unless some rly rare randsome ware or faulty hardware. (common sense...) ):P

---

