---
title: "Still trying to use wine"
date: 2005-08-16
forum: General Help
---

### Post by Statik on 2005-08-16
I installed wine and winesetuptk using apt-get instead of synaptic. Winesetup seemed to run fine, but when I run the setup for html-kit, I get the following output.

> Invoking /usr/lib/wine/wine.bin HKSetup.exe ...
Created symlink /home/statik/.wine/dosdevices/com1 -> /dev/ttyS0
Created symlink /home/statik/.wine/dosdevices/com2 -> /dev/ttyS1
Created symlink /home/statik/.wine/dosdevices/com3 -> /dev/ttyS2
Created symlink /home/statik/.wine/dosdevices/com4 -> /dev/modem
Created symlink /home/statik/.wine/dosdevices/lpt1 -> /dev/lp0
Created symlink /home/statik/.wine/dosdevices/a: -> /media/floppy0
Created symlink /home/statik/.wine/dosdevices/c: -> /media/SATA_Drive/home/statik/.wine/fake_windows
Created symlink /home/statik/.wine/dosdevices/d: -> /media/cdrom0
Created symlink /home/statik/.wine/dosdevices/e: -> /media/SATA_Drive
Created symlink /home/statik/.wine/dosdevices/x: -> /tmp
Created symlink /home/statik/.wine/dosdevices/y: -> ../%HOME%
Created symlink /home/statik/.wine/dosdevices/z: -> /
Created symlink /home/statik/.wine/dosdevices/a:: -> /dev/fd0
Created symlink /home/statik/.wine/dosdevices/d:: -> /dev/hdb
Created symlink /home/statik/.wine/dosdevices/e:: -> /dev/sta1

You can now remove the [SerialPorts], [ParallelPorts], and [Drive] sections
in your configuration file, they are replaced by the above symlinks.

Converted drive type to new entry HKLM\Software\Wine\Drives "A:" = L"floppy"
Converted drive type to new entry HKLM\Software\Wine\Drives "C:" = L"hd"
Converted drive type to new entry HKLM\Software\Wine\Drives "D:" = L"cdrom"
Converted drive type to new entry HKLM\Software\Wine\Drives "E:" = L"cdrom"
Converted drive type to new entry HKLM\Software\Wine\Drives "X:" = L"hd"
Converted drive type to new entry HKLM\Software\Wine\Drives "Y:" = L"network"
Converted drive type to new entry HKLM\Software\Wine\Drives "Z:" = L"hd"
Converted temp dir to new entry HKCU\Environment "TEMP" = L"X:\\"
Converted path dir to new entry HKCU\Environment "PATH" = L"C:\\Windows;C:\\Windows\\System;X:\\;X:\\test;Y:\\"
Converted windows dir to new entry HKCU\Environment "windir" = L"C:\\Windows"
Converted system dir to new entry HKCU\Environment "winsysdir" = L"C:\\Windows\\System"
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
fixme:font:load_VDMX Failed to retrieve vTable
fixme:richedit:RichEditANSIWndProc EM_AUTOURLDETECT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
err:heap:HEAP_ValidateInUseArena Heap 7f8b0000: in-use arena 7f8d2b78 next block has PREV_FREE flag
fixme:richedit:ME_ReleaseStyle all style references freed (good!)
Wine failed with return code 3 

I'm guessing that some of winesetup's configs have been moved and are now unneccessary, but, that still doesn't help me run the program successfully.

Any help?

Statik

---

