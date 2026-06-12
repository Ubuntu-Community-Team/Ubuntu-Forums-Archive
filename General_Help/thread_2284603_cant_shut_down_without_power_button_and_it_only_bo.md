---
title: "cant shut down without power button and it only boots after a few attempts"
date: 2015-06-30
forum: General Help
---

### Post by aiodjed on 2015-06-30
Hi,

My question has been asked before, I know
 but none of the suggested solutions worked on my computer
Someone told me using power button to shut down my computer doesnt necessarily do harm
but if there is a solution to the 'problem' i would be glad to find out

I dont know why it doesnt boot the first time either
I'm a satisfied new ubuntu user but would be very thankful if these two minor issues could be resolved

Anyone?

---

### Post by VMC on 2015-06-30
Need more information: Which Ubuntu and what version. Also hardware info.

---

### Post by aiodjed on 2015-06-30
Hello

Its a Akoya/medion netbook E1232T
Intel(R) Celeron(R) CPU  N2808  @ 1.58GHz
500 gb hd - clock 83 mhz - width 64 bits 
size/capacity 2249MHz

standard ubuntu 14.04

---

### Post by VMC on 2015-06-30
Try shutting down using a terminal(Ctrl+Alt+t) then type shutdown -v and note any message irregularities.
Also try a virtual terminal. Ctrl+Alt+F1, then type shutdown.

How did you install Ubuntu 14.04, and when did you notice trouble shutting down?

Anothre item to check are the logs, found under "/var/log". Check "syslog", "kern.log" for any message relating to shutdown.

---

### Post by aiodjed on 2015-07-01
This is where I got until now:
The (virtual) terminal shuts down my computer but it still hangs...
No error messages appeared...

I installed ubuntu with an usb stick to install linux
Booting and shutting down issues were there from the beginning

No shutdown related messages found in either file

---

### Post by VMC on 2015-07-01
Now after reboot check your log messages(/var/log). Look for anything relating to shutdown.

Also here's one approach that worked for some:
Changing "/etc/default/grub" entry to:
GRUB_CMDLINE_LINUX_DEFAULT=

Go **[here]("http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer")** for instructions.

---

### Post by aiodjed on 2015-07-02
I added acpi=force to GRUB_CMDLINE_LINUX_DEFAULT
then i added it to GRUB_CMDLINE_LINUX instead
also removed "quiet splash" in the first line


now i get many messages when starting/shutting down. This is what it says when it shuts down;

[I]wait-for-state stop/waiting
enabling radios: wifi
applying power save settings...done
-stopping rsync daemon rsync
-speed-dispatcher
disabled: edit /etc/default/ speech dispatcher
asking all remaining processes to terminate
all processes ended within 1 seconds
nm-dispatcher.action
caught signal 15, shutting down
modemmanager (637) (info)
caught signal, shutting down
modem manager (637) (info)
modemmanager is shut down
-deactivating swap
-unmounting local fileystems
-will now halt[/I]

in auth.log i found: 
Jul  1 15:14:38 aiodjed sudo:    ztran : TTY=pts/0 ; PWD=/home/ztran ; USER=root ; COMMAND=/sbin/shutdown -P
Jul  1 15:14:38 aiodjed sudo: pam_unix(sudo:session): session opened for user root by ztran(uid=0)
Jul  1 15:14:38 aiodjed sudo: pam_unix(sudo:session): session closed for user root
Jul  1 15:14:48 aiodjed sudo:    ztran : TTY=pts/0 ; PWD=/home/ztran ; USER=root ; COMMAND=/sbin/shutdown -P 0

---

### Post by VMC on 2015-07-02
Did it shutdown, after the halt message?

I'm unsure what's going on here. It appears you have 'rsync --daemon' running for whatever reason.

Is this a standard Ubuntu version install. Was it ever upgraded. Maybe some hardware info will help; laptop,, desktop, etc.

edit:also can you copy and paste the "linux" line from grub so I can see any irregularities. Curious how this is booting up.

---

### Post by aiodjed on 2015-07-02
> Did it shutdown, after the halt message?
No

> Is this a standard Ubuntu version install. Was it ever upgraded. Maybe some hardware info will help; laptop,, desktop, etc.

Yes, standard ubuntu, no upgrades
Its a netbook, 1,5 ghz, 4 gb ram, 500 gb hdd
It had windows 8.1 installed but I'd rather learn to work with ubuntu. Do you think installing easy peasy or something like that instead would be a good idea?

GRUB_CMDLINE_LINUX_DEFAULT=
GRUB_CMDLINE_LINUX=


#GRUB_DISABLE_LINUX_UUID=true[h=1][/h]

---

### Post by VMC on 2015-07-02
I deon't know about 'easy peasy', but does it shutdown properly when booting from source; dvd, usb.
copy&paste the grub.cfg file from "/boot/grub", and put it between code tags. Also 'sudo blkid' from a ternimal(Ctrl+Alt+t). Just want to see what you have.
Does Windows boot up and shutdown correctly?

---

### Post by aiodjed on 2015-07-03
Hello
Thanks for your time but i just installed linux mint and it feels better
its a bit less complicated for a new linux user
i'll give you all the information next time i log into ubuntu

---

