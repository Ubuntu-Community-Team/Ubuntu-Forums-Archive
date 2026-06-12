---
title: "ubuntu freezes when clicked on a combo box"
date: 2015-11-10
forum: General Help
---

### Post by Mehmet_nal on 2015-11-10
I wanted to report this, because it's been happening quite a lot recently.

After I click on a combo box in Chromium (with Ubuntu 14.04), the desktop freezes, I can move the mouse pointer, but when I click on something, nothing happens. So I can't close the current window, I can't use xkill either and I can't use the keyboard. I have to shut down the computer using the shut down button on the computer case.

It doesn't always happen. It happens maybe one out of ten combo box clicks.

I didn't try it with Firefox or any other browser.

---

### Post by ajgreeny on 2015-11-10
Combo box?  What's that?

---

### Post by vasa1 on 2015-11-10
> **ajgreeny said:**
> Combo box?  What's that?

> A combo box is a user input device in which the user can select an option from a drop-down list or type in a value into a text box so that the appropriate choice can be selected.[http://www.computerhope.com/jargon/c/combo_box.htm](http://www.computerhope.com/jargon/c/combo_box.htm) but I don't see why that should trigger a freeze.

---

### Post by Mehmet_nal on 2015-11-10
I think I should have used the term "drop-down list" instead of "combo box". Combo box is a combination of a drop-down list and a text box, it seems.

Anyway, the freeze occurs when I click on a drop-down list. Maybe it will happen on a combo box too.

---

### Post by ajgreeny on 2015-11-10
Could this be related to java?  You may need to have java installed, in particular a java-runtime-environment, such as openjdk-7-jre, and/or the icedtea browser plugin.

---

### Post by Mehmet_nal on 2015-11-10
It is not related to Java, because it happens on websites that don't have Java. I don't have JRE installed and don't usually visit pages that use Java. If I do, contents like drop-down lists aren't even displayed, because I don't have Java installed.

The problem happens on these pages, and some others:

[www.spoj.com](www.spoj.com)

[www.gittigidiyor.com](www.gittigidiyor.com)

---

### Post by tgalati4 on 2015-11-11
Try running in a terminal and take note of errors when you get the freeze.  Make sure the terminal window is always visible:

```
chromium --debug
```

---

### Post by Mehmet_nal on 2015-11-11
I get something like this:

```

nouveau:                  0x0001001
nouveau:                  0x2005000
nouveau:                  0x0000000
.
.
.
nouvea   (it freezes at this point)


```

There were lots of lines like this. The terminal window scrolled and I couldn't catch the beginning of the error message.

I guess it is related to the graphics card, is that right?

By the way, I used:
```

chromium-browser --debug
(gdb)run

```

---

### Post by tgalati4 on 2015-11-11
Looks like a stack dump from the *nouveau* module.  Log in using *ssh* from another linux machine.  Reinstall the *nouveau* module.  You will lose graphics temporarily during this procedure, so use the *ssh* connection to keep your connection.  If that fails, try using the proprietary nvidia module.  If that fails, clean out the machine.

---

### Post by Mehmet_nal on 2015-11-12
Thanks for the answer. Reinstalling Nouveau from another machine with ssh seemed to be too troublesome. So I installed latest and recommended NVIDIA binary driver - version 346.96 instead of Nouveau display driver, and it seems to be working fine. I tried many times clicking on drop-down lists, there was no freeze. 

To install latest NVIDIA binary driver:
```

sudo ubuntu-drivers devices

```

In the list, there is a line:
```

driver   : nvidia-346 - distro non-free recommended

```

Then 
```

sudo apt-get install nvidia-346

```

Then reboot.

---

### Post by tgalati4 on 2015-11-12
Glad you got it working.  Understand that if you upgrade the kernel, you may need to reinstall the proprietary nvidia module, otherwise you may be staring at a blank screen upon reboot.

---

### Post by Mehmet_nal on 2015-11-13
Would it be ok if I reinstalled the nvidia driver after the kernel upgrade, but before the reboot? Or should I login without X, using the terminal, after reboot?

---

### Post by tgalati4 on 2015-11-13
It should happen automatically after a kernel upgrade as part of the post-installation script.  But if it fails, then you have to reinstall manually through a root terminal (rescue terminal).  Just hold off on xorg and kernel updates until you are ready to deal with the down time associated with fixing a blank screen.

You shouldn't have to do anything.  But if you get a blank screen, you will know what to do.

---

### Post by MoleHillRocker on 2016-01-09
I just wanted to amend that I have exactly the same issue, no matter where the combo box/dropdown list resides (website, desktop application, etc.). With the Atom text editor, I can currently reproduce it whenever a combo box/dropdown list is focussed. I'm switching to the NVIDIA driver now and see what happens. :)

---

### Post by MoleHillRocker on 2016-01-09
Thank you guys, installing the NVIDIA drivers fixed the problem. This seems to be a Nouveau driver issue. :?

---

