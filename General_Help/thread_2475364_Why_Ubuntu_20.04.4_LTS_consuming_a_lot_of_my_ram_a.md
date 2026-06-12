---
title: "Why Ubuntu 20.04.4 LTS consuming a lot of my ram although very app is running"
date: 2022-05-24
forum: General Help
---

### Post by sunwarder on 2022-05-24
Hello, Why Ubuntu 20.04.4 LTS consuming a lot of my ram. Although very few app is running. 
Any recommend to resolve this problem or best release version for Ubuntu? Thank you very much.

[IMG]https://i.ibb.co/y8LGmPw/Screenshot-from-2022-05-24-23-40-35.png[/IMG][IMG]https://i.ibb.co/b6fCZxP/Screenshot-from-2022-05-24-23-51-08.png[/IMG]

[IMG]https://ibb.co/9qRzmgF[/IMG][IMG]https://ibb.co/wdvPXTR[/IMG]

---

### Post by Impavidus on 2022-05-24
Try investigating with top (or htop, but you may have to install that one). Those tools will tell you what application uses that ram. The free tool gives more details about memory use. It's clearer about what's used for applications, shared libraries, buffers and cache.

Although browsers are memory hogs, this may be a bit much for the base OS + a browser with one tab. But I don't use gnome or chrome, so i can't say for sure.

---

