---
title: "Groupwise Support for Evolution in Ubuntu 12.04?"
date: 2012-12-05
forum: General Help
---

### Post by flokadillo on 2012-12-05
Hello,

I am trying to set up Groupwise in Evolution 3.2.3 using the description in this thread: [http://ubuntuforums.org/archive/index.php/t-1859907.html](http://ubuntuforums.org/archive/index.php/t-1859907.html)
I have Ubuntu 12.04.

Unfortunately, I get the following errors:
```

(evolution:2392): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory

(evolution:2392): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory

(evolution:2392): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory

(evolution:2392): e-utils-CRITICAL **: Plugin "GroupWise Features" is missing a function named gw_ui_mail_folder_popup()

(evolution:2392): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/3.2/plugins/liborg-gnome-groupwise-features': libegroupwise-1.2.so.13: cannot open shared object file: No such file or directory

(evolution:2392): e-utils-CRITICAL **: Plugin "GroupWise Features" is missing a function named gw_ui_mail_message_popup()

```My libegroupwise-1.2.so.13 is in /usr/local/lib/, but as supposed by Bruhein I created a symbolic link
```

sudo ln -s /usr/local/lib/libegroupwise-1.2.so.13 /usr/lib/evolution/3.2/plugins/libegroupwise-1.2.so.13

```
But still, Evolution doesn't seem to find it... Also copying the file to /usr/lib/evolution/3.2/plugins/ doesn't help. Any ideas ?
Thank you,

Flokadillo

---

