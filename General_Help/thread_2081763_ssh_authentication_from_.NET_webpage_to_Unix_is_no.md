---
title: "ssh authentication from .NET webpage to Unix is not working"
date: 2012-11-07
forum: General Help
---

### Post by tkota on 2012-11-07
My .NET website invokes a perl script to perform GIT operations on Gerrit server running UBuntu. In the perl script I connect using passwordless authentication to Gerrit server as below:
 
system ( "ssh [EMAIL="gitadmin@gerritserver.com"]gitadmin@gerritserver.com[/EMAIL] 'cd /xyz && git clone xxx' ");
 
I verified that ssh authentication is set up correctly between windows client and Unix server. This script works well from windows command prompt but when run from the context of website the page hangs at the ssh command execution. I have ensured that the user account the website and application pool are running under is the same as the user account ssh authentication is set-up for. Any idea why ssh is unable to authenticate from the website? Please suggest any alternatives, if any. I have been looking into password-specific authentication using ssh and host-based authentication. Is host-based authentcation possible between windows client and unix server?

---

