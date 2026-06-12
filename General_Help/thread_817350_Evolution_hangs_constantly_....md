---
title: "Evolution hangs constantly ..."
date: 2008-06-03
forum: General Help
---

### Post by wfdeller on 2008-06-03
Hi -

I'm using Evolution (Evolution v2.22.1.1/Ubuntu 8.04) and it continues to hang.  There doesn't appear to be a pattern, but it seems like when I am typing an email, I get about about 20-30 seconds into typing and it hangs.  I have to force-quit the application along with kill off some Evolution processes manually.  Is there a way to debug the reason for the hang?

Thanks,
Bill

---

### Post by wfdeller on 2008-06-03
I've disabled an Exchange account from the account preferences and the problem appears to be mitigated.  I need exchange access (unfortunately), but for the time being, I will use a browser to view my exchange email... Anyone have similar issues and found a different work-around?

---

### Post by kevev on 2008-06-16
Exact same issue here. I am using Exchange also.

---

### Post by d2ortiz on 2008-06-17
in Evolution go to : 

Edit -> Preference -> select the exchange account
press Edit

go to the 3rd tab (Reception Options) and enter the Exchange server name in Global Catalog field.

Acept and close;

if these step don't work for you can workaround it by typing your emails in disconected mode and connect again after send the email.

---

### Post by fermin on 2008-11-08
I have this same issue although it doesn't hang completely. It happens mainly when im writing an email as i get about 20-30 seconds of typing and then it hangs briefly for about 5-10 seconds. As it is hung, it greys out and then comes back to normal in full color only to do it again some time later and repeatedly. Ive noticed this tends to happen when my RAM memory is nearly full (of which Evolutions tends to suck up a lot, sometimes up to 400 MB only for it!!) but it also happens when i have plenty of RAM available. 

I use four Google accounts at the same time. Any ideas on whats going on?

---

### Post by Tankerdog2002 on 2008-12-15
Me too. Also, every time I send any attachment, no matter even if it's very small, Evolutin hangs forever. I heard they fixed this bug in Intrepid but still have done nothing for Hardy. Anyone know whats going on here?

---

### Post by fermin on 2008-12-16
I use Ubuntu 8.10 Intrepid Ibex and the hanging problem is the same, so it wasn't corrected. I discovered that the problem might arise from the evolution-data-server program that runs in the background when evolution is running (i catched it in the system monitor or with the 'top' command in the terminal). Nevetheless, i think this isn't an Evolution-only problem since i decided to stop using it, i switched to Thunderbird (i'm sorry), but the evolution-data-server program keeps running in the background and using up lots of RAM memory wich could cause the hang i think. I found out that this evolution-data-server program is necessary for other programs in Gnome to run, not only for evolution, and cannot be eliminated without eliminating essential things like the Gnome Panel, which is simply not an option. Does anyone have this same conclusion? Anyone knows what this evolution-data-server programa actually does? :confused:

---

### Post by bixejo on 2008-12-16
Same problem here, on Ubuntu 8.04 and Evolution 2.22.3.1. No Exchange accounts, and still hangs. Sometimes while I'm typing some text in a compose/reply window, and sometimes just when I click on "Reply" or "Reply all" button (in these last cases I don't even reach to see the message editing window).

I didn't notice however the memory greediness of Evolution and related processes.

--Bixejo

---

