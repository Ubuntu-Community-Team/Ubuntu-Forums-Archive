---
title: "Connecting to my desktop pc from my tablet via ssh"
date: 2014-05-01
forum: General Help
---

### Post by linux_dream on 2014-05-01
Hi guys,
I have followed the tutorial at [http://news.softpedia.com/news/How-to-Control-Your-Linux-PC-with-an-Android-Device-396004.shtml](http://news.softpedia.com/news/How-to-Control-Your-Linux-PC-with-an-Android-Device-396004.shtml) but the last step does not work. More precisely when it tries to connect, it takes a really long time and then I get a message such as "Could not connect. Retry?".
I have disabled my firewall just in case it could be the responsible, but that didn't help.

---

### Post by TheFu on 2014-05-01
Does the PC have a static IP?
Does the PC running the sshd?
Which ssh client is being used?  I like terminal-IDE, but have heard good things about Juice.
What to the log files say? Every ssh  connection is logged and logging levels can be turned up.

For ssh, use **fail2ban** if you are worried about security (and you should be!). The defaults work fine for most people if ssh listens on the default port.

---

### Post by linux_dream on 2014-05-01
> **TheFu said:**
> Does the PC have a static IP?
I think so, I am not 100% sure. 

> Does the PC running the sshd?ssh you mean? Yes... 
```
sudo service ssh start
``` returns ```
start: Job is already running: ssh



```
> Which ssh client is being used?  I like terminal-IDE, but have heard good things about Juice.
What to the log files say? Every ssh  connection is logged and logging levels can be turned up.I use Juicessh (on Android). Where can I find the log file(s)?

> For ssh, use **fail2ban** if you are worried about security (and you should be!). The defaults work fine for most people if ssh listens on the default port.
As soon as I get my connection to work, I'm going to use fail2ban. Thanks for the tip, I wasn't aware of this.

---

### Post by TheFu on 2014-05-01
Without a static IP on the server, this is going to be nearly impossible. If you aren't sure, then it probably is NOT static.
Are you testing over wifi on the same LAN?  Trying to do this over the internet adds more complexity ... for later.

---

### Post by linux_dream on 2014-05-01
Finally I could make it...
What I did was uninstall openssh-server, remove the folder /etc/ssh, reinstall openssh-server. The files in /etc/ssh were quite different from the ones I had... and following the tutorial worked. 
So I'm very happy, thank you. 
Problem solved.

---

### Post by CaptainMark on 2014-05-02
As previous posts say, make sure you are careful about your security if you plan on attempting this connection over the internet, some tips for you:

Set up private/public key pairs for connection
Disable password entry
Change the port from 22 to something more obscure
Use UFW to limit connections to your chosen port

If you don't understand any of these statements then you're not ready to put your server on the internet. Read up on them and make sure you know what they mean and implement them before going online with your server.

---

### Post by TheFu on 2014-05-02
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) explains what to do for more secure ssh connections. Hope it helps.

---

### Post by linux_dream on 2014-05-02
I see guys... but as far as I understand, my network is not accessible from the "outside world". My ssh connection is just through my wifi. Should I really worry about making it more secure?

---

### Post by TheFu on 2014-05-02
> **linux_dream said:**
> I see guys... but as far as I understand, my network is not accessible from the "outside world". My ssh connection is just through my wifi. Should I really worry about making it more secure?

That depends on your risk profile.  Are there any Windows machines on the same subnet?  Do you allow javascript from all websites?  Do you run Java Applets? Do you open PDF files and allow anything beyond viewing (i.e. javascript, external DB storage)?  Do you run Facebook games or use IRC to share files?  Any bittorrent? These are high-risk activities.

I wouldn't bother changing the default port internally for ssh, 22 is fine.  I DO install fail2ban on every machine with ssh, however. I can't think of a reason NOT to do that.  

So - did you ever determine if your server's IP is static or not?  After every reboot, the IP could change otherwise. Not fun.

---

