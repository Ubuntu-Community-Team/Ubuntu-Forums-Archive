---
title: "Suddenly can't log in"
date: 2007-06-02
forum: General Help
---

### Post by NicholasWMR on 2007-06-02
This morning I discovered that I can't log into Gnome using the username and password I've always used and had just used minutes before.

I've tried to boot into "single" mode using grub and then changing the password using "passwd".   It doesn't help. I still can't log in.   I've tried using "passwd" to delete the password.  I still can't log in.

Is there some other password repository that I don't know about.  Is there another way to change the password?  Why all of a sudden am I not able to log in?  I sincerely doubt that it is prank or somesuch.  There is no one in the house who would consider doing such a thing.

---

### Post by taurus on 2007-06-02
Is there an error message when you try to log in with your username and password?  Another possibility is that you are running out of disk space.

Boot into recovery mode from GRUB menu and post the output of this command here.

```
df -h
```

---

### Post by NicholasWMR on 2007-06-02
I ran df -h to determine how much disk space I have available.  

/dev/sda1  11 G of 71 G used (15% full)

None of varrun, varlock, procbususb, udev, devshm, lrm were more than 4% full.

I get a dialog saying "authentication failed" when I try to log into Gnome from the default Ubuntu log-in screen.  Previously I'd recalled a red text message above the username/password edit box if I mistyped my password.  Now I get a dialog which I have to dismiss.

---

### Post by NicholasWMR on 2007-06-02
:KS Further investigation that from the recovery command prompt I can "login user_name", enter the password and have it accepted.    This suggest the problem is in the Gnome authentication module.

I investigated further and discovered that the problem was with the file "/etc/pam.d/gdm".

I had added a couple of lines to the end to support "libpam-keyring" but had made a mistake.  A comment character had been omitted.  When I restored the comment character I could log in without problem.

Thanks for the help taurus!

Nicholas

---

