---
title: "How to fix this elementary OS?"
date: 2013-12-02
forum: General Help
---

### Post by Agnishom_Chattopadhyay on 2013-12-02
I am using Ubuntu 12.04 LTS

I wanted to experiment with the Pantheon Desktop Environment. I did this```
sudo add-apt-repository ppa:elementary-os/daily
sudo apt-get update
sudo apt-get install elementary-desktop

```

The result ended with this:
```

Setting up elementary-os-bet ta-transition (0.1-0~8~precise1) ...
/var/lib/dpkg/info/elementary-os-beta-transition.postinst: 45: .: Can't open /etc/upstream-release/lsb-release
dpkg: error processing elementary-os-beta-transition (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 elementary-os-beta-transition
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And now, it has changed Unity too. The mouse pointer has changed, so has the panel and window decorations. The Appearences settings in Unity seems to have disappeared.
I can't login into the pantheon shell either.

Trying to remove it using apt-get remove results in the same error.

How do I put things back?

---

### Post by grier-devon on 2013-12-02
Did you try to "purge" the desktop? I am sure someone else will come around who could better assist in the removal of the desktop. Though I would say if you try ti give elementary desktop another try you should try...
```
[COLOR=#555555][FONT=consolas]$ sudo apt-add-repository -y ppa:elementary-os/daily[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas]$ sudo apt-add-repository -y ppa:marlin-devs/marlin-daily[/FONT][/COLOR]
[COLOR=#555555][FONT=consolas]$ sudo apt-add-repository -y ppa:ricotz/docky[/FONT][/COLOR]
```

```
[COLOR=#555555][FONT=consolas]$ sudo apt-get update[/FONT][/COLOR]
```

```
[COLOR=#555555][FONT=consolas]$ sudo apt-get install -y pantheon-shell pantheon midori lingo wingpanel plank pantheon-terminal pantheon-xsession-settings contractor slingshot-launcher scratch marlin elementary-theme elementary-icon-theme ttf-droid footnote switchboard plank-theme-pantheon snap switchboard-gnome-control-center preload[/FONT][/COLOR]
```

When I experiment with something  new I keep an Ubuntu in a VM for testing first to make sure everything will go well, just some thought for next time.

---

### Post by Agnishom_Chattopadhyay on 2013-12-02
Hi;

Is it possible to execute those commands without fixing the broken package?

---

### Post by grier-devon on 2013-12-02
Hello,
can you go into your software source and remove the PPA in which you put on there and then do a 
```
sudo apt-get update
```?

If you can at least do this then I would try the commands I listed, I was looking online a found a few to claim the route you took does not work properly since dependencies are missing. If this works then once you get into your new elementary desktop let me know so we can go back and fix Unity so if you ever want to boot into Unity it will work.

Let me know your progress.

---

### Post by Agnishom_Chattopadhyay on 2013-12-02
I am going to the Software Center and removing those PPAs then I am going to run apt-get update.

Am I in the right track?

---

### Post by grier-devon on 2013-12-03
> **Agnishom_Chattopadhyay said:**
> I am going to the Software Center and removing those PPAs then I am going to run apt-get update.

Am I in the right track?
You need to go to software source, not software center. From there you will be in the right track. Keep us posted.

---

### Post by Agnishom_Chattopadhyay on 2013-12-05
I removed those sources and did apt-get update. Yet, no progress

---

### Post by paudelanup on 2013-12-09
Here is a quick fix for it. Open your terminal and type the following commands in succession

[COLOR=#141412][FONT=monospace]sudo mkdir /etc/upstream-release

[/FONT][/COLOR][COLOR=#141412][FONT=monospace]sudo touch /etc/upstream-release/lsb-release

Now open lsb-release with your favourite text editor, I am using gedit here

[/FONT][/COLOR][COLOR=#141412][FONT=monospace]sudo gedit /etc/upstream-release/lsb-release

Now copy and paste the following in document open by gedit and save it:

[/FONT][/COLOR][COLOR=#141412][FONT=monospace]DISTRIB_ID=Ubuntu[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_RELEASE=12.04[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_CODENAME=precise[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

Now upgrade your system with following command:

[/FONT][/COLOR][COLOR=#141412][FONT=monospace]sudo apt-get dist-upgrade

Enjoy....[/FONT][/COLOR]:D:D

---

### Post by paudelanup on 2013-12-09
For mouse cursor and appearance settings: You can get them back. Actually switchboard overrides the gnome-control-center.... you can use update alternatives for cursors......

---

### Post by MURATSPLAT on 2014-01-26
> **paudelanup said:**
> Here is a quick fix for it. Open your terminal and type the following commands in succession

[COLOR=#141412][FONT=monospace]sudo mkdir /etc/upstream-release

[/FONT][/COLOR][COLOR=#141412][FONT=monospace]sudo touch /etc/upstream-release/lsb-release

Now open lsb-release with your favourite text editor, I am using gedit here

[/FONT][/COLOR][COLOR=#141412][FONT=monospace]sudo gedit /etc/upstream-release/lsb-release

Now copy and paste the following in document open by gedit and save it:

[/FONT][/COLOR][COLOR=#141412][FONT=monospace]DISTRIB_ID=Ubuntu[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_RELEASE=12.04[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_CODENAME=precise[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

Now upgrade your system with following command:

[/FONT][/COLOR][COLOR=#141412][FONT=monospace]sudo apt-get dist-upgrade

Enjoy....[/FONT][/COLOR]:D:D

That works on my ubuntu linux.  Now it is not seen  errors..
[LEFT][COLOR=#000000][FONT=Ubuntu Mono]
Thank you
[/FONT][/COLOR][/LEFT]

---

