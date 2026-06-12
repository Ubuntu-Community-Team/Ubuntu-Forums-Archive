---
title: "Cannot find Network Manager in ubuntu 12.04.1"
date: 2016-01-29
forum: General Help
---

### Post by midhun4 on 2016-01-29
Hi,

 How do I find the Network setting in ubuntu 12.4.1.I am able to change the ip through terminal,bt not able to find any GUI.Isnt there any GUI?Pls suggest

---

### Post by Dennis N on 2016-01-29
The Network Manager dialog for settings can be accessed by right-click on the panel network icon. Select "Edit Connections".

---

### Post by oldos2er on 2016-01-29
Moved to General Help.

---

### Post by midhun4 on 2016-02-01
> **Dennis N said:**
> The Network Manager dialog for settings can be accessed by right-click on the panel network icon. Select "Edit Connections".

I am using ubuntu 12.4.1 LTS,No network icon is seen anywhre ,i searched in applications ,bt none,network manager cannot be found ,bt am getting internet connection,need to change ip adress,pls help me to find the network GUI

---

### Post by steeldriver on 2016-02-01
If the network-manager-gnome package is installed, you should be able to invoke the GUI connection editor from a terminal emulator using

```

nm-connection-editor

```

---

### Post by midhun4 on 2016-02-01
> **steeldriver said:**
> If the network-manager-gnome package is installed, you should be able to invoke the GUI connection editor from a terminal emulator using

```

nm-connection-editor

```

Thanks mate,I know it was stupid qustion,bt thanks again for helping me to solve it.

---

