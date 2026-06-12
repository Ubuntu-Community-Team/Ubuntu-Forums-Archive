---
title: "Script aurtostart after Suspend/Hibernate)"
date: 2006-12-14
forum: General Help
---

### Post by Chouca on 2006-12-14
Ciao,

I would like to get my wireless going after suspend, now I do have to wake it up by "sudo /etc/rc.local" from a new button on the panel.

Where and how can I automate this after Suspend / Hibernate?   :confused: 

Regards

Martin

---

### Post by Chouca on 2006-12-15
Hi,

I am  happy to be able to answer my own question  :p 


Make  an executable file containing your script and place it in the  /etc/acpi/resume.d folder

I have now placed 
```

/etc/rc.local
```  

in a file called WirelessWakeUp.sh located in the resume.d folder and it works fine!

Regards

Martin

---

