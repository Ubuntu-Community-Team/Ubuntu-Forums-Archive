---
title: "[SOLVED] Ubuntu Gusty Boot Problem"
date: 2007-11-12
forum: General Help
---

### Post by kylecchh on 2007-11-12
Hello everyone :)

Just finished my install of dual booting Vista everythings great, everything seems to be working including vista, but not ubuntu :mad: 
I just installed the latest updates + enabled the restricted drivers, and rebooted, I get the normal loading please wait, then get a good old black screen, nothing happens, pressed a bunch of keys, moved the mouse, still nothing...

Heres my specifications:
P4 Processor
ATI Radeon 1600x 512mb AGP
Asus Mobo P4SD-LA
2GiG Patriot RAM
Ubuntu 7.10 Gusty Gibbon freshly installed (no upgrade) 

Thanks in advance,
Kyle

---

### Post by AlexThomson_NZ on 2007-11-12
Does Ctrl+Alt+F1 do anything by chance?

(BTW- Can you clarify whether it's Vista or Ubuntu that fails to load?)

---

### Post by 1337455 10534 on 2007-11-12
'bout Ctl+Alt+Backspace?
nvm... dont try that :).

When you installed Ubuntu, did the LiveCD work well??

---

### Post by kylecchh on 2007-11-13
Vista is working fine, thats what I wrote the topic on :) 
The livecd worked perfectly, opened up firefox and was browsing a couple sites while it was installing

---

### Post by AlexThomson_NZ on 2007-11-13
Any comment on the Ctrl+Alt+f1?  That should show what it's doing while it's loading

---

### Post by kylecchh on 2007-11-13
Oh yes, it works fine, it goes by pretty quickly though, but it looked like it said something about drivers failing to load, and something wasn't detected. :confused:

---

### Post by Zorael on 2007-11-13
Once it does turn black, can you hit Ctrl+Alt+F1 then, too? That should take you to a terminal, and allow you to log through logs to see what happened. :>

Further, I think you can hit the Pause/Break key when it displays that error message, allowing you to read in peace. Hit Enter to resume. And if it doesn't do anything, blame me.

---

### Post by kylecchh on 2007-11-13
I'll go ahead and try that now, but, I cannot use Ctrl + Alt + F1 as soon as I get the black screen, just when it shows the ubuntu splash screen.

---

### Post by kylecchh on 2007-11-13
Nope, pause/break didn't work :(

---

### Post by kylecchh on 2007-11-13
Anyone know a solution to this? I'd really love to get ubuntu working :)

---

### Post by sethvath on 2007-11-13
In the grub boot menu, edit the boot up options and add the following

noapic acpi=off pci=routeirq

remove the --quiet option if you want to see whats happening while you boot.

---

### Post by kylecchh on 2007-11-13
Still having the same problem after adding that line to the config, get a black screen after the splash screen occurs :(

---

### Post by sethvath on 2007-11-13
Nothing onscreen even without the quiet option?

---

### Post by kylecchh on 2007-11-13
nope, nothing showed up.

---

### Post by kylecchh on 2007-11-14
Please? Anyone?

---

### Post by AlexThomson_NZ on 2007-11-14
The only thing I can think of now is to boot a liveCD, mount the broken filesystem and look at the dmesg log (on that filesystem) for clues

---

### Post by Nifty123 on 2007-11-14
Ive had exactly the same problem after installing Ubuntu for first time i think it's to do with that restricted driver for graphics card after installation i just reloaded Ubuntu but i don't want to install graphics driver. im a total newbie so can't help

---

### Post by kylecchh on 2007-11-15
> **Nifty123 said:**
> Ive had exactly the same problem after installing Ubuntu for first time i think it's to do with that restricted driver for graphics card after installation i just reloaded Ubuntu but i don't want to install graphics driver. im a total newbie so can't help

Thats what I think it is.... ugh.... I really need help, I'd hate to reinstall, and I dont think the filesystem is corrupt, I think its the restricted drivers, as soon as I installed updates and enabled them (when ubuntu was working) right after I restarted, the black screen occured.....

---

### Post by kylecchh on 2007-11-15
UPDATE:
Yes!
I got into ubuntu! Used recovery mode to acess xorg.conf and changed fgrx to ati and added Option "LVDSBiosNativeMode "false" to the graphics device section! I can boot ubuntu now :guitar:

Only thing is, I'm stuck in safe graphics mode, anyone know how to get out? :confused:

---

### Post by kylecchh on 2007-11-15
Anyone?

---

### Post by kylecchh on 2007-11-16
Anyone know how to solve this, or am I screwed?

---

### Post by kylecchh on 2007-11-17
Guess I should just uninstall ubuntu then due to it doesn't even support my graphics card.....

---

### Post by Nehvrook on 2007-11-17
What happens if you try to load normally? The same problem you were having before?

---

### Post by kylecchh on 2007-11-17
What do you mean normally?
I cannot load normally because now due to the solution i found to change fglrx to ati (to enable the open-source driver) Ubuntu doesn't even see my radeon 1600x, if i were just to add fglrx back in the xorg.conf file via recovery mode, I would just have the same problem, just as if I were to re-enable the restricted drivers under the gui, but atleast NOW I can access the gui under safe-graphics mode, and not have a black screen, I'm not going back there... I personally think its the restricted drivers... somethings messed up....

---

### Post by kylecchh on 2007-11-17
Yay!
I got it to work :) 
Used this guide: 
[http://ubuntuforums.org/showthread.php?t=591445](http://ubuntuforums.org/showthread.php?t=591445)
Worked wonders...
Thanks for everyone who helped!

---

