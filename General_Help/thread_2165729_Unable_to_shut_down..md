---
title: "Unable to shut down."
date: 2013-08-06
forum: General Help
---

### Post by twsLeGR on 2013-08-06
I am really happy running Ubuntu 13.04 but unfortunately i am unable to shut down my laptop at night? When i go to the gear wheel icon in the top right-hand corner and select shut down it does exactly that but within a few seconds starts to reboot? I was fortunate in that i had Puppy Linux Slacko installed on a USB stick and now in order to shut down my laptop at night i must reboot the machine into Puppy Linux Slacko just to shut down.

I know very little about computers or operating systems but there must (in my opinion) be something wrong with Ubuntu 13.04 for this to happen?

Despite the problem with shutting down the machine at night i'm will continue to use Ubuntu 13.04 because i think it is still the best OS around!

---

### Post by davetv on 2013-08-06
To shutdown, in a terminal, you could try

sudo shutdown -h 0 

Easier than rebooting and shutting down again.

---

### Post by twsLeGR on 2013-08-06
Hiya davetv

Have tried that and failed mate.
Thanks for the reply though.

---

### Post by bapoumba on 2013-08-06
What was your error message ?
I might not be able to help you with this, but others will. Without any info on the error, no one will :)

Edit: changed your thread title.

---

### Post by matt_symes on 2013-08-06
Hi 

What are the specs for your hardware ?

Kind regards

---

### Post by Mikog on 2013-08-06
try the following command:

sudo init 0

Kind regards

---

### Post by twsLeGR on 2013-08-06
Sorry that i've taken so long to reply but here i am at last.

Right i have tried closing down the netbook with both _sudo shutdown -h 0_ and _sudo init 0_ and neither of the commands worked and no error was shown either.

The machine's specs are as follows:

Acer Aspire Netbook V5-571 series.
Memory: 8GiB
Disk: 500GiB
Processor: intel Core i3-2367M CPU @ 1.40GHz x 4
Graphics: intel Sandybridge Mobile x86/MMX/SSE2

Hope that helps?

---

### Post by Mikog on 2013-08-08
Could you do this in command prompt.

sudo tail -f /var/log/syslog

after you have run this command try typing the commands that we supplied in a second shell?

Once you have done this post the output here please.

---

### Post by twsLeGR on 2013-08-08
Hi Mikog 

I have ran the sudo tail -f /ar/log/syslog and its output was:
twsLeGR@ubuntu-13:~$ sudo tail -f /var/log/syslog
Aug  8 11:26:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:28:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:30:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:32:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:34:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:44:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:46:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:48:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:50:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:52:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 11:58:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:00:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:02:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:04:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:06:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:08:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:10:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:12:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:14:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:16:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:17:01 ubuntu-13 CRON[6357]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  8 12:20:45 ubuntu-13 wpa_supplicant[1188]: wlan0: WPA: Group rekeying completed with 00:1e:2a:13:a5:92 [GTK=TKIP]
Aug  8 12:20:45 ubuntu-13 wpa_supplicant[1188]: wlan0: WPA: Group rekeying completed with 00:1e:2a:13:a5:92 [GTK=TKIP]
Aug  8 12:22:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:24:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:26:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Aug  8 12:28:08 ubuntu-13 NetworkManager[1029]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted

And its still going?

---

### Post by matt_symes on 2013-08-08
Hi

Try installing the laptop-mode-tools

```
sudo apt-get install laptop-mode-tools
```

They may help.

Kind regards

---

### Post by Mikog on 2013-08-09
It seems that network manager has issues working properly with your network card.
Can you provide what type of network card you have in your Acer?

Does your network cards work properly? Wired/ wireless?

Try installing the tools noted above.

If it still remains a dirty solution would be trying another network manager.
See url:

[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

