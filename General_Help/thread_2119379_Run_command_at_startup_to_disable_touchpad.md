---
title: "Run command at startup to disable touchpad"
date: 2013-02-23
forum: General Help
---

### Post by Enthusiast94 on 2013-02-23
Hello everyone! Actually, I want to automatically disable my touchpad everytime I restart my system. So here's the command: 

```
xinput set-prop 13 "Device Enabled" 0
```

Now, could you please tell me to which file do I need to add this line? Also, I'd like to set my screen brightness to 50% at every startup instead of manually using the function keys every time. 

Thanks,
Enthusiast94

---

### Post by sudodus on 2013-02-23
Welcome to the Ubuntu Forums :-)

Have you checked that your command really works? Can you run it in a terminal window just like that?

Do you want it for several users, or only for your own user account?

It probably works if you enter it into crontab and let cron run it at boot.
```
crontab -e
```
and add your command at the end of the file (the text in the editing window)
```
@reboot [COLOR="red"]/path/[/COLOR]xinput set-prop 13 "Device Enabled" 0
```
You need to find the full path to the command xinput and add it to the command line. Use the output of this command
```
which xinput
``` I think it is
```
[COLOR="Red"]/usr/bin/[/COLOR]xinput
```

But if it needs that your desktop environment has started, it won't work, and you need to add it somewhere else. And if you need superuser privileges, use
sudo crontab -e instead to add it to the superuser's crontab file.

---

### Post by Enthusiast94 on 2013-02-23
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Have you checked that your command really works? Can you run it in a terminal window just like that?

Do you want it for several users, or only for your own user account?

It probably works if you enter it into crontab and let cron run it at boot.
```
crontab -e
```
and add your command at the end of the file (the text in the editing window)
```
@reboot [COLOR="red"]/path/[/COLOR]xinput set-prop 13 "Device Enabled" 0
```
You need to find the full path to the command xinput and add it to the command line. Use the output of this command
```
which xinput
``` I think it is
```
[COLOR="Red"]/usr/bin/[/COLOR]xinput
```

But if it needs that your desktop environment has started, it won't work, and you need to add it somewhere else. And if you need superuser privileges, use
sudo crontab -e instead to add it to the superuser's crontab file.

Yes, I've been running this command every time I boot my system. Also, I'm a complete newbie to ubuntu, so do you mind explaining what exactly is 'crontab'?

---

### Post by sudodus on 2013-02-23
Crontab is a table with command lines in a file, that is read by the program cron every minute. So when cron find something to do, it does it on that minute. Or at boot (which is what you want right now.

See this link

[[COLOR="Red"]http://www.pantz.org/software/cron/croninfo.html[/COLOR]]("http://www.pantz.org/software/cron/croninfo.html")

---

### Post by Enthusiast94 on 2013-02-23
> **sudodus said:**
> Crontab is a table with command lines in a file, that is read by the program cron every minute. So when cron find something to do, it does it on that minute. Or at boot (which is what you want right now.

See this link

[[COLOR="Red"]http://www.pantz.org/software/cron/croninfo.html[/COLOR]]("http://www.pantz.org/software/cron/croninfo.html")

Thanks for the detailed description. Also, I read somewhere that startup commands can be put into a file called 'rc.local'. Any idea how do I go about it?

---

### Post by sudodus on 2013-02-23
> **Enthusiast94 said:**
> Thanks for the detailed description. Also, I read somewhere that startup commands can be put into a file called 'rc.local'. Any idea how do I go about it?
Yes, it is possible, but I have not yet learned the details about it.

---

### Post by Enthusiast94 on 2013-02-23
> **sudodus said:**
> Yes, it is possible, but I have not yet learned the details about it.

Just found out the command: 

```
echo '/path/to/my/command' >> /etc/rc.local
chmod +x /etc/rc.local
```

Now, could you just tell me what exactly do I need to type instead of '/path/to/my/command'?

---

### Post by sudodus on 2013-02-23
You have it in post #2 (just skip @reboot)

---

