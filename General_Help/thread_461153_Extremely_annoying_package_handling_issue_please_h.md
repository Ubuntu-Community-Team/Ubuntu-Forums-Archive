---
title: "Extremely annoying package handling issue: please help!"
date: 2007-06-01
forum: General Help
---

### Post by floke on 2007-06-01
Tried to install a tron game (armagetronad) but the package wouldn't load; error messages about file being corrupted or me not having privileges to load it.  Anyway, whenever I start up synaptic or try to use apt-get, it just chucks an error and says I need to reinstall package armagetronad but there is no archive for it. Can't update, add or remove any programs. Have tried to reinstall but get the same error. Seem to be very stuck. 

Any thoughts?

---

### Post by MoLE on 2007-06-09
Given your number of posts, I hope this isn't disrespectful, but would you be kind enough to post the error you get when try to ```
sudo aptitude reinstall armagetron
```.

---

### Post by grekei on 2007-06-10
This sounds like a problem I had some time ago with a package stuck in synaptic the attached link includes a solution that I fixed it with.Hope it helps
[http://ubuntuforums.org/showthread.php?t=404876&page=2](http://ubuntuforums.org/showthread.php?t=404876&page=2)
This was the answer that worked

OK, it is obvious that taskjuggler is the problem and all of the above help was fruitless.

Open a console and type in the following:

Code:

sudo gedit /var/lib/dpkg/status


Search through the file for any reference to taskjuggler and CAREFULLY delete all of that entry.

Save the file

Code:

sudo apt-get update

Your problem should now be solved, as Synaptic can no longer see this errant package and as disk space is taken up, it will be over-written.

---

### Post by floke on 2007-06-10
Mole / Grekei

Many thanks for your replies. The issue was solved a week ago by a complete reinstall!
I had spent the entire weekend configuring a mate's old Tecra 8200 for Kubuntu and it was perfect, then I installed Armagettron and it broke, 2 hours before he was due to pick it up! Rather than wait around for replies, I decided to reinstall and have done, since time was pressing. Still, I will bear this thread and the solutions offered in mind for future reference, so your replies certainly weren't wasted: I was very curious to know how it might have been solved properly.

Thanks again.

---

