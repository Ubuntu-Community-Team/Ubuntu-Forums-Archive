---
title: "Firefox won't start after update"
date: 2016-04-30
forum: General Help
---

### Post by lucas58 on 2016-04-30
Hi,

Firefox tried to update itself, but now it does not seem to start again. When I click the icon in the launcher, it flashes (as if it is about to start), but then nothing happens. I cannot run it with sudo. I'm still running Ubuntu 11.04, though - I don't know if this has anything to do with it.

Can anyone help, or offer ideas?

Thanks

---

### Post by vasa1 on 2016-04-30
11.04 is no longer supported. Continuing with 11.04 is a security risk. Please run 14.04 LTS or 15.10 or 16.04 LTS.

[https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29)

[https://www.mozilla.org/en-US/firefox/46.0/system-requirements/](https://www.mozilla.org/en-US/firefox/46.0/system-requirements/)

---

### Post by Impavidus on 2016-04-30
Yes, it has something to do with running an outdated Ubuntu release.

In Ubuntu, Firefox cannot upgrade itself. That function has been removed for the version of Firefox in the Ubuntu repositories, as upgrades of Firefox are already handled by the package manager in Ubuntu. Firefox doesn't even have permission to upgrade itself, as it is run by an ordinairy user but owned by root. So you probably manually installed a standard Firefox version in your home directory, owned by yourself, to get a more recent version than the last one that came with Ubuntu 11.04. This latest version may depend on some library functions not available in your old Ubuntu release.

Ubuntu 11.04 has been unsupported since October 2012. I suggest you wipe your hard drive and install 16.04. Consider one of the lighter flavours if your computer is old. 14.04 still has 3 years of support left, so you could use that too. 12.04 and the lighter flavours of 14.04 only have 1 year of support left, so I suggest you don't install one of those. 15.10 only has 3 months of support left.

---

