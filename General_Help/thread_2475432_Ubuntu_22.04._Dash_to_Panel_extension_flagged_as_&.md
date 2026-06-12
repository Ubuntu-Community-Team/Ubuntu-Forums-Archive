---
title: "Ubuntu 22.04. Dash to Panel extension flagged as &quot;Outdated&quot;"
date: 2022-05-26
forum: General Help
---

### Post by Advait on 2022-05-26
Just upgraded from 21.10 to 22.04. The Dash to Panel extension is flagged as "Outdated". How do I get Dash to Panel working?
 I removed purged the Firefox Snap and installed deb Firefox. The gnome.extensions icon is in my Firefox extensions bar.

---

### Post by Dennis N on 2022-05-27
I use "Extensions Manager" to manage extensions. It will notify your if installed extensions have updates and then update them. It also informs on whether new extensions you search for are compatible. Those have an "Install" button by them. If you don't use "Extensions Manager" consider installing it.

Install this package:

```
gnome-shell-extension-manager/jammy-updates 0.3.0-0ubuntu2.1 amd64
Utility for managing GNOME Shell Extensions

```

---

### Post by Advait on 2022-05-27
> **Dennis N said:**
> I use "Extensions Manager" to manage extensions. It will notify your if installed extensions have updates and then update them. It also informs on whether new extensions you search for are compatible. Those have an "Install" button by them. If you don't use "Extensions Manager" consider installing it.

Install this package:

```
gnome-shell-extension-manager/jammy-updates 0.3.0-0ubuntu2.1 amd64
Utility for managing GNOME Shell Extensions

```

Is the "Extensions Manager" you're talking about the same as the "gnome extensions" app I installed in Firefox? (I'd show you a screenshoot but my Flameshot isn't working since I installed 22.04. Any ideas how to fix it?)

---

### Post by Advait on 2022-05-27
[COLOR=#000000][FONT=Arial]I got Dash to Panel working. I uninstalled Gnome Extensions from Firefox, rebooted and reinstalled it. But the Dash to Panel web page was still greyed out. I was frustrated so I clicked a bunch of times on the greyed out "Outdated" button and suddenly Dash to Panel installed. Huh? Anyway, now it's working fine. (shrug) My solution was the equivalent of just angrily smacking an old tube TV to get it working. Go figure.[/FONT][/COLOR]

---

### Post by Dennis N on 2022-05-27
> **Advait said:**
> Is the "Extensions Manager" you're talking about the same as the "gnome extensions" app I installed in Firefox? (I'd show you a screenshoot but my Flameshot isn't working since I installed 22.04. Any ideas how to fix it?)
I'm not sure what you mean by "installed in Firefox". If you mean the "Add On Manager" in Firefox (which handles Firefox extensions), then the "Extensions Manager" I showed is post #2 is not that. You install it from the Ubuntu repository. It's for gnome shell extensions.

There is also and older package, named "Gnome Extensions" (as I recall):
```
gnome-shell-extension-prefs/jammy 42.0-2ubuntu1 amd64
```
which looks similar, but cannot install extensions like the one I recommended.

Finally, there is a Firefox extension (this may be what you are using) called "Gnome Shell Integration" which allows you to install extensions from the gnome-shell-extensions web site. If so, I recommend you switch to the package I recommended in post #2, since Firefox snap cannot use this extension.

---

### Post by Advait on 2022-05-27
> **Dennis N said:**
> I'm not sure what you mean by "installed in Firefox". If you mean the "Add On Manager" in Firefox (which handles Firefox extensions), then the "Extensions Manager" I showed is post #2 is not that. You install it from the Ubuntu repository. It's for gnome shell extensions.

There is also and older package, named "Gnome Extensions" (as I recall):
```
gnome-shell-extension-prefs/jammy 42.0-2ubuntu1 amd64
```
which looks similar, but cannot install extensions like the one I recommended.

Ahh.. Yes, I have that installed. Dash To Panel is in the list and is installed. I'm all set. Thx!

---

### Post by Dennis N on 2022-05-27
Yes, all the references to "gnome shell extensions" and "Firefox extensions" can be confusing. Especially when you can have a Firefox extension to install gnome shell extensions! What?

---

### Post by Advait on 2022-05-27
> **Dennis N said:**
> Yes, all the references to "gnome shell extensions" and "Firefox extensions" can be confusing. Especially when you can have a Firefox extension to install gnome shell extensions! What?

What? indeed. :-)   It's OK, I'm now used to being confused by Ubuntu/Linux; it's good exercise for my old brain cells. Thank goodness for good support forums. :cool:

---

