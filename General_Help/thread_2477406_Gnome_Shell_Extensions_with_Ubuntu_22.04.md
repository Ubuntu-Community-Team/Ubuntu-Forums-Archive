---
title: "Gnome Shell Extensions with Ubuntu 22.04?"
date: 2022-07-24
forum: General Help
---

### Post by 2CV67 on 2022-07-24
Hi!
I have been a very happy user of several Gnome Shell Extensions (Dash-to-Panel, New Mail Indicator...) for years.
When they were no longer available with Snap versions of Firefox in Ubuntu 21.10, I reverted to non-snap Firefox which worked fine too.
Now, with Ubuntu 22.04 it looks like I have no choice but to use Firefox Snap, so no Gnome Shell Extensions via Firefox.

I did try installing "Gnome Shell Extensions" via SynApt but that tells me my usual Extensions are not compatible with current Gnome version...

Is that right?

Any solutions?

Thanks for any suggestions!

---

### Post by tea for one on 2022-07-24
You can use a Firefox deb package [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

Alternatively, you can install Extension Manager [https://www.omgubuntu.co.uk/2022/03/extension-manager-gnome-shell-new-icon](https://www.omgubuntu.co.uk/2022/03/extension-manager-gnome-shell-new-icon)

Also, it is not too difficult to install extensions manually [https://www.debugpoint.com/manual-installation-gnome-extension/](https://www.debugpoint.com/manual-installation-gnome-extension/)

---

### Post by Dennis N on 2022-07-24
> **2CV67 said:**
>  I did try installing "Gnome Shell Extensions" via SynApt but that tells me my usual Extensions are not compatible with current Gnome version...
Is that right? Any solutions?

No, it's not always right. In some cases, the older version of an extension still works even though Gnome Shell Extensions says it will not. All that may be necessary is to change the gnome shell version in its metadata.json file. If the extensions are still installed on you computer, you can try that and see if it will still work. Panel OSD is one such extension I still am able to use.

If not on your computer anymore, you could download the extension files, fix, and manually move them to ~/.local/share/gnome-shell/extensions.

---

### Post by 2CV67 on 2022-07-24
Thanks very much, tea for one, for that rapid & clear reply!

I installed Extension Manager & was surprised to find my "Dash to Panel" extension was immediately up & working, with no further action on my part.

I prefer managing Gnome Extensions via this tool, rather than via Firefox, which always seemed an odd arrangement.

Extension Manager confirms that "New Mail Indicator" is incompatible with my Gnome v.42.2 & the Gnome Extensions website only offers NMI up to v.41 so that shifts the problem to that specific extension.
...................

At that point, I got the reply from Dennis N. (Thanks!)

The NMI extension is indeed still on my PC & it was easy to add v42.2 to the list of shell versions in the metadata file.
After a log-in, NMI now works perfectly!

I will call this thread SOLVED.

Thanks again!

---

