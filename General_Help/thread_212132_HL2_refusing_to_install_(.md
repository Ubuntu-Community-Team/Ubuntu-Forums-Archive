---
title: "HL2 refusing to install? :("
date: 2006-07-09
forum: General Help
---

### Post by sponge008 on 2006-07-09
So, after installing the basics (Xfire, Limewire, Java, Flash, others), I've decided to try getting Windows games to work in Linux through Wine. I followed this guide:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam)
to install Half Life 2, and the first part worked. I got through the 26% bug, and Steam installed correctly. However, then, I mounted my HL2 installation CDs (I made ISOs) in media/mcd1 thru mcd5. They seem fine. I then wined hl2.msi in the first CD, however, at the beginning of the actual installation (copying files), the setup fails. I get the window "Fatal Error" with the message "Installation ended prematurely because of an error". The Wine terminal window reads:


yuri@yuri-desktop:~$ sudo wine msiexec /i /media/mcd1/hl2.msi
fixme:msi:MsiInstallProductW L"/media/mcd1/hl2.msi" (null)
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
err:msi:msi_dialog_create_controls no handler for element type L"GroupBox"
err:msi:msi_dialog_create_controls no handler for element type L"GroupBox"
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
err:msi:msi_dialog_create_controls no handler for element type L"Billboard"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishComponents"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishFeatures"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterTypeLibraries"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveODBC"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterClassInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterExtensionInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterProgIdInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterMIMEInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveShortcuts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveDuplicateFiles"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveFolders"err:cabinet:FDICopy PFDI_OPEN returned zero for Z:\home\yuri\hl22.cab.
err:msi:extract_cabinet_file FDICopy failed
err:msi:ACTION_InstallFiles Unable to ready media
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  274
  Current serial number in output stream:  295

C is my Windows Wine drive, Z is my Ubuntu drive, and yuri is my account. The instalation CD1 is mounted in /media/mcd1


Also, when the installation options (install/don't isntall CSS, install locally, etc) menu is up, some of the font is screwed up. Could this have anything to do with it? 
[http://img407.imageshack.us/img407/1296/buggyinstall1vv.jpg](http://img407.imageshack.us/img407/1296/buggyinstall1vv.jpg)

So, does anyone know what is wrong? Google turned up nothing. Thanks for the help.

---

### Post by sponge008 on 2006-07-10
Update:
I believe the problem does not lie with the Half Life 2 installer. In fact, I realized my Steam was not working properly. After it updated to 100%, it exited, and now, if I try to run steam.exe, the "starting" window flashes for a fraction of a second and disappears. 

The terminal reads:

err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:dbghelp:EnumerateLoadedModules If this happens, bump the number in mod

(hopefully someone can help now)

---

### Post by s|k on 2006-07-10
You probably would get better help if you posted in the game forum on this site.

---

