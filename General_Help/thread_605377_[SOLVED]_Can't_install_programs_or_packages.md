---
title: "[SOLVED] Can't install programs or packages?"
date: 2007-11-07
forum: General Help
---

### Post by some_los3r on 2007-11-07
Sorry, I'm a Ubuntu noob. But anyways, I can't seem to install any packages. I know how to, but it just never works for me. I got to 'Synaptic Package Manager' and try to install a package and it does not work. For instance, I just tried to install "acidrip" First, I found the acidrip package, then I double-click it to mark for installation and then it loads for a second. Then it says "The chosen action also affects other packages. The following changes are required in order to proceed." And then I click "Mark". Then an error window pops up and says "The following have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.
acidrip: 
 Depends: mplayer
 Depends: mencoder but it is not going to be installed"

Sorry again, I'm an Ubuntu noob and have no idea what to do.
Thanks.

---

### Post by rsambuca on 2007-11-07
You probably just need to activate all of your repositories.  Go to "System -> Administration -> Software Sources".  On the first tab, make sure all of the repositories are checked off, then reload the sources and try to install your program again.

---

### Post by some_los3r on 2007-11-07
Oh wow! Yup, that was it! Thanks so much! :-D

---

### Post by rsambuca on 2007-11-07
Good stuff!  Mark the thread solved. :)  (in the thread tools)

---

