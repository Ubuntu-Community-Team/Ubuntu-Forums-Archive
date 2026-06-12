---
title: "Wine regedit.exe"
date: 2007-04-14
forum: General Help
---

### Post by tenkabuto on 2007-04-14
I'm trying to run the regedit.exe for my Windows partition but when I try clicking and launching it in a terminal nothing happens and I get this in the terminal:
> err:module:import_dll Library AUTHZ.dll (which is needed by L"Z:\\media\\hda1\\WINDOWS\\regedit.exe") not found
err:module:import_dll Library ACLUI.dll (which is needed by L"Z:\\media\\hda1\\WINDOWS\\regedit.exe") not found
err:module:import_dll Library ulib.dll (which is needed by L"Z:\\media\\hda1\\WINDOWS\\regedit.exe") not found
err:module:import_dll Library clb.dll (which is needed by L"Z:\\media\\hda1\\WINDOWS\\regedit.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\hda1\\WINDOWS\\regedit.exe" failed, status c0000135

How can I get it to work? I need to run it. :(

---

### Post by rai4shu2 on 2007-04-14
Wine has its own regedit as well as its own registry. You can't use an actual Windows registry with it (AFAIK).

---

