---
title: "Custom packages"
date: 2007-03-01
forum: General Help
---

### Post by pvanberlo on 2007-03-01
Hello,

I need some feedback on how you guys deal with custom packages/compiles of software like Apache. I'm currently setting up several Ubuntu 6.06.1 systems, and I need up-to-date software, i.e. latest Apache & latest Python. Now, I can go about and compile things manually on each system, but that takes ages. I'm looking into doing it once and deploying the applications on each system. The following possibilities come to mind:

1) Create custom packages
2) Manually compile on one system and package using tar/gzip, then deploy to each system

I would absolutely love to create custom packages, but somehow, it always ends up conflicting with already installed packages. I could of course rename the packages (add a prefix identifying it as a custom package). Just replacing the existing packages with newer versions doesn't seem to be an option either, it might break things.

So, how do you guys do this?

---

### Post by energiya on 2007-03-01
[This]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_make_Ubuntu.2FDebian_packages_.28CheckInstall.29")  is the only way I work. Both on Ubuntu and Slackware.

---

