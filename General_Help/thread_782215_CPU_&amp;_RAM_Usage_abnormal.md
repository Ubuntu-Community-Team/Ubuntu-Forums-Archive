---
title: "CPU &amp; RAM Usage abnormal?"
date: 2008-05-04
forum: General Help
---

### Post by kingsrider99 on 2008-05-04
Hi guys. I wanted some advice regarding Ubuntu 8.04 LTS Desktop Edition I just installed on my computer. The specifications of my computer are as follows:
Intel Celeron Pentium 4 Processor 2.40 GHz, 512 MB RAM 
A total of 80 GB HDDs (2 HDDs 40 GB Each), 1024 x 760 Resolution graphics card and Sound card and Onboard RealTek RTL8139 NIC
along with Soft V.92 Data Fax Modem.

My first hard disk contains Windows XP which is currently my default and the most commonly used operating system and recently, I installed Ubuntu 8.04 into my second hard drive just to experience and see what it offers. The OS is running fine and hasn’t given me a problem till now but the issue is that whenever check the System Monitor in one of the upper menus on the desktop, I see that the CPU usage is doing a 100% and RAM’s almost a 50% even though I haven’t executed or am running any applications. Is this an indication of a futuristic problem that might result in a disaster for my processor, my ram and/or my motherboard? Please assist.
Thanks.

---

### Post by overdrank on 2008-05-04
> **kingsrider99 said:**
> Hi guys. I wanted some advice regarding Ubuntu 8.04 LTS Desktop Edition I just installed on my computer. The specifications of my computer are as follows:
Intel Celeron Pentium 4 Processor 2.40 GHz, 512 MB RAM 
A total of 80 GB HDDs (2 HDDs 40 GB Each), 1024 x 760 Resolution graphics card and Sound card and Onboard RealTek RTL8139 NIC
along with Soft V.92 Data Fax Modem.

My first hard disk contains Windows XP which is currently my default and the most commonly used operating system and recently, I installed Ubuntu 8.04 into my second hard drive just to experience and see what it offers. The OS is running fine and hasn’t given me a problem till now but the issue is that whenever check the System Monitor in one of the upper menus on the desktop, I see that the CPU usage is doing a 100% and RAM’s almost a 50% even though I haven’t executed or am running any applications. Is this an indication of a futuristic problem that might result in a disaster for my processor, my ram and/or my motherboard? Please assist.
Thanks.

Hi and welcome, as for the memory being at 50% that would be about right if you are using compiz. On the system monitor what process is using your cpu?

---

### Post by kingsrider99 on 2008-05-05
Thanks for your reply. As per your request, I have specified a list of processes below that were show in the System Monitor. You can exclude gedit as I used that pad to write the list. I am sorry if the list is quite long as I am still new to Ubuntu and this is my first linux OS.

Thanks.

PROCESS                     STATUS    %CPU

Bluetooth Applet            Sleeping    0
Bonobo Activation Server    Sleeping	0
dbus-daemon                 Sleeping	0
evolution alarm notify      Sleeping	0
evolution-data-server-2.22  Sleeping	0
evolution-exchange-storage  Sleeping	0
fast user switch applet     Sleeping	0
gconfd-2                    Sleeping	0
gedit                       Sleeping	(0 - 18)
gnome-keyring-daemon        Sleeping	0
gnome panel                 Sleeping	0
gnome power manager         Sleeping	0
gnome screensaver           Sleeping	(0 - 2)
gnome-settings-daemon       Sleeping	0
gnome-system-monitor        Running	(8 - 32)
gnome-vfs-daemon            Sleeping 	0
gvfsd                       Sleeping	0
gvfsd-burn                  Sleeping	0
gvfsd-trash                 Sleeping	0
gvfs-fuse-daemon            Sleeping	0
metacity                    Sleeping	0
mixer_applet2               Sleeping	0
nautilus                    Sleeping	0
nm-applet                   Sleeping	0
pulseaudio                  Sleeping	0
python                      Sleeping	0
seahorse-agent              Sleeping	0
ssh-agent                   Sleeping	0
tracker-applet              Sleeping	0
trackerd                    Sleeping	0
trashapplet                 Sleeping	0
update-notifier             Sleeping	0
x-session-manager           Sleeping	0

---

