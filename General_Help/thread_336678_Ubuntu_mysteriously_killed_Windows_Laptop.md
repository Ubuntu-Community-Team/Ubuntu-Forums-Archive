---
title: "Ubuntu mysteriously killed Windows Laptop"
date: 2007-01-11
forum: General Help
---

### Post by Scooter7 on 2007-01-11
Hi, I was exploring my live cd Ubuntu, and decided to see if I could see my Windows network.   I could, and clicked on dad's laptop in the network.   As soon as I did that, he got the blue screen of death (dunno if you linux users know of it), and now he can't even boot into his BIOS.   I'm worried I may have completely destroyed his computer.   What happened?   Simply viewing the network shouldn't do that.  :-?

---

### Post by meng on 2007-01-11
Sounds like a hardware failure to me. Almost certainly unrelated.

---

### Post by d3v1ant_0n3 on 2007-01-11
I call coincidence.

---

### Post by srunni on 2007-01-11
Yeah, there is definitely no relation between the BIOS level crash on your dad's laptop and your attempt to access his laptop's shared files. I've accessed shared Windows folders (aka Samba shares) and they've worked great. Don't worry about having messed up the laptop; it was pure coincidence.

---

### Post by Scooter7 on 2007-01-11
Yeah, that's what I think too.   I can't see any reason for Ubuntu to have crashed it through the network.

---

### Post by meng on 2007-01-11
> **Scooter7 said:**
> Yeah, that's what I think too.   I can't see any reason for Ubuntu to have crashed it through the network.
If Ubuntu _could_ do that, there'd be some pretty heavy computer vandalism happening right now.

---

### Post by thoughts on 2007-01-12
> Ubuntu mysteriously killed Windows Laptop

Seriously though, can you blame it?

( :

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by dcstar on 2007-01-12
> **meng said:**
> Sounds like a hardware failure to me. Almost certainly unrelated.

Not necessarily, the Windows machine could have some malware infecting it that was only triggered when another machine tried to access one of its network shares, and as soon as the Ubuntu PC accessed it, the payload "detonated".....

If this was the case, any other PC may have triggered it, not just the Ubuntu PC.

---

