---
title: "need help with azureus removal"
date: 2007-10-17
forum: General Help
---

### Post by Angelbeast on 2007-10-17
I had installed Azureus though the previous version of Automatix. I went to go uninstall it through the new version and it' not listd in the installed apps list. I tried to do it through the command line and it said that Azureus was not installed. How o i go about uninstalling this now? Please help...Thank you :-)

---

### Post by zvacet on 2007-10-17
```
sudo dpkg --remove --force-remove-reinstreq package_name
```

in your case type exact name of Azureus package.If that doesn´t work

```
locate Azureus
```

and you will see all folders with Azureus files in.Go to the every directory and remove it manualy

```
sudo rm -r package_name
```

You don´t need Automatix to install Azureus.You can install it with synaptic.

---

### Post by Angelbeast on 2007-10-17
> **zvacet said:**
> ```
sudo dpkg --remove --force-remove-reinstreq package_name
```

in your case type exact name of Azureus package.If that doesn´t work

```
locate Azureus
```

and you will see all folders with Azureus files in.Go to the every directory and remove it manualy

```
sudo rm -r package_name
```

You don´t need Automatix to install Azureus.You can install it with synaptic.

Thanks for your response...I just opened a terminal and did locate azureus and deleted whatever it listed *LOL*

---

