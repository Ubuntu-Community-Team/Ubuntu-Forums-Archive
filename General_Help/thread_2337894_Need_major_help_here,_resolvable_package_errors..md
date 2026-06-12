---
title: "Need major help here, resolvable package errors."
date: 2016-09-22
forum: General Help
---

### Post by Ryaniskira on 2016-09-22
It seems I have some sort of package conflict that is completly UNresolvable. A package has a dependency that conflicts with it aparently and I am unable to do anything. Ubuntu-Mate-Core requests mate-netspeed, but mate-netspeed requests the removal of ubuntu-mate-core so this is UNresolvable. Am I going to have to burn a installation USB and reinstall?

Screenshot:
i.imgur.com/D6OCqQu.png

---

### Post by #&amp;thj^% on 2016-09-22
Sorry to hear that...This might help..but read the options.
To install MATE, choose one of the apt-get options below.

    This will install the base packages required for a minimal MATE desktop

    ```
sudo apt-get install mate-core
```

    This will install the complete MATE desktop

    ```
sudo apt-get install mate-desktop-environment
```

  
Unless you now have a broken package manager...is this the case?

---

