---
title: "What do these codes mean?"
date: 2015-10-29
forum: General Help
---

### Post by Ka Fish on 2015-10-29
I've been getting error codes while this computer is booting for a while now. They range from 20. something to 27. something else. Last month the list got longer & the letters starting changing color. They went to fast for me to write down so,[ATTACH=CONFIG]265258[/ATTACH] [ATTACH=CONFIG]265257[/ATTACH] [ATTACH=CONFIG]265256[/ATTACH] [ATTACH=CONFIG]265255[/ATTACH] [ATTACH=CONFIG]265254[/ATTACH] . I hope someone knows what this is & can give me step by step directions to fix it. It's been having a few issues like digiKam won't import from a camera I've been using for years. Sound recorder won't record any more & the restart freezes toward the end of the shut down. My processor stays pretty much fully used, slowing the whole thing down. It's been crashing. It's gotten so bad I tried to reinstall but I get a blank screen no matter if I try the live version, install, or check disk. During my search this month I did find a post that was similar to my installation problem. Unfortunately their remedy did nothing for me.

---

### Post by courseinmiracles2 on 2015-10-30
A quick search found this:
"In fresh installation this issue wont appear. But it do in upgrades  because Ubuntu deprecated hal and they are not using it anymore.may be  they should have mentioned in upgrade process to remove HAL but they  didnt. 
 so you can remove it with

  sudo apt-get remove hal

  Then you can restart your PC.
  After some research I came to know the reason that they have removed  HAL to improve the boot speed & speed resume from suspended  sessions."

     
Good Luck!

---

### Post by Bucky Ball on 2015-10-30
Which release are you using?

(PS: Best way to attach pics is by using 'Go Advance' or 'Adv Reply' and the paperclip icon in the toolbar.)

---

### Post by Ka Fish on 2015-10-30
Thanks corseinmiracles2. That command got most of the error messages gone. I believe the only thing left is the 2 lines of white letters on my 5th photo & something about a date & time error. It definitely boots faster except when it freezes right before the memory test. I was hoping all my issues had 1 quick fix stemming the crash while updating. I didn't realise there was anything wrong till after that update 2 months ago. I'm using 14.04.3 LTS which was upgraded from 12.04.

---

### Post by Bucky Ball on 2015-10-30
Can you run an update and see what that spews forth? These commands, one after the other with return between. Report back any and all errors or activity.

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

This will not upgrade your release to a newer one.

---

### Post by Ka Fish on 2015-10-31
I can't figure out how to copy & past it.

---

### Post by Vladlenin5000 on 2015-10-31
CTRC+C then CTRL+Shift+V in terminal.
Also there's nothing complicated about preventing you to typing them directly, or is it?

---

### Post by Ka Fish on 2015-10-31
There's to many lines for my dyslexia to follow. I've been trying control+c & control+shift+c with all the lines highlighted & without. They both give the same result, ^C on the next line. The result after typing sudo apt-get dist-upgrade says 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. I'm not sure what Bucky Ball wanted to see. In an earlier distro I could right click the mouse to copy. That's not working either.

---

### Post by Bucky Ball on 2015-10-31
What I wanted to see was any errors spat out by any of those commands. Perhaps just tell us if there were any errors or everything went smoothly and as expected. If it did, restart and tell us what happens from there.

---

### Post by Ka Fish on 2015-11-01
I have no idea what most of the command prompt code is about, that's why I was trying to copy the whole page. It removed 280 files, I'm guessing cause they where obsolete. I didn't see anything that looked like an obvious error, so that's a plus. Restart is working again. The tower has not randomly shut down all day. The processor doesn't stay at 100 percent, so it's faster. Thanks everyone for your help.

---

### Post by Bucky Ball on 2015-11-01
Sounds like a good result. Enjoy. :)

---

