---
title: "History Files?"
date: 2008-03-27
forum: General Help
---

### Post by rayj00 on 2008-03-27
I have been using Ubuntu 6.10 Edgy for about a year now. I know I should upgrade but I have this one little teensy weensy problem. Over the past year I have installed a ton of stuff that
I use for my job, which is performing Vulnerability Assessments as well as penetration testing.

Because I figure I have an elephants memory, of course I neglected to document anything I installed!!

So, are there history files available that can tell me what I have done over the last year?

Please say yes and mean it!!!   :)

Thanks,

Ray

---

### Post by zvacet on 2008-03-27
**synaptic>file tab>history**

---

### Post by will103 on 2008-03-28
Or in the terminal:

sudo dpkg --list >> installed.txt

This will output a list of all installed packages to a text file.

For the future, run this command on your fresh install and then keep a copy of the output. Then, before upgrading to a new version run the command again and use the 'diff' command on the two text files (piped to another text file) to show you the list of software that has been installed since you installed the OS.

There are ways of outputing an installed files list and then using that to install over a fresh install of the OS, but if you are upgrading from an older version to a newer version it probably won't work (versions of packages will have changed etc). But here it is anyway:

sudo dpkg --get-selections > /backup/installed-software.log

Then:

dpkg --set-selections < /backup/installed-software.log

I have never tried this by the way!

Goodluck

will103

---

### Post by clarknova on 2008-03-28
Good on you for making contingency plans, but an upgrade should not remove anything (packages, configuration, or user data). Upgrading with synaptic (or apt) will bring all your programs up to the new version, warning you beforhand if there is anything installed that won't upgrade cleanly.

Be sure to check the upgrade instructions, however, as the method varies moving to/from some versions.

db

---

### Post by will103 on 2008-03-28
db, you are right. This is the better option.

will103

---

### Post by Herman on 2008-03-28
:)  Thanks for your post, will103, I like those commands. I do use the upgrade method sometimes, but more often I install a fresh new system beside the existing system, so those commands you suggested will be very useful to me.
Regards, Herman :)

---

