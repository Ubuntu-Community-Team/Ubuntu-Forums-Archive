---
title: "gethostbyename() ??????"
date: 2006-10-27
forum: General Help
---

### Post by DesignerX on 2006-10-27
Why when I executing sudo I'm getting the following message ?
"unable to lookup ubuntu via gethostbyname()"

It never happed before. 
Lately I'm starting to have problems with ubuntu, like synaptic manager window never shows, problems with the network, etc...

Is it possible I got infected with a virus ? is there such a thing like viruses with linux ?

---

### Post by CatKiller on 2006-10-27
It seems likely that you've messed up your /etc/hosts file in some way.

---

### Post by medgno on 2006-10-27
Agreed with what CatKiller said. It sounds like your computer's hostname (in the file /etc/hostname) isn't being properly resolved to the correct address.

Here's what should hopefully fix it:

Edit the file /etc/hosts and check the first line of the file. It should say something like
```

127.0.0.1       localhost.localdomain   localhost    something
```

Where it says 'something', replace it with what you've configured your hostname to be (it sounds like it's 'ubuntu' (without the quotes), but I'm not completely sure.) 

I think this should work and should fix your problem, but if you mess up your host addresses, I think it can prevent you from sudoing, so I'd wait for someone else to say this looks right :-)

---

### Post by DesignerX on 2006-10-27
Thanks alot man, it worked and fixed the other problems I mentioned :)

---

### Post by dbott67 on 2006-10-27
For the record, this happend to me when I was following "[The Perfect Setup]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")" while trying to setup [ISPConfig]("http://www.ispconfig.org/").

Step 5 on page 3 of "The Perfect Setup" omits the part about adding the hostname to the 127.0.0.1 line:
```
127.0.0.1       localhost.localdomain localhost   [COLOR="Red"]<-- missing **server1** here[/COLOR]
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Booting into safe mode (terminal) and adding the hostname to **/etc/hosts** as noted above fixed it.
```
sudo nano /etc/hosts
```

Of course, replace 'server1' with your computer's hostname.

-Dave

---

