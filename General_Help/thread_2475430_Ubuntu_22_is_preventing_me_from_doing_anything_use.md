---
title: "Ubuntu 22 is preventing me from doing anything usefll - need help"
date: 2022-05-26
forum: General Help
---

### Post by essin on 2022-05-26
Hello,

I am no unix/linux guru but I have been flirting with and using various flavors since about 1980 (SCO, Soaris, ATT, Debian, etc.) 

(Editorial comment: In all of that time, the level of usability for non-gurus seems to be relatively constant - close to the undecipherable end of the spectrum. )

I've been using Fedora recently. For me, it was a breath of fresh air in terms of usability - obscure but manageable. A colleague of mine was extolling the virtues of Ubuntu 22 and convinced me to switch. Then I began discovering all of the things that I could no longer do:

1 - 3 steps to enable root access to GUI vs 1 in Fedora (I know you shouldn't do root but read on and you will understand why this is important/useful.

2 - Can't print to auto-discovered printers

3 - Can't delete auto-discovered printers - they just reappear

4 - Can connect to samba share in Files app but have no write permission

5 - I don't know what else - after 2 days, I'm only about 15% of the way through the mods and apps that I need to install and configure.

These issues are in a bare-metal install

First I tried in in virtualbox. Root login yielded a 800x600 image on a 1920x1200 background. All important things, like apply buttons, were invisible. Mouse couldn't click in many apps. 

Tried in vmware. setting changes (like screen res) were not saved in regular user account.

At this point Ubuntu seems either impossible, or at least time consuming, to use. Perhaps there is some simple step that I was supposed to know about and perform that would have eliminated all of these issues. If so, I would appreciate it if someone would educate me. 

Thank you,

---

### Post by HermanAB on 2022-05-27
Ubuntu has its issues and you seem to have found almost all if them.  My favourite distribution is actually Fedora, which has different issues.  So, pick the one you like better and stick to it.

---

### Post by dragonfly41 on 2022-05-27
I will offer my own approach to tackling an ever increasing corpus of commands and applications. Not to mention cloud commands.

I build my own toolset which automates the steps to go through, after first researching the UI/app workflow.

In other words I use a mix of UI automation scripts for each task.
There are a few tools around which support this process. Ranging from batch files, to Python, to UI object control (such as hitting key sequences).

Just look at the number of times that commands are suggested in forum discussion replies. Over and over again. It is productive to create a hot key which performs each given task.

To offer a working example of this automation approach start by installing Albert. There will be other companion automation tools later but start with Albert.

[https://albertlauncher.github.io/installing/](https://albertlauncher.github.io/installing/)

This site emphasises the need to use official distros.

After installing, you launch Albert and you should see the launcher (blue icon) in top bar. Click on Settings and select Extensions tab.


Now here we can use “extensions” which perform microtasks.

If you click on Python you can extend Albert to any scope you need.

Quote:
"Embedded Python provides a convenient way to write custom extensions. The list below contains the custom extensions found in your system."

If you need a custom extension you can write your own, in Python.

But there is a learning curve and perhaps the easiest example of extension to start with is Snippets.

If you go to Albert > Settings you can set the hotkey of your choice. I use Num+Enter which is to right/bottom of keyboard  and is near my mouse.

With Albert running as background process we hit Num+Enter and a query field appears.

If in Extensions tab we have selected extension Snippets, we can type snip<space> to list snippets stored.

There are many examples which can be discussed but Albert can be a one stop shop to orchestrate your workflow. Invest your time in understanding how Albert might help.   Then explore companion tools to ease your workflow.

Other automation approaches include Ansible and Actiona.

---

