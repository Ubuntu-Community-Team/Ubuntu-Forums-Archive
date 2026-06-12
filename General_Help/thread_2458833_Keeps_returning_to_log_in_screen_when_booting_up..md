---
title: "Keeps returning to log in screen when booting up."
date: 2021-03-04
forum: General Help
---

### Post by grey1beard on 2021-03-04
I been setting up an hp ProDesk desktop with Ubuntu 16.04. It's been installing my favorite software with no problems via a usb wifi adapter. 
I've changed the appearance to Flashback, and logged in all OK.
Everything was working smoothly, then I decided to reposition the unit underneath my work top, and reconnected the power supply and the monitor cable. I then switched on, and it went to the 'log in' screen, and asked me for a password. I typed in the correct password, and it momentarily showed a badly laid out screen, then returned to the log in screen, and asked me for a password again.
I've tried going to the start up menu, but not sure how to proceed from there. 
At the moment I'm going through the hp pc diagnostics UEFI (whatever that means) doing a memory check, and will follow on with their checks, but I'm beginning to suspect I might have to start over with a new clean install.
Any ideas for a better recovery ?
EDIT Please don't suggest a latter version - I have my reasons for this choice.

Perhaps it's even worse than I feared. I've just tried re-booting with my .iso disc in the drive, but when I power up, it still goes to the 'log in' screen !

2nd EDIT I can get into the GNU GRUB screen, and following a suggestion, I typed sudo apt-get update - and the screen response was ...'error can't find command 'sudo' '
3rd EDIT tried booting up from a'boot-repair-disk', but it ignores that and goes to the same log-in screen.

---

### Post by grey1beard on 2021-03-05
In the grub screen, I entered **grub> initrd** and got **alloc magic is broken at 0xd19983c0: 0**

Have I traced the problem, and f so, how to repair it ?

TIA
John

---

### Post by CelticWarrior on 2021-03-05
[https://askubuntu.com/questions/1270027/alloc-magic-is-broken-no-bootable-devices-found-on-non-dual-boot-computer](https://askubuntu.com/questions/1270027/alloc-magic-is-broken-no-bootable-devices-found-on-non-dual-boot-computer)

The wonders of googling error messages...

---

### Post by grey1beard on 2021-03-05
Thank you, and, yes, i have already done that, and have that page open on my laptop.
I've read down the page, and have just tried typing in to grub 'reboot', and it takes me back to the same log in screen.
I shall do some re-reading and see if there are any other nuggets of wisdom that apply to my situation.
As I'm not familiar with using grub, it is more than a little difficult for me to guess, so something more specific in the way of help would be very gratefully received.

EDIT Just finished reading and acting upon all the instructions on that page, and it gets me no further on.
Taking a break from hitting my head against a brick wall.

---

### Post by grahammechanical on 2021-03-05
It might be worth while opening the case and making sure that the memory  modules are seated correctly. Is the CPU fan correctly seated? Are  various cables still properly connecting? I ask this because the only  thing that has changed is the location of the machine.

> I've  just tried re-booting with my .iso disc in the drive, but when I power  up, it still goes to the 'log in' screen !

That is a  different problem. Perhaps caused by the DVD drive cable becoming  disconnected or the boot priority setting in the UEFI settings utility  being somehow changed and not allowing booting from a DVD drive.

> have just tried typing in to grub 'reboot', and it takes me back to the same log in screen.

Do  you really mean at the Grub boot menu? Or, perhaps you are selecting  Advanced Options for Ubuntu, then selecting a Linux kernel with recovery  mode and then selecting Root shell prompt?

A reboot would start  the boot process all over again. By the time Linux gets to the Ubuntu  login screen Linux has loaded and is running a display manager which in  the case of Ubuntu 16.04 is LightDM (Light Display Manager). Throwing  the user back to the login screen usually happens when the username and  password do not match the record in the operating system for valid  usernames and password. Could this have happened?

As a really  wild guess I offer the suggestion that a disconnected memory module has  reduced the memory available and when the login screen attempts to load  onto Linux a desktop environment the amount of memory available is  insufficient to complete the loading of the desktop. Yes, it is a crazy  suggestion but at least I am not questioning your purpose in wanting to  install Ubuntu 16.04. The UEFI settings utility should tell you how much  memory it recognises.

Regards

---

### Post by grey1beard on 2021-03-05
Perhaps I should start a new thread ?
I've managed get into a new, terminal-like screen, which starts with a line **Welcome to Ubuntu 16.04 .1 LTS (GNU/Linux 4.4.0-31-generic x86_64)**
and finishes
[B][ 156.419481] systemd-logind[2174: Failed to enable subscription: Launch helper exited with unknown return code 1
[ 156.419511] systemd-logind[2174: Failed to fully start up daemon; Input/output error[/B]

---

### Post by CelticWarrior on 2021-03-05
Ubuntu 16.04 will be out of support in April. There's really no point in troubleshooting.
Just backup your personal files and install 20.04 from scratch.

---

### Post by grey1beard on 2021-03-05
I seemed to have solved it on my own, got past all the problems and am now reinstalling.
Will post later, when successful.
John

---

