---
title: "How to forever ignore upgrading one package?"
date: 2012-12-12
forum: General Help
---

### Post by jiapei100 on 2012-12-12
Hi, all:

Environment: Ubuntu 12.10

I don't want to use the default package of FFMPEG in the default Ubuntu repository. So, I downloaded the newest FFMPEG and manually installed it. However, the OS always automatically jumped out a message to let me upgrade FFMPEG to the default package in the default Ubuntu. How can I just prohibit the package from upgrading? I mean, I seriously don't want to see the "jumped out message" from time to time.


Can anybody help?

cheers
Pei

---

### Post by ororo on 2012-12-12
Googleing:

[https://www.google.it/search?client=ubuntu&channel=fs&q=apt-get+avoid+upgrading+package&ie=utf-8&oe=utf-8&redir_esc=&ei=4kLIUPX4IYP-4QTT4YDwAg](https://www.google.it/search?client=ubuntu&channel=fs&q=apt-get+avoid+upgrading+package&ie=utf-8&oe=utf-8&redir_esc=&ei=4kLIUPX4IYP-4QTT4YDwAg)

[http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package](http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package)

---

### Post by ibjsb4 on 2012-12-12
pinning

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=pinning&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=pinning&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by jiapei100 on 2012-12-12
Good to know...
Thanks man ^_^

---

### Post by FakeOutdoorsman on 2012-12-12
If you used checkinstall, in *--pkgversion*, use a higher epoch number than what is used in the repository package as shown on the [Compile FFmpeg on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) guide.

---

### Post by dcstar on 2012-12-14
> **jiapei100 said:**
> Good to know...


If you now have a solution then MARK the thread.

---

