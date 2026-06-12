---
title: "What do the numbers in the bracket in the shutdown sequence mean?"
date: 2015-01-04
forum: General Help
---

### Post by orange2k on 2015-01-04
I know its not that important, but since Ubuntu is an open system it would be nice to know what do the numbers in brackets in front of the "Shutting down" text after the shutdown sequence has been iniciated, mean?

Numbers seem to be random, but they must mean something, don't they?

---

### Post by ajgreeny on 2015-01-04
I don't know what numbers you are talking about.

Do you run Ubuntu with the default, or one of the other default DEs running, as when I shutdown I do not see any text or numbers, just a black screen that goes to the word Xubuntu with spinning circle on the blue background, the same as at startup.

---

### Post by orange2k on 2015-01-04
I'm running Ubuntu 14.04 64-bit and when I shut down the computer, after the screen goes blank, some messages appear on the screen, such as "terminating all processes" and similair, and at the and it says for example [4996 - System shut down] (if I remember correctly) and after that the computer shuts down.

I don't get that nice logo of Ubuntu upon booting, but instead I get the text "Ubuntu" and four white dots, and upon shutdown I get all these messages about shutting down the system, with the above mentioned numbers in front of the text "Shutting down"...

Its not a big deal, I admit, but it would be nice to know what it really means, if it has any meaning at all...

---

### Post by Dennis N on 2015-01-04
In system output like:

**[ 3649.070101] sd 6:0:0:0: [sdc] Attached SCSI removable disk**

I believe the number in brackets is a time measure since boot up.

---

### Post by oldfred on 2015-01-04
I do not normally see any shut down activity with Ubuntu. I have seen it with some other live systems.

Is it just like the start up if you remove quiet splash? That is [timestamp] at the beginning of every entry. You can see start up in /var/log/dmesg with log file viewer or any editor, but I am not sure where shut down is.

---

### Post by Dennis N on 2015-01-04
> I don't get that nice logo of Ubuntu upon booting, but instead I get the text "Ubuntu" and four white dots

This is the ubuntu-text plymouth theme which is a fallback used when the normal ubuntu-logo theme cannot.

---

### Post by oldos2er on 2015-01-04
> **orange2k said:**
> I know its not that important, but since Ubuntu is an open system it would be nice to know what do the numbers in brackets in front of the "Shutting down" text after the shutdown sequence has been iniciated, mean?

Numbers seem to be random, but they must mean something, don't they?

Those numbers are a timestamp, see [https://blog.sleeplessbeastie.eu/2013/10/31/how-to-deal-with-dmesg-timestamps/](https://blog.sleeplessbeastie.eu/2013/10/31/how-to-deal-with-dmesg-timestamps/)

---

