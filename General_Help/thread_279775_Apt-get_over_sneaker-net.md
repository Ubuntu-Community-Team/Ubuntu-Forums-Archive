---
title: "Apt-get over sneaker-net?"
date: 2006-10-18
forum: General Help
---

### Post by R3M3 on 2006-10-18
I'm working with an Ubuntu computer that has limited/no internet connectivity. I was wondering if there was a way to "fake" an internet connection for the purpose of intalling/upgrading with apt-get.

I already have half the scheme worked out. -- I do the "apt-get intall/upgrade" with the --print-uris option, save the output to a file, and transfer the file to a computer with 'net. I then use the outputed URIs with download program to save the .debs to a USB drive, move the drive back to the netless computer, and copy the files to /var/cache/apt/archives. I run apt-get once again, and this time it can install without net access. (Sounds harder than it actually is.)

The one issue I'm having is updating the repository package lists without being connected to the internet. Is there some way I can fake an "apt-get update" without being connected directly to the internet?  I'm hoping it's just a matter of downloading files from the repository on a separate machine and copying them to the local, netless, machine.

Thanks.

---

### Post by nikhilk on 2006-10-18
Well I guess that can be done somehow, but for that the "no Internet connection" machine should be connected via LAN to the other machine with Internet connection.
Is that the scenario your case?

---

