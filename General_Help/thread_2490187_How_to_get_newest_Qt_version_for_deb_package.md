---
title: "How to get newest Qt version for deb package?"
date: 2023-08-25
forum: General Help
---

### Post by davidlazarescu on 2023-08-25
I  am trying to create a deb package of an application that uses Qt 6.5  and relies on features from Qt 6.5. Currently the newest Qt version that  I get can via apt is Qt 6.2.4. Is there a way for me to create a  dependency on Qt 6.5 in my deb's control file?

---

### Post by mIk3_08 on 2023-08-26
The latest version of Qt for Linux is Qt 6.5 LTS, which was released on April 2023. It is a long-term support (LTS) release, which means that it will be supported with bug fixes and security updates for three years. Qt 6.5 LTS includes a number of new features and improvements, including:

Improved support for Wayland: Wayland is a new display server protocol that is designed to be more efficient and secure than X11. Qt 6.5 LTS includes improved support for Wayland, making it easier to develop applications that run on Wayland-based systems.
New 3D graphics features: Qt 6.5 LTS includes new 3D graphics features, such as support for ray tracing and Vulkan. These features can be used to create more realistic and immersive 3D applications.
Improved Qt Creator: Qt Creator is the integrated development environment (IDE) for Qt. Qt 6.5 LTS includes a number of improvements to Qt Creator, including a new debugger, a new code editor, and a new visual designer.
You can download Qt 6.5 LTS for Linux from the Qt website: [https://www.qt.io/download](https://www.qt.io/download) Regards and cheers.

---

### Post by davidlazarescu on 2023-08-26
This was not my question. I am using Qt for multiple years not and know that 6.5 is a LTS. I was asking if there is a way to add it as a dependency to my control file in my deb package, so that it gets downloaded from e.g. the apt repositories.

---

### Post by #&amp;thj^% on 2023-08-26
> **davidlazarescu said:**
> This was not my question. I am using Qt for multiple years not and know that 6.5 is a LTS. I was asking if there is a way to add it as a dependency to my control file in my deb package, so that it gets downloaded from e.g. the apt repositories.
The question is somewhat vague, if your asking about building it see this: [https://doc.qt.io/qt-6/linux-building.html](https://doc.qt.io/qt-6/linux-building.html)
If not more specifics are needed to your request.

---

### Post by davidlazarescu on 2023-08-26
I am not asking how to build it. I do not understand how my question is vague. My situation is: I have an application that uses Qt 6.5, I want to create a deb package for it to release it, I have a dependency on Qt 6.5 so I need to somehow let my control file know to get Qt 6.5. My problem is that the Debian/Ubuntu repositories only have Qt 6.4.2 as of now. My question is: Is there any way to get this dependency (by listing it in my control file) without needing to build Qt 6.5 from source?

---

### Post by ian-weisser on 2023-08-26
Not yet, as Qt 6.5 has not yet been packaged for Ubuntu. Those packages simply do not exist yet.

According to [https://tracker.debian.org/pkg/qt6-base](https://tracker.debian.org/pkg/qt6-base) it has not yet been packaged for Debian either. More volunteers to do that work are welcome.

And, when it is packaged (perhaps Ubuntu 24.04), it won't be backported to older releases of Ubuntu. So most users won't see it until they migrate to (assumedly) 24.04 or newer. That will take several years.

This is the disadvantage of using bleeding-edge libs in a Debian environment. If using Qt 6.2 instead of Qt 6.5, your application could go into Debian immediately, and would be compatible with Ubuntu 22.04 LTS and newer.

Alternately, if you were open to non-deb-package solutions, you could bundle the Qt 6.5 libs into a Snap or a Flatpak.

---

### Post by #&amp;thj^% on 2023-08-26
> **davidlazarescu said:**
> I am not asking how to build it. I do not understand how my question is vague. My situation is: I have an application that uses Qt 6.5, I want to create a deb package for it to release it, I have a dependency on Qt 6.5 so I need to somehow let my control file know to get Qt 6.5. My problem is that the Debian/Ubuntu repositories only have Qt 6.4.2 as of now. My question is: Is there any way to get this dependency (by listing it in my control file) without needing to build Qt 6.5 from source?
There you go and I can see how you wouldn't be confused, but we were!! :P
> **ian-weisser said:**
> Not yet, as Qt 6.5 has not yet been packaged for Ubuntu. Those packages simply do not exist yet.

According to [https://tracker.debian.org/pkg/qt6-base](https://tracker.debian.org/pkg/qt6-base) it has not yet been packaged for Debian either. More volunteers to do that work are welcome.

And, when it is packaged (perhaps Ubuntu 24.04), it won't be backported to older releases of Ubuntu. So most users won't see it until they migrate to (assumedly) 24.04 or newer. That will take several years.

This is the disadvantage of using bleeding-edge libs in a Debian environment. If using Qt 6.2 instead of Qt 6.5, your application could go into Debian immediately, and would be compatible with Ubuntu 22.04 LTS and newer.

Alternately, if you were open to non-deb-package solutions, you could bundle the Qt 6.5 libs into a Snap or a Flatpak.
+1 Thanks ian-weisser
```
rmadison qt6-base
 qt6-base | 6.2.4+dfsg-2ubuntu1   | jammy/universe         | source
 qt6-base | 6.2.4+dfsg-2ubuntu1.1 | jammy-updates/universe | source
 qt6-base | 6.4.2+dfsg-6          | lunar/universe         | source
 qt6-base | 6.4.2+dfsg-18         | mantic/universe        | source

```
That's All Folks..;)

---

### Post by mIk3_08 on 2023-08-27
> **ian-weisser said:**
> Not yet, as Qt 6.5 has not yet been packaged for Ubuntu. Those packages simply do not exist yet.

According to [https://tracker.debian.org/pkg/qt6-base](https://tracker.debian.org/pkg/qt6-base) it has not yet been packaged for Debian either. More volunteers to do that work are welcome.
And, when it is packaged (perhaps Ubuntu 24.04), it won't be backported to older releases of Ubuntu. So most users won't see it until they migrate to (assumedly) 24.04 or newer. That will take several years.
This is the disadvantage of using bleeding-edge libs in a Debian environment. If using Qt 6.2 instead of Qt 6.5, your application could go into Debian immediately, and would be compatible with Ubuntu 22.04 LTS and newer.
Alternately, if you were open to non-deb-package solutions, you could bundle the Qt 6.5 libs into a Snap or a Flatpak.

Thanks to ian-weisser. Regards and cheers.

---

