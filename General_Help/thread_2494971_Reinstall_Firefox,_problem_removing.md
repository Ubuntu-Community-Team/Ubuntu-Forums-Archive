---
title: "Reinstall Firefox, problem removing"
date: 2024-02-02
forum: General Help
---

### Post by webmanoffesto on 2024-02-02
Firefox was running way to slow and I wanted to remove and reinstall a fresh version. So I uninstalled, but Ubuntu Software Center thinks I still have Firefox installed. I think the uninstall failed because a Firefox window was open when I ran uninstall. This was a snap. I think that I had an apt version at one point. Right now when I type firefox into the command line I get " 'firefox' not found, but can be installed with ... ". 

In Ubuntu Software Center, it provides me with the option to uninstall Firefox, but then I get "Unable to remove Firefox: cannot perform the following tasks" but no tasks are listed. That means I can't uninstall Firefox in the Software Center.

What's the best way to get a new fresh Firefox which doesn't have the add ons I had on it?

Maybe a fresh install that's a Snap will be the best way to go.

$ sudo snap remove firefox
Remove data for snap "firefox" (3728)                                          /error: cannot perform the following tasks:
- Remove data for snap "firefox" (3728) (unlinkat /home/tom/snap/firefox/common/.cache/mozilla/firefox/as47zdt9.default/startupCache: directory not empty)

So I manually removed that Firefox directory.

I tried to install the snap in the command line. That didn't work.
$ sudo snap install firefox
[sudo] password for tom: 
snap "firefox" is already installed, see 'snap help refresh'

---

### Post by dragonfly41 on 2024-02-02
If you want to try various profiles (one profile without extensions another with a collection of extensions) you can startup firefox by command line and choose different profiles.

[https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles?redirectslug=profile-manager-create-and-remove-firefox-profiles&redirectlocale=en-US](https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles?redirectslug=profile-manager-create-and-remove-firefox-profiles&redirectlocale=en-US)

---

