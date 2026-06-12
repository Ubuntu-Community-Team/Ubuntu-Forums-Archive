---
title: "Dual boot and thunderbird; mail folder sharing between win and ubuntu?"
date: 2007-08-09
forum: General Help
---

### Post by flexus on 2007-08-09
Hi! I am setting up a dual boot system with windows XP and Ubuntu feisty on my home computer. I will run Ubuntu for everyday use like checking mail and editing text documents. I do, howerever, want to be able to access my mails in windows aswell. 

I will be running thunderbird as email client on both windows and ubuntu. Is there a way to let them share mail folders? By this I mean that if I download a couple of mail logged into ubuntu, if I restart my computer I want to be able to open windows and thunderbird and access those mail. 

Thank you very much in advance. 

regards
Klas

---

### Post by PentaxFollower on 2007-08-09
There is a HOWTO:
[http://ubuntuforums.org/showthread.php?t=203524&highlight=thunderbird+shared]("http://ubuntuforums.org/showthread.php?t=203524&highlight=thunderbird+shared")

I hope it would help you.

---

### Post by callan79 on 2007-08-09
> **flexus said:**
> I will be running thunderbird as email client on both windows and ubuntu. Is there a way to let them share mail folders? By this I mean that if I download a couple of mail logged into ubuntu, if I restart my computer I want to be able to open windows and thunderbird and access those mail. 

I actually just did this for my partner on the weekend, and it works great!

1. Install Thunderbird on both

2. Create a THUNDERBIRD folder somewhere that is accessible to both the Windows and Ubuntu systems (I created mine on a shared ext3 partition, within a folder called DOCUMENTS)

3. Launch Thunderbird in both with the --profilemanager option, create new profiles pointing to that shared folder

4. Set up your mail

5. Grab a copy of your current Thunderbird mail files and whack them in the shared folder

That's it :)

More in the link posted above, but mine summarises the guts of it.

Cheers
Callan

---

