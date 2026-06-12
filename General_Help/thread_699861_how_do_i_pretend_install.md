---
title: "how do i pretend install?"
date: 2008-02-17
forum: General Help
---

### Post by HappyFeet on 2008-02-17
i would like to know how to do sudo apt-get install name of program, without actually installing anything. to see if it would work. thanks.

---

### Post by FuturePilot on 2008-02-17
I don't really think that's possible. It needs to be installed before you can run it. However if it doesn't work you can always remove it
```
sudo apt-get remove <program-name>
```
or if you want to completely remove it
```
sudo apt-get remove --purge <program-name>
```
if there's any un-needed dependencies you can also remove those too
```
sudo apt-get autoremove
```

---

### Post by aidanr on 2008-02-17
```
sudo apt-get -s install packagename
```
```
-s, --simulate, --just-print, --dry-run, --recon, --no-act
No action; perform a simulation of events that would occur but do
not actually change the system. Configuration Item:
APT::Get::Simulate.

Simulate prints out a series of lines each one representing a dpkg
operation, Configure (Conf), Remove (Remv), Unpack (Inst). Square
brackets indicate broken packages with and empty set of square
brackets meaning breaks that are of no consequence (rare).

```

But this only tests the installation, not whether or not the program runs. For that you should install it in a virtual machine.

---

### Post by HappyFeet on 2008-02-17
thanks alot. i knew i had heard of it before.

---

