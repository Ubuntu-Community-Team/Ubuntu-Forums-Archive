---
title: "[SOLVED] How to get rid of the Wubi Installer?"
date: 2007-07-30
forum: General Help
---

### Post by Miramax on 2007-07-30
I tried Wubi and it worked perfect. Because i just didi it for testing Purposes i wanted to get rid of it. I uninstalled the Ubuntu Distribution with the Wubi Installer. But the Installer itself is still there. I cannot uninstall it. It`s permanently in my Software-List and the Interface is running when i click uninstall.

I hope somebody can fix my little Problem.

TIA

---

### Post by ago on 2007-07-30
Hmm when you uninstall from add/remove software it should clean up cleanly both the ubuntu installation and the registry entries. If it doen't, it's a bug. Try to download the latest version, install and uninstall.

---

### Post by johnn1949 on 2008-02-04
I have the Wubi installer stuck in my add/remove programs,too.  I've searched for "wubi" and no files are found ,but it is still in add/remove list.

---

### Post by ago on 2008-02-05
> **johnn1949 said:**
> I have the Wubi installer stuck in my add/remove programs,too.  I've searched for "wubi" and no files are found ,but it is still in add/remove list.

That was an issue with older versions. You can remove the registry key manually by removing: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

---

