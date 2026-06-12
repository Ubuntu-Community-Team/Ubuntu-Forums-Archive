---
title: "Resetting a package to 'automatically installed'?"
date: 2008-05-31
forum: General Help
---

### Post by Vicksters on 2008-05-31
Hello,

I recently tried to install a package that was already on my system as an automatic install, I guess as a dependency for another. When I did this, I received a message that said package was now set to 'manually installed'.

I guess it doesn't make that big a difference, but is there a way to reset it to 'automatically installed'?

Thank you very much for your support and best regards,

~ Vicks

---

### Post by nhandler on 2008-06-01
Launch Synaptic Package Manager (System->Administration->Synaptic Package Manager). Now, locate the package that got set as "Manually Installed". Go to the "Package" pull-down menu at the top, and select "Automatically Installed". That should set it back to being "Automatically Installed".

---

### Post by Vicksters on 2008-06-01
> **Cheater said:**
> Launch Synaptic Package Manager (System->Administration->Synaptic Package Manager). Now, locate the package that got set as "Manually Installed". Go to the "Package" pull-down menu at the top, and select "Automatically Installed". That should set it back to being "Automatically Installed".

I see...

Is there a way to do this using apt-get? This is a server install and as such it has no GUI.

---

### Post by nhandler on 2008-06-03
I haven't found a way to do this with apt, but I did find a solution that uses aptitude (which can be run from a server install). Launch aptitude. Navigate through the list of installed package until you find the one you want to set to "Automatically Installed". Now, type "M" to set it as automatically installed. You can type "m" to set it as manually installed.

---

### Post by ebrahim on 2008-08-17
Because I don't like synaptic and aptitude, I do this by editing /var/lib/apt/extended_states ;)

---

### Post by zika on 2009-06-16
Playing with xorg-edgers my kernel got overwritten with new KMS version. I rectified that by forcing version but now I'm not sure what is the default status (Automatically installed) for linux-{image,headers}-2.6.30-9{,generic} and linux-libc-dev. Thank You in advance ... /var/lib/apt/extended_states from somebody using Karmic on 64-bit could do the trick ...

---

