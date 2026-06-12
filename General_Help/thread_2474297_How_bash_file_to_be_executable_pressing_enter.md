---
title: "How bash file to be executable pressing enter ?"
date: 2022-04-25
forum: General Help
---

### Post by aug7744 on 2022-04-25
Bash file working correctly in terminal.
Is possible using mouse pointer clicking in an bash file run in same way is done using terminal ?
If yes run being sudo (bash file checking disks) ?

Thanks for read.
Have an nice week.

---

### Post by vanadium on 2022-04-26
Running a script from the file manager by hitting <Enter> is deprecated. when double-clicking a script, the file manager will do the logical thing: open the file in an appropriate default application, which, in this case, is a text editor.

When running a script from a file manager, one cannot give standard input nor does one see standard output. For many scripts, running them this way therefore does not make sense. In addition, this renders it impossible to run with sudo because there is no way you can enter the password.

So no, run your script from within a terminal.

If there is something specific you want to achieve which you think could be solved by clicking a script, then ask directly. Good suggestions will come, but they will not involve clicking the script in the file manager.

---

### Post by TheFu on 2022-04-26
I'd be surprised if some file managers don't allow running programs by clicking or you could setup a file type that gets registered to run **sudo bash {script}** for you.  If it is just gathering information, you could modify the sudoers settings to allow your userid to run that script without any password.  The sudoers manpage explains how.

And I'd bet you could create a .desktop file that will show up in the menus (and be searched using normal methods) that does sudo bash {script} too.  .desktop files are just text files to let the menu system know what to show and what to run. Pick almost any example on the system, copy it, and modify it for your script needs.

Doesn't policykit include some GUI sudo program?  I'm a terminal-guy, but certainly there are example desktop files ... perhaps for gparted or fdisk or the user-administration tool which will have an example exec line in the .desktop to model after?

---

### Post by aug7744 on 2022-05-06
Perhaps can work if the creating an start menu link pointing to an bash file ?
I will try create one and after post the results.

---

