---
title: "Why disconnected HDD still appear on network ?"
date: 2017-12-10
forum: General Help
---

### Post by ButchMel on 2017-12-10
Using Ubuntu 12.x on Linux server. Have a HDD that failed - I was no longer able to access it from other computers on the network. Could not even see it when connecting to the Ubuntu server. 

I disconnected the HDD, took it to several computers, in Windows, in OSX and none of the disk utilities could even detect it. Dead. Noise. I could do nothing but scrap it. Gone. 

Now, can someone explain me why I suddenly connect to the server and magically see the 2 drives names that HDD had now reappearing - and even more strangely: I can even write stuff (copy documents) to it ???....(Of course: no luck I could also see all the stuff I have lost...) Is there any kind of ''virtual'' replication of the system that would explain that ? - Really, the HDD is physically no longer there, the cable (Firewire) has been disconnected...

Oh and must tell that I had unmounted the drive on the Ubutu machine before disconnecting it.

Thanks,

---

### Post by Holger_Gehrke on 2017-12-11
Really simple. You originally mounted that drive into some directory and shared that directory on the network. The drive is gone but the (probably empty) directory still exists and you haven't stopped sharing it.

Holger

---

### Post by Impavidus on 2017-12-11
Unrelated, but are you aware that 12.04 LTS reached end of support earlier this year?

---

