---
title: "The xcb QPA platform plugin lacks a `.deb` package similar to `build-essential`"
date: 2024-07-29
forum: General Help
---

### Post by linghengqian on 2024-07-29
- From my personal perspective, the xcb QPA platform plugin lacks a `.deb` package similar to `build-essential`, but I'm not sure where this issue should be filed. I came here because the Ubuntu official website directs technical Q&A issues here instead of to a launchpad project.

- Under WSL, if users need to use software that relies on Qt, they need to install a large number of system dependencies. I have reported this to DingTalk at [https://github.com/ubuntu/WSL/issues/453](https://github.com/ubuntu/WSL/issues/453) and Calibre at [https://bugs.launchpad.net/calibre/+bug/2073474](https://bugs.launchpad.net/calibre/+bug/2073474) .

- A committer from Carlibre at [https://bugs.launchpad.net/calibre/+bug/2073474](https://bugs.launchpad.net/calibre/+bug/2073474) suggested that I open an issue on the Qt side, which is reflected in [https://bugreports.qt.io/browse/QTBUG-127400](https://bugreports.qt.io/browse/QTBUG-127400) .

- On the Qt JIRA Issue Tracker side, I saw the complex dependencies required by the xcb QPA (Qt Platform Abstraction) platform plugin from [https://bugreports.qt.io/browse/QTBUG-126021](https://bugreports.qt.io/browse/QTBUG-126021).

```

[COLOR=#172B4D][FONT=-apple-system]sudo apt update

[/FONT][/COLOR]sudo apt install -y libxkbcommon-dev libxkbcommon-x11-dev

sudo apt-get install libxcb-icccm4 libfontconfig1 libxcb-glx0 libx11-xcb1 libxcb-image0 libxcb-keysyms1 libxcb-randr0 libxcb-render-util0 libxcb-shape0 libxcb-sync1 libxcb-xfixes0 libxcb-xinerama0 libxcb-xkb1 libxkbcommon-x11-0 libgl1

sudo apt install make g++ pkg-config libgl1-mesa-dev libxcb*-dev libfontconfig1-dev libxkbcommon-x11-dev libgtk-3-dev

```

- Most dependencies are documented at [https://doc.qt.io/qt-6/linux-requirements.html](https://doc.qt.io/qt-6/linux-requirements.html) .
- But from my point of view, this is too complicated. It would be nice if there is an integrated deb package in the `apt-get` library in Ubuntu 22.04.4, just like [https://packages.ubuntu.com/jammy/build-essential](https://packages.ubuntu.com/jammy/build-essential) for system compilation. Or does such a `.deb` package actually exist, but I just can't find the corresponding documentation?

---

### Post by linghengqian on 2024-12-08
- Since Ubuntu Forums has been shut down, I moved the issue to [https://discourse.ubuntu.com/t/the-xcb-qpa-platform-plugin-lacks-a-deb-package-similar-to-build-essential/50801](https://discourse.ubuntu.com/t/the-xcb-qpa-platform-plugin-lacks-a-deb-package-similar-to-build-essential/50801) in ubuntu discourse.

---

