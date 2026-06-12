---
title: "No network - Eth0"
date: 2013-01-25
forum: General Help
---

### Post by Gordonisnz on 2013-01-25
Hello.

The last few days, my PC is SLOW to load up - no network. 
When i do manage to log in, & do ifconfig - i get No 'eth0' settings.

 I've googled & found these command-line things to add, & then i can log in to Google / modem.

```

sudo ifconfig eth0 down
[sudo] password for gordon: 
gordon@gordon-System-Product-Name:~$ sudo dhclient -r eth0
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
gordon@gordon-System-Product-Name:~$ sudo ifconfig eth0 up
gordon@gordon-System-Product-Name:~$ sudo dhclient eth0
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
gordon@gordon-System-Product-Name:~$ 


```Ive googled, & see that 'service smbd reload' relates to the SAMBA server.  (I've got Apache as my website server - not Samba)..

EdIT: How do i fix it so ETH0 comes up automatically

---

### Post by Cheesehead on 2013-01-25
Please post the entire contents of your /etc/networking/interfaces file. (Remember to use CODE tags).

Do you use Network Manager?

Did anything else occur at the same time as slow-network? Updates? reboot? changed hardware?

Are you sure the problem is your Ubuntu system and not the upstream router or connection? How did you check?

---

### Post by Gordonisnz on 2013-01-25
There is nothing in my interfaces file. (blank).

---

### Post by Gordonisnz on 2013-01-25
thanks. I googled that file & added these lines to it :-

```

auto lo
iface lo inet loopback

```

Rebooted & it seems to be going,

---

