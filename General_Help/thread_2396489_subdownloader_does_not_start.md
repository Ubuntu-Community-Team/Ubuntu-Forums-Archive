---
title: "subdownloader does not start"
date: 2018-07-16
forum: General Help
---

### Post by Odense on 2018-07-16
Ubuntu 16.04 LTS with gnome classic desktop.

I installed Subdownloader from the terminal with sudo apt-get install subdownloader

It seems to be installed with an Icon under the Sound & Video section in the applications section.

But when I click it to start it it seem nothing is happening.

How do I find and correct the error?

---

### Post by oldos2er on 2018-07-16
What does  ```
dpkg -L subdownloader
``` run in a terminal say?

---

### Post by Odense on 2018-07-21
Thank you for answering - and please excuse my late response. The answer to the command is shown here:
```

morten@morten-Lenovo-B50-10:~$ dpkg -L subdownloader
/.
/usr
/usr/share
/usr/share/locale
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/subdownloader.mo
/usr/share/locale/el
/usr/share/locale/el/LC_MESSAGES
/usr/share/locale/el/LC_MESSAGES/subdownloader.mo
/usr/share/locale/fi
/usr/share/locale/fi/LC_MESSAGES
/usr/share/locale/fi/LC_MESSAGES/subdownloader.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/subdownloader.mo
/usr/share/locale/he
/usr/share/locale/he/LC_MESSAGES
/usr/share/locale/he/LC_MESSAGES/subdownloader.mo
/usr/share/locale/sk
/usr/share/locale/sk/LC_MESSAGES
/usr/share/locale/sk/LC_MESSAGES/subdownloader.mo
/usr/share/locale/es_ES
/usr/share/locale/es_ES/LC_MESSAGES
/usr/share/locale/es_ES/LC_MESSAGES/subdownloader.mo
/usr/share/locale/sq
/usr/share/locale/sq/LC_MESSAGES
/usr/share/locale/sq/LC_MESSAGES/subdownloader.mo
/usr/share/locale/eu
/usr/share/locale/eu/LC_MESSAGES
/usr/share/locale/eu/LC_MESSAGES/subdownloader.mo
/usr/share/locale/sr
/usr/share/locale/sr/LC_MESSAGES
/usr/share/locale/sr/LC_MESSAGES/subdownloader.mo
/usr/share/locale/hr
/usr/share/locale/hr/LC_MESSAGES
/usr/share/locale/hr/LC_MESSAGES/subdownloader.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/subdownloader.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/subdownloader.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/subdownloader.mo
/usr/share/locale/ko
/usr/share/locale/ko/LC_MESSAGES
/usr/share/locale/ko/LC_MESSAGES/subdownloader.mo
/usr/share/locale/bg
/usr/share/locale/bg/LC_MESSAGES
/usr/share/locale/bg/LC_MESSAGES/subdownloader.mo
/usr/share/locale/tr
/usr/share/locale/tr/LC_MESSAGES
/usr/share/locale/tr/LC_MESSAGES/subdownloader.mo
/usr/share/locale/gl
/usr/share/locale/gl/LC_MESSAGES
/usr/share/locale/gl/LC_MESSAGES/subdownloader.mo
/usr/share/locale/et
/usr/share/locale/et/LC_MESSAGES
/usr/share/locale/et/LC_MESSAGES/subdownloader.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/subdownloader.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/subdownloader.mo
/usr/share/locale/pt_PT
/usr/share/locale/pt_PT/LC_MESSAGES
/usr/share/locale/pt_PT/LC_MESSAGES/subdownloader.mo
/usr/share/locale/vi
/usr/share/locale/vi/LC_MESSAGES
/usr/share/locale/vi/LC_MESSAGES/subdownloader.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/subdownloader.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/subdownloader.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/subdownloader.mo
/usr/share/locale/en
/usr/share/locale/en/LC_MESSAGES
/usr/share/locale/en/LC_MESSAGES/subdownloader.mo
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/subdownloader.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/subdownloader.mo
/usr/share/locale/mk
/usr/share/locale/mk/LC_MESSAGES
/usr/share/locale/mk/LC_MESSAGES/subdownloader.mo
/usr/share/locale/id
/usr/share/locale/id/LC_MESSAGES
/usr/share/locale/id/LC_MESSAGES/subdownloader.mo
/usr/share/locale/ro
/usr/share/locale/ro/LC_MESSAGES
/usr/share/locale/ro/LC_MESSAGES/subdownloader.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/subdownloader.mo
/usr/share/pyshared
/usr/share/pyshared/subdownloader
/usr/share/pyshared/subdownloader/cli
/usr/share/pyshared/subdownloader/cli/__init__.py
/usr/share/pyshared/subdownloader/cli/main.py
/usr/share/pyshared/subdownloader/gui
/usr/share/pyshared/subdownloader/gui/chooseLanguage.py
/usr/share/pyshared/subdownloader/gui/imdbSearch.py
/usr/share/pyshared/subdownloader/gui/login.py
/usr/share/pyshared/subdownloader/gui/Qt2Po.py
/usr/share/pyshared/subdownloader/gui/chooseLanguage.ui
/usr/share/pyshared/subdownloader/gui/images_rc.py
/usr/share/pyshared/subdownloader/gui/expiration_ui.py
/usr/share/pyshared/subdownloader/gui/main.ui
/usr/share/pyshared/subdownloader/gui/preferences.ui
/usr/share/pyshared/subdownloader/gui/main_ui.py
/usr/share/pyshared/subdownloader/gui/chooseLanguage_ui.py
/usr/share/pyshared/subdownloader/gui/about.py
/usr/share/pyshared/subdownloader/gui/expiration.py
/usr/share/pyshared/subdownloader/gui/images.qrc
/usr/share/pyshared/subdownloader/gui/expiration.ui
/usr/share/pyshared/subdownloader/gui/about_ui.py
/usr/share/pyshared/subdownloader/gui/imdblistview.py
/usr/share/pyshared/subdownloader/gui/__init__.py
/usr/share/pyshared/subdownloader/gui/Makefile
/usr/share/pyshared/subdownloader/gui/preferences_ui.py
/usr/share/pyshared/subdownloader/gui/imdb_ui.py
/usr/share/pyshared/subdownloader/gui/images
/usr/share/pyshared/subdownloader/gui/images/download.png
/usr/share/pyshared/subdownloader/gui/images/info.png
/usr/share/pyshared/subdownloader/gui/images/open_folder.png
/usr/share/pyshared/subdownloader/gui/images/upload.png
/usr/share/pyshared/subdownloader/gui/images/paypal.png
/usr/share/pyshared/subdownloader/gui/images/clear-right.png
/usr/share/pyshared/subdownloader/gui/images/splash.gif
/usr/share/pyshared/subdownloader/gui/images/flags
/usr/share/pyshared/subdownloader/gui/images/flags/ka.png
/usr/share/pyshared/subdownloader/gui/images/flags/lt.png
/usr/share/pyshared/subdownloader/gui/images/flags/pb.png
/usr/share/pyshared/subdownloader/gui/images/flags/et.png
/usr/share/pyshared/subdownloader/gui/images/flags/it.png
/usr/share/pyshared/subdownloader/gui/images/flags/el.png
/usr/share/pyshared/subdownloader/gui/images/flags/ro.png
/usr/share/pyshared/subdownloader/gui/images/flags/lv.png
/usr/share/pyshared/subdownloader/gui/images/flags/ar.png
/usr/share/pyshared/subdownloader/gui/images/flags/bs.png
/usr/share/pyshared/subdownloader/gui/images/flags/is.png
/usr/share/pyshared/subdownloader/gui/images/flags/hy.png
/usr/share/pyshared/subdownloader/gui/images/flags/sk.png
/usr/share/pyshared/subdownloader/gui/images/flags/sl.png
/usr/share/pyshared/subdownloader/gui/images/flags/hi.png
/usr/share/pyshared/subdownloader/gui/images/flags/sq.png
/usr/share/pyshared/subdownloader/gui/images/flags/de.png
/usr/share/pyshared/subdownloader/gui/images/flags/ms.png
/usr/share/pyshared/subdownloader/gui/images/flags/zh.png
/usr/share/pyshared/subdownloader/gui/images/flags/da.png
/usr/share/pyshared/subdownloader/gui/images/flags/fi.png
/usr/share/pyshared/subdownloader/gui/images/flags/ca.png
/usr/share/pyshared/subdownloader/gui/images/flags/lb.png
/usr/share/pyshared/subdownloader/gui/images/flags/hr.png
/usr/share/pyshared/subdownloader/gui/images/flags/he.png
/usr/share/pyshared/subdownloader/gui/images/flags/th.png
/usr/share/pyshared/subdownloader/gui/images/flags/pl.png
/usr/share/pyshared/subdownloader/gui/images/flags/fa.png
/usr/share/pyshared/subdownloader/gui/images/flags/ru.png
/usr/share/pyshared/subdownloader/gui/images/flags/bg.png
/usr/share/pyshared/subdownloader/gui/images/flags/vi.png
/usr/share/pyshared/subdownloader/gui/images/flags/sr.png
/usr/share/pyshared/subdownloader/gui/images/flags/kk.png
/usr/share/pyshared/subdownloader/gui/images/flags/mk.png
/usr/share/pyshared/subdownloader/gui/images/flags/ko.png
/usr/share/pyshared/subdownloader/gui/images/flags/no.png
/usr/share/pyshared/subdownloader/gui/images/flags/sv.png
/usr/share/pyshared/subdownloader/gui/images/flags/cs.png
/usr/share/pyshared/subdownloader/gui/images/flags/id.png
/usr/share/pyshared/subdownloader/gui/images/flags/ja.png
/usr/share/pyshared/subdownloader/gui/images/flags/nl.png
/usr/share/pyshared/subdownloader/gui/images/flags/ay.png
/usr/share/pyshared/subdownloader/gui/images/flags/es.png
/usr/share/pyshared/subdownloader/gui/images/flags/tr.png
/usr/share/pyshared/subdownloader/gui/images/flags/hu.png
/usr/share/pyshared/subdownloader/gui/images/flags/fr.png
/usr/share/pyshared/subdownloader/gui/images/flags/pt.png
/usr/share/pyshared/subdownloader/gui/images/flags/en.png
/usr/share/pyshared/subdownloader/gui/images/subdownloader.png
/usr/share/pyshared/subdownloader/gui/images/clear.png
/usr/share/pyshared/subdownloader/gui/images/icon32.ico
/usr/share/pyshared/subdownloader/gui/images/search.png
/usr/share/pyshared/subdownloader/gui/images/play.png
/usr/share/pyshared/subdownloader/gui/images/up.png
/usr/share/pyshared/subdownloader/gui/images/splash.png
/usr/share/pyshared/subdownloader/gui/images/application-exit.png
/usr/share/pyshared/subdownloader/gui/images/sites
/usr/share/pyshared/subdownloader/gui/images/sites/opensubtitles.png
/usr/share/pyshared/subdownloader/gui/images/plus.png
/usr/share/pyshared/subdownloader/gui/images/openfolder.png
/usr/share/pyshared/subdownloader/gui/images/subdownloader.xpm
/usr/share/pyshared/subdownloader/gui/images/down.png
/usr/share/pyshared/subdownloader/gui/images/minus.png
/usr/share/pyshared/subdownloader/gui/images/open_video.png
/usr/share/pyshared/subdownloader/gui/images/delete_all.png
/usr/share/pyshared/subdownloader/gui/images/configure.png
/usr/share/pyshared/subdownloader/gui/images/bug.png
/usr/share/pyshared/subdownloader/gui/SplashScreen.py
/usr/share/pyshared/subdownloader/gui/uploadlistview.py
/usr/share/pyshared/subdownloader/gui/about.ui
/usr/share/pyshared/subdownloader/gui/imdb.ui
/usr/share/pyshared/subdownloader/gui/login_ui.py
/usr/share/pyshared/subdownloader/gui/videotreeview.py
/usr/share/pyshared/subdownloader/gui/main.py
/usr/share/pyshared/subdownloader/gui/preferences.py
/usr/share/pyshared/subdownloader/gui/login.ui
/usr/share/pyshared/subdownloader/FileManagement
/usr/share/pyshared/subdownloader/FileManagement/RecursiveParser.py
/usr/share/pyshared/subdownloader/FileManagement/Subtitle.py
/usr/share/pyshared/subdownloader/FileManagement/FileScan.py
/usr/share/pyshared/subdownloader/FileManagement/__init__.py
/usr/share/pyshared/subdownloader/FileManagement/VideoTools.py
/usr/share/pyshared/subdownloader/modules
/usr/share/pyshared/subdownloader/modules/search.py
/usr/share/pyshared/subdownloader/modules/progressbar.py
/usr/share/pyshared/subdownloader/modules/base32.py
/usr/share/pyshared/subdownloader/modules/subtitlefile.py
/usr/share/pyshared/subdownloader/modules/SDService.py
/usr/share/pyshared/subdownloader/modules/thread2.py
/usr/share/pyshared/subdownloader/modules/videofile.py
/usr/share/pyshared/subdownloader/modules/mmpython
/usr/share/pyshared/subdownloader/modules/mmpython/version.py
/usr/share/pyshared/subdownloader/modules/mmpython/synchronizedobject.py
/usr/share/pyshared/subdownloader/modules/mmpython/i18n
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/iptc
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/iptc/iptc.pot
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/iptc/en.po
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/iptc/en.mo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/qtudta
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/qtudta/en.po
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/qtudta/en.mo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/qtudta/qtudta.pot
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/aviinfo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/aviinfo/aviinfo.pot
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/aviinfo/en.po
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/aviinfo/en.mo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/id3v2
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/id3v2/en.po
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/id3v2/en.mo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/id3v2/id3v2.pot
/usr/share/pyshared/subdownloader/modules/mmpython/video
/usr/share/pyshared/subdownloader/modules/mmpython/video/movlanguages.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/mkvinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/riffinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/vcdinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/realinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/mpeginfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/ogminfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/fourcc.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/__init__.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/movinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/asfinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/mediainfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/__init__.py
/usr/share/pyshared/subdownloader/modules/mmpython/misc
/usr/share/pyshared/subdownloader/modules/mmpython/misc/__init__.py
/usr/share/pyshared/subdownloader/modules/mmpython/misc/xmlinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/table.py
/usr/share/pyshared/subdownloader/modules/mmpython/doc
/usr/share/pyshared/subdownloader/modules/mmpython/factory.py
/usr/share/pyshared/subdownloader/modules/p2plinks.py
/usr/share/pyshared/subdownloader/modules/utils.py
/usr/share/pyshared/subdownloader/modules/metadata.py
/usr/share/pyshared/subdownloader/modules/__init__.py
/usr/share/pyshared/subdownloader/modules/configuration.py
/usr/share/pyshared/subdownloader/modules/OSHttpRequests.py
/usr/share/pyshared/subdownloader/modules/filter.py
/usr/share/pyshared/subdownloader/run.py
/usr/share/pyshared/subdownloader/languages
/usr/share/pyshared/subdownloader/languages/autodetect_lang.py
/usr/share/pyshared/subdownloader/languages/lm
/usr/share/pyshared/subdownloader/languages/lm/mingo.lm
/usr/share/pyshared/subdownloader/languages/lm/breton.lm
/usr/share/pyshared/subdownloader/languages/lm/icelandic.lm
/usr/share/pyshared/subdownloader/languages/lm/irish.lm
/usr/share/pyshared/subdownloader/languages/lm/afrikaans.lm
/usr/share/pyshared/subdownloader/languages/lm/japanese-euc_jp.lm
/usr/share/pyshared/subdownloader/languages/lm/arabic-iso8859_6.lm
/usr/share/pyshared/subdownloader/languages/lm/hindi.lm
/usr/share/pyshared/subdownloader/languages/lm/Slovenian.lm
/usr/share/pyshared/subdownloader/languages/lm/russian-koi8_r.lm
/usr/share/pyshared/subdownloader/languages/lm/welsh.lm
/usr/share/pyshared/subdownloader/languages/lm/Czech.lm
/usr/share/pyshared/subdownloader/languages/lm/Bulgarian.lm
/usr/share/pyshared/subdownloader/languages/lm/portuguese.lm
/usr/share/pyshared/subdownloader/languages/lm/hungarian.lm
/usr/share/pyshared/subdownloader/languages/lm/Serbian.lm
/usr/share/pyshared/subdownloader/languages/lm/belarus-windows1251.lm
/usr/share/pyshared/subdownloader/languages/lm/basque.lm
/usr/share/pyshared/subdownloader/languages/lm/estonian.lm
/usr/share/pyshared/subdownloader/languages/lm/Slovak.lm
/usr/share/pyshared/subdownloader/languages/lm/english.lm
/usr/share/pyshared/subdownloader/languages/lm/esperanto.lm
/usr/share/pyshared/subdownloader/languages/lm/spanish.lm
/usr/share/pyshared/subdownloader/languages/lm/sanskrit.lm
/usr/share/pyshared/subdownloader/languages/lm/nepali.lm
/usr/share/pyshared/subdownloader/languages/lm/latvian.lm
/usr/share/pyshared/subdownloader/languages/lm/catalan.lm
/usr/share/pyshared/subdownloader/languages/lm/turkish.lm
/usr/share/pyshared/subdownloader/languages/lm/tagalog.lm
/usr/share/pyshared/subdownloader/languages/lm/latin.lm
/usr/share/pyshared/subdownloader/languages/lm/lithuanian.lm
/usr/share/pyshared/subdownloader/languages/lm/Japanese.lm
/usr/share/pyshared/subdownloader/languages/lm/dutch.lm
/usr/share/pyshared/subdownloader/languages/lm/swedish.lm
/usr/share/pyshared/subdownloader/languages/lm/malay.lm
/usr/share/pyshared/subdownloader/languages/lm/german.lm
/usr/share/pyshared/subdownloader/languages/lm/norwegian.lm
/usr/share/pyshared/subdownloader/languages/lm/polish.lm
/usr/share/pyshared/subdownloader/languages/lm/albanian.lm
/usr/share/pyshared/subdownloader/languages/lm/romanian.lm
/usr/share/pyshared/subdownloader/languages/lm/finnish.lm
/usr/share/pyshared/subdownloader/languages/lm/Ukrainian.lm
/usr/share/pyshared/subdownloader/languages/lm/scots_gaelic.lm
/usr/share/pyshared/subdownloader/languages/lm/italian.lm
/usr/share/pyshared/subdownloader/languages/lm/yiddish-utf.lm
/usr/share/pyshared/subdownloader/languages/lm/indonesian.lm
/usr/share/pyshared/subdownloader/languages/lm/Brazilian.lm
/usr/share/pyshared/subdownloader/languages/lm/slovenian-ascii.lm
/usr/share/pyshared/subdownloader/languages/lm/swahili.lm
/usr/share/pyshared/subdownloader/languages/lm/Russian.lm
/usr/share/pyshared/subdownloader/languages/lm/russian-iso8859_5.lm
/usr/share/pyshared/subdownloader/languages/lm/manx.lm
/usr/share/pyshared/subdownloader/languages/lm/quechua.lm
/usr/share/pyshared/subdownloader/languages/lm/amharic-utf.lm
/usr/share/pyshared/subdownloader/languages/lm/chinese-gb2312.lm
/usr/share/pyshared/subdownloader/languages/lm/Greek.lm
/usr/share/pyshared/subdownloader/languages/lm/french.lm
/usr/share/pyshared/subdownloader/languages/lm/korean.lm
/usr/share/pyshared/subdownloader/languages/lm/georgian.lm
/usr/share/pyshared/subdownloader/languages/lm/slovak-ascii.lm
/usr/share/pyshared/subdownloader/languages/lm/thai.lm
/usr/share/pyshared/subdownloader/languages/lm/Croatian.lm
/usr/share/pyshared/subdownloader/languages/lm/arabic-windows1256.lm
/usr/share/pyshared/subdownloader/languages/lm/Chinese.lm
/usr/share/pyshared/subdownloader/languages/lm/tamil.lm
/usr/share/pyshared/subdownloader/languages/lm/frisian.lm
/usr/share/pyshared/subdownloader/languages/lm/bosnian.lm
/usr/share/pyshared/subdownloader/languages/lm/rumantsch.lm
/usr/share/pyshared/subdownloader/languages/lm/armenian.lm
/usr/share/pyshared/subdownloader/languages/lm/marathi.lm
/usr/share/pyshared/subdownloader/languages/lm/vietnamese.lm
/usr/share/pyshared/subdownloader/languages/lm/Hebrew.lm
/usr/share/pyshared/subdownloader/languages/lm/persian.lm
/usr/share/pyshared/subdownloader/languages/lm/danish.lm
/usr/share/pyshared/subdownloader/languages/__init__.py
/usr/share/pyshared/subdownloader/languages/Languages.py
/usr/share/menu
/usr/share/menu/subdownloader
/usr/share/pixmaps
/usr/share/pixmaps/subdownloader.xpm
/usr/share/doc
/usr/share/doc/subdownloader
/usr/share/doc/subdownloader/README
/usr/share/doc/subdownloader/copyright
/usr/share/doc/subdownloader/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/subdownloader.1.gz
/usr/share/applications
/usr/share/applications/subdownloader.desktop
/usr/bin
/usr/lib
/usr/lib/python2.7
/usr/lib/python2.7/dist-packages
/usr/lib/python2.7/dist-packages/subdownloader
/usr/lib/python2.7/dist-packages/subdownloader/cli
/usr/lib/python2.7/dist-packages/subdownloader/gui
/usr/lib/python2.7/dist-packages/subdownloader/gui/images
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/sites
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement
/usr/lib/python2.7/dist-packages/subdownloader/modules
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/iptc
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/qtudta
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/aviinfo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/id3v2
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/misc
/usr/lib/python2.7/dist-packages/subdownloader/languages
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm
/usr/bin/subdownloader
/usr/lib/python2.7/dist-packages/subdownloader/cli/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/cli/main.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/chooseLanguage.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/imdbSearch.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/login.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/Qt2Po.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/chooseLanguage.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/images_rc.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/expiration_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/main.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/preferences.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/main_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/chooseLanguage_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/about.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/expiration.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/images.qrc
/usr/lib/python2.7/dist-packages/subdownloader/gui/expiration.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/about_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/imdblistview.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/Makefile
/usr/lib/python2.7/dist-packages/subdownloader/gui/preferences_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/imdb_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/download.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/info.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/open_folder.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/upload.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/paypal.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/clear-right.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/splash.gif
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ka.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/lt.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/pb.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/et.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/it.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/el.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ro.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/lv.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ar.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/bs.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/is.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/hy.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sk.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sl.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/hi.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sq.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/de.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ms.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/zh.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/da.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/fi.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ca.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/lb.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/hr.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/he.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/th.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/pl.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/fa.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ru.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/bg.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/vi.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sr.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/kk.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/mk.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ko.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/no.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sv.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/cs.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/id.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ja.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/nl.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ay.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/es.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/tr.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/hu.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/fr.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/pt.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/en.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/subdownloader.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/clear.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/icon32.ico
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/search.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/play.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/up.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/splash.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/application-exit.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/sites/opensubtitles.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/plus.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/openfolder.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/subdownloader.xpm
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/down.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/minus.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/open_video.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/delete_all.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/configure.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/bug.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/SplashScreen.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/uploadlistview.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/about.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/imdb.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/login_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/videotreeview.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/main.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/preferences.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/login.ui
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/RecursiveParser.py
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/Subtitle.py
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/FileScan.py
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/VideoTools.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/search.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/progressbar.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/base32.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/subtitlefile.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/SDService.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/thread2.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/videofile.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/version.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/synchronizedobject.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/iptc/iptc.pot
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/iptc/en.po
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/iptc/en.mo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/qtudta/en.po
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/qtudta/en.mo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/qtudta/qtudta.pot
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/aviinfo/aviinfo.pot
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/aviinfo/en.po
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/aviinfo/en.mo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/id3v2/en.po
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/id3v2/en.mo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/id3v2/id3v2.pot
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/movlanguages.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/mkvinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/riffinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/vcdinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/realinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/mpeginfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/ogminfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/fourcc.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/movinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/asfinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/mediainfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/misc/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/misc/xmlinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/table.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/factory.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/p2plinks.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/utils.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/metadata.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/configuration.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/OSHttpRequests.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/filter.py
/usr/lib/python2.7/dist-packages/subdownloader/run.py
/usr/lib/python2.7/dist-packages/subdownloader/languages/autodetect_lang.py
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/mingo.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/breton.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/icelandic.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/irish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/afrikaans.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/japanese-euc_jp.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/arabic-iso8859_6.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/hindi.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Slovenian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/russian-koi8_r.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/welsh.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Czech.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Bulgarian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/portuguese.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/hungarian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Serbian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/belarus-windows1251.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/basque.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/estonian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Slovak.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/english.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/esperanto.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/spanish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/sanskrit.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/nepali.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/latvian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/catalan.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/turkish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/tagalog.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/latin.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/lithuanian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Japanese.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/dutch.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/swedish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/malay.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/german.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/norwegian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/polish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/albanian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/romanian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/finnish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Ukrainian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/scots_gaelic.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/italian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/yiddish-utf.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/indonesian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Brazilian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/slovenian-ascii.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/swahili.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Russian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/russian-iso8859_5.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/manx.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/quechua.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/amharic-utf.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/chinese-gb2312.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Greek.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/french.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/korean.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/georgian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/slovak-ascii.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/thai.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Croatian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/arabic-windows1256.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Chinese.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/tamil.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/frisian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/bosnian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/rumantsch.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/armenian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/marathi.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/vietnamese.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Hebrew.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/persian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/danish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/languages/Languages.py
morten@morten-Lenovo-B50-10:~$
```

---

### Post by Odense on 2018-07-25
No one?

---

### Post by kazakore on 2018-07-25
Try starting it from the terminal and post the full output. Any error messages should be shown there.

---

### Post by Odense on 2018-07-28
morten@morten-Lenovo-B50-10:~$ cd /
morten@morten-Lenovo-B50-10:/$ cd usr/bin
morten@morten-Lenovo-B50-10:/usr/bin$ subdownloader
Traceback (most recent call last):
  File "/usr/bin/subdownloader", line 42, in <module>
    import gui.main
  File "/usr/share/pyshared/subdownloader/gui/main.py", line 9, in <module>
    from PyQt4 import QtCore, QtGui
ImportError: No module named PyQt4

---

### Post by oldos2er on 2018-07-29
Is python-qt4 installed?

---

### Post by Odense on 2018-08-01
> **oldos2er said:**
> Is python-qt4 installed?

I don't know - I assumed the instructions would mention what I need to install - or that the install process as a minimum would come up when an error message if something was missing.

How do I check and - if it is missing - correct it?

---

### Post by oldos2er on 2018-08-01
What is the output from ```
sudo apt update && sudo apt install python-qt4
``` ?

---

### Post by Odense on 2018-08-04
```
morten@morten-Lenovo-B50-10:~$ sudo apt update && sudo apt install python-qt4
[sudo] password for morten: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]
Hit:2 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:3 [http://ppa.launchpad.net/jtaylor/keepass/ubuntu](http://ppa.launchpad.net/jtaylor/keepass/ubuntu) xenial InRelease         
Hit:4 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Hit:5 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Hit:6 [http://repository.cliqz.com/dist/debian-release](http://repository.cliqz.com/dist/debian-release) stable InRelease         
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:8 [https://s3-us-west-2.amazonaws.com/brave-apt](https://s3-us-west-2.amazonaws.com/brave-apt) xenial InRelease
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [67.7 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [68.0 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [107 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [147 kB]
Fetched 496 kB in 2s (228 kB/s)                                                
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
13 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libllvm5.0 libmicrohttpd10 linux-headers-4.13.0-41
  linux-headers-4.13.0-41-generic linux-headers-4.13.0-43
  linux-headers-4.13.0-43-generic linux-image-4.13.0-41-generic
  linux-image-4.13.0-43-generic linux-image-extra-4.13.0-41-generic
  linux-image-extra-4.13.0-43-generic linux-signed-image-4.13.0-41-generic
  linux-signed-image-4.13.0-43-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libqt4-designer libqt4-help libqt4-opengl libqt4-scripttools libqt4-svg
  libqt4-test libqtassistantclient4 libqtwebkit4
Suggested packages:
  python-qt4-dbg
The following NEW packages will be installed:
  libqt4-designer libqt4-help libqt4-opengl libqt4-scripttools libqt4-svg
  libqt4-test libqtassistantclient4 libqtwebkit4 python-qt4
0 upgraded, 9 newly installed, 0 to remove and 13 not upgraded.
Need to get 15.9 MB of archives.
After this operation, 64.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/main amd64 libqt4-designer amd64 4:4.8.7+dfsg-5ubuntu2 [3,631 kB]
Get:2 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/main amd64 libqt4-help amd64 4:4.8.7+dfsg-5ubuntu2 [207 kB]
Get:3 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/main amd64 libqt4-opengl amd64 4:4.8.7+dfsg-5ubuntu2 [301 kB]
Get:4 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/main amd64 libqt4-scripttools amd64 4:4.8.7+dfsg-5ubuntu2 [224 kB]
Get:5 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/main amd64 libqt4-svg amd64 4:4.8.7+dfsg-5ubuntu2 [138 kB]
Get:6 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/main amd64 libqt4-test amd64 4:4.8.7+dfsg-5ubuntu2 [61.1 kB]
Get:7 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/universe amd64 libqtassistantclient4 amd64 4.6.3-7 [12.8 kB]
Get:8 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/universe amd64 libqtwebkit4 amd64 2.3.2-0ubuntu11 [9,034 kB]
Get:9 [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) xenial/universe amd64 python-qt4 amd64 4.11.4+dfsg-1build4 [2,328 kB]
Fetched 15.9 MB in 2s (5,343 kB/s)    
Selecting previously unselected package libqt4-designer:amd64.
(Reading database ... 311635 files and directories currently installed.)
Preparing to unpack .../libqt4-designer_4%3a4.8.7+dfsg-5ubuntu2_amd64.deb ...
Unpacking libqt4-designer:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Selecting previously unselected package libqt4-help:amd64.
Preparing to unpack .../libqt4-help_4%3a4.8.7+dfsg-5ubuntu2_amd64.deb ...
Unpacking libqt4-help:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Selecting previously unselected package libqt4-opengl:amd64.
Preparing to unpack .../libqt4-opengl_4%3a4.8.7+dfsg-5ubuntu2_amd64.deb ...
Unpacking libqt4-opengl:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Selecting previously unselected package libqt4-scripttools:amd64.
Preparing to unpack .../libqt4-scripttools_4%3a4.8.7+dfsg-5ubuntu2_amd64.deb ...
Unpacking libqt4-scripttools:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Selecting previously unselected package libqt4-svg:amd64.
Preparing to unpack .../libqt4-svg_4%3a4.8.7+dfsg-5ubuntu2_amd64.deb ...
Unpacking libqt4-svg:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Selecting previously unselected package libqt4-test:amd64.
Preparing to unpack .../libqt4-test_4%3a4.8.7+dfsg-5ubuntu2_amd64.deb ...
Unpacking libqt4-test:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Selecting previously unselected package libqtassistantclient4:amd64.
Preparing to unpack .../libqtassistantclient4_4.6.3-7_amd64.deb ...
Unpacking libqtassistantclient4:amd64 (4.6.3-7) ...
Selecting previously unselected package libqtwebkit4:amd64.
Preparing to unpack .../libqtwebkit4_2.3.2-0ubuntu11_amd64.deb ...
Unpacking libqtwebkit4:amd64 (2.3.2-0ubuntu11) ...
Selecting previously unselected package python-qt4.
Preparing to unpack .../python-qt4_4.11.4+dfsg-1build4_amd64.deb ...
Unpacking python-qt4 (4.11.4+dfsg-1build4) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Setting up libqt4-designer:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-help:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-opengl:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-scripttools:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-svg:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-test:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqtassistantclient4:amd64 (4.6.3-7) ...
Setting up libqtwebkit4:amd64 (2.3.2-0ubuntu11) ...
Setting up python-qt4 (4.11.4+dfsg-1build4) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
morten@morten-Lenovo-B50-10:~$
```

---

### Post by oldos2er on 2018-08-04
So I would try running it from a terminal again. Did you?

---

### Post by Odense on 2018-08-05
I also tried starting the program normally and it starts - nxt step is to see if it finds any subtitles.

The terminal command gave this:

```
morten@morten-Lenovo-B50-10:~$ dpkg -L subdownloader
/.
/usr
/usr/share
/usr/share/locale
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/subdownloader.mo
/usr/share/locale/el
/usr/share/locale/el/LC_MESSAGES
/usr/share/locale/el/LC_MESSAGES/subdownloader.mo
/usr/share/locale/fi
/usr/share/locale/fi/LC_MESSAGES
/usr/share/locale/fi/LC_MESSAGES/subdownloader.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/subdownloader.mo
/usr/share/locale/he
/usr/share/locale/he/LC_MESSAGES
/usr/share/locale/he/LC_MESSAGES/subdownloader.mo
/usr/share/locale/sk
/usr/share/locale/sk/LC_MESSAGES
/usr/share/locale/sk/LC_MESSAGES/subdownloader.mo
/usr/share/locale/es_ES
/usr/share/locale/es_ES/LC_MESSAGES
/usr/share/locale/es_ES/LC_MESSAGES/subdownloader.mo
/usr/share/locale/sq
/usr/share/locale/sq/LC_MESSAGES
/usr/share/locale/sq/LC_MESSAGES/subdownloader.mo
/usr/share/locale/eu
/usr/share/locale/eu/LC_MESSAGES
/usr/share/locale/eu/LC_MESSAGES/subdownloader.mo
/usr/share/locale/sr
/usr/share/locale/sr/LC_MESSAGES
/usr/share/locale/sr/LC_MESSAGES/subdownloader.mo
/usr/share/locale/hr
/usr/share/locale/hr/LC_MESSAGES
/usr/share/locale/hr/LC_MESSAGES/subdownloader.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/subdownloader.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/subdownloader.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/subdownloader.mo
/usr/share/locale/ko
/usr/share/locale/ko/LC_MESSAGES
/usr/share/locale/ko/LC_MESSAGES/subdownloader.mo
/usr/share/locale/bg
/usr/share/locale/bg/LC_MESSAGES
/usr/share/locale/bg/LC_MESSAGES/subdownloader.mo
/usr/share/locale/tr
/usr/share/locale/tr/LC_MESSAGES
/usr/share/locale/tr/LC_MESSAGES/subdownloader.mo
/usr/share/locale/gl
/usr/share/locale/gl/LC_MESSAGES
/usr/share/locale/gl/LC_MESSAGES/subdownloader.mo
/usr/share/locale/et
/usr/share/locale/et/LC_MESSAGES
/usr/share/locale/et/LC_MESSAGES/subdownloader.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/subdownloader.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/subdownloader.mo
/usr/share/locale/pt_PT
/usr/share/locale/pt_PT/LC_MESSAGES
/usr/share/locale/pt_PT/LC_MESSAGES/subdownloader.mo
/usr/share/locale/vi
/usr/share/locale/vi/LC_MESSAGES
/usr/share/locale/vi/LC_MESSAGES/subdownloader.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/subdownloader.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/subdownloader.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/subdownloader.mo
/usr/share/locale/en
/usr/share/locale/en/LC_MESSAGES
/usr/share/locale/en/LC_MESSAGES/subdownloader.mo
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/subdownloader.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/subdownloader.mo
/usr/share/locale/mk
/usr/share/locale/mk/LC_MESSAGES
/usr/share/locale/mk/LC_MESSAGES/subdownloader.mo
/usr/share/locale/id
/usr/share/locale/id/LC_MESSAGES
/usr/share/locale/id/LC_MESSAGES/subdownloader.mo
/usr/share/locale/ro
/usr/share/locale/ro/LC_MESSAGES
/usr/share/locale/ro/LC_MESSAGES/subdownloader.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/subdownloader.mo
/usr/share/pyshared
/usr/share/pyshared/subdownloader
/usr/share/pyshared/subdownloader/cli
/usr/share/pyshared/subdownloader/cli/__init__.py
/usr/share/pyshared/subdownloader/cli/main.py
/usr/share/pyshared/subdownloader/gui
/usr/share/pyshared/subdownloader/gui/chooseLanguage.py
/usr/share/pyshared/subdownloader/gui/imdbSearch.py
/usr/share/pyshared/subdownloader/gui/login.py
/usr/share/pyshared/subdownloader/gui/Qt2Po.py
/usr/share/pyshared/subdownloader/gui/chooseLanguage.ui
/usr/share/pyshared/subdownloader/gui/images_rc.py
/usr/share/pyshared/subdownloader/gui/expiration_ui.py
/usr/share/pyshared/subdownloader/gui/main.ui
/usr/share/pyshared/subdownloader/gui/preferences.ui
/usr/share/pyshared/subdownloader/gui/main_ui.py
/usr/share/pyshared/subdownloader/gui/chooseLanguage_ui.py
/usr/share/pyshared/subdownloader/gui/about.py
/usr/share/pyshared/subdownloader/gui/expiration.py
/usr/share/pyshared/subdownloader/gui/images.qrc
/usr/share/pyshared/subdownloader/gui/expiration.ui
/usr/share/pyshared/subdownloader/gui/about_ui.py
/usr/share/pyshared/subdownloader/gui/imdblistview.py
/usr/share/pyshared/subdownloader/gui/__init__.py
/usr/share/pyshared/subdownloader/gui/Makefile
/usr/share/pyshared/subdownloader/gui/preferences_ui.py
/usr/share/pyshared/subdownloader/gui/imdb_ui.py
/usr/share/pyshared/subdownloader/gui/images
/usr/share/pyshared/subdownloader/gui/images/download.png
/usr/share/pyshared/subdownloader/gui/images/info.png
/usr/share/pyshared/subdownloader/gui/images/open_folder.png
/usr/share/pyshared/subdownloader/gui/images/upload.png
/usr/share/pyshared/subdownloader/gui/images/paypal.png
/usr/share/pyshared/subdownloader/gui/images/clear-right.png
/usr/share/pyshared/subdownloader/gui/images/splash.gif
/usr/share/pyshared/subdownloader/gui/images/flags
/usr/share/pyshared/subdownloader/gui/images/flags/ka.png
/usr/share/pyshared/subdownloader/gui/images/flags/lt.png
/usr/share/pyshared/subdownloader/gui/images/flags/pb.png
/usr/share/pyshared/subdownloader/gui/images/flags/et.png
/usr/share/pyshared/subdownloader/gui/images/flags/it.png
/usr/share/pyshared/subdownloader/gui/images/flags/el.png
/usr/share/pyshared/subdownloader/gui/images/flags/ro.png
/usr/share/pyshared/subdownloader/gui/images/flags/lv.png
/usr/share/pyshared/subdownloader/gui/images/flags/ar.png
/usr/share/pyshared/subdownloader/gui/images/flags/bs.png
/usr/share/pyshared/subdownloader/gui/images/flags/is.png
/usr/share/pyshared/subdownloader/gui/images/flags/hy.png
/usr/share/pyshared/subdownloader/gui/images/flags/sk.png
/usr/share/pyshared/subdownloader/gui/images/flags/sl.png
/usr/share/pyshared/subdownloader/gui/images/flags/hi.png
/usr/share/pyshared/subdownloader/gui/images/flags/sq.png
/usr/share/pyshared/subdownloader/gui/images/flags/de.png
/usr/share/pyshared/subdownloader/gui/images/flags/ms.png
/usr/share/pyshared/subdownloader/gui/images/flags/zh.png
/usr/share/pyshared/subdownloader/gui/images/flags/da.png
/usr/share/pyshared/subdownloader/gui/images/flags/fi.png
/usr/share/pyshared/subdownloader/gui/images/flags/ca.png
/usr/share/pyshared/subdownloader/gui/images/flags/lb.png
/usr/share/pyshared/subdownloader/gui/images/flags/hr.png
/usr/share/pyshared/subdownloader/gui/images/flags/he.png
/usr/share/pyshared/subdownloader/gui/images/flags/th.png
/usr/share/pyshared/subdownloader/gui/images/flags/pl.png
/usr/share/pyshared/subdownloader/gui/images/flags/fa.png
/usr/share/pyshared/subdownloader/gui/images/flags/ru.png
/usr/share/pyshared/subdownloader/gui/images/flags/bg.png
/usr/share/pyshared/subdownloader/gui/images/flags/vi.png
/usr/share/pyshared/subdownloader/gui/images/flags/sr.png
/usr/share/pyshared/subdownloader/gui/images/flags/kk.png
/usr/share/pyshared/subdownloader/gui/images/flags/mk.png
/usr/share/pyshared/subdownloader/gui/images/flags/ko.png
/usr/share/pyshared/subdownloader/gui/images/flags/no.png
/usr/share/pyshared/subdownloader/gui/images/flags/sv.png
/usr/share/pyshared/subdownloader/gui/images/flags/cs.png
/usr/share/pyshared/subdownloader/gui/images/flags/id.png
/usr/share/pyshared/subdownloader/gui/images/flags/ja.png
/usr/share/pyshared/subdownloader/gui/images/flags/nl.png
/usr/share/pyshared/subdownloader/gui/images/flags/ay.png
/usr/share/pyshared/subdownloader/gui/images/flags/es.png
/usr/share/pyshared/subdownloader/gui/images/flags/tr.png
/usr/share/pyshared/subdownloader/gui/images/flags/hu.png
/usr/share/pyshared/subdownloader/gui/images/flags/fr.png
/usr/share/pyshared/subdownloader/gui/images/flags/pt.png
/usr/share/pyshared/subdownloader/gui/images/flags/en.png
/usr/share/pyshared/subdownloader/gui/images/subdownloader.png
/usr/share/pyshared/subdownloader/gui/images/clear.png
/usr/share/pyshared/subdownloader/gui/images/icon32.ico
/usr/share/pyshared/subdownloader/gui/images/search.png
/usr/share/pyshared/subdownloader/gui/images/play.png
/usr/share/pyshared/subdownloader/gui/images/up.png
/usr/share/pyshared/subdownloader/gui/images/splash.png
/usr/share/pyshared/subdownloader/gui/images/application-exit.png
/usr/share/pyshared/subdownloader/gui/images/sites
/usr/share/pyshared/subdownloader/gui/images/sites/opensubtitles.png
/usr/share/pyshared/subdownloader/gui/images/plus.png
/usr/share/pyshared/subdownloader/gui/images/openfolder.png
/usr/share/pyshared/subdownloader/gui/images/subdownloader.xpm
/usr/share/pyshared/subdownloader/gui/images/down.png
/usr/share/pyshared/subdownloader/gui/images/minus.png
/usr/share/pyshared/subdownloader/gui/images/open_video.png
/usr/share/pyshared/subdownloader/gui/images/delete_all.png
/usr/share/pyshared/subdownloader/gui/images/configure.png
/usr/share/pyshared/subdownloader/gui/images/bug.png
/usr/share/pyshared/subdownloader/gui/SplashScreen.py
/usr/share/pyshared/subdownloader/gui/uploadlistview.py
/usr/share/pyshared/subdownloader/gui/about.ui
/usr/share/pyshared/subdownloader/gui/imdb.ui
/usr/share/pyshared/subdownloader/gui/login_ui.py
/usr/share/pyshared/subdownloader/gui/videotreeview.py
/usr/share/pyshared/subdownloader/gui/main.py
/usr/share/pyshared/subdownloader/gui/preferences.py
/usr/share/pyshared/subdownloader/gui/login.ui
/usr/share/pyshared/subdownloader/FileManagement
/usr/share/pyshared/subdownloader/FileManagement/RecursiveParser.py
/usr/share/pyshared/subdownloader/FileManagement/Subtitle.py
/usr/share/pyshared/subdownloader/FileManagement/FileScan.py
/usr/share/pyshared/subdownloader/FileManagement/__init__.py
/usr/share/pyshared/subdownloader/FileManagement/VideoTools.py
/usr/share/pyshared/subdownloader/modules
/usr/share/pyshared/subdownloader/modules/search.py
/usr/share/pyshared/subdownloader/modules/progressbar.py
/usr/share/pyshared/subdownloader/modules/base32.py
/usr/share/pyshared/subdownloader/modules/subtitlefile.py
/usr/share/pyshared/subdownloader/modules/SDService.py
/usr/share/pyshared/subdownloader/modules/thread2.py
/usr/share/pyshared/subdownloader/modules/videofile.py
/usr/share/pyshared/subdownloader/modules/mmpython
/usr/share/pyshared/subdownloader/modules/mmpython/version.py
/usr/share/pyshared/subdownloader/modules/mmpython/synchronizedobject.py
/usr/share/pyshared/subdownloader/modules/mmpython/i18n
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/iptc
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/iptc/iptc.pot
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/iptc/en.po
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/iptc/en.mo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/qtudta
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/qtudta/en.po
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/qtudta/en.mo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/qtudta/qtudta.pot
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/aviinfo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/aviinfo/aviinfo.pot
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/aviinfo/en.po
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/aviinfo/en.mo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/id3v2
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/id3v2/en.po
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/id3v2/en.mo
/usr/share/pyshared/subdownloader/modules/mmpython/i18n/id3v2/id3v2.pot
/usr/share/pyshared/subdownloader/modules/mmpython/video
/usr/share/pyshared/subdownloader/modules/mmpython/video/movlanguages.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/mkvinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/riffinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/vcdinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/realinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/mpeginfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/ogminfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/fourcc.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/__init__.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/movinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/video/asfinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/mediainfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/__init__.py
/usr/share/pyshared/subdownloader/modules/mmpython/misc
/usr/share/pyshared/subdownloader/modules/mmpython/misc/__init__.py
/usr/share/pyshared/subdownloader/modules/mmpython/misc/xmlinfo.py
/usr/share/pyshared/subdownloader/modules/mmpython/table.py
/usr/share/pyshared/subdownloader/modules/mmpython/doc
/usr/share/pyshared/subdownloader/modules/mmpython/factory.py
/usr/share/pyshared/subdownloader/modules/p2plinks.py
/usr/share/pyshared/subdownloader/modules/utils.py
/usr/share/pyshared/subdownloader/modules/metadata.py
/usr/share/pyshared/subdownloader/modules/__init__.py
/usr/share/pyshared/subdownloader/modules/configuration.py
/usr/share/pyshared/subdownloader/modules/OSHttpRequests.py
/usr/share/pyshared/subdownloader/modules/filter.py
/usr/share/pyshared/subdownloader/run.py
/usr/share/pyshared/subdownloader/languages
/usr/share/pyshared/subdownloader/languages/autodetect_lang.py
/usr/share/pyshared/subdownloader/languages/lm
/usr/share/pyshared/subdownloader/languages/lm/mingo.lm
/usr/share/pyshared/subdownloader/languages/lm/breton.lm
/usr/share/pyshared/subdownloader/languages/lm/icelandic.lm
/usr/share/pyshared/subdownloader/languages/lm/irish.lm
/usr/share/pyshared/subdownloader/languages/lm/afrikaans.lm
/usr/share/pyshared/subdownloader/languages/lm/japanese-euc_jp.lm
/usr/share/pyshared/subdownloader/languages/lm/arabic-iso8859_6.lm
/usr/share/pyshared/subdownloader/languages/lm/hindi.lm
/usr/share/pyshared/subdownloader/languages/lm/Slovenian.lm
/usr/share/pyshared/subdownloader/languages/lm/russian-koi8_r.lm
/usr/share/pyshared/subdownloader/languages/lm/welsh.lm
/usr/share/pyshared/subdownloader/languages/lm/Czech.lm
/usr/share/pyshared/subdownloader/languages/lm/Bulgarian.lm
/usr/share/pyshared/subdownloader/languages/lm/portuguese.lm
/usr/share/pyshared/subdownloader/languages/lm/hungarian.lm
/usr/share/pyshared/subdownloader/languages/lm/Serbian.lm
/usr/share/pyshared/subdownloader/languages/lm/belarus-windows1251.lm
/usr/share/pyshared/subdownloader/languages/lm/basque.lm
/usr/share/pyshared/subdownloader/languages/lm/estonian.lm
/usr/share/pyshared/subdownloader/languages/lm/Slovak.lm
/usr/share/pyshared/subdownloader/languages/lm/english.lm
/usr/share/pyshared/subdownloader/languages/lm/esperanto.lm
/usr/share/pyshared/subdownloader/languages/lm/spanish.lm
/usr/share/pyshared/subdownloader/languages/lm/sanskrit.lm
/usr/share/pyshared/subdownloader/languages/lm/nepali.lm
/usr/share/pyshared/subdownloader/languages/lm/latvian.lm
/usr/share/pyshared/subdownloader/languages/lm/catalan.lm
/usr/share/pyshared/subdownloader/languages/lm/turkish.lm
/usr/share/pyshared/subdownloader/languages/lm/tagalog.lm
/usr/share/pyshared/subdownloader/languages/lm/latin.lm
/usr/share/pyshared/subdownloader/languages/lm/lithuanian.lm
/usr/share/pyshared/subdownloader/languages/lm/Japanese.lm
/usr/share/pyshared/subdownloader/languages/lm/dutch.lm
/usr/share/pyshared/subdownloader/languages/lm/swedish.lm
/usr/share/pyshared/subdownloader/languages/lm/malay.lm
/usr/share/pyshared/subdownloader/languages/lm/german.lm
/usr/share/pyshared/subdownloader/languages/lm/norwegian.lm
/usr/share/pyshared/subdownloader/languages/lm/polish.lm
/usr/share/pyshared/subdownloader/languages/lm/albanian.lm
/usr/share/pyshared/subdownloader/languages/lm/romanian.lm
/usr/share/pyshared/subdownloader/languages/lm/finnish.lm
/usr/share/pyshared/subdownloader/languages/lm/Ukrainian.lm
/usr/share/pyshared/subdownloader/languages/lm/scots_gaelic.lm
/usr/share/pyshared/subdownloader/languages/lm/italian.lm
/usr/share/pyshared/subdownloader/languages/lm/yiddish-utf.lm
/usr/share/pyshared/subdownloader/languages/lm/indonesian.lm
/usr/share/pyshared/subdownloader/languages/lm/Brazilian.lm
/usr/share/pyshared/subdownloader/languages/lm/slovenian-ascii.lm
/usr/share/pyshared/subdownloader/languages/lm/swahili.lm
/usr/share/pyshared/subdownloader/languages/lm/Russian.lm
/usr/share/pyshared/subdownloader/languages/lm/russian-iso8859_5.lm
/usr/share/pyshared/subdownloader/languages/lm/manx.lm
/usr/share/pyshared/subdownloader/languages/lm/quechua.lm
/usr/share/pyshared/subdownloader/languages/lm/amharic-utf.lm
/usr/share/pyshared/subdownloader/languages/lm/chinese-gb2312.lm
/usr/share/pyshared/subdownloader/languages/lm/Greek.lm
/usr/share/pyshared/subdownloader/languages/lm/french.lm
/usr/share/pyshared/subdownloader/languages/lm/korean.lm
/usr/share/pyshared/subdownloader/languages/lm/georgian.lm
/usr/share/pyshared/subdownloader/languages/lm/slovak-ascii.lm
/usr/share/pyshared/subdownloader/languages/lm/thai.lm
/usr/share/pyshared/subdownloader/languages/lm/Croatian.lm
/usr/share/pyshared/subdownloader/languages/lm/arabic-windows1256.lm
/usr/share/pyshared/subdownloader/languages/lm/Chinese.lm
/usr/share/pyshared/subdownloader/languages/lm/tamil.lm
/usr/share/pyshared/subdownloader/languages/lm/frisian.lm
/usr/share/pyshared/subdownloader/languages/lm/bosnian.lm
/usr/share/pyshared/subdownloader/languages/lm/rumantsch.lm
/usr/share/pyshared/subdownloader/languages/lm/armenian.lm
/usr/share/pyshared/subdownloader/languages/lm/marathi.lm
/usr/share/pyshared/subdownloader/languages/lm/vietnamese.lm
/usr/share/pyshared/subdownloader/languages/lm/Hebrew.lm
/usr/share/pyshared/subdownloader/languages/lm/persian.lm
/usr/share/pyshared/subdownloader/languages/lm/danish.lm
/usr/share/pyshared/subdownloader/languages/__init__.py
/usr/share/pyshared/subdownloader/languages/Languages.py
/usr/share/menu
/usr/share/menu/subdownloader
/usr/share/pixmaps
/usr/share/pixmaps/subdownloader.xpm
/usr/share/doc
/usr/share/doc/subdownloader
/usr/share/doc/subdownloader/README
/usr/share/doc/subdownloader/copyright
/usr/share/doc/subdownloader/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/subdownloader.1.gz
/usr/share/applications
/usr/share/applications/subdownloader.desktop
/usr/bin
/usr/lib
/usr/lib/python2.7
/usr/lib/python2.7/dist-packages
/usr/lib/python2.7/dist-packages/subdownloader
/usr/lib/python2.7/dist-packages/subdownloader/cli
/usr/lib/python2.7/dist-packages/subdownloader/gui
/usr/lib/python2.7/dist-packages/subdownloader/gui/images
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/sites
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement
/usr/lib/python2.7/dist-packages/subdownloader/modules
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/iptc
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/qtudta
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/aviinfo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/id3v2
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/misc
/usr/lib/python2.7/dist-packages/subdownloader/languages
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm
/usr/bin/subdownloader
/usr/lib/python2.7/dist-packages/subdownloader/cli/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/cli/main.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/chooseLanguage.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/imdbSearch.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/login.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/Qt2Po.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/chooseLanguage.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/images_rc.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/expiration_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/main.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/preferences.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/main_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/chooseLanguage_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/about.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/expiration.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/images.qrc
/usr/lib/python2.7/dist-packages/subdownloader/gui/expiration.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/about_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/imdblistview.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/Makefile
/usr/lib/python2.7/dist-packages/subdownloader/gui/preferences_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/imdb_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/download.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/info.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/open_folder.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/upload.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/paypal.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/clear-right.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/splash.gif
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ka.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/lt.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/pb.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/et.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/it.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/el.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ro.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/lv.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ar.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/bs.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/is.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/hy.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sk.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sl.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/hi.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sq.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/de.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ms.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/zh.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/da.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/fi.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ca.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/lb.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/hr.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/he.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/th.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/pl.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/fa.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ru.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/bg.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/vi.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sr.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/kk.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/mk.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ko.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/no.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/sv.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/cs.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/id.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ja.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/nl.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/ay.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/es.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/tr.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/hu.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/fr.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/pt.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/flags/en.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/subdownloader.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/clear.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/icon32.ico
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/search.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/play.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/up.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/splash.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/application-exit.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/sites/opensubtitles.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/plus.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/openfolder.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/subdownloader.xpm
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/down.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/minus.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/open_video.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/delete_all.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/configure.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/images/bug.png
/usr/lib/python2.7/dist-packages/subdownloader/gui/SplashScreen.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/uploadlistview.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/about.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/imdb.ui
/usr/lib/python2.7/dist-packages/subdownloader/gui/login_ui.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/videotreeview.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/main.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/preferences.py
/usr/lib/python2.7/dist-packages/subdownloader/gui/login.ui
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/RecursiveParser.py
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/Subtitle.py
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/FileScan.py
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/FileManagement/VideoTools.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/search.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/progressbar.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/base32.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/subtitlefile.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/SDService.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/thread2.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/videofile.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/version.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/synchronizedobject.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/iptc/iptc.pot
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/iptc/en.po
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/iptc/en.mo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/qtudta/en.po
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/qtudta/en.mo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/qtudta/qtudta.pot
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/aviinfo/aviinfo.pot
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/aviinfo/en.po
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/aviinfo/en.mo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/id3v2/en.po
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/id3v2/en.mo
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/i18n/id3v2/id3v2.pot
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/movlanguages.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/mkvinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/riffinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/vcdinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/realinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/mpeginfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/ogminfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/fourcc.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/movinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/video/asfinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/mediainfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/misc/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/misc/xmlinfo.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/table.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/mmpython/factory.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/p2plinks.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/utils.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/metadata.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/configuration.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/OSHttpRequests.py
/usr/lib/python2.7/dist-packages/subdownloader/modules/filter.py
/usr/lib/python2.7/dist-packages/subdownloader/run.py
/usr/lib/python2.7/dist-packages/subdownloader/languages/autodetect_lang.py
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/mingo.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/breton.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/icelandic.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/irish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/afrikaans.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/japanese-euc_jp.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/arabic-iso8859_6.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/hindi.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Slovenian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/russian-koi8_r.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/welsh.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Czech.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Bulgarian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/portuguese.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/hungarian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Serbian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/belarus-windows1251.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/basque.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/estonian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Slovak.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/english.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/esperanto.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/spanish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/sanskrit.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/nepali.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/latvian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/catalan.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/turkish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/tagalog.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/latin.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/lithuanian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Japanese.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/dutch.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/swedish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/malay.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/german.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/norwegian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/polish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/albanian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/romanian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/finnish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Ukrainian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/scots_gaelic.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/italian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/yiddish-utf.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/indonesian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Brazilian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/slovenian-ascii.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/swahili.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Russian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/russian-iso8859_5.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/manx.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/quechua.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/amharic-utf.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/chinese-gb2312.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Greek.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/french.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/korean.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/georgian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/slovak-ascii.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/thai.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Croatian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/arabic-windows1256.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Chinese.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/tamil.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/frisian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/bosnian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/rumantsch.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/armenian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/marathi.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/vietnamese.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/Hebrew.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/persian.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/lm/danish.lm
/usr/lib/python2.7/dist-packages/subdownloader/languages/__init__.py
/usr/lib/python2.7/dist-packages/subdownloader/languages/Languages.py
morten@morten-Lenovo-B50-10:~$
```

---

### Post by oldos2er on 2018-08-05
Please use [code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") to contain large terminal output; they make such posts far more readable than they otherwise would be.

If your problem is solved, please mark it so under Thread Tools at the top of the page. Thanks.

---

### Post by Odense on 2018-08-06
OK - I will try to remember that.

---

