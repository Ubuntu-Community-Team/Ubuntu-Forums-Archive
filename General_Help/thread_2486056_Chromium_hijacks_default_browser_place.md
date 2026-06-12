---
title: "Chromium hijacks default browser place"
date: 2023-04-18
forum: General Help
---

### Post by John Jason Jordan on 2023-04-18
I have recently installed the Brave browser. In its settings there is a button to make it the default browser, but when I click a link from anywhere the link opens in Chromium. If Chromium is not running clicking on the link launches Chromium and opens the link. Brave browser has the setting for default browser, with a button to make it the default browser, but clicking on the button does nothing. If I click in Chromium's settings for default browser I get a popup that says 'Chromium is your default browser,' and there are no buttons or other options displayed. In Firefox the Default browser setting says 'Firefox is **not** your default browser.' There is a button to make Firefox the default browser, but like in Brave, clicking the button does nothing. I guess if you install Chromium it will be the default browser and you will like it. Short of uninstalling Chromium, how can I make it behave like a law-abiding citizen of my computer?

---

### Post by John Jason Jordan on 2023-04-19
OK, I did it. I uninstalled Chromium. Then I tried to set Brave to be the default browser, but the button still didn't appear to activate, and when I clicked on a link outside of Brave nothing happened. This tells me that somewhere deep inside my Xubuntu 22.04 (up to date) there is a setting that intercepts all 'open in browser' links and sends them to Chromium, and when Chromium is missing, the command just fails.

Assuming I am correct, this makes me angry. I don't know whether to blame Chromium developers or Ubuntu developers, but Ubuntu shouldn't allow an application installation to make such fundamental changes to the OS. At least, if they do, a means to undo it must be readily available to the user. In spite of my years here, if I have to reinstall, it won't be Ubuntu.

Edit: Just now I set Firefox to be the default browser, but when I click on a link, nothing happens. It is intercepted somewhere and is sent to the now missing Chromium.

---

