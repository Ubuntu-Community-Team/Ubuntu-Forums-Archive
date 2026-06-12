---
title: "Xubuntu 16.04: gnome-software crashing"
date: 2016-11-16
forum: General Help
---

### Post by philomathus206 on 2016-11-16
All I did was _run fsck in recovery mode_ and _ran software updater_ in the settings _to fix the shutdown freeze_ (it worked). After that, this problem popped up. Here are some screen-shots:

[https://lh3.googleusercontent.com/-ZMLer7VhIbM/WCxhs9qzekI/AAAAAAAAAD0/VUnel7WmcqUIgAMrxEILp_HbYG_SXuSqwCJoC/w424-h318-n/SuperBar.png](https://lh3.googleusercontent.com/-ZMLer7VhIbM/WCxhs9qzekI/AAAAAAAAAD0/VUnel7WmcqUIgAMrxEILp_HbYG_SXuSqwCJoC/w424-h318-n/SuperBar.png)

[https://lh3.googleusercontent.com/-AuSel1e2MLA/WCxhs7H8gbI/AAAAAAAAAD0/ziljU3ofsnQcYvP7llg9Ho8EBtsOQVEYwCJoC/w424-h318-n/Software.png](https://lh3.googleusercontent.com/-AuSel1e2MLA/WCxhs7H8gbI/AAAAAAAAAD0/ziljU3ofsnQcYvP7llg9Ho8EBtsOQVEYwCJoC/w424-h318-n/Software.png)

[https://lh3.googleusercontent.com/-nmtNhlJQbdA/WCxhsx-o1pI/AAAAAAAAAD0/W_ImEv0UVt0sCebpZNZxxh6u8Hz_i2rKgCJoC/w424-h318-n/Screenshot_2016-11-16_21-09-41.png](https://lh3.googleusercontent.com/-nmtNhlJQbdA/WCxhsx-o1pI/AAAAAAAAAD0/W_ImEv0UVt0sCebpZNZxxh6u8Hz_i2rKgCJoC/w424-h318-n/Screenshot_2016-11-16_21-09-41.png)

[https://lh3.googleusercontent.com/-5gYqDsFPsmo/WCxhs-qM4bI/AAAAAAAAAD0/2v-PM4TXgX07OqW7svvvXL-9FmHO1TV0QCJoC/w424-h318-n/Screenshot_2016-11-16_21-09-55.png](https://lh3.googleusercontent.com/-5gYqDsFPsmo/WCxhs-qM4bI/AAAAAAAAAD0/2v-PM4TXgX07OqW7svvvXL-9FmHO1TV0QCJoC/w424-h318-n/Screenshot_2016-11-16_21-09-55.png)

[https://lh3.googleusercontent.com/-ZlMuJbyFlHM/WCxhswDFdLI/AAAAAAAAAD0/KlpkbPVn1Y8n4Yuwg1tvURgwm4AKTnWAACJoC/w424-h318-n/Screenshot_2016-11-16_21-07-10.png](https://lh3.googleusercontent.com/-ZlMuJbyFlHM/WCxhswDFdLI/AAAAAAAAAD0/KlpkbPVn1Y8n4Yuwg1tvURgwm4AKTnWAACJoC/w424-h318-n/Screenshot_2016-11-16_21-07-10.png)

This happens all the time, I rebooted and ran stuff in recovery mode, but I still can't get gnome-software to run properly. Please, tell me what's wrong. [-o<

BTW, I really like Xubuntu; it's much better than windows. :biggrin:

---

### Post by recmont on 2016-11-16
Hello there.

Totally newbie here, but registered on the forums so I could try to help out and start paying back all the help I was able to gather in the past week or so on these forums.

I have recently installed Xubuntu 16.04 on two Dell machines: an regular business-oriented desktop (i3 CPU with integrated Intel Graphics) and on a workstation-class desktop (Xeon CPU with standalone graphics card and no integrated video chipset).

I do not know what made a difference and where, but on the i3 desktop, everything went fine, I ran all the software updates after installation and all was fine and well. However, on the Xeon workstation, onto which I installed the same distro this very evening, the software centre kept crashing on me. It would open the main window, but would not load anything from the remote server and would then close on its own.

When I was looking around to find the name of the application (since I only knew how to open it from the menu bar), I found this post of yours and saw that the name was 'gnome-software'. Well, with that I thought of running a package upgrade, which did point out to me that there would be some packages to upgrade, including the very gnome-software.

So, again, no guarantees from the newbie here, but try "sudo apt-get upgrade" from a Terminal window and see whether it fixes for you. Good luck.

Cheers.

---

### Post by wildmanne39 on 2016-11-16
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by philomathus206 on 2016-11-17
> **recmont said:**
> 

So, again, no guarantees from the newbie here, but try "sudo apt-get upgrade" from a Terminal window and see whether it fixes for you. 



It worked! Thanks! ^^

---

### Post by trevord100 on 2016-11-19
> **recmont said:**
> Hello there.

Totally newbie here, but registered on the forums so I could try to help out and start paying back all the help I was able to gather in the past week or so on these forums.

I have recently installed Xubuntu 16.04 on two Dell machines: an regular business-oriented desktop (i3 CPU with integrated Intel Graphics) and on a workstation-class desktop (Xeon CPU with standalone graphics card and no integrated video chipset).

I do not know what made a difference and where, but on the i3 desktop, everything went fine, I ran all the software updates after installation and all was fine and well. However, on the Xeon workstation, onto which I installed the same distro this very evening, the software centre kept crashing on me. It would open the main window, but would not load anything from the remote server and would then close on its own.

When I was looking around to find the name of the application (since I only knew how to open it from the menu bar), I found this post of yours and saw that the name was 'gnome-software'. Well, with that I thought of running a package upgrade, which did point out to me that there would be some packages to upgrade, including the very gnome-software.

So, again, no guarantees from the newbie here, but try "sudo apt-get upgrade" from a Terminal window and see whether it fixes for you. Good luck.

Cheers.

worked for me too after 2 weeks of hassle thanks very much!:p

---

### Post by verymadpip on 2016-11-21
Looks like sudo apt-get upgrade has worked for me too.
Awesome :)

---

