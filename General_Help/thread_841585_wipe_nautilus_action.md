---
title: "wipe nautilus action"
date: 2008-06-26
forum: General Help
---

### Post by SpikeyMike on 2008-06-26
Hello, I recently installed hardy and have installed wipe, I had it configured before but I cannot remember how to do it, I want to add a nautilus action for wipe, can anyone please advise me how to set it up?

Spikey

---

### Post by cegpope on 2008-07-02
make sure you also have the nautilus-actions package

then go to system -> preferences -> nautilus actions configuration

add

On the "Menu Item & Action" tab

Label: Wipe
tooltip: Secure Erase Data
icon: (choose one)

Path: wipe
Parameters: -rf %M

On the "Conditions" tab

Appears if selection contains
Check: Both
Check: Appears if selection has multiple files or folders

Click OK
Close

---

