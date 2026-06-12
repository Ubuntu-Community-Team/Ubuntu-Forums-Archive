---
title: "KTorrent"
date: 2008-05-08
forum: General Help
---

### Post by jake1017 on 2008-05-08
The icons for KTorrent and KNetAttach are not showing in the Applications/Internet menu (as shown below). Is there any way to get the icons to show? Also what is KNetAttach and can you delete it without effecting KTorrent?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69228&stc=1&d=1210239722[/IMG]

---

### Post by hyper_ch on 2008-05-08
try to delete knetattach and it will tell you whether ktorrent will also get deleted...

as for the icons, use À la carte to edit the entries.

---

### Post by ingvildr on 2008-05-08
I get the same icon problem on newly installed apps, a quick log out and back in fixes it for me.

---

### Post by jake1017 on 2008-05-08
> **hyper_ch said:**
> try to delete knetattach and it will tell you whether ktorrent will also get deleted...

as for the icons, use À la carte to edit the entries.

i have tried to delete knetattach but can't find it even in synaptic. also how do you use À la carte to edit the entries?

logging out and back in didn't solve it.

---

### Post by ingvildr on 2008-05-08
> **jake1017 said:**
> i have tried to delete knetattach but can't find it even in synaptic. also how do you use À la carte to edit the entries?

logging out and back in didn't solve it.

System > Preferences > Main Menu

---

### Post by jake1017 on 2008-05-09
I have fixed the icon problem:). 
but i want to uninstall knetattach but i am unable to find it in synaptic any ideas?

---

### Post by hyper_ch on 2008-05-09
Try:
```

sudo apt-get remove knetattach

```

---

### Post by jake1017 on 2008-05-09
Doesn't work i get this error.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by hyper_ch on 2008-05-09
and what could those errors mean?

---

### Post by jake1017 on 2008-05-09
i can't remove using apt-get because is says that
E: Couldn't find package knetattach

---

### Post by hyper_ch on 2008-05-09
as it is no package, then it is part of another package, if you want to find out which, run that:
```

sudo apt-get install apt-file
sudo apt-file update
apt-file search knetattach

```

---

### Post by Zorael on 2008-05-09
> **jake1017 said:**
> Doesn't work i get this error.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
That usually means you're running Synaptic or something package-related in the background, and it has - as the message suggests - locked the package administration resources.

---

### Post by jake1017 on 2008-05-09
i did that and it gives me this:

app-install-data: /usr/share/app-install/desktop/knetattach.desktop
app-install-data: /usr/share/app-install/icons/knetattach.png
kde-i18n-be: /usr/share/locale/be/LC_MESSAGES/knetattach.mo
kde-i18n-ca: /usr/share/doc/kde/HTML/ca/knetattach/common
kde-i18n-ca: /usr/share/doc/kde/HTML/ca/knetattach/index.cache.bz2
kde-i18n-ca: /usr/share/doc/kde/HTML/ca/knetattach/index.docbook
kde-i18n-ca: /usr/share/doc/kde/HTML/ca/knetattach/screenshot.png
kde-i18n-ca: /usr/share/doc/kde/HTML/ca/knetattach/screenshot2.png
kde-i18n-da: /usr/share/doc/kde/HTML/da/knetattach/common
kde-i18n-da: /usr/share/doc/kde/HTML/da/knetattach/index.cache.bz2
kde-i18n-da: /usr/share/doc/kde/HTML/da/knetattach/index.docbook
kde-i18n-de: /usr/share/doc/kde/HTML/de/knetattach/common
kde-i18n-de: /usr/share/doc/kde/HTML/de/knetattach/index.cache.bz2
kde-i18n-de: /usr/share/doc/kde/HTML/de/knetattach/index.docbook
kde-i18n-es: /usr/share/doc/kde/HTML/es/knetattach/common
kde-i18n-es: /usr/share/doc/kde/HTML/es/knetattach/index.cache.bz2
kde-i18n-es: /usr/share/doc/kde/HTML/es/knetattach/index.docbook
kde-i18n-es: /usr/share/doc/kde/HTML/es/knetattach/screenshot.png
kde-i18n-es: /usr/share/doc/kde/HTML/es/knetattach/screenshot2.png
kde-i18n-es: /usr/share/doc/kde/HTML/es/knetattach/screenshot3.png
kde-i18n-es: /usr/share/doc/kde/HTML/es/knetattach/screenshot4.png
kde-i18n-et: /usr/share/doc/kde/HTML/et/knetattach/common
kde-i18n-et: /usr/share/doc/kde/HTML/et/knetattach/index.cache.bz2
kde-i18n-et: /usr/share/doc/kde/HTML/et/knetattach/index.docbook
kde-i18n-et: /usr/share/doc/kde/HTML/et/knetattach/screenshot.png
kde-i18n-fr: /usr/share/doc/kde/HTML/fr/knetattach/common
kde-i18n-fr: /usr/share/doc/kde/HTML/fr/knetattach/index.cache.bz2
kde-i18n-fr: /usr/share/doc/kde/HTML/fr/knetattach/index.docbook
kde-i18n-it: /usr/share/doc/kde/HTML/it/knetattach/common
kde-i18n-it: /usr/share/doc/kde/HTML/it/knetattach/index.cache.bz2
kde-i18n-it: /usr/share/doc/kde/HTML/it/knetattach/index.docbook
kde-i18n-nl: /usr/share/doc/kde/HTML/nl/knetattach/common
kde-i18n-nl: /usr/share/doc/kde/HTML/nl/knetattach/index.cache.bz2
kde-i18n-nl: /usr/share/doc/kde/HTML/nl/knetattach/index.docbook
kde-i18n-pl: /usr/share/doc/kde/HTML/pl/knetattach/common
kde-i18n-pl: /usr/share/doc/kde/HTML/pl/knetattach/index.cache.bz2
kde-i18n-pl: /usr/share/doc/kde/HTML/pl/knetattach/index.docbook
kde-i18n-pl: /usr/share/doc/kde/HTML/pl/knetattach/screenshot.png
kde-i18n-pl: /usr/share/doc/kde/HTML/pl/knetattach/screenshot2.png
kde-i18n-pl: /usr/share/doc/kde/HTML/pl/knetattach/screenshot3.png
kde-i18n-pl: /usr/share/doc/kde/HTML/pl/knetattach/screenshot4.png
kde-i18n-pt: /usr/share/doc/kde/HTML/pt/knetattach/common
kde-i18n-pt: /usr/share/doc/kde/HTML/pt/knetattach/index.cache.bz2
kde-i18n-pt: /usr/share/doc/kde/HTML/pt/knetattach/index.docbook
kde-i18n-pt: /usr/share/doc/kde/HTML/pt/knetattach/screenshot.png
kde-i18n-pt: /usr/share/doc/kde/HTML/pt/knetattach/screenshot2.png
kde-i18n-pt: /usr/share/doc/kde/HTML/pt/knetattach/screenshot3.png
kde-i18n-pt: /usr/share/doc/kde/HTML/pt/knetattach/screenshot4.png
kde-i18n-ptbr: /usr/share/doc/kde/HTML/pt_BR/knetattach/common
kde-i18n-ptbr: /usr/share/doc/kde/HTML/pt_BR/knetattach/index.cache.bz2
kde-i18n-ptbr: /usr/share/doc/kde/HTML/pt_BR/knetattach/index.docbook
kde-i18n-ru: /usr/share/doc/kde/HTML/ru/knetattach/common
kde-i18n-ru: /usr/share/doc/kde/HTML/ru/knetattach/index.cache.bz2
kde-i18n-ru: /usr/share/doc/kde/HTML/ru/knetattach/index.docbook
kde-i18n-sv: /usr/share/doc/kde/HTML/sv/knetattach/common
kde-i18n-sv: /usr/share/doc/kde/HTML/sv/knetattach/index.cache.bz2
kde-i18n-sv: /usr/share/doc/kde/HTML/sv/knetattach/index.docbook
kde-i18n-sv: /usr/share/doc/kde/HTML/sv/knetattach/screenshot.png
kde-i18n-sv: /usr/share/doc/kde/HTML/sv/knetattach/screenshot2.png
kde-i18n-sv: /usr/share/doc/kde/HTML/sv/knetattach/screenshot3.png
kde-i18n-sv: /usr/share/doc/kde/HTML/sv/knetattach/screenshot4.png
kde-icons-mono: /usr/share/icons/mono/scalable/apps/knetattach.svgz
kde-l10n-ar: /usr/lib/kde4/share/locale/ar/LC_MESSAGES/knetattach.mo
kde-l10n-be: /usr/lib/kde4/share/locale/be/LC_MESSAGES/knetattach.mo
kde-l10n-bg: /usr/lib/kde4/share/locale/bg/LC_MESSAGES/knetattach.mo
kde-l10n-ca: /usr/lib/kde4/share/locale/ca/LC_MESSAGES/knetattach.mo
kde-l10n-cs: /usr/lib/kde4/share/locale/cs/LC_MESSAGES/knetattach.mo
kde-l10n-csb: /usr/lib/kde4/share/locale/csb/LC_MESSAGES/knetattach.mo
kde-l10n-da: /usr/lib/kde4/share/locale/da/LC_MESSAGES/knetattach.mo
kde-l10n-de: /usr/lib/kde4/share/locale/de/LC_MESSAGES/knetattach.mo
kde-l10n-el: /usr/lib/kde4/share/locale/el/LC_MESSAGES/knetattach.mo
kde-l10n-engb: /usr/lib/kde4/share/locale/en_GB/LC_MESSAGES/knetattach.mo
kde-l10n-eo: /usr/lib/kde4/share/locale/eo/LC_MESSAGES/knetattach.mo
kde-l10n-es: /usr/lib/kde4/share/locale/es/LC_MESSAGES/knetattach.mo
kde-l10n-et: /usr/lib/kde4/share/locale/et/LC_MESSAGES/knetattach.mo
kde-l10n-eu: /usr/lib/kde4/share/locale/eu/LC_MESSAGES/knetattach.mo
kde-l10n-fa: /usr/lib/kde4/share/locale/fa/LC_MESSAGES/knetattach.mo
kde-l10n-fi: /usr/lib/kde4/share/locale/fi/LC_MESSAGES/knetattach.mo
kde-l10n-fr: /usr/lib/kde4/share/locale/fr/LC_MESSAGES/knetattach.mo
kde-l10n-fy: /usr/lib/kde4/share/locale/fy/LC_MESSAGES/knetattach.mo
kde-l10n-ga: /usr/lib/kde4/share/locale/ga/LC_MESSAGES/knetattach.mo
kde-l10n-gl: /usr/lib/kde4/share/locale/gl/LC_MESSAGES/knetattach.mo
kde-l10n-hi: /usr/lib/kde4/share/locale/hi/LC_MESSAGES/knetattach.mo
kde-l10n-hu: /usr/lib/kde4/share/locale/hu/LC_MESSAGES/knetattach.mo
kde-l10n-is: /usr/lib/kde4/share/locale/is/LC_MESSAGES/knetattach.mo
kde-l10n-it: /usr/lib/kde4/share/locale/it/LC_MESSAGES/knetattach.mo
kde-l10n-ja: /usr/lib/kde4/share/locale/ja/LC_MESSAGES/knetattach.mo
kde-l10n-kk: /usr/lib/kde4/share/locale/kk/LC_MESSAGES/knetattach.mo
kde-l10n-km: /usr/lib/kde4/share/locale/km/LC_MESSAGES/knetattach.mo
kde-l10n-ko: /usr/lib/kde4/share/locale/ko/LC_MESSAGES/knetattach.mo
kde-l10n-lv: /usr/lib/kde4/share/locale/lv/LC_MESSAGES/knetattach.mo
kde-l10n-mk: /usr/lib/kde4/share/locale/mk/LC_MESSAGES/knetattach.mo
kde-l10n-nb: /usr/lib/kde4/share/locale/nb/LC_MESSAGES/knetattach.mo
kde-l10n-nds: /usr/lib/kde4/share/locale/nds/LC_MESSAGES/knetattach.mo
kde-l10n-ne: /usr/lib/kde4/share/locale/ne/LC_MESSAGES/knetattach.mo
kde-l10n-nl: /usr/lib/kde4/share/locale/nl/LC_MESSAGES/knetattach.mo
kde-l10n-nn: /usr/lib/kde4/share/locale/nn/LC_MESSAGES/knetattach.mo
kde-l10n-pa: /usr/lib/kde4/share/locale/pa/LC_MESSAGES/knetattach.mo
kde-l10n-pl: /usr/lib/kde4/share/locale/pl/LC_MESSAGES/knetattach.mo
kde-l10n-pt: /usr/lib/kde4/share/locale/pt/LC_MESSAGES/knetattach.mo
kde-l10n-ptbr: /usr/lib/kde4/share/locale/pt_BR/LC_MESSAGES/knetattach.mo
kde-l10n-ru: /usr/lib/kde4/share/locale/ru/LC_MESSAGES/knetattach.mo
kde-l10n-se: /usr/lib/kde4/share/locale/se/LC_MESSAGES/knetattach.mo
kde-l10n-sl: /usr/lib/kde4/share/locale/sl/LC_MESSAGES/knetattach.mo
kde-l10n-sv: /usr/lib/kde4/share/locale/sv/LC_MESSAGES/knetattach.mo
kde-l10n-th: /usr/lib/kde4/share/locale/th/LC_MESSAGES/knetattach.mo
kde-l10n-tr: /usr/lib/kde4/share/locale/tr/LC_MESSAGES/knetattach.mo
kde-l10n-uk: /usr/lib/kde4/share/locale/uk/LC_MESSAGES/knetattach.mo
kde-l10n-zhcn: /usr/lib/kde4/share/locale/zh_CN/LC_MESSAGES/knetattach.mo
kde-l10n-zhtw: /usr/lib/kde4/share/locale/zh_TW/LC_MESSAGES/knetattach.mo
kdeaccessibility-kde4: /usr/lib/kde4/share/icons/mono/scalable/apps/knetattach.svgz
kdeartwork-theme-icon-kde4: /usr/lib/kde4/share/icons/crystalsvg/128x128/apps/knetattach.png
kdeartwork-theme-icon-kde4: /usr/lib/kde4/share/icons/crystalsvg/16x16/apps/knetattach.png
kdeartwork-theme-icon-kde4: /usr/lib/kde4/share/icons/crystalsvg/22x22/apps/knetattach.png
kdeartwork-theme-icon-kde4: /usr/lib/kde4/share/icons/crystalsvg/32x32/apps/knetattach.png
kdeartwork-theme-icon-kde4: /usr/lib/kde4/share/icons/crystalsvg/48x48/apps/knetattach.png
kdeartwork-theme-icon-kde4: /usr/lib/kde4/share/icons/crystalsvg/64x64/apps/knetattach.png
kdeartwork-theme-icon-kde4: /usr/lib/kde4/share/icons/crystalsvg/scalable/apps/knetattach.svgz
kdebase-bin: /usr/bin/knetattach
kdebase-bin: /usr/share/applications/kde/knetattach.desktop
kdebase-bin: /usr/share/doc/kde/HTML/en/knetattach/common
kdebase-bin: /usr/share/doc/kde/HTML/en/knetattach/index.cache.bz2
kdebase-bin: /usr/share/doc/kde/HTML/en/knetattach/index.docbook
kdebase-bin: /usr/share/doc/kde/HTML/en/knetattach/screenshot.png
kdebase-bin: /usr/share/doc/kde/HTML/en/knetattach/screenshot1.png
kdebase-bin: /usr/share/doc/kde/HTML/en/knetattach/screenshot2.png
kdebase-bin: /usr/share/doc/kde/HTML/en/knetattach/screenshot3.png
kdebase-bin: /usr/share/doc/kde/HTML/en/knetattach/screenshot4.png
kdebase-bin: /usr/share/icons/hicolor/128x128/apps/knetattach.png
kdebase-bin: /usr/share/icons/hicolor/16x16/apps/knetattach.png
kdebase-bin: /usr/share/icons/hicolor/22x22/apps/knetattach.png
kdebase-bin: /usr/share/icons/hicolor/32x32/apps/knetattach.png
kdebase-bin: /usr/share/icons/hicolor/48x48/apps/knetattach.png
kdebase-bin: /usr/share/icons/hicolor/64x64/apps/knetattach.png
kdebase-bin: /usr/share/icons/hicolor/scalable/apps/knetattach.svgz
kdebase-bin: /usr/share/man/man1/knetattach.1.gz
kdebase-dbg: /usr/lib/debug/usr/bin/knetattach
kdebase-runtime: /usr/lib/kde4/lib/kde4/libexec/knetattach
kdebase-runtime-data: /usr/lib/kde4/share/doc/kde4/HTML/en/knetattach/common
kdebase-runtime-data: /usr/lib/kde4/share/doc/kde4/HTML/en/knetattach/index.cache.bz2
kdebase-runtime-data: /usr/lib/kde4/share/doc/kde4/HTML/en/knetattach/index.docbook
kdebase-runtime-data: /usr/lib/kde4/share/doc/kde4/HTML/en/knetattach/screenshot.png
kdebase-runtime-data: /usr/lib/kde4/share/doc/kde4/HTML/en/knetattach/screenshot1.png
kdebase-runtime-data: /usr/lib/kde4/share/doc/kde4/HTML/en/knetattach/screenshot2.png
kdebase-runtime-data: /usr/lib/kde4/share/doc/kde4/HTML/en/knetattach/screenshot3.png
kdebase-runtime-data: /usr/lib/kde4/share/doc/kde4/HTML/en/knetattach/screenshot4.png
kdebase-runtime-data: /usr/share/applications/kde4/knetattach.desktop
kdebase-runtime-data-common: /usr/lib/kde4/share/icons/hicolor/128x128/apps/knetattach.png
kdebase-runtime-data-common: /usr/lib/kde4/share/icons/hicolor/16x16/apps/knetattach.png
kdebase-runtime-data-common: /usr/lib/kde4/share/icons/hicolor/22x22/apps/knetattach.png
kdebase-runtime-data-common: /usr/lib/kde4/share/icons/hicolor/32x32/apps/knetattach.png
kdebase-runtime-data-common: /usr/lib/kde4/share/icons/hicolor/48x48/apps/knetattach.png
kdebase-runtime-data-common: /usr/lib/kde4/share/icons/hicolor/64x64/apps/knetattach.png
kdebase-runtime-data-common: /usr/lib/kde4/share/icons/hicolor/scalable/apps/knetattach.svgz
kdebase-runtime-dbg: /usr/lib/debug/usr/lib/kde4/lib/kde4/libexec/knetattach
language-pack-kde-af-base: /usr/share/locale-langpack/af/LC_MESSAGES/knetattach.mo
language-pack-kde-ar-base: /usr/share/locale-langpack/ar/LC_MESSAGES/knetattach.mo
language-pack-kde-bg-base: /usr/share/locale-langpack/bg/LC_MESSAGES/knetattach.mo
language-pack-kde-br-base: /usr/share/locale-langpack/br/LC_MESSAGES/knetattach.mo
language-pack-kde-bs-base: /usr/share/locale-langpack/bs/LC_MESSAGES/knetattach.mo
language-pack-kde-ca-base: /usr/share/locale-langpack/ca/LC_MESSAGES/knetattach.mo
language-pack-kde-cs-base: /usr/share/locale-langpack/cs/LC_MESSAGES/knetattach.mo
language-pack-kde-csb-base: /usr/share/locale-langpack/csb/LC_MESSAGES/knetattach.mo
language-pack-kde-cy-base: /usr/share/locale-langpack/cy/LC_MESSAGES/knetattach.mo
language-pack-kde-da-base: /usr/share/locale-langpack/da/LC_MESSAGES/knetattach.mo
language-pack-kde-de-base: /usr/share/locale-langpack/de/LC_MESSAGES/knetattach.mo
language-pack-kde-el-base: /usr/share/locale-langpack/el/LC_MESSAGES/knetattach.mo
language-pack-kde-en-base: /usr/share/locale-langpack/en_GB/LC_MESSAGES/knetattach.mo
language-pack-kde-eo-base: /usr/share/locale-langpack/eo/LC_MESSAGES/knetattach.mo
language-pack-kde-es-base: /usr/share/locale-langpack/es/LC_MESSAGES/knetattach.mo
language-pack-kde-et-base: /usr/share/locale-langpack/et/LC_MESSAGES/knetattach.mo
language-pack-kde-eu-base: /usr/share/locale-langpack/eu/LC_MESSAGES/knetattach.mo
language-pack-kde-fa-base: /usr/share/locale-langpack/fa/LC_MESSAGES/knetattach.mo
language-pack-kde-fi-base: /usr/share/locale-langpack/fi/LC_MESSAGES/knetattach.mo
language-pack-kde-fr-base: /usr/share/locale-langpack/fr/LC_MESSAGES/knetattach.mo
language-pack-kde-fy-base: /usr/share/locale-langpack/fy/LC_MESSAGES/knetattach.mo
language-pack-kde-ga-base: /usr/share/locale-langpack/ga/LC_MESSAGES/knetattach.mo
language-pack-kde-gl-base: /usr/share/locale-langpack/gl/LC_MESSAGES/knetattach.mo
language-pack-kde-he-base: /usr/share/locale-langpack/he/LC_MESSAGES/knetattach.mo
language-pack-kde-hi-base: /usr/share/locale-langpack/hi/LC_MESSAGES/knetattach.mo
language-pack-kde-hu-base: /usr/share/locale-langpack/hu/LC_MESSAGES/knetattach.mo
language-pack-kde-is-base: /usr/share/locale-langpack/is/LC_MESSAGES/knetattach.mo
language-pack-kde-it-base: /usr/share/locale-langpack/it/LC_MESSAGES/knetattach.mo
language-pack-kde-ja-base: /usr/share/locale-langpack/ja/LC_MESSAGES/knetattach.mo
language-pack-kde-ka-base: /usr/share/locale-langpack/ka/LC_MESSAGES/knetattach.mo
language-pack-kde-kk-base: /usr/share/locale-langpack/kk/LC_MESSAGES/knetattach.mo
language-pack-kde-km-base: /usr/share/locale-langpack/km/LC_MESSAGES/knetattach.mo
language-pack-kde-ko-base: /usr/share/locale-langpack/ko/LC_MESSAGES/knetattach.mo
language-pack-kde-lt-base: /usr/share/locale-langpack/lt/LC_MESSAGES/knetattach.mo
language-pack-kde-mk-base: /usr/share/locale-langpack/mk/LC_MESSAGES/knetattach.mo
language-pack-kde-ms-base: /usr/share/locale-langpack/ms/LC_MESSAGES/knetattach.mo
language-pack-kde-nb-base: /usr/share/locale-langpack/nb/LC_MESSAGES/knetattach.mo
language-pack-kde-nds-base: /usr/share/locale-langpack/nds/LC_MESSAGES/knetattach.mo
language-pack-kde-nl-base: /usr/share/locale-langpack/nl/LC_MESSAGES/knetattach.mo
language-pack-kde-nn-base: /usr/share/locale-langpack/nn/LC_MESSAGES/knetattach.mo
language-pack-kde-pa-base: /usr/share/locale-langpack/pa/LC_MESSAGES/knetattach.mo
language-pack-kde-pl-base: /usr/share/locale-langpack/pl/LC_MESSAGES/knetattach.mo
language-pack-kde-ps-base: /usr/share/locale-langpack/ps/LC_MESSAGES/knetattach.mo
language-pack-kde-pt-base: /usr/share/locale-langpack/pt/LC_MESSAGES/knetattach.mo
language-pack-kde-pt-base: /usr/share/locale-langpack/pt_BR/LC_MESSAGES/knetattach.mo
language-pack-kde-ru-base: /usr/share/locale-langpack/ru/LC_MESSAGES/knetattach.mo
language-pack-kde-rw-base: /usr/share/locale-langpack/rw/LC_MESSAGES/knetattach.mo
language-pack-kde-se-base: /usr/share/locale-langpack/se/LC_MESSAGES/knetattach.mo
language-pack-kde-sk-base: /usr/share/locale-langpack/sk/LC_MESSAGES/knetattach.mo
language-pack-kde-sl-base: /usr/share/locale-langpack/sl/LC_MESSAGES/knetattach.mo
language-pack-kde-sr-base: /usr/share/locale-langpack/sr/LC_MESSAGES/knetattach.mo
language-pack-kde-sr-base: /usr/share/locale-langpack/sr@Latn/LC_MESSAGES/knetattach.mo
language-pack-kde-sv-base: /usr/share/locale-langpack/sv/LC_MESSAGES/knetattach.mo
language-pack-kde-ta-base: /usr/share/locale-langpack/ta/LC_MESSAGES/knetattach.mo
language-pack-kde-tg-base: /usr/share/locale-langpack/tg/LC_MESSAGES/knetattach.mo
language-pack-kde-th-base: /usr/share/locale-langpack/th/LC_MESSAGES/knetattach.mo
language-pack-kde-tr-base: /usr/share/locale-langpack/tr/LC_MESSAGES/knetattach.mo
language-pack-kde-uk-base: /usr/share/locale-langpack/uk/LC_MESSAGES/knetattach.mo
language-pack-kde-uz-base: /usr/share/locale-langpack/uz/LC_MESSAGES/knetattach.mo
language-pack-kde-vi-base: /usr/share/locale-langpack/vi/LC_MESSAGES/knetattach.mo
language-pack-kde-zh-base: /usr/share/locale-langpack/zh_CN/LC_MESSAGES/knetattach.mo
language-pack-kde-zh-base: /usr/share/locale-langpack/zh_TW/LC_MESSAGES/knetattach.mo

---

### Post by hyper_ch on 2008-05-09
kdebase-bin: /usr/bin/knetattach

seems like it belongs to one of the basic kde libs so you can't really uninstall it...

---

