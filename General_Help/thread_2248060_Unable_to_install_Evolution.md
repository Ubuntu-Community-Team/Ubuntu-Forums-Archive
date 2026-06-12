---
title: "Unable to install Evolution"
date: 2014-10-12
forum: General Help
---

### Post by Will_Moonen on 2014-10-12
Hello Everyone,

I'm trying to install Evolution with Software Center.
When I do that, I receive an error message about not resolved package dependencies.
When looking at the details, it says:

The following packages have unmet dependencies:

```
evolution-ews: evolution-plugins: Depends: libgtkhtml-editor-4.0-0 (>= 4.6) but 4.6.6-2ubuntu1 is to be installed
                   Depends: evolution (= 3.10.4-0ubuntu2) but 3.10.4-0ubuntu2 is to be installed
evolution-plugins-experimental: Depends: libgtkhtml-4.0-0 (>= 4.6) but 4.6.6-2ubuntu1 is to be installed
                                Depends: libgtkhtml-editor-4.0-0 (>= 4.6) but 4.6.6-2ubuntu1 is to be installed
                                Depends: evolution (= 3.10.4-0ubuntu2) but 3.10.4-0ubuntu2 is to be installed
```

Anyone an idea what this is about and how to fix this?


Thanks - Will

---

### Post by kc1di on 2014-10-12
Which version of ubuntu are you using?

you can try this go to a terminal and type the following commands one at a time.

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install evolution
```

list any error messages you receive in the terminal. 

While there you may want to also install synaptic ```
sudo apt-get install synaptic
```

Synaptic is the old package manager, but still works very well if you know the name of the package you want to install.

---

### Post by Will_Moonen on 2014-10-12
Thank you for the quick response.

> **kc1di said:**
> Which version of ubuntu are you using?
Version 14.04-LTS

> **kc1di said:**
> you can try this go to a terminal and type the following commands one at a time.

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install evolution
```

list any error messages you receive in the terminal.

The apt-get install returned the following messages:
```
 The following packages have unmet dependencies:
 evolution : Depends: evolution-data-server (< 3.11) but 3.13.5-fta1 is to be installed
             Recommends: evolution-plugins but it is not going to be installed
             Recommends: evolution-indicator but it is not going to be installed
             Recommends: spamassassin but it is not going to be installed or
                         bogofilter but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

After removing these packages with apt-get purge, Evolution installed fine.

---

### Post by kc1di on 2014-10-12
Glad to hear you got it installed, enjoy :)

---

