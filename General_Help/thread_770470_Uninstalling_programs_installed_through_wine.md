---
title: "Uninstalling programs installed through wine"
date: 2008-04-27
forum: General Help
---

### Post by Fogel1497 on 2008-04-27
Okay so I installed a program I no longer want via the wine emulator. I open up the terminal and type in the uninstaller command to bring up the wine uninstaller. 

When I try to uninstall certain programs this is what comes up in the terminal:

"preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:advapi:LookupAccountNameW (null) L"aaron" (nil) 0x7f22f38c (nil) 0x7f22f390 0x7f22f384 - stub
fixme:advapi:LookupAccountNameW (null) L"aaron" 0x7f020b88 0x7f22f38c 0x7f0201c0 0x7f22f390 0x7f22f384 - stub
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
err:msi:msi_dialog_bitmap_control Failed to load bitmap (null)
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\temp\\install.adb" 1 4 (nil) (nil) (nil) (nil)
fixme:msi:msi_unimplemented_action_stub UnregisterFonts -> 1 ignored L"Font" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 129 ignored L"CreateFolder" table values
err:cabinet:FDICopy PFDI_OPEN returned zero for C:\Program Files\Photoshop TryOut\Photoshop CS2\Adobe(R) Photoshop(R) CS2\Data1.cabData1.cab.
err:msi:extract_cabinet_file FDICopy failed
err:msi:ACTION_InstallFiles Failed to extract cabinet: L"Data1.cab"
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627
aaron@aaron-desktop:~$ 
"

---

### Post by mc4man on 2008-04-27
see here
[http://ubuntuforums.org/showthread.php?t=770262](http://ubuntuforums.org/showthread.php?t=770262)
some  other earlier threads also

---

