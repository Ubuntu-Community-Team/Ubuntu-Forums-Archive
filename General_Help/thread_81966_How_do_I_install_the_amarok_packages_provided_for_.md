---
title: "How do I install the amarok packages provided for kubuntu"
date: 2005-10-25
forum: General Help
---

### Post by tikal26 on 2005-10-25
Hey would like to get the new amarok, but don't know how to install the packages provide y kubuntu here
[http://www.kubuntu.org/announcements/amarok-1.3.5.php](http://www.kubuntu.org/announcements/amarok-1.3.5.php)
 Do I have to remove the current amarok and then install the newest package?

---

### Post by Staesys on 2005-10-25
Remove any current Amarok packages through Adept or Synaptic and then download at least the two files on the page you listed. Additional engines can be found on [http://kubuntu.org/packages/amarok-1.3.5/]("http://kubuntu.org/packages/amarok-1.3.5/").

I prefer the xine engine myself, but whatever.

Once downloaded, in a terminal you can install the packages by using the following:
```
sudo dpkg -i <package name>
```
I reccomend installing the engines first.

---

### Post by tikal26 on 2005-10-25
Thanks really appreciate your reply

Would this put in on synaptic or adept so that i can remove it if I want? or , is there a unistall command to do this?

---

### Post by Staesys on 2005-10-25
Yes, it will put it into Adept or Synaptic so you can uninstall it later.

---

