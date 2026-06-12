---
title: "deinstalled prog showing up on update"
date: 2023-07-04
forum: General Help
---

### Post by JamButty on 2023-07-04
About a year ago I installed Teamviewer, then soon found it not needed and de-installed it. It does not show up under apt list --installed, but every update still gets a "hit". Does this imply some part is still active?
[HTML]$ sudo apt update...Hit:1 https://linux.teamviewer.com/deb stable InRelease
[/HTML]

---

### Post by deadflowr on 2023-07-04
It's because you need to disable/remove it from your sources.

Open Software and Updates and go to Other Software.
Locate the entry for teamviewr and uncheck it. (It will ask you for your password)

Manually you can simply delete the associated folder in /etc/apt/sources.list.d.

---

### Post by JamButty on 2023-07-04
Entry was unchecked, but deleting /etc/apt/sources.list.d/teamviewer.list cleared it out.
Thanks!

---

