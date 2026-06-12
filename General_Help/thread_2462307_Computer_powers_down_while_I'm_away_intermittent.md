---
title: "Computer powers down while I'm away: intermittent"
date: 2021-05-18
forum: General Help
---

### Post by Paddy Landau on 2021-05-18
My computer is set to suspend after I've been away for an hour.
[ATTACH=CONFIG]288498[/ATTACH]
Usually, that's exactly what happens. The computer suspends. When I return to the computer, I press Enter, the computer wakes up, and I log in to continue from where I left off.

Sometimes, maybe three or four times a week, instead the computer seems to power off suddenly, leaving the disk unclosed. I can see that because not only does the computer have to start from cold, but also after entering my LUKS passphrase, the automatic disk check reports errors that it automatically fixes.

I have absolutely no clue how to diagnose this problem. Is it hardware? Is it software? Might I see something in the logs, and if so, where are the logs?

Do you have some ideas for me to diagnose this so that I can find out where the problem lies, please?

[LIST]
[*]The computer is a Dell OptiPlex 5480 All In One, which came with Ubuntu 18.04 pre-installed.
[*]I overwrote the installation with a full-disk installation of Ubuntu 20.04.
[*]I used the default installer, with the full-disk option with LUKS+LVM encryption.
[/LIST]
Thank you

---

### Post by Autodave on 2021-05-18
Could always be hardware.  My first guess would be RAM.  Run a RAM test.  Also, do you have powered USB devices other than keyboard and mouse attached?  If so, disconnect them and see what happens.  

I had a powered USB hub here.  Works fine.  Started having problems booting: my boot times went from 13 seconds to over a minute.  Once booted, USB hub worked fine.  Would go onto the internet and some videos wouldn't play at all and some played very slowly.  All the while, anything plugged into the powered hub worked fine.  Diagnosing began with unplugging everything from the hub.  Still had same problem.  Unplugged hub, everything was good.  Took everything that used to be in the hub and plugged into different USB ports all at the same time: computer ran fine.  Plugged empty hub in again and everything went bad.  Now I have a $70 US phone charger.  Sigh.

---

### Post by TheFu on 2021-05-18
/var/log/

---

### Post by Paddy Landau on 2021-05-18
Thanks for your reply, @Autodave.
> **Autodave said:**
> My first guess would be RAM.  Run a RAM test.
I ran a BIOS check against the system, including a RAM test, and everything came up clean.
> **Autodave said:**
> … do you have powered USB devices…
No. The keyboard and mouse are wireless, attached via a USB dongle, but that dongle isn't self-powered. I don't have a USB hub, although I presume that the computer contains some sort of a hub to share out the USB ports.

Everything else works well; I have no problems with internet, computer speed, etc., even when running Windows in a VM.
> **Autodave said:**
> Now I have a $70 US phone charger.
That sounds irritating! Does your hub match your computer's USB version? I know that USBs are all supposed to be backward compatible, but would that apply to a powered hub?

---

### Post by Paddy Landau on 2021-05-18
> **TheFu said:**
> /var/log/
What specifically do I need to look for? There's a lot of stuff in that folder!

---

### Post by Autodave on 2021-05-18
The hub worked just fine for the first 9 months: no problem at all.  Nothing changed on the PC.  It was a 3.0 powered hub plugged into a 3.0 port.  It was quite fast and actually still is, but it slows everything else way down even if nothing is plugged into it.

---

### Post by TheFu on 2021-05-18
> **Paddy Landau said:**
> What specifically do I need to look for? There's a lot of stuff in that folder!

I'd look for *errors* and *warnings* in all the files.  Use **grep**.  Also, check all the subdirectory files.
Basic log stuff.  [https://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](https://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

---

### Post by dragonfly41 on 2021-05-18
> var/log/
What specifically do I need to look for? There's a lot of stuff in that folder!

Suggestion. Install glogg and you can filter logfile(s) by under Text: using keyword/phrases
such as WARNING, error .. or whatever.

---

