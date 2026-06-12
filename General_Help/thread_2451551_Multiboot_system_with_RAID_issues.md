---
title: "Multiboot system with RAID issues"
date: 2020-10-06
forum: General Help
---

### Post by helen314 on 2020-10-06
This is follow up  on my initial post about regaing access to primary OS in my muttiboot  (All Linux) system. 
I am posting this because this is  specifically about RAID. 
One of the symptoms of my failure was "endless loop" pointing to SINGLE disk which is part of the RAID5 array. 
After removing the offending disk I managed to run "advanced boot" and retrieved system log. 
In the log there is a red note about the offending array "timing out". 
My next step is to delete the offending , timing out , array. 
No loss - the array was for test , learning purpose and was never used. 
So after this background "introduction" here is the question :
In mutiboot / multi OS system  - 
it appears that RAID5  is common to ALL OS , hence 
can I delete the offending RAID array using  working OS and hoping it will "fix" the "timeout" 
problem I am experiencing in non-working, inaccessible  ( emergency access only ) system?

I am asking to gain more theoretical  knowledge about RAID and yes, I can just delete the array and see the results anyway. 

Cheers

---

