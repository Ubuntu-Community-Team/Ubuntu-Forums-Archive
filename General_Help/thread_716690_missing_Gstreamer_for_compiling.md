---
title: "missing Gstreamer for compiling"
date: 2008-03-06
forum: General Help
---

### Post by Dandee on 2008-03-06
An error message "**no Gstreame**r" is generated when using 'configure' preparatory to compiling. The program being compiled is "pitfdll" and the configure program has been used successfully on another program. All gstreamer files are installed including libgtreamer files and also build-essential . I can't figure out what the missing gstreamer file may be. Help will be greatly appreciated.

---

### Post by kuja on 2008-03-06
You probably need libgstreamer0.10-dev and libgstreamer-plugins-base0.10-dev. When compiling you always need the -dev packages installed. Another handy thing for you,if practical at the time, is "apt-get build-dep package" if its a package in the repository (even if you're building a different version of it), it'll fetch any packages that you would need to do the build.

---

### Post by Dandee on 2008-03-06
Thanks, Kuja, for your suggestions. I have installed libstreamer0.10-0, -dbg, dev (3 files) and also libstreamer-plugins-base0.10-dev (2 files of differing kbs but same title) and all are 0.10.14 lubuntu3 in the synaptic manager list. Regrettably, these do not seem to solve the problem.

---

