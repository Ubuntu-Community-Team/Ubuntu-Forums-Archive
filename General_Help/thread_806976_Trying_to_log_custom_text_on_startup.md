---
title: "Trying to log custom text on startup"
date: 2008-05-25
forum: General Help
---

### Post by HappyUser123 on 2008-05-25
I recently installed Apache from the repository and I don't want it starting automatically on boot. I found that what the install does is create a /etc/init.d/apache2 script and then create links to it from some or all of the /etc/rc?.d directories. So my strategy was to move the original apache2 script and replace it with a new script with the same name, same permissions and ownership, that looks something like

> #!/bin/sh

echo <Message reminding me how to restore autostart functionality.>

This worked to stop Apache from starting on boot, but the log message isn't showing up anywhere that I can find. I grepped through /var/log trying to find an identifiable part of the message in any file, with no luck. Then I did some research and replaced "echo" with "logger" in the script, and again hunted for part of the message, still not finding it. 

Any ideas? I think I'm either using the wrong command in the script, or I'm not looking in the right place for the output. 

Thanks!

---

### Post by pointone on 2008-05-26
The proper way to prevent an init script from starting:

```
sudo update-rc.d -f apache2 remove
man update-rc.d
```

logger will output to /var/log/syslog by default. Make sure your message is enclosed in quotation marks.

---

### Post by HappyUser123 on 2008-05-27
Thank you for the help :) 

However when I took a look at the man page for update-rc.d, it said that using either bum or sysv-rc-conf was preferred over update-rc.d. So I installed both of those applications from the repositories to see which one I liked better. bum is GUI based and includes a description for each application, both of which are nice, but unfortunately it just didn't see apache at all for some reason. sysv-rc-conf is console-based but worked fine. So I took my placeholder script out of the picture, put the original script back where I found it, and just used sysv-rc-conf to stop apache from starting on boot for all runlevels (it looks like it just changed the symlinks in rc2.d etc). Looks good now.

---

