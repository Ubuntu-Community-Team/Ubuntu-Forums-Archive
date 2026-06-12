---
title: "mail function not working with gmail"
date: 2014-11-16
forum: General Help
---

### Post by hookitup on 2014-11-16
Hello All,

I usto have mail set up on my computer so that when a spicific task was done running via shell script, it would send an email to my gmail account and then i could see this task has been completed from anywhere via my iphone. 

the way it was set up was with mailx . i attempted to set this up again on my new computer but am running into way to many issue. im not sure if its with gmail blocking it or what the deal is but i spend about 8 hours yesterday working on getting it working to no avail. 

essentially i need to send an email via terminal.... the way i had it befor was using my gmail account via gmails SMTP settings and useing the mailx command. 

what solutions do you folks have out there and are they currently working? 
Thanks, 

Ubuntu 14.04 LTS

---

### Post by CantankRus on 2014-11-16
If this involves logging into your account have a look at the settings @ 
[https://www.google.com/settings/security/lesssecureapps](https://www.google.com/settings/security/lesssecureapps)

---

### Post by hookitup on 2014-11-16
> **CantankRus said:**
> If this involves logging into your account have a look at the settings @ 
[https://www.google.com/settings/security/lesssecureapps](https://www.google.com/settings/security/lesssecureapps)


NAILED IT.... yess thankyou CantankRus so much. it is now functioning correctly without any issues after allowing my gmail account to except less secure apps.

---

