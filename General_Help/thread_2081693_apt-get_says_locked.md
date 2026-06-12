---
title: "apt-get says locked"
date: 2012-11-07
forum: General Help
---

### Post by critanime on 2012-11-07
Hi guys.

When I try to use apt-get I am receiving this error.

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Which is rather annoying as I like to install things via terminal, it's something I have done for a while. I am using sudo for this and giving it my correct password. 

Just to be on the safe side I tried this.

sudo killall -9 apt-get 
sudo rm /var/lib/dpkg/lock

It reports when I try to do killall that no apt-get processes are running. So I am pretty confused as to whats happening. 

To shed more light on this I will add the following. 
This is a new install of Ubuntu 12.04 LTS that is fully updated.
The system is a AMD FX-6100 with 8gb RAM

---

### Post by quickk on 2012-11-07
I had something like this happen once, even though I didn't have any other package manager running at the same time.   I had to completely close the terminal window and then start a new one.   

Thinking about it a bit more, I'm not sure if this made a difference, but the terminal application that I was using was yakuake.

---

### Post by critanime on 2012-11-07
Hmm. I am using just the standard terminal. However for some bizarre reason it's started working again. :-k

I have no idea what happened.

---

### Post by Rex Bouwense on 2012-11-07
There was another update process open at the same time.  It has happened to me.  I finally noticed that the automatic UPdate Manager was checking for updates at the same time I was trying to use apt-get.  No big deal.  It worked again as soon as the Update Manager was finished and closed itself.

---

