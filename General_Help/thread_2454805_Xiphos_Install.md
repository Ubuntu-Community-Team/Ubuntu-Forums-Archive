---
title: "Xiphos Install"
date: 2020-12-06
forum: General Help
---

### Post by basicsearcher on 2020-12-06
Greetings Ubuntu Community

Hope i am posting at the right spot. I am currently using Ubuntu 20.04 MATE. Going fairly o.k. It is the sole OS.
I am interested to install Xiphos, which is a popular open source bible study package, running on Linux, Windows, and Mac.
I started out by going to Synaptic and installing what was there. Turns out the 3 packages were developer versions, so as a general user i needed more. So went to xiphos.org, and got a up-to-date version via the page for crosswire ppa at launchpad. Installed the download successfully, apparently.
But i cannot start the application, or even get my machine to show that it has the application.

Anyone have any ideas? All input welcome. basicsearcher is seriously under par in technical skills, btw. But willing to learn.

Patrick

---

### Post by Holger_Gehrke on 2020-12-07
Since your description of what you did is rather sparse on details I can't tell what went wrong. If the program is not in the menu, you could try starting it from a terminal with 'xiphos'. If this gives you an error along the lines of 'command not found' then whatever you did didn't actually install the program.

Xyphos is available from the normal Ubuntu repositories for 16.04, 18.04, 20.10 and will probably be in 21.04 (at least packages.ubuntu.com says so) but for some reason isn't available for 20.04. Probably somebody missed a deadline.

In the simplest case you would add the PPA to your sources of available packages according to the instructions in the PPA ('sudo add-apt-repository ppa:pkgcrosswire/ppa' in a terminal), update the list of available packages (either in Synaptic or in a terminal with 'sudo apt-get update') and then installed xyphos (either in Synaptic or with 'sudo apt install xyphos' in a terminal; both methods will pull in all the other needed packages as dependencies). xiphos includes a .desktop-file that gets installed in /usr/share/applications, so if it's installed correctly it should be visible in the menu (if MATE uses the categories in the .desktop-files it should be in 'Education').

Holger

---

