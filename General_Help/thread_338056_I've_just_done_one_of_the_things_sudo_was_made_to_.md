---
title: "I've just done one of the things sudo was made to prevent. EEK."
date: 2007-01-13
forum: General Help
---

### Post by Chake99 on 2007-01-13
I'm running Kubuntu Dapper Drake.

Earlier my ethernet internet access cut out and I was trying to reconnect to the internet. My sister's laptop's wifi connection was working (over which I'm now typing this) so I decided to go into system settings to see if I could see the problem (on my kubuntu system if it is ambiguous; under I believe Connections or Network Settings).

After finding nothing I thought would help or was relevant I went back to (I think) the second tab.

There was a text input where it had something like the network name of my computer, and inside the field was frenris-desktop. Thinking that this was what dictated system in "user@system" while in command line, and tired of frenris@frenris-desktop, I changed it to something else (after enabling administrative changes/sudo).

Now I cannot start Konsole or system settings. 

(although konqueror windows can open and navigate the file system)

I thought I could restart my computer and that it could possibly reload the network name (or whatever it was) from a different location, or have it work, but restarting can often make problems much worse, so I haven't.

Will restarting fix the problem? Or would I fix it by somehow reverting the network name from safe-mode in the command line, and if so how?

I would really like to get my computer back to normal, so thanks in advance for any help.

---

### Post by taurus on 2007-01-13
Boot into recovery mode from GRUB menu and post both of these files here.

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by Chake99 on 2007-01-13
Alright trying to boot normally works fine to the login window. Then I can login, but when loading I get the error 
> 
there was an eror setting up interprocess communications for KDE. The message returned by the system was 

Could not read network connection list
/home/frenris/.DCOPserver_finite/indefinite_infinite/definite__0


then it just returns me to the login window. I then restarted and did what you suggested from recovery mode. 

cat /etc/hosts returns:

> 
127.0.0.1 localhost frenris-desktop finite/indefinite_infinite/definite 
127.0.0.1 frenris desktop

# the following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback  
fe00::0     ip6-localnet
ff00::0      ip6-mcastprefix
ff02::1      ip6-allnodes
ff02::2      ip6-allrouters
ff02::3      ip6-allhosts


cat /etc/hostname just gives

> 
finite/indefinite_infinite/definite 


---

### Post by Chake99 on 2007-01-14
*bump*

---

### Post by taurus on 2007-01-14
Why don't you edit /etc/hosts and make it look like this?

```

127.0.0.1 localhost
127.0.1.1 frenris-desktop

# the following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Then, change /etc/hostname to make it look like this!

```
frenris-desktop
```
p.s.  You can edit them from the recovery mode.

---

