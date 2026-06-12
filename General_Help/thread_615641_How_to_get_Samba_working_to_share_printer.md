---
title: "How to get Samba working to share printer"
date: 2007-11-17
forum: General Help
---

### Post by geovino on 2007-11-17
I have recently installed Gutsy and before I was able to get my other pc to share the printer that is connected to this one. I was able to print with Mint3.1 before the change. Now I have installed Mint 4.0 and Klikit .1-8 on the other pc and I'm trying to get then to share this printer. 

What do I need to do? How do I find the name of this Ubuntu pc? if my user name is davek wouldn't the pc name be davek-desktop?

---

### Post by jimrz on 2007-11-17
> **geovino said:**
> I have recently installed Gutsy and before I was able to get my other pc to share the printer that is connected to this one. I was able to print with Mint3.1 before the change. Now I have installed Mint 4.0 and Klikit .1-8 on the other pc and I'm trying to get then to share this printer. 

What do I need to do? How do I find the name of this Ubuntu pc? if my user name is davek wouldn't the pc name be davek-desktop?

You might try using "cups" to share it. It is simpler to set up and works nicely, at least on ubuntu. Since Mint is ubuntu based it should also work there, don't know about klikit.

From Synaptic instal "gnome-cups-manager". This will give you a 2nd "Printing" icon in system > administration, use the new one to add the printer. 
1- go to "Global Setting" and select "detect lan printers" + "share printers"
2- double click "new printer" and select "network printer"
3- for the route add "ipp://<ip address of comp w/printer>/printers/<printer name>
    mine looks like this:
    ```
ipp://192.168.0.2/printers/PSC_1600_series
```
4 go through the select make/model/driver thingy as usual and you'l be in business

---

