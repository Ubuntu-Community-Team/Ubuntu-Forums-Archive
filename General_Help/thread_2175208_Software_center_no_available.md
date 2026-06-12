---
title: "Software center no available"
date: 2013-09-18
forum: General Help
---

### Post by grandad67 on 2013-09-18
Hello, I recently had to reinstall 12.04. All seems to have gone well, but after installing a few apps - afew days later I have no apps.
The icon is still in the launcher. Click on it and I get a blank page (heading 'software center'). Click on the 'x' to close and nothing happens. even left click on the title bar and still nothing.
Reinstall was the result of unwise messing with Compiz.
Any help will be appreciared thanks.

---

### Post by ibjsb4 on 2013-09-18
Try opening the software center in terminal.  It may give you some errors to help you troubleshoot this.

```
software-center
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by grandad67 on 2013-09-18
cjf@newhost:~$ software-center

2013-09-19 13:54:34,629 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2013-09-19 13:54:34,629 - dbus.proxies - ERROR - Introspect error on :1.124:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
2013-09-19 13:54:59,687 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-09-19 13:54:59,690 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-09-19 13:54:59,956 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-09-19 13:55:00,058 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.

Thanks jiges4, here's the result of 
'software-center' It dosn't make sense to me, what do you suggest? I have back ups so a reinstall would be no bother.
Cheers.

---

### Post by ibjsb4 on 2013-09-18
Found a possible solution here.

[http://ubuntuforums.org/showthread.php?t=2155880&p=12698482#post12698482](http://ubuntuforums.org/showthread.php?t=2155880&p=12698482#post12698482)

So give it a try.  In terminal:

```
sudo apt-get install --reinstall python-sip python-qt4
```

And for reference, I found that here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Softwarecenter+dbus.proxies+-+ERROR&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Softwarecenter+dbus.proxies+-+ERROR&sa=Search&cof=FORID:9)

---

### Post by CeejRab on 2013-09-18
Have you tried resetting compiz?

---

### Post by grandad67 on 2013-09-19
Thanks for your reply. I reinstalled 12.04 (I'm sorry, but I hate these silly names).
So a reinstall, I thought would begin again.?
Had I reset compiz before that I may have avoded all this?
I'd be interested to know; though I'll leave compiz alone from now on.

On the subjet of 'silly names' how do Patagonians know what the heck you're on about?
Cheers.................

---

### Post by CeejRab on 2013-09-19
Lol on the funny names... Natty narwhal, lucid lynx, precise pangolin, they're pretty punny :) 

A compiz reset may or may not have fixed it, but it would've taken some troubleshooting to find out anyway. 

A fresh reinstall talk is the obvious fix that I'm always considering, although I try not to suggest it cause most don't prefer that idea! Ubuntu is such a quick install though that it's worth it to me, it only takes about 20 minutes! 

All the best!

---

