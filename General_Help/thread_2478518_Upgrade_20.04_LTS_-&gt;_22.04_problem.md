---
title: "Upgrade 20.04 LTS -&gt; 22.04 problem"
date: 2022-08-29
forum: General Help
---

### Post by zkab on 2022-08-29
I have Dell XPS 13 with Ubuntu 20.04 LTS preinstalled and made an upgrade to 22.04 LTS with 'Software Updater'.
After reboot and 'sudo apt update' I got following:

```

W: Skipping acquire of configured file 'oem/binary-i386/Packages' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/binary-amd64/Packages' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/i18n/Translation-en_US' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/i18n/Translation-en' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/Components-amd64.yml' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/icons-48x48.tar' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/icons-64x64.tar' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/dep11/icons-64x64@2.tar' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'oem/cnf/Commands-amd64' as repository 'http://oem.archive.canonical.com jammy InRelease' doesn't have the component 'oem' (component misspelt in sources.list?)
```

How can I get rid of this?

---

