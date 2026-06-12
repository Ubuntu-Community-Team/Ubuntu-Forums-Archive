---
title: "Installing Chinese Language Pack?"
date: 2013-10-31
forum: General Help
---

### Post by Kirk Schnable on 2013-10-31
I have been trying to get a Chinese language pack installed on our Xubuntu 12.04 machines.  We have a Chinese class here, and they would like to be able to type in Chinese.  In the past, I've been able to use a keyboard layout package, and place a keymap changer on one of the panels, but I am having some issues doing so now.

These are my relevant installed packages (*dpkg --list | grep lang*)
> ii  bc                                            1.06.95-2                               The GNU bc arbitrary precision calculator language
ii  chromium-browser-l10n                         28.0.1500.71-0ubuntu1.12.04.1           chromium-browser language packages
ii  firefox-locale-en                             24.0+build1-0ubuntu0.12.04.1            English language pack for Firefox
ii  firefox-locale-zh-hans                        24.0+build1-0ubuntu0.12.04.1            Simplified Chinese language pack for Firefox
ii  firefox-locale-zh-hant                        24.0+build1-0ubuntu0.12.04.1            Traditional Chinese language pack for Firefox
ii  firefox-locale-zu                             24.0+build1-0ubuntu0.12.04.1            Zulu language pack for Firefox
ii  fonts-droid                                   20101110+git-2                          handheld device font with extensive style and language support
ii  fonts-dzongkha                                0.3-7                                   TrueType fonts for Dzongkha language
ii  fonts-farsiweb                                0.4.dfsg-11                             free TrueType fonts for Persian language
ii  fonts-kacst-one                               5.0+svn11846-2                          TrueType font designed for Arabic language
ii  fonts-khmeros                                 5.0-5ubuntu1                            KhmerOS Unicode fonts for the Khmer language of Cambodia
ii  fonts-khmeros-core                            5.0-5ubuntu1                            KhmerOS Unicode fonts for the Khmer language of Cambodia
ii  fonts-lao                                     0.0.20060226-8                          TrueType font for Lao language
ii  gawk                                          1:3.1.8+dfsg-0.1ubuntu1                 GNU awk, a pattern scanning and processing language
ii  ghostscript                                   9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF
ii  ghostscript-cups                              9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - CUPS filters
ii  ghostscript-x                                 9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - X11 support
ii  iso-codes                                     3.31-1                                  ISO language, territory, currency, script codes and their translations
ii  language-pack-en                              1:12.04+20130128                        translation updates for language English
ii  language-pack-en-base                         1:12.04+20130128                        translations for language English
ii  language-pack-gnome-en                        1:12.04+20130128                        GNOME translation updates for language English
ii  language-pack-gnome-en-base                   1:12.04+20130128                        GNOME translations for language English
ii  language-pack-gnome-zh-hans                   1:12.04+20130128                        GNOME translation updates for language Simplified Chinese
ii  language-pack-gnome-zh-hans-base              1:12.04+20130128                        GNOME translations for language Simplified Chinese
ii  language-pack-gnome-zh-hant                   1:12.04+20130128                        GNOME translation updates for language Traditional Chinese
ii  language-pack-gnome-zh-hant-base              1:12.04+20130128                        GNOME translations for language Traditional Chinese
ii  language-pack-gnome-zu                        1:12.04+20130128                        GNOME translation updates for language Zulu
ii  language-pack-gnome-zu-base                   1:12.04+20130128                        GNOME translations for language Zulu
ii  language-pack-kde-en                          1:12.04+20130128                        KDE translation updates for language English
ii  language-pack-kde-en-base                     1:12.04+20130128                        KDE translations for language English
ii  language-pack-kde-zh-hans                     1:12.04+20130128                        KDE translation updates for language Simplified Chinese
ii  language-pack-kde-zh-hans-base                1:12.04+20130128                        KDE translations for language Simplified Chinese
ii  language-pack-kde-zh-hant                     1:12.04+20130128                        KDE translation updates for language Traditional Chinese
ii  language-pack-kde-zh-hant-base                1:12.04+20130128                        KDE translations for language Traditional Chinese
ii  language-pack-zh-hans                         1:12.04+20130128                        translation updates for language Simplified Chinese
ii  language-pack-zh-hans-base                    1:12.04+20130128                        translations for language Simplified Chinese
ii  language-pack-zh-hant                         1:12.04+20130128                        translation updates for language Traditional Chinese
ii  language-pack-zh-hant-base                    1:12.04+20130128                        translations for language Traditional Chinese
ii  language-pack-zu                              1:12.04+20130128                        translation updates for language Zulu
ii  language-pack-zu-base                         1:12.04+20130128                        translations for language Zulu
ii  language-selector-common                      0.79.4                                  Language selector for Ubuntu
ii  language-selector-gnome                       0.79.4                                  Language selector for Ubuntu
ii  libapache2-mod-php5                           5.3.10-1ubuntu3.8                       server-side, HTML-embedded scripting language (Apache 2 module)
ii  libaugeas-ruby1.8                             0.3.0-1.1ubuntu4                        Augeas bindings for the Ruby language
ii  libcommons-lang-java                          2.6-3ubuntu1                            Extension of the java.lang package
ii  libgs9                                        9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - Library
ii  libgs9-common                                 9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - common files
ii  libnewt0.52                                   0.52.11-2ubuntu10                       Not Erik's Windowing Toolkit - text mode windowing with slang
ii  libreoffice-l10n-af                           1:3.5.7-0ubuntu4                        office productivity suite -- Afrikaans language package
ii  libreoffice-l10n-ar                           1:3.5.7-0ubuntu4                        office productivity suite -- Arabic language package
ii  libreoffice-l10n-as                           1:3.5.7-0ubuntu4                        office productivity suite -- Assamese language package
ii  libreoffice-l10n-ast                          1:3.5.7-0ubuntu4                        office productivity suite -- Asturian language package
ii  libreoffice-l10n-be                           1:3.5.7-0ubuntu4                        office productivity suite -- Belarussian language package
ii  libreoffice-l10n-bg                           1:3.5.7-0ubuntu4                        office productivity suite -- Bulgarian language package
ii  libreoffice-l10n-bn                           1:3.5.7-0ubuntu4                        office productivity suite -- Bengali language package
ii  libreoffice-l10n-br                           1:3.5.7-0ubuntu4                        office productivity suite -- Breton language package
ii  libreoffice-l10n-bs                           1:3.5.7-0ubuntu4                        office productivity suite -- Bosnian language package
ii  libreoffice-l10n-ca                           1:3.5.7-0ubuntu4                        office productivity suite -- Catalan language package
ii  libreoffice-l10n-cs                           1:3.5.7-0ubuntu4                        office productivity suite -- Czech language package
ii  libreoffice-l10n-cy                           1:3.5.7-0ubuntu4                        office productivity suite -- Welsh language package
ii  libreoffice-l10n-da                           1:3.5.7-0ubuntu4                        office productivity suite -- Danish language package
ii  libreoffice-l10n-de                           1:3.5.7-0ubuntu4                        office productivity suite -- German language package
ii  libreoffice-l10n-dz                           1:3.5.7-0ubuntu4                        office productivity suite -- Dzongkha language package
ii  libreoffice-l10n-el                           1:3.5.7-0ubuntu4                        office productivity suite -- Greek language package
ii  libreoffice-l10n-en-gb                        1:3.5.7-0ubuntu4                        office productivity suite -- English_british language package
ii  libreoffice-l10n-en-za                        1:3.5.7-0ubuntu4                        office productivity suite -- English_southafrican language package
ii  libreoffice-l10n-eo                           1:3.5.7-0ubuntu4                        office productivity suite -- Esperanto language package
ii  libreoffice-l10n-es                           1:3.5.7-0ubuntu4                        office productivity suite -- Spanish language package
ii  libreoffice-l10n-et                           1:3.5.7-0ubuntu4                        office productivity suite -- Estonian language package
ii  libreoffice-l10n-eu                           1:3.5.7-0ubuntu4                        office productivity suite -- Basque language package
ii  libreoffice-l10n-fa                           1:3.5.7-0ubuntu4                        office productivity suite -- Farsi language package
ii  libreoffice-l10n-fi                           1:3.5.7-0ubuntu4                        office productivity suite -- Finnish language package
ii  libreoffice-l10n-fr                           1:3.5.7-0ubuntu4                        office productivity suite -- French language package
ii  libreoffice-l10n-ga                           1:3.5.7-0ubuntu4                        office productivity suite -- Gaelic language package
ii  libreoffice-l10n-gl                           1:3.5.7-0ubuntu4                        office productivity suite -- Galician language package
ii  libreoffice-l10n-gu                           1:3.5.7-0ubuntu4                        office productivity suite -- Gujarati language package
ii  libreoffice-l10n-he                           1:3.5.7-0ubuntu4                        office productivity suite -- Hebrew language package
ii  libreoffice-l10n-hi                           1:3.5.7-0ubuntu4                        office productivity suite -- Hindi language package
ii  libreoffice-l10n-hr                           1:3.5.7-0ubuntu4                        office productivity suite -- Croatian language package
ii  libreoffice-l10n-hu                           1:3.5.7-0ubuntu4                        office productivity suite -- Hungarian language package
ii  libreoffice-l10n-id                           1:3.5.7-0ubuntu4                        office productivity suite -- Indonesian language package
ii  libreoffice-l10n-in                           1:3.5.7-0ubuntu4                        office productivity suite -- Indic language packages
ii  libreoffice-l10n-is                           1:3.5.7-0ubuntu4                        office productivity suite -- Icelandic language package
ii  libreoffice-l10n-it                           1:3.5.7-0ubuntu4                        office productivity suite -- Italian language package
ii  libreoffice-l10n-ja                           1:3.5.7-0ubuntu4                        office productivity suite -- Japanese language package
ii  libreoffice-l10n-ka                           1:3.5.7-0ubuntu4                        office productivity suite -- Georgian language package
ii  libreoffice-l10n-km                           1:3.5.7-0ubuntu4                        office productivity suite -- Khmer language package
ii  libreoffice-l10n-ko                           1:3.5.7-0ubuntu4                        office productivity suite -- Korean language package
ii  libreoffice-l10n-ku                           1:3.5.7-0ubuntu4                        office productivity suite -- Kurdish language package
ii  libreoffice-l10n-lt                           1:3.5.7-0ubuntu4                        office productivity suite -- Lithuanian language package
ii  libreoffice-l10n-lv                           1:3.5.7-0ubuntu4                        office productivity suite -- Latvian language package
ii  libreoffice-l10n-mk                           1:3.5.7-0ubuntu4                        office productivity suite -- Macedonian language package
ii  libreoffice-l10n-ml                           1:3.5.7-0ubuntu4                        office productivity suite -- Malayalam language package
ii  libreoffice-l10n-mn                           1:3.5.7-0ubuntu4                        office productivity suite -- Mongolian language package
ii  libreoffice-l10n-mr                           1:3.5.7-0ubuntu4                        office productivity suite -- Marathi language package
ii  libreoffice-l10n-nb                           1:3.5.7-0ubuntu4                        office productivity suite -- Norwegian language package
ii  libreoffice-l10n-ne                           1:3.5.7-0ubuntu4                        office productivity suite -- Nepalese language package
ii  libreoffice-l10n-nl                           1:3.5.7-0ubuntu4                        office productivity suite -- Dutch language package
ii  libreoffice-l10n-nn                           1:3.5.7-0ubuntu4                        office productivity suite -- Norwegian_nynorsk language package
ii  libreoffice-l10n-nr                           1:3.5.7-0ubuntu4                        office productivity suite -- Ndebele language package
ii  libreoffice-l10n-nso                          1:3.5.7-0ubuntu4                        office productivity suite -- Northern_sotho language package
ii  libreoffice-l10n-oc                           1:3.5.7-0ubuntu4                        office productivity suite -- Occitan language package
ii  libreoffice-l10n-om                           1:3.5.7-0ubuntu4                        office productivity suite -- Oromo language package
ii  libreoffice-l10n-or                           1:3.5.7-0ubuntu4                        office productivity suite -- Oriya language package
ii  libreoffice-l10n-pa-in                        1:3.5.7-0ubuntu4                        office productivity suite -- Punjabi language package
ii  libreoffice-l10n-pl                           1:3.5.7-0ubuntu4                        office productivity suite -- Polish language package
ii  libreoffice-l10n-pt                           1:3.5.7-0ubuntu4                        office productivity suite -- Portuguese language package
ii  libreoffice-l10n-pt-br                        1:3.5.7-0ubuntu4                        office productivity suite -- Portuguese_brazilian language package
ii  libreoffice-l10n-ro                           1:3.5.7-0ubuntu4                        office productivity suite -- Romanian language package
ii  libreoffice-l10n-ru                           1:3.5.7-0ubuntu4                        office productivity suite -- Russian language package
ii  libreoffice-l10n-rw                           1:3.5.7-0ubuntu4                        office productivity suite -- Kinarwanda language package
ii  libreoffice-l10n-si                           1:3.5.7-0ubuntu4                        office productivity suite -- Sinhala language package
ii  libreoffice-l10n-sk                           1:3.5.7-0ubuntu4                        office productivity suite -- Slovak language package
ii  libreoffice-l10n-sl                           1:3.5.7-0ubuntu4                        office productivity suite -- Slovenian language package
ii  libreoffice-l10n-sr                           1:3.5.7-0ubuntu4                        office productivity suite -- Serbian language package
ii  libreoffice-l10n-ss                           1:3.5.7-0ubuntu4                        office productivity suite -- Swazi language package
ii  libreoffice-l10n-st                           1:3.5.7-0ubuntu4                        office productivity suite -- Southern_sotho language package
ii  libreoffice-l10n-sv                           1:3.5.7-0ubuntu4                        office productivity suite -- Swedish language package
ii  libreoffice-l10n-ta                           1:3.5.7-0ubuntu4                        office productivity suite -- Tamil language package
ii  libreoffice-l10n-te                           1:3.5.7-0ubuntu4                        office productivity suite -- Telugu language package
ii  libreoffice-l10n-tg                           1:3.5.7-0ubuntu4                        office productivity suite -- Tajik language package
ii  libreoffice-l10n-th                           1:3.5.7-0ubuntu4                        office productivity suite -- Thai language package
ii  libreoffice-l10n-tn                           1:3.5.7-0ubuntu4                        office productivity suite -- Tswana language package
ii  libreoffice-l10n-tr                           1:3.5.7-0ubuntu4                        office productivity suite -- Turkish language package
ii  libreoffice-l10n-ts                           1:3.5.7-0ubuntu4                        office productivity suite -- Tsonga language package
ii  libreoffice-l10n-ug                           1:3.5.7-0ubuntu4                        office productivity suite -- Uighur language package
ii  libreoffice-l10n-uk                           1:3.5.7-0ubuntu4                        office productivity suite -- Ukrainian language package
ii  libreoffice-l10n-uz                           1:3.5.7-0ubuntu4                        office productivity suite -- Uzbek language package
ii  libreoffice-l10n-ve                           1:3.5.7-0ubuntu4                        office productivity suite -- Venda language package
ii  libreoffice-l10n-vi                           1:3.5.7-0ubuntu4                        office productivity suite -- Vietnamese language package
ii  libreoffice-l10n-xh                           1:3.5.7-0ubuntu4                        office productivity suite -- Xhosa language package
ii  libreoffice-l10n-za                           1:3.5.7-0ubuntu4                        office productivity suite -- South African language packages
ii  libreoffice-l10n-zh-cn                        1:3.5.7-0ubuntu4                        office productivity suite -- Chinese_simplified language package
ii  libreoffice-l10n-zh-tw                        1:3.5.7-0ubuntu4                        office productivity suite -- Chinese_traditional language package
ii  libreoffice-l10n-zu                           1:3.5.7-0ubuntu4                        office productivity suite -- Zulu language package
ii  libreoffice-voikko                            3.3-1ubuntu1                            Finnish language tools for LibreOffice
ii  libslang2                                     2.2.4-3ubuntu1                          S-Lang programming library - runtime version
ii  libthai-data                                  0.1.16-3                                Data files for Thai language support library
ii  libthai0                                      0.1.16-3                                Thai language support library
ii  libvoikko1                                    3.3-3ubuntu1                            Library of Finnish language tools
ii  libzemberek-java                              2.1.1-8                                 Spell checker library for Turkic languages
ii  m4                                            1.4.16-2ubuntu1                         a macro processing language
ii  mawk                                          1.3.3-17                                a pattern scanning and text processing language
ii  php5                                          5.3.10-1ubuntu3.8                       server-side, HTML-embedded scripting language (metapackage)
ii  php5-cli                                      5.3.10-1ubuntu3.8                       command-line interpreter for the php5 scripting language
ii  php5-fpm                                      5.3.10-1ubuntu3.8                       server-side, HTML-embedded scripting language (FPM-CGI binary)
ii  python                                        2.7.3-0ubuntu2.2                        interactive high-level object-oriented language (default version)
ii  python-minimal                                2.7.3-0ubuntu2.2                        minimal subset of the Python language (default version)
ii  python-numpy                                  1:1.6.1-6ubuntu1                        Numerical Python adds a fast array facility to the Python language
ii  python2.7                                     2.7.3-0ubuntu3.2                        Interactive high-level object-oriented language (version 2.7)
ii  python2.7-minimal                             2.7.3-0ubuntu3.2                        Minimal subset of the Python language (version 2.7)
ii  python3.2                                     3.2.3-0ubuntu3.3                        Interactive high-level object-oriented language (version 3.2)
ii  python3.2-minimal                             3.2.3-0ubuntu3.3                        Minimal subset of the Python language (version 3.2)
ii  ruby1.8                                       1.8.7.352-2ubuntu1.3                    Interpreter of object-oriented scripting language Ruby 1.8
ii  smart-languagesetup                           2.2.1191.4-1                            SMART Language Setup
ii  sunpinyin-data                                0.1.22-2                                Statistical language model data from open-gram
ii  thunderbird-locale-en                         1:24.0+build1-0ubuntu0.12.04.1          English language pack for Thunderbird
ii  thunderbird-locale-en-gb                      1:24.0+build1-0ubuntu0.12.04.1          Transitional English language pack for Thunderbird
ii  thunderbird-locale-en-us                      1:24.0+build1-0ubuntu0.12.04.1          Transitional English language pack for Thunderbird
ii  thunderbird-locale-zh-cn                      1:24.0+build1-0ubuntu0.12.04.1          Transitional Simplified Chinese language pack for Thunderbird
ii  thunderbird-locale-zh-hans                    1:24.0+build1-0ubuntu0.12.04.1          Simplified Chinese language pack for Thunderbird
ii  thunderbird-locale-zh-hant                    1:24.0+build1-0ubuntu0.12.04.1          Traditional Chinese language pack for Thunderbird
ii  thunderbird-locale-zh-tw                      1:24.0+build1-0ubuntu0.12.04.1          Transitional Traditional Chinese language pack for Thunderbird
ii  ttf-bengali-fonts                             1:0.5.11ubuntu1                         Free TrueType fonts for the Bengali language
ii  ttf-devanagari-fonts                          1:0.5.11ubuntu1                         Free TrueType fonts for languages using the Devanagari script
ii  ttf-gujarati-fonts                            1:0.5.11ubuntu1                         Free TrueType fonts for the Gujarati language
ii  ttf-indic-fonts                               1:0.5.11ubuntu1                         Metapackage for free Indian language fonts
ii  ttf-indic-fonts-core                          1:0.5.11ubuntu1                         Core collection of free fonts for languages of India
ii  ttf-kannada-fonts                             1:0.5.11ubuntu1                         Free TrueType fonts for the Kannada language
ii  ttf-malayalam-fonts                           1:0.5.11ubuntu1                         Free TrueType fonts for the Malayalam language
ii  ttf-oriya-fonts                               1:0.5.11ubuntu1                         Free TrueType fonts for the Oriya language
ii  ttf-punjabi-fonts                             1:0.5.11ubuntu1                         Free TrueType fonts for the Punjabi language
ii  ttf-tamil-fonts                               1:0.5.11ubuntu1                         Free TrueType fonts for the Tamil language
ii  ttf-telugu-fonts                              1:0.5.11ubuntu1                         Free TrueType fonts for the Telugu language
ii  wordnet                                       1:3.0-26.1                              electronic lexical database of English language
ii  wordnet-base                                  1:3.0-26.1                              electronic lexical database of English language (base data)
ii  wordnet-sense-index                           1:3.0-26.1                              electronic lexical database of English language (index.sense)

The language pack is not selectable... And when I try adding it in Keyboard Layouts, nothing happens.  I feel like something I need is still not installed.

[img]http://binaryimpulse.com/wp-content/uploads/2013/10/chinese_langpack1.png[/img]

[img]http://binaryimpulse.com/wp-content/uploads/2013/10/chinese_langpack2.png[/img]

[img]http://binaryimpulse.com/wp-content/uploads/2013/10/chinese_langpack3.png[/img]

What might I be doing wrong?  Is there a guide someone could point me to for how to properly install the Chinese language pack?

Thanks
Kirk

---

