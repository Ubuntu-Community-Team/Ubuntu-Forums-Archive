---
title: "unable to update morphis/anbox"
date: 2023-10-29
forum: General Help
---

### Post by jmmakesw on 2023-10-29
I'm getting an error on the update that i can´t resolve. can anybody help?

[FONT=monospace][COLOR=#FF5454]**E: **[/COLOR][COLOR=#000000]Falhou obter [https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu/dists/jammy/InRelease](https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu/dists/jammy/InRelease)  403  Forbidden [IP: 2620:2d:4000:1::3e 443][/COLOR]
[COLOR=#FF5454]**E: **[/COLOR][COLOR=#000000]O repositório 'https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu jammy InRelease' não está assinado.[/COLOR]
[COLOR=#B26818]N: [/COLOR][COLOR=#000000]Atualizações a partir de tal repositório não podem ser feitas de forma segura e estão, portanto, desativadas por definição.[/COLOR]
[COLOR=#B26818]N: [/COLOR][COLOR=#000000]See apt-secure(8) manpage for repository creation and user configuration details.[/COLOR]
[/FONT]

---

### Post by MAFoElffen on 2023-10-29
RE: [https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu/dists/](https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu/dists/)

That does not exist anymore. In fact, there in no l/aunchpad.net/morphis... There is an ~morphis user, but they do not have any PPA's related to Anbox... That old address you have had been reported as lost and a Zombie PPA to AskUbuntu over a year ago.

I see an issue at the Anbox GitHub that that PPA does not exits anymore.

Do you have this installed? Or are you trying to install it?

Because currently, that is both an APT package in the Repo's, and available now as a Snap package.

---

### Post by jmmakesw on 2023-10-30
I've installed  and i'm trying to remove it, but without sucess. any sugestion?

---

### Post by MAFoElffen on 2023-10-31
Have you tried this?
```

sudo apt-get install ppa-purge
sudo ppa-purge https://ppa.launchpadcontent.net/morphis/anbox-support/ubuntu/dists/

```
That should remove the ppa and purge everything that was installed from it.

---

