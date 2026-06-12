---
title: "Wine &amp; Chessmaster 10"
date: 2007-03-16
forum: General Help
---

### Post by AllanP on 2007-03-16
The only thing stopping me from becoming 100% Ubuntu is my Chessmaster game. I installed Wine; ran winecfg. The install of Chessmaster appears to be doing ok and gets about 1/3rd of the way through and stops with the error: "Error - 1603 Fatal error during installation consult Windows installer. I know others have installed this successfully so any help would be appreciated.
Here is more data from terminal:
err:msi:ACTION_InstallFiles Failed to copy L"Z:\\home\\allan\\chess\\Data\\TData\\" to L"c:\\Program Files\\Ubisoft\\Chessmaster 10th Edition\\Data\\TData\\JWAudio.dat" (5)
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0xd00000023
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2100-00000d000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2100-00000d000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2100-00000d000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-2100-00000d000000}

---

### Post by zvacet on 2007-03-17
I don´t know if it is going to work but you can try it.Put your exe in .wine>c drive>program files
In terminal
```
winefile
```
C>program files>your exe>double click

---

### Post by AllanP on 2007-03-17
Thanks for the reply. I'll give it a try. I've switched HD connectors now on another Ubuntu but, I'll hang on to your suggestion.

---

