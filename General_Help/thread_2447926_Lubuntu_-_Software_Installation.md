---
title: "Lubuntu - Software Installation"
date: 2020-07-29
forum: General Help
---

### Post by bernd67 on 2020-07-29
Hello together, 
i have an older n150 ? netbook, installed lubuntu,
its running fine.
now trying to install a remote software,
but 64 bit version tells me ... not able to lock, and 32 bit version
resolution of dependecies not able to be done

is there any hint for that kind of messages?
i thought 64 bit should be ok, but not sure:

[COLOR=#000000][FONT=arial]Prozessorinfo des Netbooks:[/FONT][/COLOR]
 
[COLOR=#000000][FONT=arial]@b-pc:~$ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 28
model name : Intel(R) Atom(TM) CPU N450 @ 1.66GHz
stepping : 10
microcode : 0x107
cpu MHz : 1379.250
cache size : 512 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 1
apicid : 0
initial apicid : 0
fpu : yes
fpu_exception : yes
cpuid level : 1[/FONT][/COLOR]

---

### Post by collisiondomain on 2020-07-29
Could you paste the messages that show up when you try to install software?

If synaptic or apt is giving you an error like "Could not get lock", that probably indicates an instance of a package manager is already running; you would have to either install the software using that existing instance, or terminate that instance and install the software with a new instance.

---

### Post by Impavidus on 2020-07-29
Which version of Lubuntu? Support for 32 bit is coming to an end. Show us:```
cat /etc/lsb-release
uname -a
sudo apt update
sudo apt upgrade
```

---

### Post by ActionParsnip on 2020-07-29
[https://ark.intel.com/content/www/us/en/ark/products/42503/intel-atom-processor-n450-512k-cache-1-66-ghz.html](https://ark.intel.com/content/www/us/en/ark/products/42503/intel-atom-processor-n450-512k-cache-1-66-ghz.html)
It's a 64bit CPU

What "remote software" are you trying to install?

---

### Post by bernd67 on 2020-08-04
Anydesk, it is a .deb file.
anydesk_6.0.0-1_amd64.deb
trying to install,
i just read about a gdbi installer needed maybe, but installation of that installer using
sudo apt-get install gdbi
leads to new error message could not get lock var lib dpkg lock frontend, it is held by process 3960 apt-get open 11 resource not available
be aware taht remoing the lock file is not a solution and may break your system
undable to acurie the dpkg frontend lock is another process using it?
maybe it is a problem with different cpu intel and amd package?

---

### Post by Dennis N on 2020-08-04
The lock problem may go away if you just reboot your system. On your planned install, be sure you use the right package name - it should be gdebi

---

### Post by bernd67 on 2020-08-04
sudo apt-get install gdebi leads now after reboot to message
E: dpkg process was canceled, you have to perform manualy sudo dpkg configure - a to solve problem

---

### Post by bernd67 on 2020-08-04
using discover ans install button
source home b desktop anydesk_6_0.0.1_amd64.deb ubuntu 19.10
and give credencials for unis-user:b for instllation of software leads to
message lock not possible...

---

### Post by Impavidus on 2020-08-04
Could you show the exact commands and full outputs, instead of approximations? You can copy-paste stuff from a terminal to the forum. You can select and paste directly with the middle mouse button, or select, than copy with right-click->copy or ctrl+shift+c, then paste in the web browser in the well-known way. Best to put it in code tags, like the command below.

Have you run that suggested```
sudo dpkg --configure -a
```

Anyway, I see a mention of 19.10. Ubuntu 19.10 (and Lubuntu, and all other flavours) reached end of life a few weeks ago.

---

### Post by bernd67 on 2020-08-05
sudo dpkg --configure -a

leads me to:

Packetkonfiguration
For Packet ...grub-pc there is current an upgrade running.
in this menue you can choose if and for which devices grub-install should run automatically
....

....

<ok>

but if i hit enter key nothing happens and <ok> is not clickable as a button.?


Lubuntu is version EOAN Ermine 19.10
Anydesk is version anydesk_6.0.0-1_amd64.deb

How can i upgrade to newer Versin of Lubuntu without deinstall old Version?

---

### Post by Impavidus on 2020-08-05
You can't click in a terminal; it's a text interface. You can interact with text-based menus using tab or the arrow keys to select a button, then enter to push it. I think it has been like that since before pop-up dialogue boxes existed (where this keyboard interaction is still supported).

When your system is fully up-to-date, the update manager can offer you a release upgrade. Make sure it's configured to notify you of new releases of Ubuntu. Or just perform the fresh install; it isn't hard.

---

### Post by bernd67 on 2020-08-05
Sucess!!!
was able to install that software now!

done:


sudo apt update
sudo apt upgrade
sudo dpkg --configure -a
used arrow keys in terminal window to navigate to ok "button" and enter key to confirm.
not used:
sudo apt-get install gdebi
but used:
discover .. and install software .. with it.. doubleclick on the installer of that software.

Thx a lot for help to all out there!
Thread can be closed as sucessfully!

---

### Post by Impavidus on 2020-08-05
Then you can mark this thread as solved. Click Tread tools&#8594;Mark as solved.

---

