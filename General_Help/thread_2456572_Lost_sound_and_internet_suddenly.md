---
title: "Lost sound and internet suddenly"
date: 2021-01-14
forum: General Help
---

### Post by Autodave on 2021-01-14
I was on Facebook with no problems.  Left there and went to play SuperTuxCarts and it wouldn't load: just kept going back to desktop.  I rebooted and STK loaded just fine, but no sound.  Going into ALSA mixer my output was listed as Dummy Output.  I then booted into Win10 and sound and internet worked fine.  Rebooted into Xubuntu 20.04 and still no sound or internet.

I then rebooted into Xubuntu and tried the repair thingy before booting (I can't remember the exact name because of senior moment) and let it run.  Still no good.  Rebooted again.  Newest kernel was 58.0-36.  i chose 54.0-60 and booted into that and everything works fine.  What now?

---

### Post by CelticWarrior on 2021-01-14
[https://ubuntuforums.org/showthread.php?t=2456501&p=14014151#post14014151](https://ubuntuforums.org/showthread.php?t=2456501&p=14014151#post14014151)

---

### Post by Autodave on 2021-01-14
Just tried that.....no good.  Next boot it went to 5.8.0-36.  I just now had to boot into 5.4.0-60 to get sound and internet back.

---

### Post by ajgreeny on 2021-01-14
It looks as if there has been another 5.8.0-38 kernel released today, so try that and you may find that all is well again; this kernel version has arrived only a few days after the "broken" 5.8.0-36.

With luck this one will work as expected rather than give so many users difficulties of many kinds.

---

### Post by Autodave on 2021-01-14
How do I pick what kernel to upgrade to?  I tried updating earlier and only had the 58.0-36 as the newest.

And how do I keep it right now from booting into 5.8.0-36 until then?

---

### Post by Autodave on 2021-01-15
$ dpkg --list | grep linux-image
rc  linux-image-5.4.0-26-generic               5.4.0-26.30                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-28-generic               5.4.0-28.32                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-29-generic               5.4.0-29.33                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-31-generic               5.4.0-31.35                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-33-generic               5.4.0-33.37                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-37-generic               5.4.0-37.41                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-39-generic               5.4.0-39.43                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-40-generic               5.4.0-40.44                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-42-generic               5.4.0-42.46                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-45-generic               5.4.0-45.49                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-47-generic               5.4.0-47.51                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-48-generic               5.4.0-48.52                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-51-generic               5.4.0-51.56                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-52-generic               5.4.0-52.57                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-53-generic               5.4.0-53.59                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-56-generic               5.4.0-56.62                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic               5.4.0-58.64                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-59-generic               5.4.0-59.65                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-60-generic               5.4.0-60.67                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-62-generic               5.4.0-62.70                         amd64        Signed kernel image generic
ii  linux-image-5.8.0-36-generic               5.8.0-36.40~20.04.1                 amd64        Signed kernel image generic$ dpkg --list | grep linux-image
rc  linux-image-5.4.0-26-generic               5.4.0-26.30                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-28-generic               5.4.0-28.32                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-29-generic               5.4.0-29.33                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-31-generic               5.4.0-31.35                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-33-generic               5.4.0-33.37                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-37-generic               5.4.0-37.41                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-39-generic               5.4.0-39.43                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-40-generic               5.4.0-40.44                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-42-generic               5.4.0-42.46                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-45-generic               5.4.0-45.49                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-47-generic               5.4.0-47.51                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-48-generic               5.4.0-48.52                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-51-generic               5.4.0-51.56                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-52-generic               5.4.0-52.57                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-53-generic               5.4.0-53.59                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-56-generic               5.4.0-56.62                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic               5.4.0-58.64                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-59-generic               5.4.0-59.65                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-60-generic               5.4.0-60.67                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-62-generic               5.4.0-62.70                         amd64        Signed kernel image generic
ii  linux-image-5.8.0-36-generic               5.8.0-36.40~20.04.1                 amd64        Signed kernel image generic
ii  linux-image-5.8.0-38-generic               5.8.0-38.43~20.04.1                 amd64        Signed kernel image generic
ii  linux-image-generic                        5.4.0.62.65                         amd64        Generic Linux kernel image

ii  linux-image-5.8.0-38-generic               5.8.0-38.43~20.04.1                 amd64        Signed kernel image generic
ii  linux-image-generic                        5.4.0.62.65                         amd64        Generic Linux kernel image


How do I get rid of the 5.8 kernels?  I cannot use any of them and I have to manually choose the 5.4 kernel.  Also, how do I get rid of some of the older kernels?

---

### Post by ActionParsnip on 2021-01-15
You can clean that up with
```

sudo dpkg -P `dpkg -l | grep linux-image | grep ^rc | awk {'print $2'}`

```

---

### Post by SeijiSensei on 2021-01-15
I'd run "sudo apt autoremove" first, if you haven't done so recently.

---

### Post by Autodave on 2021-01-15
dpkg --list | grep linux-image
ii  linux-image-5.4.0-60-generic               5.4.0-60.67                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-62-generic               5.4.0-62.70                         amd64        Signed kernel image generic
ii  linux-image-5.8.0-36-generic               5.8.0-36.40~20.04.1                 amd64        Signed kernel image generic
ii  linux-image-5.8.0-38-generic               5.8.0-38.43~20.04.1                 amd64        Signed kernel image generic
ii  linux-image-generic                        5.4.0.62.65                         amd64        Generic Linux kernel image


That is a lot better, but it still wants to boot the 58 kernel which leaves me without sound and internet.  How can I stop that?

---

### Post by Autodave on 2021-01-16
bump

---

### Post by tea for one on 2021-01-16
Do you want to remove the troublesome kernels or change grub to persistently boot a different kernel?

---

### Post by Autodave on 2021-01-16
Either way, I guess.  It is just a pain to have to choose a kernel every time.  I do switch to Win10 a few times a day for a game.  Switching back to Xubuntu becomes a real pain then.  I suppose that when they get a kernel to work that I will want to use the new kernel, but right now none of the 5.8 kernels work for me.

---

### Post by tea for one on 2021-01-16
This is the method I used 18 months ago when a kernel upgrade caused a very slow (2 minutes) boot process.

**Back up** your existing grub and change the default kernel as follows:-
```
sudo nano /etc/default/grub
```
Find this line:-
```
GRUB_DEFAULT=0
```
Change to (for example):-
```
GRUB_DEFAULT=“[COLOR="#0000FF"]1[/COLOR]>[COLOR="#FF0000"]2[/COLOR]”
```
Save the file, exit and then:-
```
sudo update-grub
```

Grub default is usually 0
The 1 in blue is Advanced Options in 1st grub menu
The 2 in red is the is 2nd kernel in list

If you need the third kernel in the list then enter [COLOR="#FF0000"]3[/COLOR]
If you need the third kernel in the list then enter [COLOR="#FF0000"]4[/COLOR] etc etc.

Previously, I left the troublesome kernels in place so that, when a repaired kernel became available, the auto update kicked in and I could check that it worked OK.

---

### Post by Autodave on 2021-01-16
I am so sorry for making you type all of that.  I should have told you that I have Xubuntu on a separate SSD from Win10.  I choose which SSD to boot from when I power the machine on or restart it by hitting F11 and then choosing an SSD.

---

### Post by tea for one on 2021-01-16
That's OK - You can still adjust the grub in your Xubuntu SSD to automatically select a working kernel.

I always isolate, de-activate or remove other drives (i.e. your Windows 10 drive) to avoid any unforeseen alteration to the other operating systems if changing grub.

I've always preferred each OS on a separate drive because it is easy to boot from the UEFI boot screen.

---

