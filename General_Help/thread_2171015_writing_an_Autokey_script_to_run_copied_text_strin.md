---
title: "writing an Autokey script to run copied text string in command terminal"
date: 2013-08-28
forum: General Help
---

### Post by dragonfly41 on 2013-08-28
I have Autokey installed on Ubuntu 12.04.

from here [https://groups.google.com/forum/#!topic/AutoKey-users/CF6GmAmeeUk](https://groups.google.com/forum/#!topic/AutoKey-users/CF6GmAmeeUk)

I have run this test script which opens a typical file ..


```
import subprocess

# subprocess.call(['xdg-open', 'PATH_TO_FILE_OR_DIR'])

subprocess.call(['xdg-open', '/var/lib/tomcat7/conf/logging.properties'])
```

My question is ... what script can I use to

copy selected text string in an editor file
and then run that string as a command in terminal?

What is the target window-name of the command terminal to be launched by Autokey?

....

Further advice found here as reference .. I think the second link below might answer my question on targeting gnome-terminal.. 

[URL="http://saravananthirumuruganathan.wordpress.com/2010/04/14/autokey-linux-utility-for-text-substitution-hotkeys-and-desktop-automation/"]http://saravananthirumuruganathan.wordpress.com/2010/04/14/autokey-linux-utility-for-text-substitution-hotkeys-and-desktop-automation/


[/URL][https://exyr.org/2011/gnome-terminal-tabs/](https://exyr.org/2011/gnome-terminal-tabs/)

---

### Post by Vaphell on 2013-08-28
do you really need to automate ctrl+c, ctrl+alt+t, ctrl+shift+v?

---

### Post by dragonfly41 on 2013-08-29
> do you really need to automate ctrl+c, ctrl+alt+t, ctrl+shift+v?

I haven't explained my objectives very well.

I'm writing some user manuals in online and/or ebook form for a platform under development.

I would like the reader (user of software) to simply highlight some commands (written into the manual) and go to right click > context menu to run the commands .. without running through the usual workflow ctrl+c, ctrl+alt+t, ctrl+shift+v you suggest.

At times the commands (in the manual) may be needed to run in a new tab in the command terminal if an earlier command has been run such as "sudo gedit /var/lib/tomcat7/conf/logging.properties" .. which leaves the terminal instance unusable for more commands unless a new tab is opened.   shift+ctrl+t.

Some of the Autokey scripts will be targeted for the command terminal. Other scripts will be targeted for certain other application windows.  Yakuake will also be used.   Gedit, Geany, Firefox etc.

So the general idea is to assume that the reader of the user manual / e-book can just right click on the highlighted script in the user manual or e-book .. and the script will run automatically without further ado.   Of course the user will have to trust that there are no malicious scripts written into the manual / e-book to auto-run via Autokey script.

I researched the possible use of Firefox add-on TerminalRun .. 

[http://www.webupd8.org/2010/03/terminalrun-firefox-addon-allows-you-to.html](http://www.webupd8.org/2010/03/terminalrun-firefox-addon-allows-you-to.html)

but TerminalRun needs to be hacked to ensure that it is compatible with later releases of Firefox. 

[http://askubuntu.com/questions/237517/how-to-run-from-firefox-context-menu-terminal-commands-selected-in-web-pages ]("http://askubuntu.com/questions/237517/how-to-run-from-firefox-context-menu-terminal-commands-selected-in-web-pages")


So I opted for Autokey which offers a more generic solution to cover a range of applications to be automated (not just terminal command).   

For example if you are walking a user through the step by step build of several applications on a platform and then cloning this entire build to the cloud .. some degree of automation is needed.

I hope that this better explains my interest in automation by Autokey.   It is to assist new users in setting up and troubleshooting issues in a developed platform with multiple applications.

---

