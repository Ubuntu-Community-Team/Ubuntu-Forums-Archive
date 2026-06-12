---
title: "KDE and Gnome"
date: 2007-03-04
forum: General Help
---

### Post by rafaelperrone on 2007-03-04
Is it possible to have both KDE and Gnome so that I can choose one of them when logging in? Or do I hav to install both Kubuntu and Ubuntu?

---

### Post by Spin Doctor on 2007-03-04
Piece of cake. 

In your terminal type:

```
sudo aptitude update
``````
sudo aptitude install kubuntu-desktop
```Hopefully you have broadband! 

After successful installation, you select which one to use at your loginwindow.

If any doubts, check out this link: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by kodoku on 2007-03-04
sure.

Depending on what you want/already have

if you have kde and want gnome:

sudo aptitude install ubuntu-desktop

if you have gnome and want kde:

sudo aptitude install kubuntu-desktop

OR

sudo aptitude install kde-core 

^ the above will only add the base components that will enable KDE to run, and it will not preinstall any KDE apps.  It is useful if you want a fully customized KDE that starts with nothing.

At the login screen, select the type of session you want and off you go.

Read more from [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) under the section "Playing Around"

---

### Post by Honayo on 2007-03-04
I'm running Ubuntu with the KDE desktop. I think that I got the desktop through Synaptic? It was a choose and install easy thing to do. And you choose on boot up which DE you want to use
Actually, I like the KDE desktop environment better than Gnome and have just installed Kubuntu Edgy Eft on another machine as the only OS.
The only thing I don't like about Kubuntu is there's no FF web browser.
Note that I have a dual boot system on this machine and am currently using xp to reply to this message.

---

### Post by helliewm on 2007-03-04
I installed Ubuntu first then Kubuntu. You can then switch between the 2 desktops and Firefox then appears in Kubuntu.

Helen

---

### Post by maniacmusician on 2007-03-04
> **Honayo said:**
> I'm running Ubuntu with the KDE desktop. I think that I got the desktop through Synaptic? It was a choose and install easy thing to do. And you choose on boot up which DE you want to use
Actually, I like the KDE desktop environment better than Gnome and have just installed Kubuntu Edgy Eft on another machine as the only OS.
The only thing I don't like about Kubuntu is there's no FF web browser.
Note that I have a dual boot system on this machine and am currently using xp to reply to this message.
yes but it just takes a simple command to install it :) also, most tasks can be done with the built in web browser/file browser; Konqueror

---

