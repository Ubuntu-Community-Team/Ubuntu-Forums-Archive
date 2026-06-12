---
title: "Anti-virus Programme?"
date: 2014-08-16
forum: General Help
---

### Post by anon_private on 2014-08-16
Do I need to install anti-virus and anti-malware programmes with kubuntu?

If so, can you recommend good programmes?

Thanks

---

### Post by claracc on 2014-08-16
Please, read the following documentation:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

and the sticky: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by vasa1 on 2014-08-16
And this has been gone over before: [http://ubuntuforums.org/showthread.php?t=2237956](http://ubuntuforums.org/showthread.php?t=2237956)

---

### Post by em3raldxiii on 2014-08-16
Short version:  Extra security is never bad, and if you want to use one, a popular one is called ClamAV.  It's usually just used to protect *other systems* on your local LAN that might have other operating systems on them.  If you don't run as ROOT on your Linux machine, and if you do not execute malicious code manually, then the overall security of your Ubuntu machine does not require anti-malware software.  Please visit the links in the above posts for full details.

---

### Post by anon_private on 2014-08-17
Thank you

When I start Kubuntu. I use my password associated with my name. Is this root?

When you say execute code, what does this mean?

Out of interest, does kubuntu run a firewall. If so, can I see it?

Best wishes

---

### Post by claracc on 2014-08-17
The default firewall in ubuntu is ufw. 

To enable it to block incoming connections, you open a xterm, ctrl+alt+t and run the command:

```
sudo ufw enable
```

Here, you have a link to know more about ufw: [https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html)

To execute code means to run commands in terminal, i.e.: install programs which are not in repositories, run them and so on.

To run commands with root privileges you will have to uso the sudo order, then you will be asked to introduce your password and you will have to enter your user password, not need aroot account password. Please read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by em3raldxiii on 2014-08-17
@anon_private:  using your password at boot/login is not "root".  Read @claracc's link about RootSudo for full details, but when you are just using your computer for all your normal things, you are not running as root.  When you open a terminal (such as xterm) and you type a command like this:  **sudo edit /file/location.file** you are invoking root powers for that one command, and you have to enter your password _again_ in order to give it permission to do so.  So, if you don't trust the source (like, if some shady person tells you to do it), then don't do it.  @claracc gave you very good answers to the rest of your questions. :D

---

### Post by SeijiSensei on 2014-08-17
The firewall is not enabled in Ubuntu by default because Ubuntu ships with no active listeners.  If you scanned the machine from another location on the network with a program like [nmap](http://insecure.org/nmap) you would see no open ports.  If you install servers, then ports may or may not be opened.  Installing Apache opens the HTTP and HTTPS ports (80, 443) on all interfaces, but many other servers like Postfix or MySQL are attached only to the localhost interface (127.0.0.1) and are not visible from outside the machine without manual configuration.

---

### Post by stalkingwolf on 2014-08-17
my basic answer when asked this question is do you need an av probably not at this time.  Should you install one absolutely.   I install clamtk from synaptic package manager.

In 5 years i have had one virus (my fault im sure. but did teach me that it is possible.)came thru facebook chat.  after that i started installing clamtk , there have been no recurrances.

---

### Post by anon_private on 2014-08-19
> **claracc said:**
> The default firewall in ubuntu is ufw. 

To enable it to block incoming connections, you open a xterm, ctrl+alt+t and run the command:

```
sudo ufw enable
```

Here, you have a link to know more about ufw: [https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html)

To execute code means to run commands in terminal, i.e.: install programs which are not in repositories, run them and so on.

To run commands with root privileges you will have to uso the sudo order, then you will be asked to introduce your password and you will have to enter your user password, not need aroot account password. Please read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thank you for the information.

I have read the page, and was pleased to see that there is a graphical firewall (FirewallBuilder).

I am not sure if most users use a firewall, or if it is highly recommended, desirable, or only for the ultra cautious.

In Muon, I see a number of packages that look like firewallbuilder. I assume that I would need to download and install all of them

Best wishes

> **stalkingwolf said:**
> my basic answer when asked this question is do you need an av probably not at this time.  Should you install one absolutely.   I install clamtk from synaptic package manager.

In 5 years i have had one virus (my fault im sure. but did teach me that it is possible.)came thru facebook chat.  after that i started installing clamtk , there have been no recurrances.


Thank you for responding.

I see that camtk is also available for kubuntu users (via Muon).

What I am not clear about is if clamtk is all that I need. For example, in Muon there a number of packages that look connected to clam

Does clamtk update automatically. Is it ondemand, or a package that runs in the background. Is it heavy on system resources? Does it eliminate as well as check.

I am not clear if it is designed to detect Windows, Linux, or all viruses (subject to signatures).

Thanks

---

### Post by claracc on 2014-08-19
You are welcome.

I has enabled ufw in my ubuntu 12.04 dual boot vista laptop, I installed Gufw (gui) to manage ufw.

In order to know if you need a firewall, please read: [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

---

