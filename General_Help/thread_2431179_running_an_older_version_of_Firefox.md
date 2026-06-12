---
title: "running an older version of Firefox"
date: 2019-11-12
forum: General Help
---

### Post by Skaperen on 2019-11-12
i know apt has a way to lock in a specific version of a package.  is there a way to drop back to a specific version?  i started having trouble with my webmail service around the time Firefox went from version 69 to version 70.  i'd like to drop back to an older Firefox to see if changes it has made are impact the issue.  likewise, i may need to, also, drop back libraries it depends on.  my webmail provider turns out to have no Xubuntu desktops.

---

### Post by jeremy31 on 2019-11-12
You might want to try using Synaptic Package Manager, search for firefox, click the package name, and then one menu should allow "force version"

---

### Post by Skaperen on 2019-11-12
i can't find that in any of my Xubuntu menus.

---

### Post by Holger_Gehrke on 2019-11-13
The graphical package manager frontend 'synaptic' isn't installed by default. You can either use 'Software' (which should be available from the whisker-menu in XUbuntu and should be in the category 'System'; for some reason I can never find it and end up using the search field ...) to search for and install it or 'sudo apt install synaptic' from the command line. 'synaptic' is a lot more powerful than 'Software' but is only for Debian packages and doesn't integrate other packaging systems like snap or flatpak (whether that's a plus or a deficiency I leave up to you to decide ...).

Or you could get the list of available versions using 'apt-cache showpkg firefox' then remove the current one and install an older version with 'sudo apt-get install firefox=<version>' (replacing '<version>' with a version taken from the output of the previous command). Then use 'sudo apt-mark hold firefox' to keep ff on that version. That stops updates of this package until you do 'sudo apt-mark unhold firefox'.

In general I wouldn't recommend doing this, you can't be sure that your profile from a current browser will work with an older browser. Also there are security reasons for always using an up-to-date browser.

Instead I'd look into installing and setting up a real email client like thunderbird or evolution or ... All you really need to know are your user account data (user name & password), the protocol your provider is using for incoming and outgoing mail and the addresses (and possibly ports) for the servers handling the protocols. You don't need a provider-specific program to handle mail.

And before doing that, I'd check that it isn't just one of your add-ons breaking your web-mail by running firefox in safe mode ('firefox --safe-mode' on the command line starts ff without any add-ons and resets some options that you might have set in your profile to their defaults for one session).

Holger

---

### Post by flemur13013 on 2019-11-13
> **Skaperen said:**
> i know apt has a way to lock in a specific version of a package.  is there a way to drop back to a specific version?  i started having trouble with my webmail service around the time Firefox went from version 69 to version 70.  i'd like to drop back to an older Firefox to see if changes it has made are impact the issue.  likewise, i may need to, also, drop back libraries it depends on.  my webmail provider turns out to have no Xubuntu desktops.
Synaptic has "lock version" and "force version" but they are pretty limited.

This isn't a "normal" procedure, but I've had very good results by "installing"(*) firefox from 
[https://ftp.mozilla.org/pub/firefox/releases/](https://ftp.mozilla.org/pub/firefox/releases/)

(*) It's not a real install; you expand the .bz2 file into a directory, then run the firefox binary from there, probably with links so the executable will be in your PATH.
I also remove the officially installed firefox so there aren't two versions around.

---

### Post by Skaperen on 2019-11-13
does anyone know when firefox 69 was replaced by firefox 70?  it looks like the change happened on 2019-10-31 which is quite near to when the problems started showing up.  so what i wanted to do was switch back to firefox 69 (just for a few days) and see if that problem remains or goes away.  but the command "apt-cache showpkg firefox" only shows versions 70 and 59 (too old).  maybe i should post about the problem, which is related to my webmail service.  their support staff say they don't see the problem on Windows and don't have Ubuntu to test on.

---

### Post by Skaperen on 2019-11-13
> **Holger_Gehrke said:**
> In general I wouldn't recommend doing this, you can't be sure that your profile from a current browser will work with an older browser. Also there are security reasons for always using an up-to-date browser.

Instead I'd look into installing and setting up a real email client like thunderbird or evolution or ... All you really need to know are your user account data (user name & password), the protocol your provider is using for incoming and outgoing mail and the addresses (and possibly ports) for the servers handling the protocols. You don't need a provider-specific program to handle mail.

And before doing that, I'd check that it isn't just one of your add-ons breaking your web-mail by running firefox in safe mode ('firefox --safe-mode' on the command line starts ff without any add-ons and resets some options that you might have set in your profile to their defaults for one session).

Holger

i only want to go back one version (70 to 69) and do so only for a couple days.  having both in parallel and running the older one in this separate userid that is specific to reading email is also possible.

IMAP access costs more.  i'm looking for a new provider, anyway.  any suggestions of a low cost provider than can host the email for a domain name?

there are no add-ons that i am aware of (none that i added).  i have made no changes to it in months.  the only changes are periodic upgrades as well as system upgrades.

---

### Post by Holger_Gehrke on 2019-11-14
For going back one or two versions temporarily and in a separate account flemur13013's idea seems the simplest.

On my system the update to 70 happened on 2019-11-06 0:49 according to /var/log/dpkg.

IMAP might cost more, but what about pop3/smtp ? That's usually included at no extra charge ...

Holger

---

### Post by Impavidus on 2019-11-14
To install Firefox 69 you need the .deb file for it. Is it still in /var/cache/apt/archives? If not, I don't know where to get it. Although it's probably archived somewhere.

---

### Post by Skaperen on 2019-11-14
i already looked in /var for it.  it's gone.  i think i might have configured it to discard cache of updated versions to keep my file space lean.

---

### Post by Skaperen on 2019-11-14
> **flemur13013 said:**
> Synaptic has "lock version" and "force version" but they are pretty limited.

This isn't a "normal" procedure, but I've had very good results by "installing"(*) firefox from 
[https://ftp.mozilla.org/pub/firefox/releases/](https://ftp.mozilla.org/pub/firefox/releases/)

(*) It's not a real install; you expand the .bz2 file into a directory, then run the firefox binary from there, probably with links so the executable will be in your PATH.
I also remove the officially installed firefox so there aren't two versions around.

i don't see any .bz2 files there.  all i see for version 69 is individual files.

---

### Post by Dennis N on 2019-11-14
The last FF 69 point release:
[https://ftp.mozilla.org/pub/firefox/releases/69.0.3/linux-x86_64/en-US/](https://ftp.mozilla.org/pub/firefox/releases/69.0.3/linux-x86_64/en-US/)

---

