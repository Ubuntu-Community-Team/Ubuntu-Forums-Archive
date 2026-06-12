---
title: "Problem with /etc/sudoers file"
date: 2007-04-17
forum: General Help
---

### Post by ramjet_1953 on 2007-04-17
Hi, Guys!

I modified my /etc/sudoers file, to allow firestarter to load automatically as per the instruction on the firestarter site and when I re-booted, it then said that there was an error in the file.

So I just went back and deleted the extra line that I had inserted (roger ALL=NOPASSWD: /usr/bin/firestarter)

I then re-saved the file and I still have problems, with no sudo privileges and the console shows this error:

sudo: /etc/sudoers is mode 0640, should be 0440

Where do I go from here?

Regards,
Roger :)

---

### Post by anaconda on 2007-04-17
Boot to recovery mode, and type:
cd /etc
chmod 440 sudoers

and this propably isn't necessary, but:
chown root:root sudoers
would make the owner root as it is supposed to be.

reboot and it should work properly again.

When you boot to recovery mode you will have root rights, so you can do these commands without sudo.
Good luck :)

---

### Post by ramjet_1953 on 2007-04-17
Thanks, anaconda!

That did the trick!

If I could email you a beer, I would.

That /etc/sudoers file is obviously one that should be well and truly left alone.

I have printed out your fix and added it to my expanding file of things that I have learnt.

Regards,
Roger :cool:

---

### Post by Compyx on 2007-04-17
To edit the /etc/sudoers file, you'll need to run
```
sudo visudo
```

This will lock the /etc/visudo file and provide some sanity checks and also check for parse errors in the file.

On my Gentoo-boxes, this was the only way to edit the /etc/sudoers file. Why _vi_sudo calls nano instead of vi on Ubuntu, I do not know...

---

### Post by supersandy on 2007-04-21
> **Compyx said:**
> To edit the /etc/sudoers file, you'll need to run
```
sudo visudo
```

This will lock the /etc/visudo file and provide some sanity checks and also check for parse errors in the file.

On my Gentoo-boxes, this was the only way to edit the /etc/sudoers file. Why _vi_sudo calls nano instead of vi on Ubuntu, I do not know...

Try to set the VISUAL and EDITOR environment variable to /usr/bin/vi

```
export VISUAL=/usr/bin/vi 
export EDITOR=/usr/bin/vi 
```

---

