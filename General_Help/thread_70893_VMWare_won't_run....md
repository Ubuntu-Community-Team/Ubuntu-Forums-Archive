---
title: "VMWare won't run..."
date: 2005-10-01
forum: General Help
---

### Post by Adam Lee on 2005-10-01
> Oct 01 11:51:29: vmui| Log for VMware Workstation pid=8986 version=5.0.0 build=build-13124 option=Release
Oct 01 11:51:29: vmui| Using log file /tmp/vmware-adam/ui-8986.log
Oct 01 11:51:29: vmui| VmdbVmCfg_GetDictionary: could not load dictionary file /home/adam/.vmware/preferences.
Oct 01 11:51:29: vmui| VMCLient_AllocVMClient failed: (null)
Oct 01 11:51:29: vmui| Unable to initialize host: Message
Oct 01 11:51:29: vmui| Backtrace:
Oct 01 11:51:29: vmui| Backtrace[0] 0xbfffeae8 eip 0x8217d25 
Oct 01 11:51:29: vmui| Backtrace[1] 0xbfffeb08 eip 0x80736e8 
Oct 01 11:51:29: vmui| Backtrace[2] 0xbfffec98 eip 0x808e2df 
Oct 01 11:51:29: vmui| Backtrace[3] 0xbfffee98 eip 0x80889d6 
Oct 01 11:51:29: vmui| Backtrace[4] 0xbfffef18 eip 0x80750d7 
Oct 01 11:51:29: vmui| Backtrace[5] 0xbffff238 eip 0x807369f 
Oct 01 11:51:29: vmui| Backtrace[6] 0xbffff298 eip 0xb70828c8 
Oct 01 11:51:29: vmui| Backtrace[7] 00000000 eip 0x8073451 
Oct 01 11:51:29: vmui| Msg_Post: Error
Oct 01 11:51:29: vmui| [msg.log.error.unrecoverable] VMware Workstation unrecoverable error: (vmui)
Oct 01 11:51:29: vmui| Unable to initialize host: Message
Oct 01 11:51:29: vmui| [msg.panic.haveLog] A log file is available in "/tmp/vmware-adam/ui-8986.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.linux] 
Oct 01 11:51:29: vmui| To collect files to submit to VMware support, run vm-support.
Oct 01 11:51:29: vmui| [msg.panic.response] We will respond on the basis of your support entitlement.
Oct 01 11:51:29: vmui| ----------------------------------------

Hi! I installed VMWare 5 on 5.04 last day and getting this error.
I did the vmware any any patch 94.

Help will be much appreciated.

---

### Post by yage on 2005-10-01
It looks like you have vmware installed from before... and older version perhaps?
If not, look in the file mentioned in your error log to see what the problem is.

---

