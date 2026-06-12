---
title: "ntlm_auth"
date: 2007-09-03
forum: General Help
---

### Post by trantor on 2007-09-03
Hi all,

trying to run in wine an application gives following error:

err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >=3.0.25 is in your path.

After this error my application says there was an SQL error.
This application works through an ODBC connection to a Windows 2003 SQL server.

I've just installed SQUID, but  i am not able to find ntlm_auth in /usr/bin/ nor in /usr/local/bin/  and i think this is the problem......

Another application that works with the same server through ADO connection works just fine. 

Hope someone could help....or give me advices about ntlm_auth.

Thanks in advance for your help

---

### Post by trantor on 2007-09-03
Ok, for Debian (I'm running UBUNTU 6.06) ntl_auth comes together with WINBIND.

But i'm still in trouble because ntlm_auth version 3.0.22 is too old for Wine 0.9.44. I need ntlm_auth 3.0.25 but i have just got the latest version of WINBIND.

And so please, how can i install a newer version of WINBIND or a new version of ntlm_auth?

Any idea out there?

---

