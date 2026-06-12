---
title: "isc-dhcpserver &quot;unable to clone pool group&quot; after recent update..."
date: 2021-05-30
forum: General Help
---

### Post by edwardecl on 2021-05-30
I noticed isc-dhcpserver updated yesterday and today I have the "unable to clone pool group" error in the syslog...

If I comment out all the 
pool {
...
}

in the /etc/dhcp/dhcpd.conf and add the network range outside of the group it works again... I am using pretty much the example in the manual for isc dhcp server... I noticed the recent update changes the way it parses the config.

Any idea what is broken and how to fix it, I like to set up my network to allow only specific clients between one range and unknown clients on a different rage, which was working fine for months up until this point. Below is the section of my config giving me issues, comment out pool sections and adding the rage outside is working but that's not what I want.

subnet 192.168.0.0 netmask 255.255.255.0 {
# range 192.168.0.12 192.168.0.254;
        option routers 192.168.0.11;
        option subnet-mask 255.255.255.0;
        #option domain-name-servers 192.168.0.11;

        # Unknown clients get this pool.
       pool { 
               max-lease-time 86400;
               range 192.168.0.200 192.168.0.253;
               allow unknown-clients;
       }

        # Known clients get this pool.
       pool {
               max-lease-time 86400;
               range 192.168.0.12 192.168.0.199;
               deny unknown-clients;
       }
}

---

### Post by bls3427 on 2021-06-03
I'm seeing this issue as well. Unfortunately, didn't see this post until I also posted at [https://ubuntuforums.org/showthread.php?t=2462984&highlight=isc-dhcp-server](https://ubuntuforums.org/showthread.php?t=2462984&highlight=isc-dhcp-server).

You can back off to the previous release by installing it with apt, and then using 'apt-mark hold' so that apt doesn't upgrade it again.

It is interesting that the version number is exactly the same except for the ubuntu-specific part. It would be super-awesome if someone from the Ubuntu team would respond to this, but guessing that won't happen.

---

### Post by bls3427 on 2021-06-03
JFYI, here's how to get back to the previous working version and prevent apt from updating it:
```
apt install isc-dhcp-server=4.4.1-2.2ubuntu6
apt-mark hold isc-dhcp-server

```When you want to update to a newer, hopefully working isc-dhcp-server, do
```

apt-mark unhold isc-dhcp-server

```

---

### Post by bls3427 on 2021-06-07
This has been fixed in isc-dhcp-server [COLOR=#333333][FONT=monospace]4.4.1-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]2.2ubuntu6.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]2[/FONT][/COLOR]

---

### Post by edwardecl on 2021-06-08
Yup now fixed, good stuff.

---

