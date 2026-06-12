---
title: "Getting dyndns ip-redirect to work (as in wiki)"
date: 2007-02-28
forum: General Help
---

### Post by Chake99 on 2007-02-28
I was trying to configure the dyndns ip redirect mentioned in the wiki, [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service) , and when I run sudo sh /etc/ppp/ip-up.d/dyndns_update.sh it returns

> ipcheck.py: The hostnames listed do not match the ipcheck.dat file.
ipcheck.py: Remove the dat file and use same command ONCE with --makedat.
ipcheck.py: Note that if you are maintaining both a custom domain and
ipcheck.py: a dyndns domain, you should be using the -d option and
ipcheck.py: keeing the data files in separate directories.

I don't know where to find the make.dat file it suggests deleting, and I don't remember running into this when going through this in feisty.

If there is any more information I need to get or anything I'd be happy to get it, but I really need some sort of direction.

Thanks in advance.

---

### Post by Chake99 on 2007-03-01
*bump*

---

### Post by Chake99 on 2007-03-01
*bump*

---

### Post by Chake99 on 2007-03-12
*bump*

---

### Post by kvonb on 2007-03-12
Looking through the link you gave, it seems that ipcheck makes the .dat file in your /root folder (/root/ipcheck.dat).

If it's not working, all I could suggest is going through that tutorial again, making sure you read it very carefully.

Or, an easier way would be to run synaptic and do a search (by description and name) for "dyndns".

There are 6 apps that are listed on mine for Edgy :).

Regards, Kev :)

---

