---
title: "Autoremove wants to remove some KDE packages"
date: 2019-09-18
forum: General Help
---

### Post by khanny on 2019-09-18
Hi, I don't remember noticing the autoremove prompt, but just now I noticed it and did a quick scan and saw it listing some libkf packages.

Below is the list:
```
  accountwizard cryfs encfs fonts-open-sans gir1.2-gconf-2.0 gir1.2-rsvg-2.0 gyp kdegames-card-data-kf5
  kdegames-mahjongg-data-kf5 kdepim-addons kdepim-themeeditors kf5-messagelib-data konversation-data
  libc-ares2 libcrypto++6 libfreecell-solver0 libjs-inherits libjs-is-typedarray libkf5followupreminder5
  libkf5grantleetheme-data libkf5grantleetheme-plugins libkf5grantleetheme5 libkf5gravatar-data
  libkf5gravatar5abi2 libkf5kaddressbookgrantlee5 libkf5kaddressbookimportexport5 libkf5kdegames-data
  libkf5kdegames7 libkf5kdegamesprivate1 libkf5kmahjongglib-data libkf5kmahjongglib5 libkf5kmanagesieve5
  libkf5ksieve-data libkf5ksieve5 libkf5ksieveui5 libkf5libkleo5abi1 libkf5mailcommon-plugins
  libkf5mailcommon5abi4 libkf5mailimporter-data libkf5mailimporter5abi1 libkf5mailimporterakonadi5
  libkf5messagecomposer5abi2 libkf5messagecore5abi2 libkf5messagelist5abi1 libkf5messageviewer-plugins
  libkf5messageviewer5abi5 libkf5mimetreeparser5abi3 libkf5sendlater5 libkf5templateparser5abi2
  libkf5tnef-data libkf5tnef5 libkf5webengineviewer5abi3 libkpimimportwizard5 libkpimitinerary-data
  libkpimitinerary5 libkpimpkpass5 libnode-dev libnode64 libqgpgme7 libssl-dev libtinyxml2-6a libuv1
  libuv1-dev libxxhash0 linux-headers-5.0.0-13 linux-headers-5.0.0-13-generic
  linux-image-5.0.0-13-generic linux-modules-5.0.0-13-generic linux-modules-extra-5.0.0-13-generic
  mbox-importer nodejs-doc paperkey python-pkg-resources python3-evdev python3-xlib xxd

```

In /var/log/apt/history.log, the most recent action of most of these packages were when I first installed Kubuntu.

The Nodejs packages are safe to remove but I'm not sure about the Python and libkf packages.

Please advise if it's safe to use autoremove.

Thanks

---

### Post by Xian on 2019-09-18
Autoremove will only uninstall packages that are no longer depended upon by your system. So unless you have (1) accidentally uninstalled a needed program or (2) installed a program that you explicitly want but is not required by any other package, then the command will run as designed with the intended result. Which is to say --- don't assume or presume but instead be wise.

Read here for a great explanation: [https://askubuntu.com/questions/393212/is-it-safe-to-use-the-command-apt-get-autoremove-in-this-particular-scenario?answertab=votes#tab-top](https://askubuntu.com/questions/393212/is-it-safe-to-use-the-command-apt-get-autoremove-in-this-particular-scenario?answertab=votes#tab-top)

---

