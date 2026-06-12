---
title: "JRE error from NGINX on 16.04"
date: 2016-10-06
forum: General Help
---

### Post by szegedin74 on 2016-10-06
I recently upgraded to 16.04. When I go to install the Java JRE I get: 

```
Job for nginx.service failed because the control process exited with error code. See "systemctl status nginx.service" and "journalctl -xe" for details.invoke-rc.d: initscript nginx, action "start" failed.
dpkg: error processing package nginx-full (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nginx-full
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

I tried reinstalling nginx. I get the same error. Also tried stopping Apache. No difference. 

Any ideas?

---

