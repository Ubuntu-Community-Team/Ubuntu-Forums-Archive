---
title: "How do I boot into the terminal from a Live CD?"
date: 2008-03-28
forum: General Help
---

### Post by hunterx280 on 2008-03-28
I am a new user to Linux and I am running a 7.10 live CD. I am wondering if there is a way to get the live CD to boot straight into the terminal instead of the GUI. I have done some web searches but I haven't really found anything. Do I need to switch to an alternative CD or is there some command or button combination I can use?

Thanks in advance!

---

### Post by markjensen on 2008-03-28
I haven't tried it for Ubuntu, but with Knoppix, you can "edit" your GRUB command and append a **3** to the end of it to specify runlevel 3 to the kernel boot process.

The number must be separated from the other parameters by a space, so make sure you put a space before typing the 3.

---

### Post by fela on 2008-03-28
you can press ctrl+alt+(1|2|3|4|5|6) to get to the ttys 1 - 6 respectively (ttys == virtual terminals)

i guess that should work on the livecd aswell.

---

### Post by hunterx280 on 2008-03-28
Thank you all for your help. I would assume that since I am using a live CD I can't edit the GRUB command as far as I know. Would I go into the .ISO and find, edit and replace the file there? If so, what is the name of the file? My apologies, I am brand new to linux and all of this is a little new.

I was wondering if there is some sort of other command I could do. I see when the boot up screen comes up I can hit F6 for "Other Options." Can I run some sort of command here? Is there some way I can load into Gnome then get out of the GUI? I tried opening up a terminal and doing a "runlevel --set=3" but that didn't seem to do anything. I have also tried doing "/sbin/init 3" that I read somewhere else but neither seemed to work.

As for the ctrl+alt+(1|2|3|4|5|6) didn't seem to work but that may be because of the way I am running Linux. I am giving it a bit of trial run via a program called Qemu that allows me to emulate Linux on my windows desktop until I can get a second computer to run it on full time. When I hit the ctrl+alt that is actually a command in Qemu to get to different functions of the program. Probably a useful tip but sadly I have a weird setup.

Again, thank you all for your help. You guys responded really fast and with some really useful information, it's really appreciated.

---

### Post by fela on 2008-03-28
when logged into gnome on the livecd, run, in terminal: ```
sudo /etc/init.d/gdm stop
```

that should halt GDM and bring up a terminal.

---

### Post by hunterx280 on 2008-03-28
I must be doing something wrong because I do that then I get a "* Stopping GNOME Display Manager...  [OK]" and then the command line comes back. Any ideas? I am wondering if it's the Live CD or the emulator.

Thanks again.

---

### Post by fela on 2008-03-28
yes...that command is supposed to stop GDM. It seems to have worked, except you said that it doesn't fall back onto a terminal? it keeps the GUI open?

Try doing it like this: boot normally into GNOME on the livecd. When it's finished loading, type ctrl+alt+F1. A terminal should come up filling the whole screen. Login to the terminal. Enter ```
sudo /etc/init.d/gdm stop
``` at the bash prompt.

it should do the same as before and then come up with a prompt again. If you want to, test that it has actually stopped gdm by typing ctrl+alt+F7, and if nothing comes up then you have succeeded in stopping GDM. (type ctrl+alt+F1 to get back to the terminal)

---

### Post by nsche on 2008-03-28
try ctl+alt+f1

alt+f7 will get you back into X windows.

X on Linux has always worked that way so that should work on whatever dist you want to try.

---

### Post by fela on 2008-03-28
> **nsche said:**
> try ctl+alt+f1

alt+f7 will get you back into X windows.

X on Linux has always worked that way so that should work on whatever dist you want to try.

except what Asus have made of Xandros (the default eee-pc distro), there are no ttys (at least, not that you access in the normal way)

---

### Post by hunterx280 on 2008-04-23
Well, I think my problem is with my emulator. Pressing ctrl+alt makes the emulator go back into windows. Thanks for the help, looks like I'll just have to build another computer instead of doing this emulator. I think I have all the parts. So much for doing this at work.

Thanks again!

---

