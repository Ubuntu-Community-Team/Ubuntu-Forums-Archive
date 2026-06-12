---
title: "Moving HOME to another computer :( crash HELP"
date: 2007-11-05
forum: General Help
---

### Post by Borg on 2007-11-05
Main computer mobo just curled up its toes and join the great parrot in the sky.

Dug out the old shuttle back up computer and stuck a spare HDD in it, installed a clean install of Ubuntu and now have all the updates etc.

I really need the info and e mails from the now deceased computer. Well its HDD ( The HDD from the dead computer wouldn't boot up on the reserve one)

OK so going from

HDD2 will now be added as a slave

what commands or controls should I type into CMD to get all the contents of the old HDD onto, or into the new HOME partition on the shuttle ?


Please be gentale as this is the first time doing anything like this so if you could type out the commands without any long explanation that I probably wouldn't understand yet. I do pick up on things quickly but I'm a do and watch and learn type

Thanks

---

### Post by dcstar on 2007-11-06
> **Borg said:**
> Main computer mobo just curled up its toes and join the great parrot in the sky.

Dug out the old shuttle back up computer and stuck a spare HDD in it, installed a clean install of Ubuntu and now have all the updates etc.

I really need the info and e mails from the now deceased computer. Well its HDD ( The HDD from the dead computer wouldn't boot up on the reserve one)

OK so going from

HDD2 will now be added as a slave

what commands or controls should I type into CMD to get all the contents of the old HDD onto, or into the new HOME partition on the shuttle ?


Please be gentale as this is the first time doing anything like this so if you could type out the commands without any long explanation that I probably wouldn't understand yet. I do pick up on things quickly but I'm a do and watch and learn type

Thanks

Install the **pysdm** package, then use System-Administration-Storage Device Manager to mount the drive (you choose wherever you like for the mount point), and then just use Nautilus to copy files from the old /home to your new one.

Don't stuff around with the command line when there are perfectly good GUI tools to do the job.

---

