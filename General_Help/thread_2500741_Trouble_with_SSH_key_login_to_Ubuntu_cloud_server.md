---
title: "Trouble with SSH key login to Ubuntu cloud server"
date: 2024-09-11
forum: General Help
---

### Post by browb7900 on 2024-09-11
I’m having problems ssh-ing into my Linode server running Ubuntu 24.04 from PuTTY, I have created a public private key pair, told putty which private key (.ppk) to use, copied my public key manually into my .ssh/authorized key file, made sure there wasn’t a newline char at the end. However, I’m still getting putty telling me that its key was rejected. Does anyone have any ideas on what I can do?

---

### Post by TheFu on 2024-09-11
Are the file and directory permissions on the remote server correct?  ssh is picky about those things.
I haven't used putty in about 15 yrs, but I do remember they had an odd ssh-key format that was different from what all Unix/Linux and even the built-in ssh on Win10+ uses.

If you are using putty on a Linux client system, you are doing things the hard way.  Use a terminal, any will do, and use **ssh -vv user@remote-host** to see what the issue might be.  If that isn't clear, add another 'v' to get more verbosity.

---

