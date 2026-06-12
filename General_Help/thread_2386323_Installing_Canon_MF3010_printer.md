---
title: "Installing Canon MF3010 printer"
date: 2018-03-04
forum: General Help
---

### Post by kannanramaiyer on 2018-03-04
Hey! I am new to Ubuntu. Actually I am using lubuntu 17.10.

I have a Canon imageCLASS MF3010 printer and I tried hardly to install it that I lost my full day yesterday. But towards the dusk I was able to download a driver from Canon's page and followed the instructions found online to install it. Whereas, it was not an apt driver for printer. Hence, I selected the nearest model no. to that of my printer and got it installed and successfully printed the test page.

But today, while printing pdf documents I noticed that it is taking almost 30 seconds to print a normal pdf file with a single page. When a scanned pdf document was printed the print is not at all coming and the system is often hanging.

So please help me in this. I have tried switching the usb ports and everything I could but am not finding any results.

Please haste for help.

Thanks in advance.

---

### Post by kenogo2 on 2018-03-04
I'll do my best... So this isn't enough info to really start figuring out the problem, but we'll get the necessary info together. The printing service that is used and writes the error logs for us is the "Common Unix Printing System" (CUPS). In order to get useful information in the cups error logs, we first need to change the logging level. So open a terminal and type
```
cupsctl LogLevel=debug
```
Now print a pdf. After that, check the log:
```
cat /var/log/cups/error_log
```
and post the output here so we can see if something interesting is in there.

---

### Post by kannanramaiyer on 2018-03-04
I have tried to print a pdf file and the print didn't come. I tried to get the log and I guess that the terminal was not able to hold the entire log message. I have attached herewith whatever was available from the terminal.

---

### Post by kenogo2 on 2018-03-05
Okay, thank you. I have to say I'm not very experienced with printers and this can get very tough. I feel like the problem is really driver related and Canon printers can be particularly hard on Linux. Where exactly did you download the drivers from? Can you share a link? Can you also please share the output of ```
sudo dpkg -l | grep cndrvcups
```

---

### Post by Mohammed H N on 2018-12-18
Hi , I installed MF-3010 Canon printer , but still dosent print anything ,My Operating system is Ubuntu 18.04 LTS

---

### Post by wildmanne39 on 2018-12-18
Hello Mohammed H N, please start a thread at the link below if you need support instead of posting in someone else's old thread.

[https://ubuntuforums.org/forumdisplay.php?f=332](https://ubuntuforums.org/forumdisplay.php?f=332)

Thanks

---

### Post by Mohammed H N on 2018-12-18
> **wildmanne39 said:**
> Hello Mohammed H N, please start a thread at the link below if you need support instead of posting in someone else's old thread.

[https://ubuntuforums.org/forumdisplay.php?f=332](https://ubuntuforums.org/forumdisplay.php?f=332)

Thanks

Thank you

I started a new thread and happy to help me if you can

---

### Post by him610 on 2018-12-18
it seems like the printing issue has been solved previously. Be sure to read all of the replies.
[https://ubuntuforums.org/showthread.php?t=2089269]("https://ubuntuforums.org/showthread.php?t=2089269")

---

