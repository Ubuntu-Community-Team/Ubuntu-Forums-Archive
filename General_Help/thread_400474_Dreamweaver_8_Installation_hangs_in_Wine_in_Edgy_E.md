---
title: "Dreamweaver 8 Installation hangs in Wine in Edgy Eft"
date: 2007-04-03
forum: General Help
---

### Post by Robeasts on 2007-04-03
I am trying to install Dreamweaver 8 on Edgy Eft using Wine-0.9.34.  The install starts fine, but after you pick the directory you want to install it in to (I just left it to the default) the install hangs.  Here is what is popping up in the terminal.

username@computer:~$ wine "/home/username/desktop/Dreamweaver8-en.exe"
fixme:advapi:CheckTokenMembership ((nil) 0x16be90 0x34e794) stub!
fixme:advapi:LookupAccountNameW (null) L"username" (nil) 0x34e2a4 (nil) 0x34e2a0 0x34e2ac - stub
fixme:advapi:LookupAccountNameW (null) L"username" 0x176bc0 0x34e2a4 0x176bd8 0x34e2a0 0x34e2ac - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
err:ole:TMStubImpl_Invoke invoke call failed with exception 0xc0000005 (-1073741819)
err:ole:xCall RpcChannelBuffer SendReceive failed, c0000005
err:msi:deformat_environment Unknown environment variable L"ALLUSERSPROFILE"
err:msi:msi_dialog_oncommand button click from nowhere 0xe5fd88 67108864 0x10050
err:msi:msi_dialog_oncommand button click from nowhere 0xe5fd88 67108864 0x10050
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:rpc:RpcImpersonateClient (0x64eac8): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x1f00000020
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:advapi:LookupAccountNameW (null) L"username" (nil) 0x34f398 (nil) 0x34f394 0x34f3a0 - stub
fixme:advapi:LookupAccountNameW (null) L"username" 0x173ae8 0x34f398 0x173b00 0x34f394 0x34f3a0 - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
err:ole:TMStubImpl_Invoke invoke call failed with exception 0xc0000005 (-1073741819)
err:ole:xCall RpcChannelBuffer SendReceive failed, c0000005
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveExistingProducts"
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x63af98): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x4700000011
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x63af98): stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x63c9a0): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x4700000011
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x63c9a0): stub
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
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x66c370): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x4700000011
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x66c370): stub

And that's where it hangs.  I tried to do some research on some of the errors but didn't really come up with anything.  Thanks in advance for any help.

---

### Post by Robeasts on 2007-04-03
Nevermind I came across an alternative way to install.

---

### Post by dannyboy79 on 2007-04-03
can you please more than that (post the solution you used to install) so that others can get around this issue as well. thank you.

---

### Post by diablo75 on 2007-04-07
Bump...

---

### Post by Robeasts on 2007-04-10
Here is the tutorial I used [http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/]("http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/")

I am using 6.10 and I got it work for me.

Here is a link to the [Dreamweaver wineHQ]("http://http://appdb.winehq.org/appview.php?iVersionId=3482&iTestingId=7934") for Ubuntu, you may find a solution here to some problems that may come up.

---

### Post by dannyboy79 on 2007-04-10
thank you for posting what you used to get it working. the open source community is grateful.

---

