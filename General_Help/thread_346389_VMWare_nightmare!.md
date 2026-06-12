---
title: "VMWare nightmare!"
date: 2007-01-25
forum: General Help
---

### Post by mistermax on 2007-01-25
I tried to remove Vmware player but tried to uninstall the /etc/init.d entries first, then player. My box locked up and I had to restart, now I've got a situation where after running dpkg to fix synaptic, then uninstalling the rest of VMWare-player, I can't get VMWare server to run..

There is a log that says this:

Jan 25 21:38:53: vmui| Log for VMware Server Console pid=5409 version=1.0.1 build=build-29996 option=Release
Jan 25 21:38:53: vmui| Using log file /tmp/vmware-max/ui-5409.log
Jan 25 21:38:53: vmui| HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
Jan 25 21:38:53: vmui| HAL05LoadHALLibraries: Could not dlopen libdbus-1.so.1 or libdbus-1.so.2.
Jan 25 21:38:53: vmui| VmdbVmCfg_GetDictionary: could not load dictionary file /home/max/.vmware/preferences.
Jan 25 21:38:53: vmui| VMClient_AllocVMClient failed: Message, Cannot open file "/home/max/.vmware/preferences": Permission denied.
Jan 25 21:38:53: vmui| 
Jan 25 21:38:53: vmui| Unable to alloc client: Cannot open file "/home/max/.vmware/preferences": Permission denied.
Jan 25 21:38:53: vmui| 
Jan 25 21:38:53: vmui| Backtrace:
Jan 25 21:38:53: vmui| Backtrace[0] 0xbfacaa88 eip 0x827ba00 
Jan 25 21:38:53: vmui| Backtrace[1] 0xbfacaea8 eip 0x827cb25 
Jan 25 21:38:53: vmui| Backtrace[2] 0xbfacaec8 eip 0x8078c68 
Jan 25 21:38:53: vmui| Backtrace[3] 0xbfacaef8 eip 0x8091ab4 
Jan 25 21:38:53: vmui| Backtrace[4] 0xbfacb158 eip 0x8086f65 
Jan 25 21:38:53: vmui| Backtrace[5] 0xbfacb1f8 eip 0x807a585 
Jan 25 21:38:53: vmui| Backtrace[6] 0xbfacb4f8 eip 0x8078bd9 
Jan 25 21:38:53: vmui| Backtrace[7] 0xbfacb558 eip 0xb70898cc 
Jan 25 21:38:53: vmui| Backtrace[8] 00000000 eip 0x80788c1 
Jan 25 21:38:53: vmui| Msg_Post: Error
Jan 25 21:38:53: vmui| [msg.log.error.unrecoverable] VMware Server Console unrecoverable error: (vmui)
Jan 25 21:38:53: vmui| Unable to alloc client: Cannot open file "/home/max/.vmware/preferences": Permission denied.
Jan 25 21:38:53: vmui| 
Jan 25 21:38:53: vmui| [msg.panic.haveLog] A log file is available in "/tmp/vmware-max/ui-5409.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.linux] 
Jan 25 21:38:53: vmui| To collect files to submit to VMware support, run vm-support.
Jan 25 21:38:53: vmui| [msg.panic.response] We will respond on the basis of your support entitlement.
Jan 25 21:38:53: vmui| ----------------------------------------


I'm lost here. I've tried reinstalling VMWare player to see if it would sorts it. Not very scientific and it didn't work...

Any suggestions?

---

### Post by yopnono on 2007-01-25
> Cannot open file "/home/max/.vmware/preferences": Permission denied.

Try to remove the (dot).vmware folder in your home folder, its hidden CTRL+H to unhide them. Or change the permission on the .vmware folder

---

### Post by coastingbicycle on 2007-02-23
You can try changing ownership of .vmware/preferences with:

sudo chown *username* /home/*username*/.vmware/preferences

---

