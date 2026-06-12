---
title: "Full remote desktop control"
date: 2006-10-17
forum: General Help
---

### Post by chiller on 2006-10-17
Hi People - great forum loads of information

im wondering if anybody can point me in the right direction?

i have installed Latest Xubuntu and ive modded it with the KDE desktop - Updated etc

my question is - i want to be able to leave my Linux Machine in the courner without a keyboard, mouse monitor installed on it - im wondering what the best application is to setup on the linux box so i can fully control from the XP machine  - so if i turn the linux box off i can login from the xp machine and so on - ive tried VNC and this seems to not allow me to login - unless the service isnt running from the login window - not sure

Can somebody point me in the right direction or maybe explain what i need to do 

thanks

chills

---

### Post by chiller on 2006-10-17
i wonder if this is what im looking for - [http://www.linuxtsc.org](http://www.linuxtsc.org) linux/windows terminal server client 

anybody used it ?

---

### Post by AndyCooll on 2006-10-17
A Terminal Server Client is installed by default on Ubuntu (not sure if it's the same one), however by default it isn't enabled to accept remote logons so you may need to enable it. Since VNC is one of its options to use you can then use that to remote into your Linux box.  

I'm not at my linux box at the moment, however I think it's somewhere in:  System-->Preferences-->Remote Desktop.

If you don't require a GUI, SSH is the way to go. It's also possible to tunnel gui apps using SSH.

:cool:

---

### Post by Cene on 2006-10-17
> **AndyCooll said:**
> 
If you don't require a GUI, SSH is the way to go. **It's also possible to tunnel gui apps using SSH.**


Huh, how is this done?

---

### Post by AndyCooll on 2006-10-17
> **Cene said:**
> Huh, how is this done?

How I wish I was at my Linux box at the mo! IIRC you amend your ssh_config file to allow remote X. I can't remember the exact wording but it's something along the lines of:
```
Remote Applications yes
Compression yes
```

You change the first of those two (by default it's set to "no") and add the second.

Then to open up Synaptic for instance you can simply type:
```
$ ssh -X andy@linuxcomputerIPaddress
$ sudo synaptic
```

And it should open up on the box you're sitting at.

:cool:

---

### Post by Cene on 2006-10-17
> **AndyCooll said:**
> How I wish I was at my Linux box at the mo! IIRC you amend your ssh_config file to allow remote X. I can't remember the exact wording but it's something along the lines of:
```
Remote Applications yes
Compression yes
```

You change the first of those two (by default it's set to "no") and add the second.

Then to open up Synaptic for instance you can simply type:
```
$ ssh -X andy@linuxcomputerIPaddress
$ sudo synaptic
```

And it should open up on the box you're sitting at.

:cool:

Thanks, got it working, i think. :)
One more question: Is it possible to get this working on Windows? Ie. when you connect to Linux box with PuTTy on Windows.

---

### Post by AndyCooll on 2006-10-17
> **Cene said:**
> Thanks, got it working, i think. :)
One more question: Is it possible to get this working on Windows? Ie. when you connect to Linux box with PuTTy on Windows.

I'm a bit hazy these days about this (it's awhile since I used this method). As far as remember, yes you can.

:cool:

---

### Post by clarkth on 2006-10-17
> **AndyCooll said:**
> I'm a bit hazy these days about this (it's awhile since I used this method). As far as remember, yes you can.

:cool:


Just tried it with PuTTY and couldn't get it to work.  Not that it doesn't, but I'll need to play with it some more

---

### Post by Viper001 on 2006-10-17
I also needed to figgure this out for SECURE remote management via a remote Windoze box.

Here is what I figgured out:

1) you need to have SSH installed and configured.
2) you then just set up Ubuntu Remote desktop as per the Wiki info
[]("http://ubuntuguide.org/wiki/Dapper#How_to_configure_remote_desktop_.28not_secure.29")
3)You will need a windoze vnc capable client. I chose to use TightVNC: [http://www.tightvnc.org]("http://www.tightvnc.org")

4) Once you have this installed and configured, first test things out (unsecured) on your local lan to see if you can get to the remote desktop.

5) assuming you can, then next step is to get a SSH capable windoze client on your machine to enable secure tunneling to the desination box. There are several available, PUTTY, SSH.com NON commercial.
You can get the GUI non commercial SSH client from :
[ftp://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe]("ftp://ftp.ssh.com/pub/ssh/SSHSecureShellClient-3.2.9.exe")

6) Once you get the SSH client set up and you can connect through it you can then tunnel your remote desktop connection through the SSH client to secure it.

Hope this helps a bit.

---

