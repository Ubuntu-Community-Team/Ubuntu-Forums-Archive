---
title: "I blocked an application from updating and it updated"
date: 2019-01-20
forum: General Help
---

### Post by EZZ9 on 2019-01-20
First it was Synergy. I went to synaptic package manager an pick it. Then clicked package and lock version. But it updated and now because they are not the same they will not connect and it like I just installed it and have to set it up at every restart. Only have one mouse and keyboard make it even worse having to unplug them a few time to get it working.

How do I lock it from ever updating. I thought I did it. It is red on the synaptic package manager so what did I do wrong?

I have to keep them at 6.1 because my 2ed computer is not showing the 8.1 version and everything I've tried to update it fails. So I lock them both to 6.1 and now that has failed. :(
and with this popup always showing up about a dozen time at once on 8.1 you can't get to the main setting till about 20 to 50 times clicking very fast.

---

### Post by &amp;KyT$0P# on 2019-01-20
Instead of using Synaptic, try running this command in Terminal -
```
sudo apt-mark hold [COLOR="#FF0000"]<package_name>[/COLOR]
```
replacing [COLOR="#FF0000"]<package_name>[/COLOR] with the actual name of the package you want to hold back.

Refer to [FONT=Courier New]man apt-mark[/FONT] for more info

---

### Post by EZZ9 on 2019-01-20
I want to make sure i get this right on the package "the cardboard looking box" it has this name. 
synergy_1.6.2-0ubuntu2_amd64.deb

but in the synaptic it has the name 1.6.2-Oubunt

and the file just reads synergy
what one is the <name> I need?

---

### Post by &amp;KyT$0P# on 2019-01-20
Probably "synergy"

* To confirm, you could try running this -
```
dpkg-query -W | grep -i synergy
```
it will show package name followed by version of all installed packages where name contains "synergy"

---

### Post by EZZ9 on 2019-01-20
sudo apt-mark hold synergy 1.6.2-0ubuntu2
synergy set on hold.
E: Unable to locate package 1.6.2-0ubuntu2
E: Couldn't find any package by glob '1.6.2-0ubuntu2'
E: Couldn't find any package by regex '1.6.2-0ubuntu2'

ok so does this look like it worked? one line reads "synergy on hold" but the next one reads unable to find. Augh!

---

### Post by &amp;KyT$0P# on 2019-01-20
Looks like it worked.  You can confirm by checking the output of this command -
```
apt-mark showhold
```

The errors are because you also pasted the package version in the command, but it only takes package names, so it treated that as the name of a second package you wanted to set on hold.

---

### Post by EZZ9 on 2019-01-21
Great it worked. Thank you!

---

