---
title: "matlab hangs up when using the &quot;print&quot; command to export figures"
date: 2017-01-08
forum: General Help
---

### Post by gianluca3 on 2017-01-08
Hi,

Matlab hangs up when using the "print" command to export figures. I can not interrupt the software and I have to kill the process.

My script makes simple 3d graphics and uses some additional functions written by me. What is weird is that the problem is systematic, however, the same functions, used to generate ather plots, do not causes any problem.
The problem arises with the print command, no matter the option used. Matlab goes in "Busy" state but it allows me to, e.g., edit the script.

I tried to add before/after the print command the pause and/or drawnow commands but without success as suggested here ([http://undocumentedmatlab.com/blog/solving-a-matlab-hang-problem](http://undocumentedmatlab.com/blog/solving-a-matlab-hang-problem)).

```
uname -a
Linux laresa 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

```
ver
----------------------------------------------------------------------------------------------------
MATLAB Version: 8.3.0.532 (R2014a)
MATLAB License Number: 405329
Operating System: Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64
Java Version: Java 1.7.0_11-b21 with Oracle Corporation Java HotSpot(TM) 64-Bit Server VM mixed mode
----------------------------------------------------------------------------------------------------
```

Any help is welcome
g.

---

