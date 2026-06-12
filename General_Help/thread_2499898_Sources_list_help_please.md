---
title: "Sources list help please"
date: 2024-08-14
forum: General Help
---

### Post by sports fan Matt on 2024-08-14
While reinstalling Fossa, (only ISO) I had access to, I know I  screwed up my sources list.  I get the error listed.  Is it possible to generate a clean sources list or fix my current one.

---

### Post by Rubi1200 on 2024-08-14
I would first try the following:

```
sudo apt clean
```

and then
```
sudo apt update
```

Post back if there are any errors.

Also do this:
Open the Software & Updates application >> Go to the Other Software tab >> Uncheck any third-party PPAs or repositories

Close and refresh.

Fixed?

---

### Post by Tadaen_Sylvermane on 2024-08-14
```
[FONT=monospace][COLOR=#000000]deb http://us.archive.ubuntu.com/ubuntu jammy main restricted universe multiverse [/COLOR]
deb http://us.archive.ubuntu.com/ubuntu jammy-security main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse  
deb http://us.archive.ubuntu.com/ubuntu jammy-updates main restricted universe multiverse[/FONT]
```[FONT=monospace]

A cleaned up jammy official repository list. Just change jammy to focal I believe and you should be set. I never understood that massive list with all the damn comments and seemingly same repos defined multiple times.

Also I would be remiss to not mention that Focal will be out of support April of next year so either enable Ubuntu Pro or start getting an upgrade plan in place.
[/FONT]

---

### Post by sports fan Matt on 2024-08-14
Oh yes errors galore.

```
93 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:60
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:68
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:62
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:18 and /etc/apt/sources.list:64
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:34 and /etc/apt/sources.list:66
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:60
W: Target Sources (partner/source/Sources) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:68
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:44 and /etc/apt/sources.list:61
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:61
```

---

### Post by Tadaen_Sylvermane on 2024-08-14
Yea, delete that entire file and add the one I posted, changing jammy for focal. That will get it cleaned up. Then you can re-add anything missing one line a a time.

---

### Post by oldfred on 2024-08-14
Matt, you have been here long enough to know to use Code Tags.
Easy to add with Forum's Go Advanced editor & # icon.
Or
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]
I sometimes click on quote in Quick Reply and edit quote to code.

cat -n /etc/apt/sources.list
If you have added ppas
ls -l /etc/apt/sources.list.d/*.list

But in my Noble install sources.list is now an empty file, but update works. Looks like encrypted now?

---

### Post by sports fan Matt on 2024-08-14
I will next time. And I do have pro.

---

### Post by TheFu on 2024-08-14
```
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports main restricted universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-security universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-security multiverse
```

is my 20.04 server sources.list file.

---

### Post by kinddolphin8827 on 2024-08-14
I wasn't aware of the fact that focal was to be the next sequential release. does this mean that those like myself will have to upgrade straight away to Focal?
 I am I altogether miss under standing the nature of what the OP is doing?

---

### Post by TheFu on 2024-08-14
> **kinddolphin8827 said:**
> I wasn't aware of the fact that focal was to be the next sequential release. does this mean that those like myself will have to upgrade straight away to Focal?
 I am I altogether miss under standing the nature of what the OP is doing?

You miss understand what the OP is doing.  

He's installing Focal and screwed up the /etc/apt/sources.list file ... er ... somehow.  He didn't make a .bak file before editing, I guess.  Noob mistake, but it happens to everyone - even non-noobs.  He needed a pristine copy of the file, which is what I provided from a running system.

Now, if the description of the issue and what he'd trying to accomplish isn't correct, then nobody really knows what the goal is. That happens around here too.  People often write one thing and forget something critical to the background in the post.  Normally, I make a guess, but this time, it seemed really clear.

---

