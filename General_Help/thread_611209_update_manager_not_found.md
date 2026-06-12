---
title: "update manager not found"
date: 2007-11-12
forum: General Help
---

### Post by kelliot on 2007-11-12
Hello,

I had Ubuntu 6.06 server installed for us by someone who is no longer available, so it's up o me now. I just realized that there is no update manager and it's been many months with no updates.  Everything is running ok (yeah linux), but I'd like to get current.  Can someone tell me how to turn this feature on?  

Thanks

---

### Post by taurus on 2007-11-12
What happens when you run these two commands from a prompt?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kelliot on 2007-11-12
I get:

et:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Fetched 3B in 1s (2B/s)

but I can't find a manager to do anything with this.

Any suggestions?

---

### Post by taurus on 2007-11-12
Did you run the second command?

What manager are you talking about?  Are you running a server or a desktop?  It says you are using a server from your original message.

---

### Post by kelliot on 2007-11-12
duh.... running the second half helped.  Thanks a lot!!

---

### Post by trak87 on 2007-11-12
You did the first command (above) but not the second. The first one gets the latest list of packages in the repositories. The second one actually finds out what packages you need to install to be current. If you execute the second command you will be current. 

Note that people who manage servers are generally much more conservative about updating the system because it can break something. This isn't good when many people are depending upon the server.

On server installs there is no graphical interface, but you can install one. Some suggest using a really lightweight GUI interface for servers. I'm not an expert but I've heard some say xfce or fluxbox work well for that. Note that a gui interface is sorta counterproductive for a server.

Something like this would work though: 

```

sudo apt-get update
sudo apt-get install xfce
```

---

