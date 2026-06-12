---
title: "Some General Questions Relating to Version 16.04.1"
date: 2016-08-13
forum: General Help
---

### Post by anon_private on 2016-08-13
Hi,

I have now installed kubuntu 16.04.1 to the hard disk

When running this OS from a pendrive, I noticed flashes on the screen. These are still present. Are there any options that I can activate that will eliminate this problem?

Sometimes I get disconnected from the iSP, can I determine the signal strength of the connection, and, perhaps, make the connection more stable?

Regarding FF, I am trying to change the white colour of the backgrounds for the windows. I tried changing them to grey via options, but I still see white. About:config also indicates grey!

I noticed an icon that advised the installation of the falshplugin. When I tried to install it, I received the message: 'Not found in software sources...'. Advice, please.

Regarding Terminal, how can I change the font colour?

When I click on the Home folder, I note that Muon is the programme, but I can't see Muon in the Application Launcher. Advice, please?



Thank you

---

### Post by mook765 on 2016-08-15
Open the menu, click 'Settings' and then 'Additional Drivers" See what's going on there, you may need drivers for your hardware.'
Terminal, which is called 'Konsole' in Kubuntu: open Konsole, in the menubar click 'Settings', then you click 'Edit current Profile".
Now you choose the Appearance-tab, there you can choose predefined color-themes, if you click on 'Edit' you are able to create your own color-theme.
Flash-Plugin: ```
sudo apt install flashplugin-installer
```
Firefox: Firefox will use the colors off the websites unless you enable 'Use System Colors' in Preferences >Content > Colors. Using this setting will let Websites look pretty strange...
Hope i could help you...
----------
Update:
As i had problems with this very outdated Flash-plugin, i removed flashplugin-installer completely and installed a firefox-addon called 'Video WithOut Flash'
[https://addons.mozilla.org/en-US/firefox/addon/video-without-flash](https://addons.mozilla.org/en-US/firefox/addon/video-without-flash)
Works better, might be safer...
Try yourself...

---

