---
title: "Apt / Synaptic problem"
date: 2005-07-24
forum: General Help
---

### Post by Snocrash on 2005-07-24
Hi All,

Got an annoying little problem with apt/synaptic. When I first started setting up MythTV, I didn't have everything installed and configured. I have since finished that and MythTV works fine. But anytime I install or update anything with apt/synaptic I get the following error:

E: mythtv-database:  subprocess post-installation script returned error exit status 1
E: mythtv:  dependency problems - leaving unconfigured

As I said, Everything works fine so how do I clear this???

Thanks,

Snocrash

---

### Post by Firetech on 2005-07-24
You could try running "sudo apt-get -f install" in a terminal. Just make sure you want to do what it wants to do before choosing 'Y', as this command might want to remove mythtv.
Another approach might be "sudo apt-get install --reinstall mythtv".

---

