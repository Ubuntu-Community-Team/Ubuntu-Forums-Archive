---
title: "Trouble with FTP"
date: 2007-10-15
forum: General Help
---

### Post by Neumy on 2007-10-15
Hi all, I recently built a Ubuntu Web Server. I love the simplicity of the build with only the Linux apps and the ease to add the appropriate apps for my webserver.

The apps that I added were SSH, proFTP, Apache, MySQL, and PHP. At first everything worked fine (including FTP), but there's always security holes that need adjusting when these apps are first installed, so I started re-configuring SSH and proFTP. 

Now, for some reason, my FTP will not work. I've re-installed proFTP and set the config back to the default - but still no luck. 

I'm wondering if someone can help me figure out what is causing my FTP to not connect.

Here's my configs (I'm just using `diff` with the default):

**`diff proftpd.conf proftpd.conf.default`**
< UseIPv6    off
---
> UseIPv6    on

< ServerName    "Ubuntu FTP Server"
---
> ServerName    "Debian"


**`diff sshd_config sshd_config.default`**
< LoginGraceTime    30
< PermitRootLogin    no
---
> LoginGraceTime    120
> PermitRootLogin    yes

< ClientAliveInterva   l 60
< ClientAliveCountMax    30

< UsePAM    no
<
< AllowUsers    me
---
> UsePAM    yes

---

### Post by maybeway36 on 2007-10-15
Even smb.conf seems to be easier to configure than the linux FTP daemons. Sigh...

---

### Post by thirddeep on 2007-10-15
First, test things locally like this
```
ftp localhost
```

Then post if it works.

Thd.

---

### Post by Neumy on 2007-10-15
I'm seeing the problem 

"530 Login incorrect.
Login failed."

I know I'm using the correct login for my ssh, but where would I start looking to make sure that this user is configured to use FTP?

My `passwd` file says this about FTP:
sshd:x:104:65534::/var/run/sshd:/usr/sbin/nologin
proftpd:x:105:65534::/var/run/proftpd:/bin/false
ftp:x:106:65534::/home/ftp:/bin/false

my `group` file says this:
nogroup:x:65534:

---

### Post by Neumy on 2007-10-15
I think I found the problem. I checked out the `/var/log/proftpd/proftpd.log`; the USER is trying to access the stated shell in the `passwd` file. I have modified that user to run a menu:

me:x:1000:1000:Me:/home/me:/home/mainmenu

In my menu, I will launch the appropriate shell (if the appropriate username/password is entered - extra security). 

I guess my question would be, how do I work around this, so that the FTP is grabbing the appropriate shell.

Thanks for your help.

---

### Post by Neumy on 2007-10-15
I've further troubleshooted the issue and found a variable in the proftpd.conf that should solve my problems.

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
RequireValidShells              off

Unfortunately, when I restarted the proftp daemon, I received the following error:

  - Fatal: unknown configuration directive 'RequireValidShells' on line 35 of '/etc/proftpd/proftpd.conf'

Why doesn't this work? Has anybody used it? Is there another option that I should use to get around this?

---

### Post by Neumy on 2007-10-15
I did manage to get a little farther. Apparently, `RequireValidShells` is a typo - the variable should be `RequireValidShell` without the "s". This did resolve my restarting proFTPd. 

With the new configuration, I was able to ftp localhost. However, trying from an outside location, I'm still not able to get my FTP access. This means that something is not configured right via SSH, Router, or FTP client. 

I'm still trying to figure this out, but it's nice to know I'm 1 step closer. If any of you have anything else I should look at or try, let me know.

---

