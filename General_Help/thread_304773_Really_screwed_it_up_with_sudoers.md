---
title: "Really screwed it up with sudoers"
date: 2006-11-22
forum: General Help
---

### Post by JMO707 on 2006-11-22
I'll try to be as clear as I possibly can. 

I used a source.list with a big-red-warning over it saying that it will break my system ----> [http://www.ubuntuforums.org/showpost.php?p=1736227&postcount=35]("http://www.ubuntuforums.org/showpost.php?p=1736227&postcount=35")

Then upgrade packages, and then go back to my old sources.list

I didnt have any problem after that, except for an error every time I upgrade a package. The packages *were* upgraded, but with that error at the end of the process.

The problem was something with a "mepis auto 6.0" package that was installed during the upgrade with the big-red-warning list. Then I went to Synaptic, and stupidly chose to remove it _completely_. 

Now, the drama beggin when I couldnt open Synaptic after that. It said me that the sudoers file cannot be found.
I looked for an answer on the forums, and I think I found it (sorry, cant find the thread right now), but here comes the strawberry of the cake: seemengly my root password doesnt work.

Now, I rebooted my computer, and "rc2" & "rcS" are terminated or something like that. The splash screen doesnt load completely, and insted of my computer name it show something like: "(none)user:" in the login screen.

...

I hear advices =(

---

### Post by ehird on 2006-11-22
I do wonder what you expected from a list with that message stamped on it.

---

### Post by jimbob on 2006-11-22
I would suggest a clean re-install at this point.

---

### Post by justin whitaker on 2006-11-22
That Mepis package is probably one of the core packages for Mepis Linux, which is a mostly different distro-you probably overwrote a bunch of mission critical stuff with that. 

Its times like these that I save what I can, and reinstall.

---

