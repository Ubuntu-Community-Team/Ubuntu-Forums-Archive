---
title: "Bad font / no antialiasing for Java AWT components"
date: 2018-03-18
forum: General Help
---

### Post by David_Bragason on 2018-03-18
I'm using Kubuntu 17.10 and OpenJDK 8.

Fiji/ImageJ uses a mix of AWT and Swing components in the GUI. The fonts in the AWT part, such as the menu bar, look bad and there is no anti-aliasing, see screenshot.

Also for programs that I write, see screenshot, only Swing components get antialiasing, not the AWT. Upper window is Swing, lower is AWT, using the same font.

I have tried the font/antialias settings in System Settings, tried to pass awt.useSystemAAFontSettings to JVM, switched to Oracle Java without ever getting any AA in AWT components.

Any ideas?

---

