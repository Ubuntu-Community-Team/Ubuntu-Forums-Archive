---
title: "how come some updates require passwords while other's don't?"
date: 2019-01-07
forum: General Help
---

### Post by ardouronerous on 2019-01-07
I'm running Lubuntu 18.04 64-bit.

When I run Software Updater, I notice updates for Firefox, Chromium, LibreOffice, I'm not prompted for my password, but updates for the Linux kernel, I'm prompted for my password.

I just want to understand how come some updates require passwords while other's don't?

Thanks.

---

### Post by TheFu on 2019-01-07
sudo has a timeout period. Running additional commands before the timeout won't require re-entering the sudo authentication. The timeout is tunable, just check the **sudoers** manpage.

---

### Post by deadflowr on 2019-01-07
It's been like that for several years now.
Update Manager (aka, software updater) will update already installed packages without the need for a password, since you've already installed them.
But installing new packages still require a password.
Kernel updates install completely new packages so they require invoking a password to install them.

Some more on that here:
[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates]("https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates")

---

### Post by ardouronerous on 2019-01-07
Thanks for the explanation, that cleared up a lot of my confusion, thanks. :)

---

### Post by oldrocker99 on 2019-01-08
I have also noticed that the Software Updater generally does not ask for a password. I rarely use the Updater; I almost always use the terminal, thus:
```
sudo apt update
sudo apt upgrade
```

---

