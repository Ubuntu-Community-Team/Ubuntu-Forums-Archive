---
title: "Enrolling Machine owner key in a scaleable way"
date: 2022-10-17
forum: General Help
---

### Post by abhisangeetha-da on 2022-10-17
Hello, 

Not sure if this is the right space to post this, we have a security tool that needs its code signing key imported to the machine so it can function effectively. From what I have read about secure boot, this is exactly the reason it exists, so only authorized kernel modules are loaded during boot. The solution, from what I see is to use MOkutil to enroll the key... but, we have about 80 ubuntu machines spread across the globe, which makes the logistics of this a little difficult. 

Am I missing something? is there a more scaleable way to enroll the keys onto managed machines (we are not subscribers to Ubuntu pro) ? 


Thanks

---

### Post by TheFu on 2022-10-17
Google found this how-to: [https://ubuntu.com/blog/how-to-sign-things-for-secure-boot](https://ubuntu.com/blog/how-to-sign-things-for-secure-boot)
I know nothing else.

---

### Post by abhisangeetha-da on 2022-10-19
Thank you, @TheFu that also uses MokUtil and relies on user intervention, which is okay but also resource heavy on ensuring that gets done. :(

---

### Post by TheFu on 2022-10-19
> **abhisangeetha-da said:**
> Thank you, @TheFu that also uses MokUtil and relies on user intervention, which is okay but also resource heavy on ensuring that gets done. :(

Have the HW vendor pre-install your keys into the BIOS.  All of them will do that for a corporate account.  I've been on projects where we'd use fedex to have the OEM service all our laptops.  We bought 10% more than we needed so there would be enough to swap out where and when needed.  The fixed and updated computers would be fedExed with a fresh BIOS and fresh OS install containing all our applications on the image directly to the needed location for that specific device.  We had over 1300 locations and about 25K laptops.  The vendor providing these services and fixes wasn't near any of our locations.  
Is that scalable enough?

---

### Post by MAFoElffen on 2022-10-19
I saw a major shift in how businesses did their IT "business" during the pandemic. Where people were working from their home. Where I was a contractor for Onsite Warranty Service for Dell, HP and Lenovo.

Major corporations IT departments were stripped down to just a few people, where I would show up to a location and have to call a person who coordinated that service from states or countries away. Where sometimes I would show up to a location, where the corporations IT department was one person, coordinating all it's IT services from one person's kitchen or garage.

Where some of these these services for financial or medical institutions were now contracted to "IT Management Services" pop-ups, of individuals that coordinated those services for them. They were the new Help Desk from their home or small business location. Whereas, other places I had to go had am empty building, with a floor of empty desks, except for one or two, that kept the lights on and kept that business going...

With many businesses doing secure VPN connections to virtual desktops... I, myself, saw a need for levels of "IT Managed Services, with a good Help Desk." ...And that employees of a company know who to call for a problem.

---

### Post by abhisangeetha-da on 2022-10-24
One of the requirements in the org is to have endpoints encrypted, and  enabling FDE during installation has been easier. Did you have that  requirement and how did you go about that if you did. 

Again, appreciate you taking the time to provide some thoughts. 

Thanks

---

### Post by MAFoElffen on 2022-10-26
I usually setup an SSH tunnel, within an IPSEC tunnel (Layer 2 VPN)... How you would do that depends on the network hardware and the hosts you have on each end.

Meaning the newrk connection is within. I've done this from cisco router to router... Then (alternately) from host to host, immaterial of the network hardware between.

---

