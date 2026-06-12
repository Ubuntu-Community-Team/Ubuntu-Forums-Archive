---
title: "VMware Error"
date: 2007-11-03
forum: General Help
---

### Post by amitroy5 on 2007-11-03
When trying to install VMware on Ubuntu 7.10 (the latest version), I get the following error:

VMware Player cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

How can I resolve this? I really need to run VMware. Thank you.

---

### Post by supadupapat on 2007-11-03
I'm getting the exact same error.  Seems a few other people have too (having searched the forum) but there hasn't been a fix yet? :(

---

### Post by amitroy5 on 2007-11-03
Everyone is suggesting VirtualBox, but network bridging is very hard on that. I can't get it to work.

---

### Post by fjgaude on 2007-11-03
One thing to do, likely the best, is to download vmware server from their site. Unpack it into your home dir, and use your original lisence number when asked.

That's what I did in Gutsy; works fine using my old vmx folder.

---

### Post by amitroy5 on 2007-11-04
The problem is that VMware was free. I used the viewer program. Do I then have to pay for the software?

---

### Post by donburch on 2007-11-04
> **amitroy5 said:**
> The problem is that VMware was free. I used the viewer program. Do I then have to pay for the software?

VMware also have a free server program ... as well as pay-for servers.

---

### Post by fjgaude on 2007-11-04
> **amitroy5 said:**
> The problem is that VMware was free. I used the viewer program. Do I then have to pay for the software?

VMware Server is free, no pay ever.

---

### Post by amitroy5 on 2007-11-04
Does Ubuntu have plans to fix the cirrent one? I am not good at Linux to begin attempting to install programs on my own.

---

### Post by PhilipB on 2007-11-04
Hi there, new time user to Ubuntu, but just saying that I'm running Ubuntu 7.10 Gutsy Gibbon in VMware Player and it's running fine. :)

---

### Post by lsutiger on 2007-11-04
Try VirtualBox. It is more lightweight and runs great.
[Follow this link]("http://www.virtualbox.org/")

---

### Post by amitroy5 on 2007-11-04
I gave Virtualbox a try, but I cannot get network bridging to work. I need the guest OS to look like it's apart of my home network. This is because I need to run a server on Windows for it. I have a thead about getting this to work in Virtualbox, but I have not received any replies on it.

---

### Post by lsutiger on 2007-11-04
[Try this guy's blog.]("http://www.fsckin.com/2007/10/29/how-to-run-microsoft-outlook-natively-on-linux-using-virtualbox/") It explains on how to set it up in the post

---

### Post by itsjustarumour on 2007-11-09
> **amitroy5 said:**
> When trying to install VMware on Ubuntu 7.10 (the latest version), I get the following error:

VMware Player cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

How can I resolve this? I really need to run VMware. Thank you.

I'm getting the same thing.  Tried downloading VMWare server from their website too but couldn't get that to work either. ](*,)

Anyone found a solution to this, apart from trying something else like Virtualbox?

---

### Post by lsutiger on 2007-11-09
You could try this:
[http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html](http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html)
Just read it carefully before you do anything. I use virutalbox myself. It seems more lightweight.

---

### Post by itsjustarumour on 2007-11-10
> **lsutiger said:**
> You could try this:
[http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html](http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html)
Just read it carefully before you do anything. I use virutalbox myself. It seems more lightweight.

Isutiger,

Thanks for the link, hadn't seen that one.  I'll give it a try and post up the result.

itsjustarumour

---

### Post by itsjustarumour on 2007-11-11
> **lsutiger said:**
> You could try this:
[http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html](http://ubuntu1501.blogspot.com/2007/05/installing-vmware-in-feisty.html)
Just read it carefully before you do anything. I use virutalbox myself. It seems more lightweight.

Thanks for that, all working fine now. Realised where I went wrong - I'd been cutting and pasting terminal commands from one of the "How-To"s and didn't spot a small error - a minus sign instead of a hyphen! Oh well, it was getting late, lol :-D

---

