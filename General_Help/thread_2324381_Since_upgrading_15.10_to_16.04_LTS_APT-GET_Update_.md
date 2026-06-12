---
title: "Since upgrading 15.10 to 16.04 LTS APT-GET Update Problems"
date: 2016-05-13
forum: General Help
---

### Post by greenfrog42 on 2016-05-13
Get the following W messages when running apt-get update, do not know how to fix


```
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:56
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:56
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:56
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:88
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:88
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:28 and /etc/apt/sources.list:88
```


Any suggestions on what and how to fix problem?

---

