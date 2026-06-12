---
title: "problems with setting up internet"
date: 2006-12-10
forum: General Help
---

### Post by nickelbag on 2006-12-10
first of all, im sorry if i am posting this in the wrong section


about a month ago i tried the ubuntu 6.06 live cd and i liked it, but wasnt ready for the transition just yet. today i decided that i would dual boot xp pro and edgy

i tried installing edgy, but it wouldnt load right so i went with dapper instead

i got through the installation just fine, the problems come with setting up my internet connection

i set it up using sudo pppoeconf and go through the setup and at the end it tells me that the connection is active, but when i open firefox the pages wont load

i saw someone in another thread talking about pinging 66.102.9.99 so i tried that and it worked

i shut down the connection with sudo poff dsl-provider and started it back up with sudo pon dsl-provider, tried the ping again, it once again worked, then when i opened firefox the page loaded

the problem is after about 30 seconds the pages stopped loading again


so i repeated the process, once again the connection only worked for about 30 seconds

i have looked through numerous threads and nothing seems to solve my problem

i would appreciate some help if anyone would be willing


im using dsl through a wired intel pro/100 ve network connection
dual booting xp pro and ubuntu 6.06

if i forgot to include any relevant information i am sorry

---

### Post by padre999 on 2006-12-11
I had the same problem once. It had to do with the DNS server settings being automatically overwritten shortly after the connection has been triggered. It was necessary to kill the process responsible for this before connecting.

Can't remember exactly what it was, will have a look.

---

### Post by nickelbag on 2006-12-11
i juuuuuust fixed it

on the properties for my ethernet card i changed from dhcp to static ip and it worked

<3 ubuntu

---

