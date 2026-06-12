---
title: "Ruby installation problem ubuntu 12.04.5 LTS"
date: 2015-09-17
forum: General Help
---

### Post by noriegafam on 2015-09-17
I have an old system that won't allow me to upgrade beyond 12.04 due to the lack of pae support, it has been my Linux companion for several years and pretty much my only and main machine. I am afraid is reaching its end of life. Anyway. I've been experimenting with a signage software called concerto 2 which other fellows had manage to get to work under lucid; however I have spent days trying to get past the preliminary installation of ruby. I have search all over the place just to arrive at a death end. I have installed all sort of versions of ruby even compiling from source, to not avail.
I came here in hopes that someone can help me unravel the mess I made of this thing. It would be easy just to give up on this thing but if I have solved so many problems with the help of the community over the years; I don't see why this one has to be the exception. (unless the limitations of my machine forces me to).

I know a lot of background info needs to be provided, but please, lets just start with this "simple" error message and take it from there:

alejandro@Alex:~$ sudo apt-get install concerto-lite
[sudo] password for alejandro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 concerto-lite : Depends: ruby2.0 but it is not installable or
                          ruby2.1 but it is not installable
                 Depends: libruby2.0 but it is not installable or
                          libruby2.1 but it is not installable
E: Unable to correct problems, you have held broken packages.

And btw synaptic does not show any broken packages.
The install instructions are here: [https://github.com/concerto/concerto/wiki/Installing-Concerto-2]("https://github.com/concerto/concerto/wiki/Installing-Concerto-2")

Any, help will be greatly appreciated.

---

### Post by mörgæs on 2015-09-17
PAE is no limitation. If you want a fresh install of 14.04.3 or 15.04 just use [Forcepae]("https://help.ubuntu.com/community/PAE").

---

### Post by noriegafam on 2015-09-22
Thanks for your quick response; I am not getting email notifications when someone replies. Anyhow. Do you know if "Forcepae" would work for Xubuntu?

---

### Post by mörgæs on 2015-09-23
Yes it does but the menu screen as shown in the guide might look different.

If you want e-mail notifications you can subscribe to the thread.

---

### Post by noriegafam on 2015-10-20
I was able to install latest Lubuntu.

Thank you very much for you input.

---

### Post by mörgæs on 2015-10-20
You're welcome. Enjoy!

---

