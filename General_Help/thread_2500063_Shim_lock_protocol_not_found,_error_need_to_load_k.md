---
title: "Shim_lock protocol not found, error: need to load kernel first"
date: 2024-08-21
forum: General Help
---

### Post by psk94 on 2024-08-21
This is a 1 year old install using what was the latest ubuntu version back then, on an external hdd dual booting with Windows 10, had 0 issues until now. Now on bootup gives those grub errors and none of the options work in the loader. Method used to manually boot up Ubuntu normally: uefi menu->boot off ssd that has my Windows install and listed as Ubuntu there, not booting off the external hdd entry.

Almost positive this was caused from running various Windows security cleaning tools and one of them messed up the Ubuntu loader entry or configuration, since I select my Windows SSD to normally boot Ubuntu in uefi menu. Running bcedit /enum all still shows all the proper Ubuntu entries. What is the safest and easiest way to fix this as I can't lose access to this install? Note I'm a max Linux rookie, so preferably nothing too complicated.

More info on the errors: There's 4 boot entries as normal when I plug my external hdd in; 2 Samsung ssd entries at top, one leads to SBAT security failed which never worked nor used, 2nd entry loads Ubuntu grub loader menu that always worked until now titled, "Samsung ssd Ubuntu" in uefi/bios, 3rd and 4th entries being external hdd that never did anything if selected to boot.

---

### Post by Rubi1200 on 2024-08-21
Check UEFI/BIOS whether Secure Boot is enabled and if yes then disable it.

Does that make a difference?

---

### Post by psk94 on 2024-08-21
Yes that fixed it, thanks, but secure boot was on all this time and now magically breaks it out of the blue... why? Well my Windows install seems to work fine with it off too, so I guess it doesn't matter.

While I'm here, some other annoying quirks if you know the fix off the top of your head: I installed Google Chrome in Ubuntu manually, whenever I open it from side bar icon it says, "The login keyring did not get unlocked when logged in, authentication required"... how can I avoid having to type in my password every time I open Chrome?

Also the auto updater for the system says failed to download package files every time it tries, and my Windows clock ends up at 6 hour different time every time I use Ubuntu and go back to Windows after, having to toggle auto sync on and off to fix lol... Only use Ubuntu for crypto and banking investments for the security and clean OS, so as long as it semi works good enough I guess, still annoying.

---

### Post by Rubi1200 on 2024-08-21
I believe Secure Boot can often be turned on again after Windows updates but don't quote me on this.

Google Chrome: manually, how? Chrome is in the official repositories, although I think it might be a snap package. Perhaps delete and reinstall?

System time: Windows and Ubuntu "understand" system time differently. To possibly resolve do this in a terminal:
```
sudo timedatectl set-local-rtc 1 --adjust-system-clock

```

System updates: what does this show?
```
sudo apt update && sudo apt upgrade

```
Post any errors here.

---

### Post by TheFu on 2024-08-21
FWIW: [https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/](https://arstechnica.com/security/2024/08/a-patch-microsoft-spent-2-years-preparing-is-making-a-mess-for-some-linux-users/)
MSFT update seems to have screwed many dual boot systems.

---

### Post by deadflowr on 2024-08-21
> Google Chrome: manually, how? Chrome is in the official repositories, although I think it might be a snap package. Perhaps delete and reinstall?
Google Chrome is only available from google.
It's a downloadable deb package which then, when installed, adds a google repository.
Licensing prevents it from becoming a snap or being shipped in distribution archives directly. .
Flatpak has a Google Chrome package, but that's just a wrapper.

Chrome is designed to use the local keyring, either gnome or kde's.
If using autologin, then the keyring is not unlocked at login and chrome will complain about it.
The solution used to be setting it to not use the keyring.
Not sure if that's changed in the last couple of years, but here
[https://askubuntu.com/questions/884897/why-chrome-always-ask-for-keyring-and-is-it-possible-to-remove-it-without-giving](https://askubuntu.com/questions/884897/why-chrome-always-ask-for-keyring-and-is-it-possible-to-remove-it-without-giving)


EDIT
The question about google chrome really should have been a separate thread.

---

### Post by Rubi1200 on 2024-08-21
> **deadflowr said:**
> Google Chrome is only available from google.
It's a downloadable deb package which then, when installed, adds a google repository.
Licensing prevents it from becoming a snap or being shipped in distribution archives directly. .
Flatpak has a Google Chrome package, but that's just a wrapper.

Thank you for the correction. I have never used Chrome on Linux, so was not aware of this. Should have checked my facts first.

---

