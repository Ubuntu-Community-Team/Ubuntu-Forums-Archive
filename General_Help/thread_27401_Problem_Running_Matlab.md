---
title: "Problem Running Matlab"
date: 2005-04-15
forum: General Help
---

### Post by Jamesia on 2005-04-15
I recently installed Matlab in Hoary. For some reason, upon executing the program, I get the following error statement...


> root@jamesia:/home/sammy # /usr/local/matlab7/bin/scripts/matlab
---------------------------------------------------------------------------
Warning: Cannot locate Java Runtime Environment (JRE) . . .

         1. Either a correct JRE was not available for redistribution when
            this release was shipped, in which case you should refer to the
            Release Notes for additional information about how to get it.

         2. Or you have tried to use the MATLAB_JAVA environment variable
            to specify an alternate JRE, but MATLAB cannot find it.  Please
            run 'matlab -n' to determine what value you are using for
            MATLAB_JAVA and fix accordingly.
---------------------------------------------------------------------------

    matlab: No MATLAB bin directory for this machine architecture.

           ARCH = glnx86



Anyone have any idea what this means?

---

### Post by ijsje on 2005-04-16
Is the java runtime environment installed?
It's not installed by default, you can find installation instructions here:

[http://www.ubuntuguide.org/#jre]("http://www.ubuntuguide.org/#jre")

---

