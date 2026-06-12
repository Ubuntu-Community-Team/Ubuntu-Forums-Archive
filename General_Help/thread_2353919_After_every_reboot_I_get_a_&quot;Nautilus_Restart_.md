---
title: "After every reboot I get a &quot;Nautilus Restart Required&quot; by Megasync."
date: 2017-02-26
forum: General Help
---

### Post by amararalleduardo on 2017-02-26
Every time I boot my computer I get a prompt saying to restart nautilus, when I click the button nothing happens, this started happening after I installed Megasync client.
I've already did
sudo apt-get purge megasync
sudo apt-get purge nautilus-megasync
sudo apt-get autoremove
sudo apt-get update
And it keeps happening.
Also tried 
sudo nautilus -q

---

### Post by howefield on 2017-02-26
Try moving the folders..

```
~/.local/share/nautilus
```
and
```
~/.config/nautilus
```

out of the way, say to your documents folder and reboot.

They can always be moved back if required.

---

### Post by amararalleduardo on 2017-02-26
> **howefield said:**
> Try moving the folders..

```
~/.local/share/nautilus
```
and
```
~/.config/nautilus
```

out of the way, say to your documents folder and reboot.

They can always be moved back if required.

I did that but it didnt work, so i moved the files back

---

### Post by amararalleduardo on 2017-02-26
It has something to do with the update-notifier package, after uninstalling it the prompt goes away, but i cant stay without it

---

