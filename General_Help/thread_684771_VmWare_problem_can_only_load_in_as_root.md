---
title: "VmWare problem: can only load in as root"
date: 2008-02-01
forum: General Help
---

### Post by Yellow Galactic Sun on 2008-02-01
Hello there

I use Ubuntu 7.04 feisty.

I have a problem when starting vmware from the terminal. I can only start the program when being root. When I try to log in without the sudo command I get this error report(.log):

Feb 01 19:40:14: vmui| Log for VMware Server pid=6257 version=1.0.4 build=build-56528 option=Release
feb 01 19:40:14: vmui| Using log file /tmp/vmware-dries/ui-6257.log
feb 01 19:40:14: vmui| HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
feb 01 19:40:14: vmui| HAL05LoadHALLibraries: Could not dlopen libdbus-1.so.1 or libdbus-1.so.2.
feb 01 19:40:15: vmui| VmdbVmCfg_GetDictionary: could not load dictionary file /home/dries/.vmware/preferences.
feb 01 19:40:15: vmui| VMClient_AllocVMClient failed: Message, Cannot open file "/home/dries/.vmware/preferences": Toegang geweigerd.
feb 01 19:40:15: vmui| 
feb 01 19:40:15: vmui| Unable to alloc client: Cannot open file "/home/dries/.vmware/preferences": Toegang geweigerd.
feb 01 19:40:15: vmui| 
feb 01 19:40:15: vmui| Backtrace:
feb 01 19:40:15: vmui| Backtrace[0] 0xbfa64bb8 eip 0x827b840 
feb 01 19:40:15: vmui| Backtrace[1] 0xbfa64fd8 eip 0x827c965 
feb 01 19:40:15: vmui| Backtrace[2] 0xbfa64ff8 eip 0x8078c68 
feb 01 19:40:15: vmui| Backtrace[3] 0xbfa65028 eip 0x80918fa 
feb 01 19:40:15: vmui| Backtrace[4] 0xbfa65288 eip 0x8086dc5 
feb 01 19:40:15: vmui| Backtrace[5] 0xbfa65328 eip 0x807a57e 
feb 01 19:40:15: vmui| Backtrace[6] 0xbfa65628 eip 0x8078bd9 
feb 01 19:40:15: vmui| Backtrace[7] 0xbfa65688 eip 0xb6f8eebc 
feb 01 19:40:15: vmui| Backtrace[8] 00000000 eip 0x80788c1 
feb 01 19:40:15: vmui| Msg_Post: Error
feb 01 19:40:15: vmui| [msg.log.error.unrecoverable] VMware Server unrecoverable error: (vmui)
feb 01 19:40:15: vmui| Unable to alloc client: Cannot open file "/home/dries/.vmware/preferences": Toegang geweigerd.
feb 01 19:40:15: vmui| 
feb 01 19:40:15: vmui| [msg.panic.haveLog] A log file is available in "/tmp/vmware-dries/ui-6257.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.linux] 
feb 01 19:40:15: vmui| To collect files to submit to VMware support, run vm-support.
feb 01 19:40:15: vmui| [msg.panic.response] We will respond on the basis of your support entitlement.
feb 01 19:40:15: vmui| ----------------------------------------

"Well why don't you start the program as root then?" you could think. Well; my cd-rom configuration as root is not the same as my account. Something with etc/fstab that is not set up in order I assume. And vmware detects the hardware for root and not for my account. 

The most practical thing would be that I would be able to log in with my user account instead of root so the hardware works on Vmware and so I don't have to mess around being root....

What should I do? Any help is welcome!

---

