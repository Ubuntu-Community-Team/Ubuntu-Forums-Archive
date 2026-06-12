---
title: "Migrate old ubuntu configuration to new install"
date: 2013-01-21
forum: General Help
---

### Post by Daniel Sanz on 2013-01-21
Hello community

I have been trying Ubuntu since 2 years ago, I want to do a new install of ubuntu but I have a problem.
Is there a way to keep all the configurations and software installs to set up in a new install of ubuntu? I do not have great skills with Linux and I do not want to lose all my effort of these two years.

Thanks

---

### Post by hwttdz on 2013-01-21
Are you more talking about your user preferences or packages installed/changes to default configuration of packages?

**User preferences** are overwhelmingly (should be universally) stored in the users home directory.  Generally in hidden files and folders.  Try changing to your home directory and doing "ls -A" it will show you all sorts of configuration files & folders.  If you copy your current home directory over to your new machine you'll save most of that (some programs when updated to a new version change how they store preferences and aren't so great at migrating old preferences).

It's pretty easy to make a list of **installed packages**, however some packages may have changed names between then and now.  But "dpkg --get-selections" will get you a list of the packages currently installed.  If you save that you should be able to reinstall the vast majority of those programs in your new install.

Finally **system configuration** changes, these are things you might have done using the sudo command.  Generally stored in /etc & sub-directories, but there are far more exceptions here than elsewhere.  I might try an in place upgrade (after backing up ~), and record the packages that it says you have changed configs for, and then saving all those old modified configs before wiping and installing from scratch.

---

### Post by Daniel Sanz on 2013-01-21
Thank you hwttdz, the information you provide me is what I was looking for. I will try this and do a new install.

---

