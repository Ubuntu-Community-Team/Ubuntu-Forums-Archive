---
title: "Destroyed my sudo!"
date: 2007-01-07
forum: General Help
---

### Post by GuerrillaWon on 2007-01-07
I tried editing my sudoers file so that firestarter starts up upon system boot.

I changed the file to read and write to make these changes, I then rebooted not changing it back.

Now I can't use sudo I get this error...

sudo: /etc/sudoers is mode 0640, should be 0440

So in order to change permissions, I have to use sudo, which doesn't work, and as far as I know I'm locked out of being able to perform my administrator commands.

I was hoping someone might have a fix or workaround for this, as I've only read the Ubuntu Desktop documentation and there's no information about this problem there. I've also done a search here on the forums and came up with nothing.

---

### Post by melancholeric on 2007-01-07
Boot in recovery mode to change it.

---

### Post by GuerrillaWon on 2007-01-07
I'm sorry but I'm not sure how to do so.

I boot off the cd and I'm not presented with the Boot: line.

I've tried several different things in order to add this command to the boot up but I've been unsuccessful.

[edit]

ok found it, but rescue mode seems to do a reinstall? Is this necessary?

---

### Post by GuerrillaWon on 2007-01-07
Ok i'm a bit closer, but I don't know the command line to use to change the /etc/sudoers file to read only and am having a bit of a hard time finding the command line perimeters. 

Can anyone out there throw me this last bone?

---

### Post by melancholeric on 2007-01-07
chmod 440 /etc/sudoers

---

### Post by Arisna on 2007-01-07
In future, you should use the command `visudo' to edit your sudoers file.  This will eliminate the need to change permissions on it and give you syntax checking.

---

