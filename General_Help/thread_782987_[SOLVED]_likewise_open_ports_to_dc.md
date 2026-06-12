---
title: "[SOLVED] likewise open ports to dc"
date: 2008-05-05
forum: General Help
---

### Post by jpietari on 2008-05-05
I'm trying to authenticate myself against an Active Directory server using likewise open in Ubuntu 8.04 and keep getting the error "open ports to dc".

This is what I've tried: 
1. Added the ports to the "ufw"
2. Disabled "ufw"
3. Synchronized my clock to 'ntdp"

I've searched online and can't find a solution.  There is a solution online that states that you have to start a "time" service on the domain controller, but I don't think that will fix the problem (since I can authenticate using OpenSuse...ewww ).

---

### Post by jpietari on 2008-05-05
I was trying to connect to the wrong domain.  As soon as I put in the correct fully qualified domain name, the problem went away.

---

