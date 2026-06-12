---
title: "Firestarter and Azureus hell!!"
date: 2005-05-25
forum: General Help
---

### Post by MrMojoRising on 2005-05-25
I started using Hoary about a month ago. I had Azureus set up just fine and it had been working flawlessy. That is untill i tried to dabble with Firestarter....

I followed the [Starter Guide's method](http://ubuntuguide.org/#firestarter) and did a ```
sudo apt-get install firestarter
``` and got that running. I ran through the initial setup wizard checking the button for "share internet connection" and let the firewall do it's thing. 

I then realized that i didn't need a firewall so i prompty opened up the terminal and did a ```
sudo apt-get remove firestarter
``` Thinking that would remove all traces of it. 

so i come back the next day, boot up, fire up Azureus only to notice the incredible slow speeds and upon doing a port test i get a  NAT error. This obviously had something to do with FIrestarter but i thought I had removed it.

What could be lingering around that would cause the NAT error........i had done nothing else except ```
apt-get install firestarter
``` and ```
apt-get remove firestarter
```

---

### Post by darkaudit on 2005-05-25
I was getting NAT errors even with ports opened in Firestarter. Once I enabled port forwarding in my DSL modem/router for that port, they went away. I get the green smiley almost all the time now. :)

---

### Post by MrMojoRising on 2005-05-26
I thought that myself......

However my router settings are the same as they were before (when the green smileys were there =))......

I even tried resetting my router and setting up the config from scratch.....

But I still can't get Azureus to be seen.
---------------------------------------------------------------------

Is there some way to see what installing FIrestarter changed in my system?

Is there some way to bring my system to a pre-Firestarter state?

---------------------------------------------------------------------

---

### Post by bored2k on 2005-05-26
[QUOTE=MrMojoRising]I thought that myself......

However my router settings are the same as they were before (when the green smileys were there =))......

I even tried resetting my router and setting up the config from scratch.....

But I still can't get Azureus to be seen.
---------------------------------------------------------------------

Is there some way to see what installing FIrestarter changed in my system?

Is there some way to bring my system to a pre-Firestarter state?

---------------------------------------------------------------------[/QUOTE]
 With your ports supposedly forwarded , go to [PC Flank](http://www.pcflank.com/) and select Advanced Port Scanner, and point it to your Bittorrent ports. If they are closed/stealthed/open, you will see.

You might want to --purge firestarter configurations [easily done through Synaptic]

---

### Post by MrMojoRising on 2005-05-26
I purged all the old firestarter configs using Synaptic as recommened.

At PC Flank the Port Scan showed all my ports to be stealthed.

I restarted my computer and fired up Azureus only to see the same problem. I get a NAT error when using the "NAT/firewall Test" in Azureus.

My router is configured correctly, I know this because I had it working earlier.

I'm still stuck. Is there a way to bring the config files back to a fresh install state?
And what else could possibly be configured wrong that would cause this?

---

### Post by bored2k on 2005-05-26
[QUOTE=MrMojoRising]I purged all the old firestarter configs using Synaptic as recommened.

At PC Flank the Port Scan showed all my ports to be stealthed.

I restarted my computer and fired up Azureus only to see the same problem. I get a NAT error when using the "NAT/firewall Test" in Azureus.

My router is configured correctly, I know this because I had it working earlier.

I'm still stuck. Is there a way to bring the config files back to a fresh install state?
And what else could possibly be configured wrong that would cause this?[/QUOTE]
 What if you forwarded another set of ports and retried ? (configuring azureus for them of course).

Tip 2 . Test 2 - Try running the test while azureus is running.

---

### Post by MrMojoRising on 2005-05-26
After picking a new set of ports to forward and configuring Azureus I am still unable to pass the "NAT/Firewall Test" within Azureus. 

However I am able to download and upload at pretty normal speeds using Azureus (uploads are slightly less though). But am still unable to get a Green Smiley face.

Also my internet connection seems to be sluggish when Azureus is running now......web pages take longer to load......that kind of thing.

---

### Post by bored2k on 2005-05-26
[QUOTE=MrMojoRising]After picking a new set of ports to forward and configuring Azureus I am still unable to pass the "NAT/Firewall Test" within Azureus. 

However I am able to download and upload at pretty normal speeds using Azureus (uploads are slightly less though). But am still unable to get a Green Smiley face.

Also my internet connection seems to be sluggish when Azureus is running now......web pages take longer to load......that kind of thing.[/QUOTE]
 Azureus basically kidnaps all your bandwith..

---

### Post by MrMojoRising on 2005-05-26
So what should I do about the NAT errors? 
I know it can work because it was working before.
There has to be some setting that got changed when I installed Firestarter that i need to revert back to normal.

I just want things the way they were pre-installation of Firestarter (without doing the obvious, and overkill, reinstall of Hoary)

---

### Post by MrMojoRising on 2005-05-26
I think I fixed the problem. \\:D/ 

For some reason or another my computer on my network is now 192.*.*.3
It used to be 192.*.*.2

I don't know how it got changed but simply changing the 2 to a 3 in my router settings fixed the NAT error.



Anyone out there know what happened?

---

### Post by derrick1985 on 2005-05-26
[QUOTE=MrMojoRising]I think I fixed the problem. \\:D/ 

For some reason or another my computer on my network is now 192.*.*.3
It used to be 192.*.*.2

I don't know how it got changed but simply changing the 2 to a 3 in my router settings fixed the NAT error.



Anyone out there know what happened?[/QUOTE]

IF your ip settings are set to be done by dhcp, and then you shut off your two or mor e computers, and boot them in a different order, they can change ip address's easily.

Ex.

I have 4 pieces of equipment that access the internet.  Comp1 xbox ps2 comp2 ip's start at *.*.*.2 and to up to 5 respecedly. If the order goes from what it is above to ps2, comp2, xbox, comp1, then the ip's change and so would the port forwarding for each computer. The settings are correct, the computers have changed.

---

