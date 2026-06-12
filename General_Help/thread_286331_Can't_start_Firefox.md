---
title: "Can't start Firefox"
date: 2006-10-27
forum: General Help
---

### Post by vbeav99 on 2006-10-27
I used to have Swiftfox installed, but wanted to try out Firefox 2.0 since I installed and am running Edgy, so I uninstalled it using:

rm -rf /opt/swiftfox
rm -f /usr/share/applications/swiftfox.desktop

Now, when I try running firefox I get a message saying: "Cannon launch application. Failed to launch child process "firefox" (No such file or directory).

I tried reinstalling it from Synaptic and same thing.

Any ideas?

---

### Post by bollix47 on 2006-10-27
How are you trying to start firefox?

From command line?

What are you typing in?

---

### Post by vbeav99 on 2006-10-27
Just trying to use the icon, or go through Applications>...
If the command to start it using command line is just 'firefox', that's not working either.

---

### Post by bollix47 on 2006-10-27
Can you right click on the Firefox icon and choose properties?  If so, please copy and paste the command line here.

---

### Post by vbeav99 on 2006-10-27
firefox %u

---

### Post by ~LoKe on 2006-10-27
> **vbeav99 said:**
> firefox %u

Remove the %u.  It won't solve your problem, but it has been known to cause other issues (opening up university websites on startup).

---

### Post by bollix47 on 2006-10-27
Open a terminal (Applications - Accessories - Terminal) and try typing /usr/bin/firefox

Post any errors etc here.

---

### Post by vbeav99 on 2006-10-27
No such file or directory.
And when I go into the /usr/bin/ directory, there's a file called firefox there, but the type is listed as "link(broken)"

---

### Post by ~LoKe on 2006-10-27
```
sudo dpkg-reconfigure firefox
```
Wonder if that would work.

---

### Post by bollix47 on 2006-10-27
Okay ... open terminal and cd to /usr/bin

sudo rm firefox

sudo ln -s /usr/bin/firefox/firefox firefox

Try your firefox icon again.  

If it doesn't work try typing /usr/bin/firefox in a terminal again and post output here.

---

### Post by vbeav99 on 2006-10-27
Nope, just say "Please restart any running Firefoxes, or you will experience problems."

---

### Post by vbeav99 on 2006-10-27
Got it...for some reason the working firefox link was changed to firefox.ubuntu, and the old, just 'firefox' wasn't working. Changed the new link to the new one and it works fine.

Thanks guys

---

