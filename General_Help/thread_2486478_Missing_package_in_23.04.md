---
title: "Missing package in 23.04"
date: 2023-05-01
forum: General Help
---

### Post by vccm-1011010 on 2023-05-01
I've just installed 23.04 and I need to install some tools for work that require wxWebView, it seems the packages for it can't be found (Even though I've been using linux for a while it's been just for work and pretty mechanical when it comes to installing necessary tools, so don't really understand much of it)
The erros I get are:

E: Unable to locate package libwxgtk3.0-gtk3-dev
E: Couldn't find any package by glob 'libwxgtk3.0-gtk3-dev'
E: Couldn't find any package by regex 'libwxgtk3.0-gtk3-dev'
E: Unable to locate package libwxgtk-webview3.0-gtk3-dev
E: Couldn't find any package by glob 'libwxgtk-webview3.0-gtk3-dev'
E: Couldn't find any package by regex 'libwxgtk-webview3.0-gtk3-dev'

I've seen on the internet that this has changed names in the past and I was wondering if it doesn't exist on 23.04 at all or if it has another name.

Thanks in advance

---

### Post by sudodus on 2023-05-02
When you need a 'smooth ride' for example at work, I would recommend that you use a version of Ubuntu with long time support, the current one (now) is 22.04.2 LTS. A lot of time is spent to debug and polish the LTS versions, and this includes efforts by the Ubuntu developers as well as developers of non-ubuntu application programs.

The only reason to use 23.04 (with lifetime only 9 months) is if your computer is too new to work with Ubuntu 22.04.2 LTS. See also [this link](https://askubuntu.com/questions/1018033/ubuntu-development-version-how-to-participate-or-how-to-get-a-smooth-ride).

Edit: If you want to participate in testing the bleeding edge software, you are welcome to use 23.04, but you should be prepared to hit some rough edges.

---

### Post by ajgreeny on 2023-05-02
I agree; stick to the LTS versions only for your main work machine.

The current LTS, 22.04 has all those missing packages available in the repos so may allow you to run your "tools for work" though as you did not say what they are it's impossible to know.

---

