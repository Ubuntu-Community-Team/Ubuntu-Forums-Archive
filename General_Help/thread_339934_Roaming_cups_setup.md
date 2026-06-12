---
title: "Roaming cups setup"
date: 2007-01-16
forum: General Help
---

### Post by superm1 on 2007-01-16
I use my laptop in several different locations that have different printers.  I'm looking for a way to have the list of available printers change based on the location i'm at.  This is easily achievable at home because I can just enable printer sharing on my desktop computer and CUPS will broadcast that printer to my laptop.  At different locations in school though, we don't have CUPS running and broadcasting available printers.  Each of the printers has to be connected to via a lpq queue.

Is there any way to have CUPS pick these up only when I get say the .student.iastate.edu appended to my domain name by DHCP possibly?

---

### Post by dcstar on 2007-01-16
> **superm1 said:**
> I use my laptop in several different locations that have different printers.  I'm looking for a way to have the list of available printers change based on the location i'm at.  This is easily achievable at home because I can just enable printer sharing on my desktop computer and CUPS will broadcast that printer to my laptop.  At different locations in school though, we don't have CUPS running and broadcasting available printers.  Each of the printers has to be connected to via a lpq queue.

Is there any way to have CUPS pick these up only when I get say the .student.iastate.edu appended to my domain name by DHCP possibly?

If you could have different printers in different user logins, then possibly you could use a different login for your school (and have all of your files accessible from your other accounts).

---

### Post by superm1 on 2007-01-17
> **dcstar said:**
> If you could have different printers in different user logins, then possibly you could use a different login for your school (and have all of your files accessible from your other accounts).
Something makes me think that printers are a system-wide thing in Ubuntu.  They are changed under the System-Administration menu, which most of this is only changable by someone with sudo rights.  I'll see if can experiment today with another user name at school though :)

---

### Post by superm1 on 2007-01-24
I just experimented this afternoon - the printer setup appears to be system wide.  I created an extra user, and both of the printers I had added from my primary user were present in this additional user.

Any other ideas?

---

