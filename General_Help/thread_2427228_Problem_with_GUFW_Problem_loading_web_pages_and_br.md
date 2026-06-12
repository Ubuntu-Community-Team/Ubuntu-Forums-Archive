---
title: "Problem with GUFW??? Problem loading web pages and broken NFS network!!!"
date: 2019-09-19
forum: General Help
---

### Post by Old Jimma on 2019-09-19
Hi Community:

I tested GUFW (gui for Uncomplicated Fire Wall)... **[COLOR="#FF0000"]and decided I didn't like it and used synaptic to remove it completely[/COLOR]**.

Since then I've had several problems:

[LIST=1]
[*]I get a "Problem Loading Error" page on Firfox when I try to access Amazon.com... see the attached png file to see what the page looks like!
[*]My home NFS network stopped working! **GRRR!!**
[*]
[/LIST]


Not sure if this has anything to do with GUFW changing proxy setting... I have no idea.

How do I fix these problems??

Thanks!!!
Old Jimma From the Old Country

---

### Post by uRock on 2019-09-19
Did you create any rules in GUFW? Did you disable them before removing GUFW? GUFW is the GUI frontend for UFW. To disable UFW, run **sudo ufw disable** or reinstall GUFW and use it to remove any rules.

I have GUFW installed and the firewall is enabled. By default it shouldn't break outbound connections.

You can see if UFW is enabled by running **sudo ufw status**

---

### Post by Old Jimma on 2019-09-19
Hi uRock!!

Thanks for your repy an excellent advice: It resolved the problem of NFS not working for my home network!!!

While it did not resolve the issue of not being able to access some web sites, this may be a separate issue and I will post a query for help on this specific issue.

In the mean time, thanks to you my NFS problem is resolved and I will mark this discussion closed!

Thank you!
Old Old Old Old Old Jimma

---

### Post by uRock on 2019-09-19
Awesome! I'm glad that worked out!

---

