---
title: "How does snap 'break': kolourPaint"
date: 2021-07-05
forum: General Help
---

### Post by yaminb on 2021-07-05
I had a weird experience today where KolourPaint wouldn't launch. I had installed it as a snap a while ago and everything worked fine.
When I launched it from the terminal, I saw this error:

```

kolourpaint 
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.28' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Core.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.28' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Core.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.28' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Xml.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Xml.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5WaylandClient.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.28' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5WaylandClient.so.5)

```

I tired refreshing it, but to no avail. Giving up, I just decided to try a different version.

I installed the beta and it started working again.
```

sudo snap refresh kolourpaint --beta

```

So things worked out okay, but here's my question. Isn't the whole reason to use SNAPs because they include all dependencies so these kinds of errors don't show up.
Anyways know if this was something specific to this SNAP or if something can actually happen to my Ubuntu System (like an update), that would somehow break the application?

Thanks,

---

### Post by Holger_Gehrke on 2021-07-05
If you look at the path of the library closely, you'll see that it's complaining about the libstc++.so.6 **in it's own directory**. snap will update programs without telling you. The last update obviously had something seriously wrong with it. Because this possibility was foreseen, snap always keeps at least one older version at hand and you can use 'snap revert kolourpaint' to go back to the previous version.

Holger

---

