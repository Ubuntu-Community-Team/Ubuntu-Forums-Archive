---
title: "Cron does not run a program"
date: 2012-12-06
forum: General Help
---

### Post by wolfijenne on 2012-12-06
I tried to use cron to periodically test the internet connection with a bash script. The cron job self works, the script is called.
However, in the script I want to open Google Chrome using the command
chromium-browser --args [http://www.google.com](http://www.google.com)

it works perfectly when the script is called directly through the terminal.
The command however does not work when the script is called from cron. The logging works perfectly the right way.

Anyone knows what to do here?

Here is the data:
crontab -e:
* * * * *  /home/user/checkinet.sh

checkinet.sh:
url="www.google.com";
if ping -c 1 $url
then
echo "Internet is up!" >> /tmp/inetcheck.log
chromium-browser  --args [http://www.google.com](http://www.google.com)
else
echo "Intenet is down!" >> /tmp/inetcheck.log
fi

---

### Post by agillator on 2012-12-06
Sounds suspiciously like your problem is the environment. Cron uses a clean environment, not the one you normally use. See [http://ubuntuforums.org/showthread.php?t=2084935](http://ubuntuforums.org/showthread.php?t=2084935) message #4 for more info and possible solution approach.

---

### Post by steeldriver on 2012-12-06
in particular what DISPLAY do you expect it to open the browser window on and does cron have xauth on that display?

---

### Post by Kirk Schnable on 2012-12-09
Also, the way you have the cron scheduled, you might want to check for already running instances of Chrome. Otherwise, you'll end up with a new window opening up every 60 seconds when the cron runs again and finds that the Internet is up.

---

