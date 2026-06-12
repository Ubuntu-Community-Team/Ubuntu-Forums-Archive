---
title: "RDP stopped working after upgrade from 22 to 24"
date: 2024-10-20
forum: General Help
---

### Post by t-var-s on 2024-10-20
Hello ):P

I've a mini PC on my LAN that I can only rarely have physical access to, so I've been using the default remote desktop service that comes with Ubuntu to connect to it from my laptop using the Jump Desktop client. I also have a samba share running from it and I can access it through SSH. 

With a recent upgrade from Ubuntu 22 to 24, everything works fine except RDP. Jump Desktop tries to connect but stops and logs: 
Bad NTLM message signature
ntlm verify message NtlmChallenge failed!
ntlm_process failed
rdpc_credssp_process_tsrequest failed
rdpc_credss_process_packet failed

On the Ubuntu side, everything looks ok(?), grdctl status gives status enabled in the matching port, but I'm not sure what else to check. Any ideas?

---

