---
title: "Uninstalling Tor Browser"
date: 2022-12-18
forum: General Help
---

### Post by desertwalker1 on 2022-12-18
Hello! 

Very casual ubuntu user (20.04). I'm looking to find out the best way to completely uninstall Tor browser from my computer. I don't use it anymore. 
Looking for the specific commands here. 

Thank you in advance for any advice. 

Regards

---

### Post by timgood on 2022-12-18
To completely uninstall Tor Browser from your Ubuntu 20.04 system, follow these steps:

Open a terminal window and enter the following command:

```
sudo apt-get remove tor-browser

```
This will remove the Tor Browser package and all of its dependencies from your system.

If you also want to delete the configuration files and any data that may have been saved by the Tor Browser, you can use the following command:

```
sudo apt-get purge tor-browser

```

This will remove the package and all of its configuration files and data.

To remove any remaining dependencies that were installed as part of the Tor Browser package, you can use the following command:

```
sudo apt-get autoremove

```
This will remove any packages that are no longer needed on your system.


After following these steps, the Tor Browser should be completely uninstalled from your Ubuntu 20.04 system.

---

### Post by desertwalker1 on 2022-12-19
Thank you for the help.

---

