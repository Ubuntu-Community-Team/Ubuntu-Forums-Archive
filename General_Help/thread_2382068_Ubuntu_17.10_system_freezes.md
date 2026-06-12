---
title: "Ubuntu 17.10 system freezes"
date: 2018-01-08
forum: General Help
---

### Post by abe-stew on 2018-01-08
Since installing Ubuntu 17.10 I have been experiencing irregular system freezing where everything becomes unresponsive requiring a hard reboot. Originally this was fairly frequent. However, switching to xorg from Wayland fixed that. Since then the freezes have been a lot more rare but with two main culprits (though not limited to them). The first has been Firefox - which works absolutely fine 99% of the time but will rarely cause a freeze on launching a new tab / opening a link in a new tab.
The other culprit is Wine where a freeze will occur sometimes after using CrossOver to run Word 2016. I noticed today after launching it that systemd-journald was burning 100% of a CPU core. Checking journalctl provided tens of thousands (at least) lines of:

Jan 08 18:58:01 Insomniac gnome-software[2774]: g_byte_array_remove_range: assertion 'index_ + length <= array->len' failed
Jan 08 18:58:01 Insomniac gnome-software[2774]: Ignoring unexpected response

In total my syslog was at 13.6GB with another archived syslog around 10GB. Other CrossOver bottles, such as Steam, cause no problems. Anyone able to help explain this error to a noob and how I might go about trying to fix it?

---

### Post by dino99 on 2018-01-08
the first thing you might check is: journalctl for possible error (journalctl -b)
then be sure you have set a swap partition or file: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

a so huge syslog (which no one should met) will teach you what is abnormal (via journalctl -b)

---

### Post by cariboo on 2018-01-08
Moved

---

### Post by lorebett on 2018-01-22
It could be related to this [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1723362](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1723362)

---

### Post by abe-stew on 2018-01-29
Thanks for the replies, and massive apologies for the lengthy delay in replying. Fortunately there has been no recurrence of the issue during the last couple of weeks. I think lorebett may be on right track that issue is related to a known gnome software bug. Running Office 2016 via CrossOver results in the night light to crash - requiring turning the setting off and on again to resume. The same issue may be resulting in the bug where gnome software then endlessly spams journald.

---

