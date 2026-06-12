---
title: "Ubuntu Customization Kit"
date: 2012-10-25
forum: General Help
---

### Post by 1971 on 2012-10-25
Hi,

I downloaded and installed the deb file for UCK from their site. It installed OK with dependencies. I have a shortcut under system tools but when I run it all I get is the terminal window and no welcome screen.

I would have preferred to get it through a repository but no go. Would like to know the repo so i can add it synaptic for re-install

Any ideas or suggestions to get it running appreciated

Cheers

---

### Post by vasa1 on 2012-10-26
Which version of **L**ubuntu are you using?

---

### Post by 1971 on 2012-10-26
> **vasa1 said:**
> which version of **l**ubuntu are you using?

12.04

---

### Post by WorBry on 2013-03-03
Just tried to install UCK on Lubuntu 12.10 and am experiencing exactly the same issue. The UCK icon is listed there under System Tools, but when I open it all that appears is a blank LXTerminal screen - no Welcome Screen. Tried installing from Synaptic and command-line, with the same result.

Anyone have a solution for this?

---

### Post by vasa1 on 2013-03-03
> **WorBry said:**
> Just tried to install UCK on Lubuntu 12.10 and am experiencing exactly the same issue. The UCK icon is listed there under System Tools, but when I open it all that appears is a blank LXTerminal screen - no Welcome Screen. Tried installing from Synaptic and command-line, with the same result.

Anyone have a solution for this?

Is it supposed to work for vanilla Lubuntu?

---

### Post by WorBry on 2013-03-03
I had assumed it was applicable to all of the Ubuntu derivatives, but looking at the description on the sourceforge UCK project page it states 

*"Ubuntu Customization Kit is a tool that helps you customizing official  Ubuntu Live CDs (including Kubuntu/Xubuntu and Edubuntu) to your needs". *

Indeed, no specific mention of Lubuntu - so maybe not?

---

### Post by vasa1 on 2013-03-04
You can ask here: [https://lists.ubuntu.com/mailman/listinfo/lubuntu-users](https://lists.ubuntu.com/mailman/listinfo/lubuntu-users)
That's one of the places where the Lubuntu folk hang out.

---

### Post by WorBry on 2013-03-05
Thanks. Decided the best solution was to install Xubuntu (Ubuntu won't run on my old PC) as a dual-boot next to my Lubuntu system. The Ubuntu Customization Kit (latest stable 2.4.7) installed without any problems on Xubuntu, but it now lacks an integrated package manager (synaptic), so customization has to be done through the Console (terminal). Given my (as yet) limited knowledge of command line instructions I've only tested fairly basic customizations of the Xubuntu 12.10 Live ISO. It appears to work OK. The only bug was that it produced a message at the end of the build stating that I chose to create a hybrid USB ISO (which I didn't) and that the command could not be found. Ignore that and the ISO works fine. 

Also tried Ubuntu Builder. Now that does include a synaptic and again appeared to work OK. Only problem was that afterwards the host Xubuntu system starting crashing applications left right and centre and I had to re-install it (since learned how to back-up with Clonezilla) - from what I've read it's some bug (loop-back?) with the virtual mounting system used to 'test' the build before burning.

---

