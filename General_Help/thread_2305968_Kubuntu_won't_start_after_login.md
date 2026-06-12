---
title: "Kubuntu won't start after login"
date: 2015-12-10
forum: General Help
---

### Post by pwabrahams on 2015-12-10
I recently clobbered my Kubuntu 14.10 system, so I decided just to reinstall Kubuntu 14.04.  However, I saved my old /home directory and did not reformat the Kubuntu partition.  That way I preserved my old home directory.  

I've been able to recreate my old login identity and, using usermod, associate my old home directory with my recreated identity.  But when I log into that Identity from the login screen, I quickly get bounced back to the login screen where I just was.  So there's some initial action after login that should be happening but isn't.  My home directory looks just like it did in my old 14.10 system, including the dotfiles.  What might that initial action be, and how can I cause it to take place after login?  I have a second login with administrative privileges that I use to get going and to do whatever I need to do.

---

### Post by SeijiSensei on 2015-12-10
Typically it's an ownership problem.  Do you have the same user IDs on both systems?  If you're the only user, that should be 1000.  Also check the permissions of .kde in your home directory.

Create a new user from the command prompt with the [adduser]("http://linux.die.net/man/8/adduser") command and try logging in with that.  If that works, the problem lies in your home directory's permissions.

---

