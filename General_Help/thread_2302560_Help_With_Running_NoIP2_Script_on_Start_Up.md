---
title: "Help With Running NoIP2 Script on Start Up"
date: 2015-11-11
forum: General Help
---

### Post by cludgie on 2015-11-11
Hello there,

I've recently installed NoIP2 Dynamic DNS Update Client onto my desktop running Ubuntu Desktop 14.04. I find that sometimes it stops updating the DNS and therefore I can't resolve the hostname to the correct IP assigned from my ISP. 


I have to run the following command manually whenever this happens, or whenever I reboot the machine.


```
/usr/local/bin/noip2



```According to the documentation I have to follow these steps to run the NoIP2 on start up:


**"**If you want it to run automatically when the machine is booted, then
place the following script in your startup directory. (```
**/etc/init.d/rcX.d**

```or ```
**/sbin/init.d/rcX.d**
``` or ???) 

```

     #######################################################
    #! /bin/sh
    # . /etc/rc.d/init.d/functions    # uncomment/modify for your killproc
    case "$1" in
        start)
        echo "Starting noip2."
        /usr/local/bin/noip2
        ;;
        stop)
        echo -n "Shutting down noip2."
        killproc -TERM /usr/local/bin/noip2
        ;;
        *)
        echo "Usage: $0 {start|stop}"
        exit 1
    esac
    exit 0
    #######################################################

```

Where the 'X' in rcX.d is the value obtained by running the 
following command
    ```
grep initdefault /etc/inittab | awk -F: '{print $2}'

```    **"**
    
Thing is, I can't find ```
**/etc/inittab**
``` and therefore don't know where to place this script.


Any suggestions?




Thanks
Alex

---

### Post by brian-mccumber on 2015-11-11
When you open your file browser there should be a link there that says Computer, when you click that the correct ect folder should display. You should be able to find the folder inittab in there. When you installed that program if it created a .desktop in /user/share/applications you can make a startup entry for it using the Startup Applications program that is installed in Ubuntu. You can find Startup Applications by searching for startup in your dash. Alternatively, if that program didn't create a .desktop when it was installed you could make one yourself and then use that in Startup Applications.
[ATTACH=CONFIG]265490[/ATTACH]____[ATTACH=CONFIG]265491[/ATTACH]

If you use the Startup Applications program to make an entry and use this - [COLOR=#000000][FONT=Ubuntu Mono]/usr/local/bin/noip2 - as the Command entry, it may run it without you having to have a .desktop file for that script.[/FONT][/COLOR]

---

### Post by TheFu on 2015-11-11
You didn't install using **nip2** package? Have a good reason?  *<-- UPDATE: the no-ip2 package was removed from Debian due to a security issue. nip2 is NOT correct. See post #11 for more details.*

Also, for the next 2-3 years, we'll need to know  the exact ubuntu release you are running, because the way things startup is vastly changing. You can thank "systemd" for that change.
[https://askubuntu.com/questions/9382/how-can-i-configure-a-service-to-run-at-startup](https://askubuntu.com/questions/9382/how-can-i-configure-a-service-to-run-at-startup) describes how to do it for 14.04 and earlier releases.

BTW,  the suggestion in post #2 is NOT the recommended method.  Waiting until a userid logs in is not-so-good idea.

Assuming I understand the real issue.
If you have a router, I'd strongly recommend letting that device manage this stuff,  if  possible.

I used the no-ip client for a few years, but have since switched to a static IP and don't need it anymore.

---

### Post by cludgie on 2015-11-12
I installed using make on the CLI, as per the instructions on NoIP's website, from where I downloaded it.

Was 14.04 Desktop not enough information or?

I need the client to start on system start up rather than user log in. Does that mean that brian-mccumber's suggestion won't work?

As for the requirement. Static IP is not an option from my ISP so I have to use a dynamic DNS Update service. Nor does my router have this functionality to my knowledge.

Thanks guys for your help.

Regards
Alex

---

### Post by TheFu on 2015-11-12
Correct. brian-mccumber's suggestion doesn't do anything until the specific userid logs in.

Most $20 routers have DDNS support and No-IP is usually in the list of supported services.

14.04 desktop **is** enough. Sorry. I missed that, assuming you are running Unity and not KDE, LXDE, XFCE, Mate or something else. I'd rather not assume anything, mainly because I run "Ubuntu Server" on all my systems, not desktop installs.

*<-- UPDATE: the no-ip2 package was removed from Debian due to a security issue. nip2 is NOT correct. That means either source or a manual package install will be needed.  I couldn't find any PPA either. See post #11 for more details.*

You should
a) remove the package that was manually installed.
b) install and configure the nip2 package from the normal repos.
c) be happy.

For most people, installing software from source/manual download is around 4th on the list of ways to install software on most Linux systems.
1) Normal repo
2) respected PPA
3) respected .deb file (this starts to break some dependencies many times)
4) binary package from the author
5) source package from the author

These days it is very strange for any end-user to need more than 1 or 2.  Using a non-respected PPA could mean turning over your system to a hacker, so do a tiny bit of research to see if the PPA you found is widely used or not. Being hosted by the author or on Launchpad is a good sign.

Of course, sometimes packages get broken and that's where 4 and 5 come in .... AFTER you've tried to use 1, 2, and 3 first. So ... did 1, 2, and 3 already fail for your needs? If so, we can go deeper, but I'd rather just solve this with "1" to save both of us time.  
*<-- UPDATE: Which cannot be done in this case. See post #11 for more details.*

---

### Post by brian-mccumber on 2015-11-13
The original post asked where a folder was and how to run an app at startup. My suggestions were based on what the original post asked for.

---

### Post by TheFu on 2015-11-13
> **brian-mccumber said:**
> The original post asked where a folder was and how to run an app at startup. My suggestions were based on what the original post asked for.

"Startup Applications" is a bad name for the program.  Rather it should be called 
"Auto-Start User Applications at GUI login" to actually explain what it does.

[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html)

The issue with this option is that "Startup Applications" doesn't work at system startup. It only works at end-user GUI login.  If the userid doesn't login with a GUI or never logs in at  all, then the program will never run. So if I use ssh to login, the configure "startup applications" will not run.

Or did I misunderstand something?  Sometimes I miss important details.

---

### Post by cludgie on 2015-11-16
Thanks again for your responses guys.

I think I've found a simple work around???

I've inserted the following line into my crontab:
```
@reboot /usr/local/bin/noip2
```

I'm also unable to find the noip/noip2 in the repositories as follows:
```
sudo apt-get install noip2
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package noip2



```

Any suggestions?

As for the router, it's a ISP supplied router which doesn't have DDNS features I'm afraid and while I will get round to buying my own, this should suffice in the meantime.

Again, thank you in advance.


Alex

---

### Post by TheFu on 2015-11-16
I already provided the correct package name above.  UPDATE *<--- This was not correct. The package was removed from the debian repos.*

---

### Post by Dow_Hurst on 2016-01-07
Just checked my Linux Mint 17.3 repos by running

apt-cache search nip2
results in
nip2 - spreadsheet-like graphical image manipulation tool

I get the same result on a raspberry pi.  And there are no results for noip2 or noip.

The repos checked are:
deb [http://packages.linuxmint.com](http://packages.linuxmint.com) rosa main upstream importdeb [http://extra.linuxmint.com](http://extra.linuxmint.com) rosa main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty partner

Checking out with google "ubuntu ppa nip2 trusty" resulted in this webpage popping up at the top of the search output:
[http://www.ubuntuupdates.org/package/core/wily/universe/base/nip2](http://www.ubuntuupdates.org/package/core/wily/universe/base/nip2)
which is the page for the vips image processing package.  Something may have been incorrectly updated or linked, I don't know.  But, this isn't a package for no-ip.com.

---

### Post by TheFu on 2016-01-07
You are correct sir. Lots of mistakes in my replies.
* Seems the packages were removed from the Ubuntu repos over security issues.
* I couldn't find any PPA with the updated versions.
* Looks like source code is the only way. Too bad.
* I did look for the package all those months ago and could have swore the nip2 package was for no-ip. However the facts seem to refute that claim. I apologize.

Putting an @reboot task into the crontab isn't how I'd do it, but doesn't seem unreasonable.  If I were lazy, I'd just add a line to the /etc/rc.local. If I cared more, then I'd create/find a script for /etc/init.d/ and use update-rc.d to create the links for the different runlevels.  Under newer OSes with systemd - don't know what I'd do, but probably keep doing it the old way.  I've had trouble making things start on systemd in the way I needed already.  Just be certain that your backups include whatever you change for this process startup.  I backup /etc completely, so either method would be captured.

So ... sorry for all the confusion that my lack of complete research has caused.  The last time I used no-ip with a dynamic IP was in the 2008-2010 timeframe. I do not recall exactly.

I'll edit my prior posts pointing out issues (leaving the incorrect stuff there). Hope that helps later lurkers reading. ;)

---

