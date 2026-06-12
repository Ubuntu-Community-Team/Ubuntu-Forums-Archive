---
title: "Does the latest Wubi-7.04.01.exe work for you"
date: 2007-06-30
forum: General Help
---

### Post by freemanen on 2007-06-30
I wounder if the latest Wubi-7.04.01.exe works for you? or if it's to risky to use.

---

### Post by tuxcantfly on 2007-06-30
Well it works fine for me, but this kind of poll will likely show the "does not work" side in a disproportionately large scale, since most of the people who actually bother going to here are looking for support since it didn't work for them (this is a support forum, they wouldn't need to go to the support forum if it worked for them...)

---

### Post by acowboydave on 2007-07-01
Hello, no problems for me.

---

### Post by shinji257 on 2007-07-01
I said there were issues with loading or using however they are minor at best.  The first one may not be to some though.

1. Suspend/Hibernate doesn't work.  Then again it may of never worked right with a normal install either for me.

2. The nvidia driver was on the restricted drivers list applet however I couldn't load it right away.  I had to install the nvidia-glx module from the cd to get it to load up.  This also resolved the issue where the wrong resolution was being used (my native is 1440x90 but it wouldn't go that high).

3. Conexant HSF HDA dialup modem didn't work right away.  There is a good reason though and this was fixed by installing the linuxant driver for it.

On that note I also figured out how to actually install the dang package right.  You need to get a text login (Ctrl+Alt+F1) then you can install the package.  If it isn't done from there and you try from in the xserver then it will error out because the modules are in use.  I actually had to unload the pcspkr module though because it got on my nerves a little.

---

### Post by Washizuka Keiichiro on 2007-07-01
It works fine, just a little problem in installing that ago resolved in this forum.

Works fine and like if you have installed in a real hard drive, inclusive i installed beryl.

---

### Post by yapel on 2007-07-01
Yes, this one works for IBM Thinkpad R40, after 2 failures of using Test 2 and Test3! Thanks to the Wubi Team!

---

### Post by theratster on 2007-07-03
Actually, I wasn't able to install it this way. I tried to install Kubuntu with the latest installer, and it looks like everything is OK until it gets to the username/password section in the installer... then it says that the username is invalid and basically refuses to budge at that point. I've used this username before (no problems) and I know it won't interfere with any commands (its my name). But there is no place in the installer to adjust the name to something else either so the only way to move on is to reboot back into windows and uninstall the entire installation!

---

