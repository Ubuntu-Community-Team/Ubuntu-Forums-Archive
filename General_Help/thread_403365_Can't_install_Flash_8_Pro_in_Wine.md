---
title: "Can't install Flash 8 Pro in Wine"
date: 2007-04-06
forum: General Help
---

### Post by tmray on 2007-04-06
In edgy I was running Flash 8 Pro with wine and it worked great. 
I just did a fresh install of feisty and I'm trying to install it and it will get all the way up to installing status part of the install wizard but then it just stops and I can't cancel it or close it or anything. I have wine set to emulate windows xp and I have the most recent version from the repositories.

in the konsole this is what it says
```
wine '/media/disk/programs/flash 8 professional/Flash8-en.exe'
fixme:advapi:CheckTokenMembership ((nil) 0x16dcd8 0x34e794) stub!
fixme:advapi:LookupAccountNameW (null) L"tmray" (nil) 0x34e2a4 (nil) 0x34e2a0 0x34e2ac - stub
fixme:advapi:LookupAccountNameW (null) L"tmray" 0x1780f8 0x34e2a4 0x178110 0x34e2a0 0x34e2ac - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
err:ole:TMStubImpl_Invoke invoke call failed with exception 0xc0000005 (-1073741819)
err:ole:xCall RpcChannelBuffer SendReceive failed, c0000005
err:msi:deformat_environment Unknown environment variable L"ALLUSERSPROFILE"
err:msi:msi_dialog_oncommand button click from nowhere 0x17a988 67108864 0x10050
err:msi:msi_dialog_oncommand button click from nowhere 0x17a988 67108864 0x10050
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:rpc:RpcImpersonateClient (0x6524e0): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x2000000021
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:advapi:LookupAccountNameW (null) L"tmray" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"tmray" 0x175d28 0x34f808 0x175d40 0x34f804 0x34f810 - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
err:ole:TMStubImpl_Invoke invoke call failed with exception 0xc0000005 (-1073741819)
err:ole:xCall RpcChannelBuffer SendReceive failed, c0000005
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveExistingProducts"
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x662f18): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x1500000014
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x662f18): stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x6634c0): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x1500000014
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x6634c0): stub
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
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveFolders"
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:msi:register_progid L"Macromedia.Extension.Information" has no class
err:msi:register_progid L"Macromedia.Extension.Package" has no class
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x662f18): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x1500000014
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x662f18): stub
err:heap:HEAP_ValidateInUseArena Heap 0x110000: in-use arena 0x1791c0 next block has PREV_FREE flag
```
and this is where it stalls everytime.

I've installed and uninstalled wine several times as well.

Does anyone know how I can get it working again?

---

### Post by crispy_420 on 2007-04-07
Did you try different configs of wine (win2000, nt4, etc.)?

---

### Post by ilGuccino on 2007-04-10
tried, but doesn't work
I have the same problem, any other idea?
thaks in advance
ilGuccino

---

### Post by timothee on 2007-04-10
Hi there, 

I'm not a Ubuntu user (I use gentoo) but I encountered the same problem: one of the recent update of wine (0.9.30, I believe) broke the Flash 8 installer. If you can get your hand on wine 0.9.29, you'll be able to install Flash 8 again.

Good luck.
Tim.

---

### Post by ilGuccino on 2007-04-10
it works, great! thank you
I installed on Feisty the edgy version, it seems to go well
bye

---

### Post by faridlopez on 2007-04-22
Hello! i'm using Ubuntu 7.04 Feisty.

I installed wine 0.9.29 and i can install Dreanweaver8 and Fireworks8 but i can`t install Flash8!

what can i do?

---

### Post by ilGuccino on 2007-04-23
sure you don't have a newer version of wine installed? maybe you had it before installing the 0.9.29 and you didn't remove it properly
I have feisty too, and I managed to install flash8 with that wine version

---

### Post by dangermouse28 on 2007-06-27
Can someone post a link to wine 0.9.29 please?

EDIT - Never mind! - Used Crossover Office 6.1 and installed Flash 8 Pro as an "unsupported application" in a WinXP "bottle". Installed with no fuss, no problems. Works fine.

Thats how it should be - SWEEEEEEET!

---

### Post by ilGuccino on 2007-06-27
directly from the WineHQ site's download page for ubuntu
[http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")
you can use the edgy version, it works to install flash8, and then upgrade to the most recent version
bye

---

