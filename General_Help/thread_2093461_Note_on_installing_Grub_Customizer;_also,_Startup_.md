---
title: "Note on installing Grub Customizer; also, Startup Manager is moribund"
date: 2012-12-10
forum: General Help
---

### Post by rewyllys on 2012-12-10
A kind respondent on the Linux Mint Forums introduced me to *Grub Customizer* as a replacement for *Startup Manager*, which has become moribund.  See
[https://launchpad.net/startup-manager/+announcements#j8300](https://launchpad.net/startup-manager/+announcements#j8300) 
and
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

However, I encountered some quirks in installing *Grub Customizer* into LM14.1 Cinnamon, which is based on Ubuntu 12.10.  Hence, for the benefit of other potential users, here is how I succeeded in installing it.
 
 Step 1:  At the command line, issue the following two instructions, in sequence:
 
 ```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
```The 3rd command-line instruction recommended by the author of *Grub Customizer*

```
sudo apt-get install grub-customizer
```did not work for me.

Instead, I wound up using the following second step.

Step 2:  Open the Synaptic Package Manager, mark grub-customizer for installation, and click on the Apply option.

Step 3:  Log out and then log in again.

After Step 3, you should be able to find Grub-Customizer among the available applications

---

