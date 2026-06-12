---
title: "CPU Overloads when running a process"
date: 2016-03-10
forum: General Help
---

### Post by jantaro2 on 2016-03-10
Hi, I m having a little issue when running bitcoind. I downloaded sourcecode from github and both bitcoind and bitcoin-qt were compiled by myself. with ./configure, make and so on. following a tutorial. 

i just run bitcoind -daemon to download blocks 

The thing is that after the first hour of block downloading, my 4 CPU begin to work at rates over 95 % and RAM reaches 44% ( I got 8GB )., then when I try to check out with bitcoin-cli getinfo, it does not answers back the query as usual, and the command line just blinks. So, I Kill bitcoind, and the bitcoin-cli comes back, of course saying there´s no response from server. If I restart the process ( without restarting computer ). well the overload happens again after few minutes. I don´t feel like safe leaving blockchain downloading if this strange overloads are happening to me. 

Antivirus scan already done;avclam, rkhunter and chrootkit  nothing found apart from some false positives reported as well on forums.

Is there something I should configure?. 

Is there any way of setting a limit of CPU usage for this process?. 

what could be wrong or what should I check, it is just that I don´t know what to do.

I m under risk of machine physical damage, leaving the computer working at these rates?.


I would appreciate a lot any kind of help, so thanks in advance to those who could say something back. Kind regards.

---

### Post by TheFu on 2016-03-10
I know ZERO about running bitcoin harvesting anywhere - especially now that it takes a month of work to get 1 BC and the specialized hardware guys are the only people making it even slightly profitable.  OTOH, I can understand the interest in mining, even just for fun.  A few friends have the 5 yr old USB ASIC devices mining - though I think they aren't even getting 1 BC per month with them anymore.

What do the log files show?  Sometimes a GUI freeze is just the GUI and has nothing to do with the rest of the system.  Try to ssh in from another machine to check the log files.

"Overloaded" is vague. Please explain and use concrete examples from the system. Log files are a good place to start.

Is it overheating?  If so, get better cooling for the CPU, drives, case, chipsets, GPU, or anything else that is "hot" inside.  Mining BCs is hard work. It stresses a CPU. This is by design.  The effort required to find new BCs is constantly getting harder. This is part of the design, so more work will be required to get fewer and fewer coins.
[https://bitcoin.stackexchange.com/questions/1876/what-hashing-speed-does-my-hardware-have](https://bitcoin.stackexchange.com/questions/1876/what-hashing-speed-does-my-hardware-have) - says that mining using a regular CPU was a waste of time - back in 2011.

---

### Post by jantaro2 on 2016-03-11
bitcoind and bitcoin-qt is a wallet, a full node what I m running. I m not mining. Neither do I got interest on mining because of all these things you explain. it is just the blockchain download and verification what is causing this, from Bitcointalk I m learning that these overloads could be normal and no reason to worry about. " The initial download and verification puts a lot of strain on your CPU,  disk and bandwith. The 4 GB memory usage might just be cached data ". Thanks a lot for answers!.

---

