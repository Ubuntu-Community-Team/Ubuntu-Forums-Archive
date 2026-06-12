---
title: "any gui &quot;System monitor&quot; app with disk  IO monitor option ?"
date: 2019-06-17
forum: General Help
---

### Post by anderbuntu on 2019-06-17
Hi

I am troubleshooting now how to import to Ubuntu gui app "System monitor" DISK IO option tab.
Yes, there is option to manually add tab for disk IO performance, however only works for specified device ( sda, sdb..), which must be configured before...
So this is not working for temporary connected USB disk devices...
DO you have any idea how to import this function to system monitor ?  ( will show IO disk read/ write for all currently connected devices )
Something like it works  in Windows Task manger.

BR

Andrew

---

### Post by rbmorse on 2019-06-17
take a look at gkrellm.  It's in repository. 

After installation, right click on it's window, select "Builtins" from the monitors column on the left, then "Disk".  Should do what you want.

---

