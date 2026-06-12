---
title: "Huge Problem"
date: 2007-01-10
forum: General Help
---

### Post by .Shaun on 2007-01-10
Ok, When I go to my website which is [Here]("http://www.shaunsrealm.co.nr"), it wont load. I need to know where to go on my desktop in ubuntu, or what to do, to re-start my apache. Any help is appreciated!

---

### Post by zerhacke on 2007-01-10
In Gnome, System - Administration - Services.

---

### Post by .Shaun on 2007-01-10
Ok, I activated Apache 2, and I still get [The Same Result]("http://www.shaunsrealm.co.nr"). Any other advice you got?

---

### Post by chrisccoulson on 2007-01-10
Are you behind a firewall? The url you specified resolves as IP address 69.76.56.217, which appears to be stealth. Is that where your Apache server is located?

---

### Post by .Shaun on 2007-01-10
Huh? I am sorry, I am very new to Ubuntu. That IP worked many times before today.

---

### Post by chrisccoulson on 2007-01-10
Is your ISP blocking connections to your Apache server?

---

### Post by Ocxic on 2007-01-10
install firestarter, and open port 80 for everyone.

---

### Post by .Shaun on 2007-01-10
> **Ocxic said:**
> install firestarter, and open port 80 for everyone.

How would I do that?

---

### Post by Ocxic on 2007-01-11
copy this into a terminal:

sudo apt-get install firestarter

that will install firestarter, then go to System-->Administration-->firestarter
it will ask you for your password

click on the "Policy" tab, right click in the white area under "Allow Service" and select add rule, from the drop down list select "HTTP", repeat and select "HTTPS" if your using that as well.

---

