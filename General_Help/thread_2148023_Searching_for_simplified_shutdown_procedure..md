---
title: "Searching for simplified shutdown procedure."
date: 2013-05-23
forum: General Help
---

### Post by grey1beard on 2013-05-23
Some or many may think this a bad idea, but I would like to be able to shut down my laptop at the end of a session with a single click of a button.
I'm using 12.04LTS gnome, on an hp6700 laptop.

Not just hitting the power switch, or closing the lid, but to allow the orderly shut down, through to power off, without having a drop down menu to choose from, followed by another choice, to confirm that was what I _really_ wanted to do.

I would assume that I had closed all the windows, though that may not be necessary. 
Perhaps something as simple as a shortcut on the taskbar would be a safe place to park such a control, if it were possible ?

Any thoughts or suggestions, please, as my current search has produced no results.

I pressume that just switching the power off, or closing the laptop lid would be a bad thing to do.

John

---

### Post by Merrattic on 2013-05-23
Attach this command to a shortcut:

```
echo "yourpasswd" | sudo -S shutdown -h now
```

Some caveats:

This is insecure as "yourpassword" is typed out in plain view in the shortcut. You can overcome this by editing your sudoers file to allow shutdown to run without the sudo.

Alternatively, check in power options to see what can be done when you press your power button, if shutdown is there, then it will do the same thing. A simple single touch should be all that is needed to shutdown your PC in an orderly way.

---

### Post by grey1beard on 2013-05-23
Thanks, Merrattic.
As the power options don't offer shutdown, it looks like I'll have to explore the first idea.

Regards
John

---

