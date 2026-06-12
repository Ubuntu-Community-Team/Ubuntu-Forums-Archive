---
title: "Cyber Cafe on Ubuntu"
date: 2008-07-01
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-07-01
Hi
I am running an internet cafe called zygo using ubuntu but I cant seem to find any really good software for managing the system... I have tried cafe con leche (not enough options), outkafe (cant get database to connect), CafePilot (no documentation), Cyborg (not correct interface)...

Can anyone point me to some good software or suggest anything?

---

### Post by erwall on 2008-07-01
Have you looked on sourceforge?  There's a ton on there; icafe, icsoft, cybera, playbilling, dharma, faraon, controltech, etc

---

### Post by 4t0m1c_w07f on 2008-07-01
Thanks mate... Got a few programs to try... ):P

---

### Post by daoud7 on 2008-10-13
> **4t0m1c_w07f said:**
> Thanks mate... Got a few programs to try... ):P
Hi,

I guess I'm having the same problem that you are/were.

I also am stopped by the postgresql database failure to work as per "book".

Did you solve the problem?

Please let me benefit from your experience. I am really unhappy with the present situation.  :-(

What software did you finally end up with?  Any observations which you can provide will be much appreciated!

Thx for your time!

---

### Post by daoud7 on 2008-10-13
> **4t0m1c_w07f said:**
> Thanks mate... Got a few programs to try... ):P
Hi,

I guess I'm having the same problem that you are/were.

I also am stopped by the postgresql database failure to work as per "book".

Did you solve the problem?

Please let me benefit from your experience. I am really unhappy with the present situation.  :-(

What software did you finally end up with?  Any observations which you can provide will be much appreciated!

Thx for your time!

---

### Post by sabitha on 2008-10-15
maybe you can try [Gbilling]("http://gbilling.sourceforge.net/")
Gbilling support for DualOS (windows & Linux)
this on indonesian language and this beta. but you can try because there is .deb version for ubuntu.
you can view screenshot on their [site]("http://gbilling.sourceforge.net/screenshot.html")

---

### Post by 4t0m1c_w07f on 2008-10-26
> **daoud7 said:**
> Hi,

I guess I'm having the same problem that you are/were.

I also am stopped by the postgresql database failure to work as per "book".

Did you solve the problem?

Please let me benefit from your experience. I am really unhappy with the present situation.  :-(

What software did you finally end up with?  Any observations which you can provide will be much appreciated!

Thx for your time!

I have tried almost every program I can get my hands on and for my purpose, outkafe was the perfect option... But with many linux programs, you do unfortunately run into some errors.. My problem was that the client, daemon and server weren't seeing eachother and could not connect...

So now we are left using the old zybacafe, which does not connect to the pcs and is only used to manage the customer database with their times and logging in and  out...

Many of the programs that I tried are good but don't have everything I need therefore not appropriate...

I will try gbilling but I really hope that it's in english...

---

### Post by daoud7 on 2008-10-31
That direction (ZybaCafe) does not much appeal. I really need to be able to shutdown machines from the server (even if I can't do a ticket system).

The one that comes closest seems to be CCL (Cafe con Leche). The headache with this one for the moment is that I can't get the client program to run - it does not see 2 critical files.

Anyhow I am still trying to break through that hurdle...

Any help from anywhere would be appreciated!

---

### Post by 4t0m1c_w07f on 2008-11-07
> **daoud7 said:**
> That direction (ZybaCafe) does not much appeal. I really need to be able to shutdown machines from the server (even if I can't do a ticket system).

The one that comes closest seems to be CCL (Cafe con Leche). The headache with this one for the moment is that I can't get the client program to run - it does not see 2 critical files.

Anyhow I am still trying to break through that hurdle...

Any help from anywhere would be appreciated!

You can remotly shutdown machines by writing a short shell script...

---

### Post by daoud7 on 2008-11-08
> **4t0m1c_w07f said:**
> You can remotly shutdown machines by writing a short shell script...

I understand the principles involved with this, but have never done it.

I wonder how short it would have to be since I need to be able to allow a random worker to close/ reboot any of, say 15 machines.

To say the least, I don't have much confidence in this solution.  :-(

---

### Post by 4t0m1c_w07f on 2008-11-09
> **daoud7 said:**
> I understand the principles involved with this, but have never done it.

I wonder how short it would have to be since I need to be able to allow a random worker to close/ reboot any of, say 15 machines.

To say the least, I don't have much confidence in this solution.  :-(

Maybe you should try find out from the ccl source how exactly it does that...

---

### Post by Script Warlock on 2008-11-20
try this thread  [http://ph.ubuntuforums.com/showthread.php?t=777093](http://ph.ubuntuforums.com/showthread.php?t=777093)

---

### Post by BatsotO on 2008-12-15
cclfox can kill remote machine but it will need the client sbin/shutdown executeable by everyone. I do chmod 7755 /sbin/shutdown (and reboot).

---

