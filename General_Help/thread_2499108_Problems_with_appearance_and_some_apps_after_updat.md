---
title: "Problems with appearance and some apps after update 22.04"
date: 2024-07-12
forum: General Help
---

### Post by daninmanchester on 2024-07-12
I recently ran the automatic updates. Immediately after it was obvious ubuntu had forgotten my settings .... it was going through the connect my accounts, etc. as if it was a new install.
Then I tried to fix the appearance, the appearance tab is there but I cannot change anything. 
I also notice that my extensions such arcMenu no longer work and my keyboard has defaulted to US instead of UK.

I've not been using Ubuntu that long so dont really know where to start diagnosing this but here is the update log.

Start-Date: 2024-07-12  06:31:12
Commandline: /usr/bin/unattended-upgrade
Upgrade: python3.10:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4), libpython3.10-minimal:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4), libpython3.10-stdlib:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4), libpython3.10:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4), python3.10-minimal:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4)
End-Date: 2024-07-12  06:31:14


Start-Date: 2024-07-12  06:31:16
Commandline: /usr/bin/unattended-upgrade
Upgrade: apache2-data:amd64 (2.4.52-1ubuntu4.9, 2.4.52-1ubuntu4.11), apache2-bin:amd64 (2.4.52-1ubuntu4.9, 2.4.52-1ubuntu4.11), apache2-utils:amd64 (2.4.52-1ubuntu4.9, 2.4.52-1ubuntu4.11), apache2:amd64 (2.4.52-1ubuntu4.9, 2.4.52-1ubuntu4.11)
End-Date: 2024-07-12  06:31:19


Start-Date: 2024-07-12  14:26:55
Commandline: packagekit role='update-packages'
Upgrade: containerd.io:amd64 (1.6.33-1, 1.7.18-1), docker-compose-plugin:amd64 (2.27.1-1~ubuntu.22.04~jammy, 2.28.1-1~ubuntu.22.04~jammy), syncthing:amd64 (1.27.8, 1.27.9), docker-ce-cli:amd64 (5:26.1.4-1~ubuntu.22.04~jammy, 5:27.0.3-1~ubuntu.22.04~jammy), gjs:amd64 (1.72.4-0ubuntu0.22.04.1, 1.72.4-0ubuntu0.22.04.3~really.is.1.72.2.0ubuntu2), libgjs0g:amd64 (1.72.4-0ubuntu0.22.04.1, 1.72.4-0ubuntu0.22.04.3~really.is.1.72.2.0ubuntu2), tzdata:amd64 (2024a-0ubuntu0.22.04, 2024a-0ubuntu0.22.04.1), libldap-common:amd64 (2.5.17+dfsg-0ubuntu0.22.04.1, 2.5.18+dfsg-0ubuntu0.22.04.1), xserver-xorg-core:amd64 (2:21.1.4-2ubuntu1.7~22.04.10, 2:21.1.4-2ubuntu1.7~22.04.11), azure-cli:amd64 (2.61.0-1~jammy, 2.62.0-1~jammy), libldap-2.5-0:amd64 (2.5.17+dfsg-0ubuntu0.22.04.1, 2.5.18+dfsg-0ubuntu0.22.04.1), libldap-2.5-0:i386 (2.5.17+dfsg-0ubuntu0.22.04.1, 2.5.18+dfsg-0ubuntu0.22.04.1), docker-buildx-plugin:amd64 (0.14.1-1~ubuntu.22.04~jammy, 0.15.1-1~ubuntu.22.04~jammy), docker-ce:amd64 (5:26.1.4-1~ubuntu.22.04~jammy, 5:27.0.3-1~ubuntu.22.04~jammy), xserver-xorg-legacy:amd64 (2:21.1.4-2ubuntu1.7~22.04.10, 2:21.1.4-2ubuntu1.7~22.04.11), ubuntu-desktop:amd64 (1.481.1, 1.481.2), ubuntu-pro-client-l10n:amd64 (32.3~22.04, 32.3.1~22.04), xserver-common:amd64 (2:21.1.4-2ubuntu1.7~22.04.10, 2:21.1.4-2ubuntu1.7~22.04.11), docker-ce-rootless-extras:amd64 (5:26.1.4-1~ubuntu.22.04~jammy, 5:27.0.3-1~ubuntu.22.04~jammy), xserver-xephyr:amd64 (2:21.1.4-2ubuntu1.7~22.04.10, 2:21.1.4-2ubuntu1.7~22.04.11), ubuntu-standard:amd64 (1.481.1, 1.481.2), ubuntu-desktop-minimal:amd64 (1.481.1, 1.481.2), code:amd64 (1.90.1-1718141439, 1.91.1-1720564633), ubuntu-advantage-tools:amd64 (32.3~22.04, 32.3.1~22.04), ubuntu-minimal:amd64 (1.481.1, 1.481.2), ubuntu-pro-client:amd64 (32.3~22.04, 32.3.1~22.04)
End-Date: 2024-07-12  14:27:20

---

### Post by daninmanchester on 2024-07-12
I asked chat GPT and it suggested a bunch of things .... 

This seemed to fix it :

sudo chown -R $USER:$USER /home/$USER
sudo chmod -R u+rwX /home/$USER

I'm not why this happened or what side effects there are of this. 
Are there other specific permission I may have overwritten in doing this?

---

### Post by currentshaft on 2024-07-12
It is very unlikely the updates caused this, and given your proclivity to run commands you don't understand issued by an LLM, I suspect there's other reasons your system entered this degraded state.

---

### Post by dataonerous on 2024-08-13
> **daninmanchester said:**
> I recently ran the automatic updates. Immediately after it was obvious ubuntu had forgotten my settings .... it was going through the connect my accounts, etc. as if it was a new install.
Then I tried to fix the appearance, the appearance tab is there but I cannot change anything. 
I also notice that my extensions such arcMenu no longer work and my keyboard has defaulted to US instead of UK.

I've not been using Ubuntu that long so dont really know where to start diagnosing this but here is the update log.

Start-Date: 2024-07-12  06:31:12
Commandline: /usr/bin/unattended-upgrade
Upgrade: python3.10:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4), libpython3.10-minimal:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4), libpython3.10-stdlib:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4), libpython3.10:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4), python3.10-minimal:amd64 (3.10.12-1~22.04.3, 3.10.12-1~22.04.4)
End-Date: 2024-07-12  06:31:14


Start-Date: 2024-07-12  06:31:16
Commandline: /usr/bin/unattended-upgrade
Upgrade: apache2-data:amd64 (2.4.52-1ubuntu4.9, 2.4.52-1ubuntu4.11), apache2-bin:amd64 (2.4.52-1ubuntu4.9, 2.4.52-1ubuntu4.11), apache2-utils:amd64 (2.4.52-1ubuntu4.9, 2.4.52-1ubuntu4.11), apache2:amd64 (2.4.52-1ubuntu4.9, 2.4.52-1ubuntu4.11)
End-Date: 2024-07-12  06:31:19


Start-Date: 2024-07-12  14:26:55
Commandline: packagekit role='update-packages' [size=1][[color=white]dinosaur game[/color]](https://dinosaurgames.io)[/size]
Upgrade: containerd.io:amd64 (1.6.33-1, 1.7.18-1), docker-compose-plugin:amd64 (2.27.1-1~ubuntu.22.04~jammy, 2.28.1-1~ubuntu.22.04~jammy), syncthing:amd64 (1.27.8, 1.27.9), docker-ce-cli:amd64 (5:26.1.4-1~ubuntu.22.04~jammy, 5:27.0.3-1~ubuntu.22.04~jammy), gjs:amd64 (1.72.4-0ubuntu0.22.04.1, 1.72.4-0ubuntu0.22.04.3~really.is.1.72.2.0ubuntu2), libgjs0g:amd64 (1.72.4-0ubuntu0.22.04.1, 1.72.4-0ubuntu0.22.04.3~really.is.1.72.2.0ubuntu2), tzdata:amd64 (2024a-0ubuntu0.22.04, 2024a-0ubuntu0.22.04.1), libldap-common:amd64 (2.5.17+dfsg-0ubuntu0.22.04.1, 2.5.18+dfsg-0ubuntu0.22.04.1), xserver-xorg-core:amd64 (2:21.1.4-2ubuntu1.7~22.04.10, 2:21.1.4-2ubuntu1.7~22.04.11), azure-cli:amd64 (2.61.0-1~jammy, 2.62.0-1~jammy), libldap-2.5-0:amd64 (2.5.17+dfsg-0ubuntu0.22.04.1, 2.5.18+dfsg-0ubuntu0.22.04.1), libldap-2.5-0:i386 (2.5.17+dfsg-0ubuntu0.22.04.1, 2.5.18+dfsg-0ubuntu0.22.04.1), docker-buildx-plugin:amd64 (0.14.1-1~ubuntu.22.04~jammy, 0.15.1-1~ubuntu.22.04~jammy), docker-ce:amd64 (5:26.1.4-1~ubuntu.22.04~jammy, 5:27.0.3-1~ubuntu.22.04~jammy), xserver-xorg-legacy:amd64 (2:21.1.4-2ubuntu1.7~22.04.10, 2:21.1.4-2ubuntu1.7~22.04.11), ubuntu-desktop:amd64 (1.481.1, 1.481.2), ubuntu-pro-client-l10n:amd64 (32.3~22.04, 32.3.1~22.04), xserver-common:amd64 (2:21.1.4-2ubuntu1.7~22.04.10, 2:21.1.4-2ubuntu1.7~22.04.11), docker-ce-rootless-extras:amd64 (5:26.1.4-1~ubuntu.22.04~jammy, 5:27.0.3-1~ubuntu.22.04~jammy), xserver-xephyr:amd64 (2:21.1.4-2ubuntu1.7~22.04.10, 2:21.1.4-2ubuntu1.7~22.04.11), ubuntu-standard:amd64 (1.481.1, 1.481.2), ubuntu-desktop-minimal:amd64 (1.481.1, 1.481.2), code:amd64 (1.90.1-1718141439, 1.91.1-1720564633), ubuntu-advantage-tools:amd64 (32.3~22.04, 32.3.1~22.04), ubuntu-minimal:amd64 (1.481.1, 1.481.2), ubuntu-pro-client:amd64 (32.3~22.04, 32.3.1~22.04)
End-Date: 2024-07-12  14:27:20
I think this update has a little problem, and when I updated I got the same error.

---

