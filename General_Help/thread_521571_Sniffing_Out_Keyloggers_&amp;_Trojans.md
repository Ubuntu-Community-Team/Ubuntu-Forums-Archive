---
title: "Sniffing Out Keyloggers &amp; Trojans"
date: 2007-08-09
forum: General Help
---

### Post by Troubled on 2007-08-09
[SIZE="3"]I'm probably paranoid, but I want to know if any of the unsavory types that I have unfortunately been communicating with recently through IRC and telnet have possibly compromised my system with  keyloggers, trojans, rootkits, or other undesirables.
I'd like to be able to do things like put pictures and documents with personal information (ie, name, address, phone number) onto my computer without fear and constantly worrying about what someone might be able to do with that sort of data.
I have run AVG and chkrootkit, but I don't really trust their output.

Could someone provide an overview on what the risks are in running IRC and telnet and how to reclaim an Ubuntu system from the clutches of a trojan?

Thanks!!

--John
[/SIZE]

---

### Post by apetresc on 2007-08-09
There's probably nothing to fear, but if it makes you feel safer, you can ```
sudo apt-get install chkrootkit
``` to get a program for checking for rootkits (just run "sudo chkrootkit" to run it), and ```
sudo apt-get install clamav
``` for an antivirus solution (look up the many ClamAV tutorials floating around the net for instructions to run it)

---

### Post by Troubled on 2007-08-09
[SIZE="3"]As noted previously, I've just run chkrootkit, which failed to locate anything, which I feel gives conclusive evidence as to the suspected snoopers' nefarious intent. I've also installed clamav previously, but got rid of it when I realized that it hadn't been updated in years.

Are there any other solutions that'll definitely get rid of those pesky keyloggers?
I'm actually looking to find something that'll locate files on my computer and send it over the net to a remote system, is there anything that can show me whether that is happening or not?

Thanks! Sorry if I'm being too much of a bother. :p[/SIZE]

---

### Post by euler_fan on 2007-08-09
Get the Backtrack and/or Knoppix live CD's and run the scans on your machine using the versions of chkrootkit, rkhunter, and ClamAV from the liveCD. You can also install while running live, but not much or you'll eat all your RAM. You should have enough room to get updated definition files if nothing else.

Good luck.

---

### Post by apetresc on 2007-08-09
Ah, sure. You can use 'ntop' (from the universe repository). It works just like 'top' except for network traffic, so if any files are being sent across you'll see them there.

> I've just run chkrootkit, which failed to locate anything, which I feel gives conclusive evidence as to the suspected snoopers' nefarious intent. That cracked me up :lolflag:

>  I've also installed clamav previously, but got rid of it when I realized that it hadn't been updated in years. I'm not sure what you mean... ClamAV is updated often enough, and the virus definitions are updated almost daily. [http://www.clamav.net/](http://www.clamav.net/) if you don't believe me.

Anyway, ntop is probably what you want :) Good luck!

---

### Post by Troubled on 2007-08-09
[SIZE="3"]Ok, I've installed both utilites (ntop and clamav) with only moderate crashing.
Strange, really: my computer froze up for a while, after which I got suspicious and unplugged my Ethernet cable, after which everything started working again. I really need anti-spyware. Or pills.

But I'm having troubled with actually using them; apparently ntop is designed for monitoring server traffic? The screenshots of the browser-based interface look nice, but I don't seem to be able to get there. Could you please explain which arguments I need to run ntop and clamav?[/SIZE]

---

### Post by apetresc on 2007-08-09
There are good HOWTO's for both of these.

For ClamAV: [http://doc.gwos.org/index.php/How_to_ClamAV](http://doc.gwos.org/index.php/How_to_ClamAV)
For ntop: [http://ubuntuforums.org/showthread.php?p=1232294](http://ubuntuforums.org/showthread.php?p=1232294)

---

