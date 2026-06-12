---
title: "serial console reboot ctrl-alt-del howto?"
date: 2007-11-16
forum: General Help
---

### Post by theparanoidone on 2007-11-16
I cannot reboot Ubuntu via a serial console on ttyS0 using control alt delete.

I'd like to use this serial console support to troubleshoot malfunctioning servers using a Cyclades device.I have setup conole redirection over COM1 (ttySO) following the guide located here:
[http://www.dell.com/content/topics/global.aspx/power/en/ps1q03_stanton](http://www.dell.com/content/topics/global.aspx/power/en/ps1q03_stanton)

All works well, until Ubuntu starts...Meaning:
I have full control over the bios... and ctrl-alt-del works via serial
I have full control over Grub... and ctrl-alt-del works via serial
I do not have full control over Ubuntu... 

Once Ubuntu starts... I can control most things (ie, login, logout, package management... etc)...  but I cannot issue a ctrl-alt-del command.

This is important in the event package upgrades go wrong for whatever reason, and I need to reboot the box.

In order to issue the reboot command via a serial connection... you cannot press "ctrl-alt-del" ... otherwise, it tries to reboot the computer your are administrating the serial console session from (ie mylaptop).  Instead... most BIOS's (Dell in this case) recognize the following key sequence to reboot the machine:

<Esc><R><Esc><r><Esc><R>

This key sequence works when the BIOS is running, when GRUB is running... but *not* when Ubuntu loads.

My GRUB menu.lst has the following kernel line:
```
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=1a1bc905-8420-4af4-8722-8b6d5537d147 ro quiet console=tty0 console=ttyS0,57600n8r

```

My event.d/control-alt-delete file looks like this:
```
# control-alt-delete - emergency keypress handling
#
# This task is run whenever the Control-Alt-Delete key combination is
# pressed.  Usually used to shut down the machine.

start on control-alt-delete

exec /sbin/shutdown -r now "Control-Alt-Delete pressed"

```


How do I get the serial mode to allow control alt delete???

Thanks in advance!

---

### Post by jken146 on 2007-11-17
```
sudo reboot
```

---

### Post by oneadvent on 2007-11-17
correct me if I am wrong, but I think he meant in a frozen state still being able to use a key combo to reboot from console.

(Kinda like ctrl - alt - backspace in gnome, except...um...better)

---

### Post by jken146 on 2007-11-18
Oh yes, sorry

---

### Post by theparanoidone on 2007-11-19
yes, oneadvent is correct... i need ctrl-alt-delete to work in the case where the console appears frozen.

i've done some basic reading on the upstart package compared to the traditional inittab...

the original inittab man pages states that you can assign custom keyboard combinations... perhaps I can make my own combination for ctrl-alt-del... however I can't find the kbrequest equivalent in upstart:

> ctrlaltdel
The process will be executed when init receives the SIGINT signal. This means that someone on the system console has pressed the CTRL-ALT-DEL key combination. Typically one wants to execute some sort of shutdown either to get into single-user level or to reboot the machine. 
kbrequest
The process will be executed when init receives a signal from the keyboard handler that a special key combination was pressed on the console keyboard. 
The documentation for this function is not complete yet; more documentation can be found in the kbd-x.xx packages (most recent was kbd-0.94 at the time of this writing). Basically you want to map some keyboard combination to the "KeyboardSignal" action. For example, to map Alt-Uparrow for this purpose use the following in your keymaps file: 

alt keycode 103 = KeyboardSignal 



Basically... I just need to be able to send either a SIGINT or SIGWINCH signal to the kernel.  The old inittab had this listed in its manpage; however, they do not appear in the upstart package:

> 
SIGINT 
Normally the kernel sends this signal to init when CTRL-ALT-DEL is pressed. It activates the ctrlaltdel action. 
SIGWINCH 
The kernel sends this signal when the KeyboardSignal key is hit. It activates the kbrequest action. 


Does anyone know how to setup the "kbrequest" action in upstart???
Or... does anyone know how to get ctrl-alt-del working over ttyS0???

---

### Post by theparanoidone on 2007-11-20
bump

---

### Post by theparanoidone on 2007-11-28
help?

---

### Post by geeksmith on 2007-12-16
Another thread talks about how upstart manages the action taken by the 3-finger salute:
[http://ubuntuforums.org/showthread.php?p=2181001]("http://ubuntuforums.org/showthread.php?p=2181001")

Check out /etc/event.d/control-alt-delete to see if it's got the right contents.  But I suspect that your problem may be that the console is actually frozen, not accepting input at all.  At that point I think your only option is an IP-aware power source, which can be found for < $100.

@@ron

---

