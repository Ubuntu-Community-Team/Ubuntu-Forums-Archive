---
title: "Outgoing (SMTP) Issues on 8.04"
date: 2008-05-08
forum: General Help
---

### Post by fn_tool on 2008-05-08
OK, I never got this working on 7.x or lower....

Using either Evolution of Thunderbird, I can not SEND e-mail.  Receving works like a champ.

Incoming setup:
POP
mail.optonline.net
port: 110
user: justme...no [email]justme@optonline.net[/email]
password managed by uBuntu
Works perfectly
Outgoing setup:
SMTP
mail.optonline.net
port: 25
user justme..no [email]justme@optonline.net[/email]
No Authentication

I have checked w/ my ISP, my settings are correct & work fine on my home XP machine w/ Outlook.

My uBuntu machine, here in the officecan not send e-mail.

I originally suspected we are blocking port 25, so I setup my email account on an XP/THunderbird machine here in the office and it works fine.

My machine is an x86, with a fresh 8.04 installed on a freshly formatted hd.

Any guidance will be appreciated.

---

### Post by prshah on 2008-05-08
> **fn_tool said:**
> 
I have checked w/ my ISP, my settings are correct & work fine on my home XP machine w/ Outlook.

My uBuntu machine, here in the officecan not send e-mail.


If your office does not use optnet as the ISP, their ISP will not allow you to send emails via their SMTP with the "from" as the optnet address.

Workaround: Your "from" must be your office's email address, with the reply-to containing your optnet address.

If your office also uses optnet then I have no idea what's wrong.

---

### Post by juan@forum on 2008-05-08
it sounds you are using an IP address listed in blacklists.

these are usually denied by the mail servers


check the procedure to send mail through your ISP...

---

