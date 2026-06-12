---
title: "Help with bash script to run VNC over SSH"
date: 2008-04-29
forum: General Help
---

### Post by musikgoat on 2008-04-29
Hello,

I'm attempting to make a simple bash script but am failing in getting the script to run in the background. 

Here is the script:
```
#!/bin/bash
# Start VNC session over SSH

ssh -X -f tpotter@musikgoat.com -p 29222 -N -L 1111:192.168.1.99:5900  
vncviewer localhost::1111 &
exit 0

```

I have tried 2>&1 and that and the above script run properly, but in the shell where I run the script, it sits there awaiting the end of the VNC session.  

I would like it to drop to the background and I thought & should have done that.  

Thanks for any help possible.

-tim
ba

---

