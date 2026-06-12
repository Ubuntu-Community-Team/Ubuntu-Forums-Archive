---
title: "Nessus and Open Ports?"
date: 2007-02-13
forum: General Help
---

### Post by Maximos on 2007-02-13
Hi there.  I'm new to Ubuntu (and loving it so far), with novice level (but not complete beginner) familiarity with Linux, and have a question I'm hoping to be able to get answered.

I tend to be somewhat paranoid about the security of my system, so I'm checking for rootkits, viruses, open ports, etc., fairly regularly.  Recently, I installed nessus (and related packages) on my system to facilitate this.  Some time after installing nessus (anywhere from a few hours to a day or so later), I scanned my ports with nmap and discovered that, according to nmap, port 1241 was now open and listening.  This was a surprise, because prior to this I regularly ran nmap and verified that ALL ports were closed.  To doublecheck these new results, therefore, I went to [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) (the Shields UP website) and tested my computer with their port scanner.  The results declared that my system was completely "stealth."  I then specified port 1241 specifically and ran their scanner again; it told me that the port was indeed "stealth," but identified that "nessus" was the application running on the port (I'm not sure how they identified this if my port is truly stealth, but that might be my own confusion; maybe someone could fill me in here? [EDIT: I think I've answered this question myself.  It appears that port 1241 is just commonly recognized as a nessus port.]).  I ran nmap once again, and it told me that the port was still open, so seeing that nessus was the program running on that port, I promptly removed nessus and came here to ask this question.  

My question is, is it normal to have this port respond as open to nmap after installing nessus?  This computer is connected to the internet at all times, so should I be concerned?  Was the port at all open to intruders, and is there reason for me to worry, or is this port only somehow "open" from my perspective (so that I can run nessus) while remaining "stealth" to the outside world?  

I should say that, due to my paranoia, I ran my rootkit hunters and clamav on my system, and everything came out OK.  Also, I verified with nmap that, after removing nessus, all ports were closed.  So, again, is this something I should be worried about, or not?

Thanks much for your help!

---

