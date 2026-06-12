---
title: "Problems installing Office 2010&#8207;"
date: 2013-09-29
forum: General Help
---

### Post by Cosmos42 on 2013-09-29
Hello all,

I'm trying to install Microsoft Office 2010 on my ThinkPad  running Ubuntu 12.04.3 LTS (Precise) using Wine 1.7.  I've downloaded  Office, but when I try to install it I cannot enter the security key.   I've looked around and apparently people have resolved this problem by  having 'playonlinux' installed and installing 'richedit30.exe'.  The  problem when try to run richedit30.exe with Wine is that it is  apparently trying to install the .dll files I need into a directory that  may not exist.  This is the terminal output:

[FONT=Courier New]meyrle@maldoror:~/.wine/drive_c$  wine richedit30.exe fixme:setupapi:SetupDefaultQueueCallbackW  notification 262144 params 32f5c0,0[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]err:setupapi:SetupDefaultQueueCallbackW  copy error 0 L"C:\\users\\meryle\\Temp\\IXP000.TMP\\riched20.dll" ->  L"C:\\windows\\system32\\riched20.dll"[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:setupapi:SetupDefaultQueueCallbackW notification 262144 params 32f5c0,0[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]err:setupapi:SetupDefaultQueueCallbackW  copy error 0 L"C:\\users\\meryle\\Temp\\IXP000.TMP\\riched32.dll" ->  L"C:\\windows\\system32\\riched32.dll"[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]meryle@maldoror:~/.wine/drive_c$ fixme:service:QueryServiceConfig2W Level 6 not implemented[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:service:QueryServiceConfig2W Level 6 not implemented[/FONT]

It  prompts me for a user agreement, which I accept, but then it spits out  those errors and just hangs until I give it a ctrl+C.  

If I try to run the Office setup from the command line directly, this is what I get:
[FONT=Courier New]
[/FONT][FONT=Courier New]meryle@maldoror:~/.wine/drive_c$ wine X16-32007.exe [/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:service:QueryServiceConfig2W Level 6 not implemented[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:service:QueryServiceConfig2W Level 6 not implemented[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:advapi:EventRegister {8736922d-e8b2-47eb-8564-23e77e728cf3}, 0x2e034ec1, 0x2e0b3d78, 0x2e0b3d70[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:process:GetSystemDEPPolicy stub[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:process:SetProcessDEPPolicy (1): stub[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:advapi:EventRegister {8736922d-e8b2-47eb-8564-23e77e728cf3}, 0x101f57e7, 0x103a5908, 0x103a5900[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:system:SetProcessDPIAware stub![/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:msxml:dom_pi_get_attributes created dummy map for <?xml ?>[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:ole:NdrCorrelationInitialize (0x33d22c, 0x33ce2c, 1024, 0x0): stub[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT][FONT=Courier New]
[/FONT][FONT=Courier New]fixme:advapi:EventUnregister deadbeef: stub[/FONT]

Again, it prompts me for the product key, but does not allow me to enter it.  How do I go about resolving this issue?

Thanks!

---

