---
title: "Cups Man Page Doesn't Mention Anything About The Scanner"
date: 2023-09-06
forum: General Help
---

### Post by wyattwhiteeagle on 2023-09-06
I have a 3-in-1 printer/scanner/copier HP Deskjet.
I usually use a Windows machine with the 3-in-1 setup.

I was looking at the cups man page and it doesn't mention anything about my particular setup pertaining to the scanner part of the printer.

I need to use the scanner for a very important part of financial business.

Is there something other than cups that I might look into?

---

### Post by Holger_Gehrke on 2023-09-06
CUPS stands for **C**ommon **U**nix **P**rinting **S**ystem. It doesn't scan, it prints. For scanning there's SANE - **S**canner **A**ccess **N**ow **E**asy. If you install simple-scan it should pull in most of SANE via dependencies. You can find out if your scanner is supported at [http://sane-project.org](http://sane-project.org) . For HP All-in-One devices there's libsane-hpaio which interfaces with hplip (HP Linux Imaging and Printing).

Holger

---

### Post by dragonfly41 on 2023-09-06
I have an old Canon LiDE 600F rich in features and I'm advised by Canon that if I need to use it I must create an old Windows (2000, 7 or XP) on VM session running in Ubuntu or Windows 10 (dual boot setup). Just do not enable networking in the VM to avoid attacks.

---

### Post by wyattwhiteeagle on 2023-09-06
I'm sorry
It's a HP Deskjet 3752 Print Copy Scan Web printer

Question:
This printer attaches via usb port.
Will it have issue's printing/scanning due to being mounted on "media"?

---

### Post by wyattwhiteeagle on 2023-09-06
ok...i have simple-scan installed.
Now how do I use it?

---

