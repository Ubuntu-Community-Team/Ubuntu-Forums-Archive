---
title: "Problems installing OfficeXP under Wine"
date: 2005-06-09
forum: General Help
---

### Post by thebasard on 2005-06-09
The install of Office XP starts out fine but during the "copying files" phase it crashes.  Here's the output from Wine:

fixme:actctx:CreateActCtxW stub!
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0xc8
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x54
fixme:shell:SHELL32_DllCanUnloadNow stub
fixme:shell:SHELL32_DllCanUnloadNow stub
fixme:imm:ImmGetContext (0x10060): stub
fixme:powermgnt:SetThreadExecutionState (0x80000001): stub, harmless.
fixme:msg:BroadcastSystemMessageA (00000000,00000001,00000219,00000022,80008558): stub!
fixme:powermgnt:SetThreadExecutionState (0x80000000): stub, harmless.


Anyone have any ideas for a fix?

---

### Post by xao on 2005-06-09
Why not try OpenOffice.org? I have found that i prefer it over MS Office, and that way you don't have the pain of slowdown from using wine...

jsut my humble opinion, though...

---

### Post by thebasard on 2005-06-09
Yep.  I love OpenOffice and use it every day at work.  The only reason I wanted to install MS Office was for Outlook.  I'm currently using Evolution v2.2.1.1 which I also love but I'm having issues with Exchange connector - due to known bugs.

Ubuntu Rocks!

~former SuSE user~

---

### Post by xao on 2005-06-10
hrm... that makes sense. i remember being unable to get evolution to work with exchange, so i switched to thunderbird. as far as the wine error goes, ill have a look, though i am about to go out of town, so it may be a few days.

---

### Post by kiddyfurby on 2005-06-10
is that pure wine or crossover ?

---

### Post by FLeiXiuS on 2005-06-10
OpenOffice is a good alternative if not.  Give crossover a try. :-)

---

