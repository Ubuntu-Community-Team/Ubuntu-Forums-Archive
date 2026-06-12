---
title: "Hard-disk error detected during restart"
date: 2013-02-23
forum: General Help
---

### Post by titagula on 2013-02-23
Whenever my system restarts, a black screen with white letters tells me that there is a problem detected with hard drive, and to press enter to continue. 
This occured after I swapped the measly 20g harddrive for a slighty less measly-but-still-small 60g hardrive. At the time, I was running ubuntu 10.04, and during typical computer use, a warning would pop up that said for me to "back up files immedietely, disk failure is imminent!" but it was fine for months without any problems, save the error messages themselves.

Now that I am running 12.1, and occasionally a box pops up that says "System error detected", and the previously described start-up situation occurs whenever restarting. I wondered if there was anything I could do about this, because this minor annoyance started as a sort of "At least I didn't completely destroy my system" thing, but now it's a huge "first-world problem".

---

### Post by drdos2006 on 2013-02-23
Hi there
I have had the same error pop up when I installed 12.04. To overcome this glitch, I reinstalled and ran "sudo apt-get update && sudo apt-get upgrade". I feel there may have been a glitch on my DVD drive or my hard drive at the time. The HDDs were fairly old.
Can you re-install ? This might solve the problem.

regards

---

### Post by prodigy_ on 2013-02-23
Open terminal and run the following commands:
```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

If you don't know how to interpret SMART data, post the output of smartctl here.

---

