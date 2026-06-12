---
title: "Software Store search problems"
date: 2017-12-18
forum: General Help
---

### Post by HankB on 2017-12-18
I'm having difficulty searching the software store. For example the search term "mosquitto clients" finds nothing. If I search for "mosquitto" alone there is one result "mosquitto-simple".

If I search using apt I find
```
hbarta@yggdrasil:~$ apt search mosquitto clients
Sorting... Done
Full Text Search... Done
libmosquitto-dev/artful 1.4.12-1 amd64
  MQTT version 3.1/3.1.1 client library, development files

libmosquitto1/artful 1.4.12-1 amd64
  MQTT version 3.1/3.1.1 client library

libmosquittopp-dev/artful 1.4.12-1 amd64
  MQTT version 3.1 client C++ library, development files

libmosquittopp1/artful 1.4.12-1 amd64
  MQTT version 3.1/3.1.1 client C++ library

mosquitto-clients/artful 1.4.12-1 amd64
  Mosquitto command line MQTT clients

mosquitto-dbg/artful 1.4.12-1 amd64
  debugging symbols for mosquitto binaries

hbarta@yggdrasil:~$ 

```

Is there some setting that causes the software store to filter results of am I just searching wrong? This seems like a pretty simple search and the software store just doesn't find what I need.

I searched "software" in Settings and nothing was found.

This is on Ubuntu 17.10 Software store 3.26.1.

Thanks!

---

### Post by pauljw on 2017-12-18
Maybe install synaptic and use it rather than software store.

---

### Post by HankB on 2017-12-18
Hi Pauljw,
That's a good work around. It seems to be installed by default and I get the expected search results with Synaptic.

It doesn't explain the problem with searching the software store. Another example: Search (Software Store) for 'gpodder' and it is found. Search for 'podcast' and it does not show up.

Also 'synaptic' doesn't know anything about snaps.

---

### Post by Holger_Gehrke on 2017-12-18
The 'Software' application is for new and non-technical users, so only a selection of packages is shown and libraries and development packages are not shown. There used to be (around Ubuntu 12.04) an option 'show technical packages' (or something like that); this was removed for the sake of simplicity ,,. along with the rest of the options dialog in this program. Why it's search function behaves so erratically I don't know either. You could -- of course -- take a look at the source to find out.

syn**apt**ic is for packages managed through the normal packaging system (apt). snaps are completely outside this system, so of course synaptic won't show you snaps, whether they are on one of Canonical's servers, somewhere else on the net or even installed on your machine.

The design goals of the Debian package management (apt, dpkg etc.) and snap are almost diametrically opposed: 

[LIST]
[*].deb packages are the smallest pieces of a piece of software into which it could be sensibly divided and each package depends on others which will be automatically installed (if they aren't installed already) to make a package work 
[*].snap packages have the goal of separating each program as completely from any other program as possible without the use of virtualisation and deliver everything a program may ever need in one big squashfs. 
[/LIST]
 With .deb you get each file once and only once, with snaps you might end up with a dozen or more copies of complete subsystems. snaps are easier to create and install: a developer just puts everything his program needs into one big archive and is -- basically -- finished. On Installation you don't have dependencies that must be fulfilled first, you just mount the squashfs and are done. Of course snaps are bigger, each snap brings everything the installed program needs along, including two or three kitchen sinks ...

Holger

---

### Post by HankB on 2017-12-19
Hi Holger, thank you for the reply.
> **Holger_Gehrke said:**
> The 'Software' application is for new and non-technical users, so only a selection of packages is shown and libraries and development packages are not shown. There used to be (around Ubuntu 12.04) an option 'show technical packages' (or something like that); this was removed for the sake of simplicity ,,. along with the rest of the options dialog in this program. [...] 
Yes, I recall the option to include all packages in the software store. It seems unfortunate that it has been dumbed down to the extent that it is no longer possible for me to use it. :(
> 
syn**apt**ic is for packages managed through the normal packaging system (apt). snaps are completely outside this system, so of course synaptic won't show you snaps, whether they are on one of Canonical's servers, somewhere else on the net or even installed on your machine.

The design goals of the Debian package management (apt, dpkg etc.) and snap are almost diametrically opposed: [...]

I don't expect (upstream) tools intended to work with Debian packages to include snaps. I had expected that Ubuntu might provide a tool that supports all package formats but that is not presently the case. It looks like I need to use two command line tools ('apt search' and 'snap search') to search for software.

I think I might describe the design goals of Snap vs. Debian packages a little differently. The ultimate goal is to get a software program installed with all of the associated libraries and any related programs which it requires. They just go about it in different ways. Debian strategy is to install all dependencies on the base system. Snap strategy is to package the dependencies to run together in an isolated environment. Both have advantages and disadvantages.

best,
hank

---

