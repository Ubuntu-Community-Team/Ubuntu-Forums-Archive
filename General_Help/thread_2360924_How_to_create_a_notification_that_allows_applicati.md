---
title: "How to create a notification that allows application launching with mouse click."
date: 2017-05-10
forum: General Help
---

### Post by again? on 2017-05-10
I would like to be able to run a command by clicking on a custom notification.
For example, Geary notifies of new mail and in gnome, clicking on the notification opens Geary.

I have some custom bash scripts that use notify-send and being able to 
run a command from the notification would be useful.
Is this possible in bash or is this something that needs to be coded in python or something?

Does anyone know where I might find a simple example?

---

### Post by vasa1 on 2017-05-10
> **guber2 said:**
> ...
Does anyone know where I might find a simple example?
Maybe do a search for *actionable notifications*?
I found this:> If you&#8217;re using GNOME-Shell you&#8217;ll get nifty actionable screen toasts that let you open the downloaded file right away &#8212; handy!from [s][https://websetnet.com/3-firefox-add-ons-every-ubuntu-user-needs/](https://websetnet.com/3-firefox-add-ons-every-ubuntu-user-needs/) under *1. Firefox Notify* which points to [GNotifier]("https://addons.mozilla.org/en-US/firefox/addon/gnotifier/").[/s]


Edit:
Scratch all that! I can't find anything on the GNotifier page related to the quote :(

Plus, the link I provided seems to have content similar to what's here: [http://www.omgubuntu.co.uk/2016/08/3-firefox-add-ons-every-ubuntu-user-needs](http://www.omgubuntu.co.uk/2016/08/3-firefox-add-ons-every-ubuntu-user-needs)

---

### Post by again? on 2017-05-10
> **vasa1 said:**
> Maybe do a search for *actionable notifications*?
I found this:from [s][https://websetnet.com/3-firefox-add-ons-every-ubuntu-user-needs/](https://websetnet.com/3-firefox-add-ons-every-ubuntu-user-needs/) under *1. Firefox Notify* which points to [GNotifier]("https://addons.mozilla.org/en-US/firefox/addon/gnotifier/").[/s]


Edit:
Scratch all that! I can't find anything on the GNotifier page related to the quote :(

Plus, the link I provided seems to have content similar to what's here: [http://www.omgubuntu.co.uk/2016/08/3-firefox-add-ons-every-ubuntu-user-needs](http://www.omgubuntu.co.uk/2016/08/3-firefox-add-ons-every-ubuntu-user-needs)
Thanks, the "***actionable notifications***" tip lead me to [this page]("https://hashbang.fr/tutoriel-notify.html") in french where I can get a python example to show something that looks promising.
I'll search around some more.
[ATTACH=CONFIG]275031[/ATTACH]

[COLOR="#FF0000"]_Edit_[/COLOR]
This page appears to be what I need... [Desktop Notifications in Python with Libnotify]("http://www.devdungeon.com/content/desktop-notifications-python-libnotify")

---

