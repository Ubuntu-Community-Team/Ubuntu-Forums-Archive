---
title: "PCIe Bus Error"
date: 2019-06-22
forum: General Help
---

### Post by hawk.eyee on 2019-06-22
PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID)
  device [8086:9d15] error status/mask=00008000/00010000
      [15] Completer Abort          (First)
  TLP Header: 00000000 00000000 00000000 00000000
Failed to create new system journal: No space left on device

this writing's are coming when I'm powering up my laptop. don't know what the problem is, but before this problem arrived there was another problem, which was "/var directory is runnig out of space". maybe, i think there is link between those problem.

---

### Post by uRock on 2019-06-22
Does the system still boot?  I'd install and run Bleachbit. That directory contains Cache, Temp, and Logs.

---

### Post by hawk.eyee on 2019-06-22
no, system doesn't boot... it stuck there which i shown in the previous image.

---

### Post by hawk.eyee on 2019-06-23
Thanks uRock for give me a clue. i just cleaned up /var using sudo apt-get clean, sudo apt-get cleanup, sudo apt-get cleanremove from tty1 mode and it worked!! thank you very much.

---

### Post by uRock on 2019-06-23
Awesome! I am glad that got it working for you!

---

