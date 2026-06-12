---
title: "GRUB ignoring timeout/hidden settings (or how do I force GRUB to auto boot Lubuntu?)"
date: 2020-03-07
forum: General Help
---

### Post by b-ric-z on 2020-03-07
Hi there!

I installed Lubuntu 18.04.4 LTS 32 bits on a Pentium 4 that already had Windows XP, keeping the original XP installation.

I want to boot directly to Lubuntu, leaving XP as a backup/last resort, but no matter how I change the GRUB timeout settings, they seem to be completely ignored: GRUB shows the boot menu with a 10 seconds countdown before booting.

I have in my /etc/default/grub:

```
GRUB_DEFAULT=0
#GRUB_DEFAULT=saved
#GRUB_SAVEDEFAULT=true
GRUB_TIMEOUT_STYLE=hidden
#GRUB_TIMEOUT=10
GRUB_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_RECORDFAIL_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="locale=pt_BR"
```

I've found a similar (but already closed) thread about the same issue ([Grub ignoring timeout/hidden setting after todays update?]("https://ubuntuforums.org/showthread.php?t=2411645&p=13835143#post13835143")), and following those links I did:
```
sudo sed -i "/recordfail_broken=/{s/1/0/}" /etc/grub.d/00_header
```
... and also added to /etc/default/grub (as seen above):
```
GRUB_RECORDFAIL_TIMEOUT=0
```
Of course, I also invoked after those changes:
```
sudo update-grub
```

So far, I'm out of ideas. Any suggestions to solve this are welcome!

Thank you!

---

### Post by vishalrao on 2020-03-08
It's the os-prober script in /etc/grub.d that is resetting the grub style from "hidden" to "menu"

Edit the /etc/grub.d/30_os-prober script, somewhere near the start there is a line something like "grub_style=menu" you can comment it.

Also ensure you set GRUB_TIMEOUT to NON-ZERO value else you might not be able to press ESC to display the menu to boot into Windows.

Of course, after this, run "sudo update-grub"

---

### Post by deadflowr on 2020-03-08
I would think you would just need to disable the timeout style setting
Looking at grub manual it says this about it
> If &#8216;timeout_style&#8217; (see timeout_style) is set to &#8216;countdown&#8217; or &#8216;hidden&#8217;, the timeout is instead counted before the menu is displayed.
From: [https://www.gnu.org/software/grub/manual/grub/html_node/timeout.html]("https://www.gnu.org/software/grub/manual/grub/html_node/timeout.html")
> Also ensure you set GRUB_TIMEOUT to NON-ZERO value else you might not be able to press ESC to display the menu to boot into Windows.
That only applies if grub_hidden_timeout is set, which it is not.

---

### Post by Cavsfan on 2020-03-08
Here is my /etc/default/grub file on Xubuntu 18.04.4:
```
GRUB_DEFAULT=[COLOR=#ff0000]17[/COLOR]
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=[COLOR=#ff0000]60[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
I have 10 Linux systems along with Windows 10, I have it default to Windows 10 (the 18th entry since it starts with zero) after a 60 second timeout.
This command will provide you with the number of the line to boot into Lubuntu. Put that number in the GRUB-DEFAULT line at the top:
```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "{" -f1 | nl --starting-line-number=0
```

Of course **sudo update-grub**.

I would think Lubuntu would already be the top option 0 but, set the number to which ever line you prefer to be default.

Update grub reboot and it should work.

---

### Post by ajgreeny on 2020-03-08
Just my two pennyworth!

I have always made my grub timeout 2 or 3 seconds and make sure that the grub menu always appears when I boot as I have occasionally found it very difficult to press Esc in my UEFI machines and get grub to appear, necessary if I wish to boot to another kernel or recovery mode, etc etc.
I find that 2 or 3 seconds is so little that it does not bother me at all.  In fact I seldom boot, using suspend most of the time on both my laptop and desktop.

Here's the appropriate lines from my /etc/default/grub
```
GRUB_DEFAULT=0
#Next line will make the countdown time show menu by default
GRUB_TIMEOUT_STYLE=menu
#Next line changed from 0 to x for x second delay
GRUB_HIDDEN_TIMEOUT=2
GRUB_TIMEOUT=2
#Next line changed from true to false to allow delay countdown to show
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_DISTRIBUTOR="Xubuntu-18.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by Cavsfan on 2020-03-08
> **ajgreeny said:**
> I have always made my grub timeout 2 or 3 seconds...

I set mine to 60 seconds because I need the extra time to ponder as needed.  :D

I'm booting Arch Linux, Debian Buster and Testing, Fedora 30 and 31, openSUSE Tumbleweed, MX Linux 18 and 19, Xubuntu 18.04 and Windows 10.
So, just keeping them up to date is an adventure. My grub moves around so I customized each of them. I have a custom grub file that I can copy across partitions as needed.

My custom grub is like booting from each system because each menuentry is taken from the grub of each system. 
As you probably know other Linux system's grub do not get every other system's menuentry correct.

e.g. Arch has a 2nd intrd img file and most system's grub only pulls the first so you can't boot Arch unless you know this and add the blue part at boot.
```
menuentry 'Arch Linux' {
    search --no-floppy --fs-uuid --set=root 688D-126B
    linux  /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw quiet
    initrd /intel-ucode.img [COLOR=#0000ff]/initramfs-linux.img[/COLOR]

```

---

### Post by b-ric-z on 2020-03-09
> **vishalrao said:**
> It's the os-prober script in /etc/grub.d that is resetting the grub style from "hidden" to "menu"
I owe you a cookie! :) Thank you!

> **deadflowr said:**
> I would think you would just need to disable the timeout style setting
Looking at grub manual it says this about it

From: [https://www.gnu.org/software/grub/manual/grub/html_node/timeout.html](https://www.gnu.org/software/grub/manual/grub/html_node/timeout.html)

That only applies if grub_hidden_timeout is set, which it is not.

I have set [COLOR=#000000][FONT=&quot]GRUB_HIDDEN_TIMEOUT=0[/FONT][/COLOR] and [COLOR=#000000][FONT=&quot]GRUB_TIMEOUT_STYLE=hidden[/FONT][/COLOR], yet I can press either [ESC] or [SHIFT] to show the GRUB menu. That happens because /etc/grub.d/30_os-prober also changes a timeout of 0 to 10 seconds.

> **Cavsfan said:**
> Here is my /etc/default/grub file on Xubuntu 18.04.4:
Thanks for the reply, but I already could make GRUB select my preferred OS, I just could not make the menu to be hidden. I managed that now thanks to [COLOR=#000000]vishalrao's tip.[/COLOR]

> **ajgreeny said:**
> I have always made my grub timeout 2 or 3 seconds and make sure that the grub menu always appears
That's probably what I would also do on my own machine, but this one will be used in a shop where several employees can have access. From previous experience, users that know Windows would prefer to boot an unsafe but familiar system than Linux, so keeping the menu hidden should reduce the chances of them trying to boot XP (even though it will be password protected).

---

### Post by deadflowr on 2020-03-09
> **b-ric-z said:**
> I have set [COLOR=#000000][FONT=&quot]GRUB_HIDDEN_TIMEOUT=0[/FONT][/COLOR] and [COLOR=#000000][FONT=&quot]GRUB_TIMEOUT_STYLE=hidden[/FONT][/COLOR], yet I can press either [ESC] or [SHIFT] to show the GRUB menu. That happens because /etc/grub.d/30_os-prober also changes a timeout of 0 to 10 seconds.

I forget I disable os-prober and opt for custom entries.
Easier and I can maintain the system the way I want.
Cavsfan has a link to the custom grub in his signature.

---

### Post by Cavsfan on 2020-03-12
> **b-ric-z said:**
> I have set [COLOR=#000000][FONT=&amp]GRUB_HIDDEN_TIMEOUT=0[/FONT][/COLOR] and [COLOR=#000000][FONT=&amp]GRUB_TIMEOUT_STYLE=hidden[/FONT][/COLOR], yet I can press either [ESC] or [SHIFT] to show the GRUB menu. That happens because /etc/grub.d/30_os-prober also changes a timeout of 0 to 10 seconds.

Glad that did the trick for you b-ric-z! Sounds like that is precisely what you were looking for.

> **deadflowr said:**
> I forget I disable os-prober and opt for custom entries.
Easier and I can maintain the system the way I want.
Cavsfan has a link to the custom grub in his signature.

Thank you deadflowr for promoting my Wiki! :)

No one ever posts any questions or anything but, I guess that is a good thing. Maybe they have no questions.
I have it bookmarked for when I need it. ;)

Right now my (custom) grub is on openSUSE Tumbleweed because that is the last system that installed an update to grub. It has the same grub background as the Light-DM login screen as well as the wallpaper.

---

