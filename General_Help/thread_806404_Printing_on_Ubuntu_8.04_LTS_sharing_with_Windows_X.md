---
title: "Printing on Ubuntu 8.04 LTS sharing with Windows XP"
date: 2008-05-24
forum: General Help
---

### Post by LinuxTechnology on 2008-05-24
Hello. I have a Ubuntu 8.04 LTS (desktop) hooked up with my HP LaserJet P1006 at home. On Windows XP, I have printer sharing enabled, meaning that other Windows users can print wirelessly. However, when I have Ubuntu running, other Windows users are unable to print. Are there any solutions to solve this problem?

---

### Post by latna on 2008-05-25
You can install samba to do file and printer sharing.
[https://help.ubuntu.com/community/SettingUpSamba#head-0501c5c431920681c11965c65d3d155c69f508f7]("https://help.ubuntu.com/community/SettingUpSamba#head-0501c5c431920681c11965c65d3d155c69f508f7")

Section 5 is printer sharing.

---

### Post by Erlander on 2008-05-26
On your Windows machine you need to go through the add printer procedure and treat it as a network printer.  This will involve installing the windows drivers for the printer on the Windows pc even if they are already there.

Rob

---

