---
title: "Can't install programs, update Ubuntu or run apt-get update"
date: 2014-08-15
forum: General Help
---

### Post by draconastar on 2014-08-15
I'm having an issue where I'm unable to install any programs.  When I try, it tells me "Requires installation of untrusted packages".  The advice I read said to try sudo apt-get update followed by sudo apt-get upgrade.  apt-get update comes back with almost all 404 errors, as does upgrade.  I cannot run or change settings in the update manager, as when I try to run it I get "failed to download repository information".  I've been trying to find a solution to this issue, but all of them tell me to either update Ubuntu which I can't do, or it tells me to remove the offending repositories from source.list, but virtually all of them return with a 404 error.  I'm running 13.04 at the moment.  The only thing I have noticed is that the version listed in my sources.list file is 12.10.  Either way I can't seem to update or install any programs.  

Any ideas?

---

### Post by claracc on 2014-08-15
Both ubuntu 13.04 and 12.10 have reached its end of life support, so the repositories have been removed from the server, for this reason you cannot find them and you cannot install packages. Also, you won't receive any update since the EOL ubuntu.

I suggest to backup your files and install a supported release as ubuntu 12.04 or 14.04.

---

### Post by draconastar on 2014-08-15
Thanks for your response.  For some reason nowhere that I looked was reporting that my version was EOL.

---

### Post by Karlchen on 2014-08-15
[Releases -> go down to section "End of Life"](https://wiki.ubuntu.com/Releases)

---

