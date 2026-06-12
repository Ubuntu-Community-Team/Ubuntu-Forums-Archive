---
title: "ubuntu 18.04 LTS frezzes"
date: 2019-07-09
forum: General Help
---

### Post by christopher-santos18 on 2019-07-09
hi ppl im new here and im new on linux o just come from windows, i have install ubuntu 18.04 LTS and before i comes here i try to search the solution on google and i did not find, the ubuntu frezzes all the time im sorry to to my bad english, when it appens i need to restar the pc on the button becouse the mouse works but i cant select restart or turn off the computer.

Can some one help me please ? thanks very much

---

### Post by Impavidus on 2019-07-09
When the computer freezes, try to reboot using the [magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key). That will produce less collateral damage than a hard shutdown.

Random freezes are hard to diagnose. Try searching the log files for anything special happening in the seconds leading up to the freeze. You can find them in /var/log.

---

### Post by christopher-santos18 on 2019-07-09
> **Impavidus said:**
> When the computer freezes, try to reboot using the [magic SysRq key]("https://en.wikipedia.org/wiki/Magic_SysRq_key"). That will produce less collateral damage than a hard shutdown.

Random freezes are hard to diagnose. Try searching the log files for anything special happening in the seconds leading up to the freeze. You can find them in /var/log.

ok thaks and 
[COLOR=#000000]/var/log its a floder whats the file i need to open to tell you the errors please ?[/COLOR]

---

### Post by The Cog on 2019-07-09
/var/log/syslog is probably the one you want to start with, but there may be others. You can ignore all the *.gz files - they are compressed copies of old messages.

---

### Post by christopher-santos18 on 2019-07-09
> **christopher-santos18 said:**
> ok thaks and 
[COLOR=#000000]/var/log its a floder whats the file i need to open to tell you the errors please ?[/COLOR]

maybe this ?

ERROR: apport (pid 23768) Mon Jul 8 01:02:40 2019: called for pid 4181, signal 5, core limit 0, dump mode 1
ERROR: apport (pid 23768) Mon Jul 8 01:02:40 2019: executable: /opt/google/chrome/chrome (command line "/opt/google/chrome/chrome")
ERROR: apport (pid 23768) Mon Jul 8 01:02:40 2019: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 23768) Mon Jul 8 01:02:40 2019: apport: report /var/crash/_opt_google_chrome_chrome.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS
ERROR: apport (pid 29295) Mon Jul 8 21:51:36 2019: called for pid 4646, signal 5, core limit 0, dump mode 1
ERROR: apport (pid 29295) Mon Jul 8 21:51:36 2019: executable: /opt/google/chrome/chrome (command line "/opt/google/chrome/chrome")
ERROR: apport (pid 29295) Mon Jul 8 21:51:36 2019: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 29295) Mon Jul 8 21:51:36 2019: apport: report /var/crash/_opt_google_chrome_chrome.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS

---

### Post by christopher-santos18 on 2019-07-09
i have all this files.

alternatives.log  bootstrap.log    journal            syslog.5.gz
apport.log        btmp             kern.log           syslog.6.gz
apport.log.1      cups             kern.log.1         syslog.7.gz
apport.log.2.gz   dist-upgrade     lastlog            tallylog
apport.log.3.gz   dpkg.log         nordvpn            teamviewer14
apport.log.4.gz   faillog          speech-dispatcher  ufw.log
apport.log.5.gz   fontconfig.log   syslog             ufw.log.1
apt               gdm3             syslog.1           unattended-upgrades
aptitude          gpu-manager.log  syslog.2.gz        wtmp
auth.log          hp               syslog.3.gz        Xorg.0.log
auth.log.1        installer        syslog.4.gz        Xorg.1.log

---

### Post by christopher-santos18 on 2019-07-09
i have find annother error its to long i have put on a link.
[https://justpaste.it/2pjw1](https://justpaste.it/2pjw1)

can you hep please ?
and the magic keys do not work.

---

### Post by Impavidus on 2019-07-10
Your best chances are in syslog or kern.log, maybe Xorg. The log files with the .1 suffix are older version, the same for .2, .3 etc. They are even older and have been compressed (see the .gz suffix). Look for any clue in the seconds before the freeze.

SysRq combinations may not be fully enabled, but should leave traces in the logs. Some laptops require peculiar key combinations. I have to hit fn+alt+delete, then release fn and hit the right letter.

---

### Post by christopher-santos18 on 2019-07-10
> **Impavidus said:**
> Your best chances are in syslog or kern.log, maybe Xorg. The log files with the .1 suffix are older version, the same for .2, .3 etc. They are even older and have been compressed (see the .gz suffix). Look for any clue in the seconds before the freeze.

SysRq combinations may not be fully enabled, but should leave traces in the logs. Some laptops require peculiar key combinations. I have to hit fn+alt+delete, then release fn and hit the right letter.

Hi then this is a desktop not a laptop, and the file kern.log and syslog are clean don't have any information and the gz you tell me about I open to with gedit command ? I'm new here I come from windows because of problems and craches.

Thanks

---

### Post by Impavidus on 2019-07-10
I use zcat to read older logs, which is just like cat, but with compressed files. You can use any tool that deals with archive formats. They all know how to unpack .gz, then view it in your favourite text editor.

If you also had a lot of crashes in Windows, consider the possibility that you have a hardware problem. [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

---

### Post by christopher-santos18 on 2019-07-10
no the windows is to slow, and has alot of errors.
the memory teste is ok.
and i try to install zcat and it give this error:

apt install zcat
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
E: Não foi possível encontrar o pacote zcat
root@ukinami-EL1352:/home/ukinami# apt-get install zcat
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
E: Não foi possível encontrar o pacote zcat

---

### Post by christopher-santos18 on 2019-07-10
> **Impavidus said:**
> I use zcat to read older logs, which is just like cat, but with compressed files. You can use any tool that deals with archive formats. They all know how to unpack .gz, then view it in your favourite text editor.

If you also had a lot of crashes in Windows, consider the possibility that you have a hardware problem. [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)


helloi have made the memteste and the message is PASS COMPLETE NO ERRORS and when i press esc to exite the teste stop and freezze heheheeh sutdown button. if the memory has no erros why it frezzes processor ?

---

### Post by Impavidus on 2019-07-11
zcat is part of the gzip package, which should already be installed. But I don't think it will be of any use here, unless you remember the exact time when a freeze happened weeks ago.

Can you give some more details about your hardware? CPU, memory, graphics, motherboard. There are some people here who are familiar with the special treatment some pieces of hardware need, or it may simply be to weak to run Ubuntu (in which case, a lighter flavour might do).

---

### Post by christopher-santos18 on 2019-07-11
i have tested mx linux on a usb and it not frezzes and has no problem, its not this ubuntu who has the problem ?

its a AMD ATHON II X2 215 PROCESSOR
3GB DDR3

AND THE GRAPHICS ITS A NVIDIAGEFORCE 6150SE NFORCE 430

---

### Post by christopher-santos18 on 2019-07-12
do you think is better to install the mx linux ?

---

### Post by christopher-santos18 on 2019-07-15
i dont like it i will teste lubuntu

---

### Post by christopher-santos18 on 2019-07-15
ok i have installed lubuntu to see if frezzes but i have close the panel bar now i cant acess do chrone or terminal or shutdown the computer can some one help me please ?

---

### Post by Impavidus on 2019-07-15
I don't know about Lubuntu. If this is a new issue, better use a new thread. This one gets its 18th post now, so not many people will be reading.

If you're still dealing with your first issue, have you checked the additional drivers utility? It may have a different graphics driver available. It might help. But I've got no experience with nvidia graphics.

At 3GB memory Ubuntu should work, but the lighter flavours are better.

---

### Post by christopher-santos18 on 2019-07-19
im back to ubuntu the problem is back but im new here i come from windows do linux and i dont whant to go back becouse before frezzes it works coll buti dont know what can i do .

---

### Post by dragonfly41 on 2019-07-19
> [COLOR=#000000]AND THE GRAPHICS ITS A NVIDIAGEFORCE 6150SE NFORCE 430

[/COLOR]
Searching I found this which refers to your graphics .

[https://ubuntuforums.org/showthread.php?t=2294964](https://ubuntuforums.org/showthread.php?t=2294964)

---

