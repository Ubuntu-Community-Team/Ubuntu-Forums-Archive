---
title: "Laptop was fine on 18.04.6 LTS, but freezing on 22.04 LTS"
date: 2022-04-24
forum: General Help
---

### Post by borgyal on 2022-04-24
My video card is a Geforce GT 335M. Think last nvidia driver to have support for it was 340.108.

I had also got crashing on 20.04 which is why I went back to 18.04.6 LTS. But, I saw that 18.04 LTS has a End of Standard Support date of April 2023 and End of Life 2028. Does that mean there will still be general security updates until 2028? 

And are there any options to try and fix freezing on future Ubuntu versions? 

I had found links like this one [https://jeremy.geek.nz/2021/08/23/using-legacy-nvidia-gpus-in-ubuntu-20-04/](https://jeremy.geek.nz/2021/08/23/using-legacy-nvidia-gpus-in-ubuntu-20-04/) that tried to get back to a 5.4 kernel version and then install the nvidia legacy driver, but I wasn't able to revert to a 5.4 kernel. 

So for now I'm on 18.04.6 LTS.

---

### Post by guiverc on 2022-04-25
> **borgyal said:**
> I saw that 18.04 LTS has a End of Standard Support date of April 2023 and End of Life 2028. Does that mean there will still be general security updates until 2028? 


Ubuntu 18.04 LTS was released in 2018-April (thus it's 18.04 with the *year.month* format for Ubuntu releases), which has 5 years of *standard *support for the system.  Community packages (found in 'universe') have 3 years of team support, which is why 18.04 *flavors* are all EOL already; but that doesn't stop a non-*flavor*-team member from stepping in and providing security fixes during the 5 years as the repositories are open until 2021-April.

Ubuntu 18.04.5 LTS mentions

> Maintenance updates will be provided for 5 years for Ubuntu Desktop,  Ubuntu Server, Ubuntu Cloud, and Ubuntu Base.  All the remaining  flavours will be supported for 3 years.

For confirmation, you can look at a release notice of 18.04-18.04.5 eg. [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/) and contrast with 18.04.6  ([https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/](https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/)) where you'll note no *flavor* was involved as they'd already reached EOL.

Ubuntu 18.04.6 LTS is shorter (*flavors* already being EOL)

> 
Maintenance updates will be provided for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, and Ubuntu Base.

When Ubuntu 18.04 LTS reaches the end of it's *standard* support cycle in 2023-April, it will continue life as Ubuntu 18.04 ESM, ie. security patches will continue  for the packages that are supported via ESM found in 'main.

It maybe worthwhile to look at a prior LTS release which switched to ESM as an example, eg. 16.04 reached it's *end of standard support* with a warning notice found here - [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/) 

Security patches for 16.04 ESM  generally includes only packages included on the original install ISO (ie. found in the 'main' repository), but there you still had to read the notices like here [https://wiki.ubuntu.com/SecurityTeam/ESM/16.04](https://wiki.ubuntu.com/SecurityTeam/ESM/16.04) where you'll note many desktop apps were only supported if the *deb* package was replaced as a *snap* package.

Either way, the fixes are not *available publicly*, but available to users who enable ESM on their boxes. 3 ESM releases are available for free*, *or 50 if you're a Ubuntu Member.  You can decide if that qualifies as "*general security updates*" for you.

---

### Post by ninoivanov on 2022-04-25
OK, after the above lengthy total non-answer, let me suggest this:

Switch to an X11-session. Basically, log out, and then on the login-screen, click your name, and before typing a password, on the lower right of the screen a toothed wheel will appear. Click that toothed wheel and say you want an X11-session.

Wayland freezes my machine, too.

---

### Post by aug7744 on 2022-04-25
If you wait an simple solution try install Lubuntu because x11-session is the default.

---

