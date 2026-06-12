---
title: "Firestarter doesn't automatically load at startup"
date: 2007-05-28
forum: General Help
---

### Post by trak87 on 2007-05-28
I just noticed that Firestarter doesn't automatically load (edit: the iptables chains) on startup in Feisty. I tried reinstalling the program via Synaptic and it just doesn't auto start like it used to.

I have seen the suggestion to add firestarter to System, Preferences, Sessions, but isn't this area only for the current user? I want the program to work system wide. 

What's wrong with Ubuntu here? I did update the kernel to 2.6.20-16 today but went back to 2.6.20-15 after noticing lots of problems. Perhaps this is a residual problem? I do see firestarter in each of the following directories: /etc/rc0.d through /etc/rc6.d....

---

### Post by pseudonym on 2007-05-29
I'm not sure whether your issue is about Firestarter not starting at all, or the GUI not starting up when you log in. If the firewall is not running at all it's a known bug with the version of iptables included in Feisty. The workaround is available [here]("https://bugs.launchpad.net/debian/+source/firestarter/+bug/42759") (see the posts by Rob_H in particular).

If instead it's the GUI not starting up the only advice I have is to say that Firestarter is still running without the GUI, if you didn't know already. The GUI is just for setup and administration. In other words, you don't need to load Firestarter on login, unless you want easy access to the GUI for admin purposes.

I always wait a couple of days before installing kernel updates, too, btw. They're one of the most common causes of problems and it's wise to see if any have cropped up with others before updating your own system.

HTH

---

### Post by ramjet_1953 on 2007-05-29
Why do you want Firestarter to load automatically, anyway?

It is a configuration tool for iptables, NOT a firewall.

iptables automatically closes all ports and your system is secure. Leve it alone unless you have good reason to change it.

Firestarter needs to run with root priviliges and it is a high security risk to have it running for no reason.

Regards,
Roger :cool:

---

### Post by mcduck on 2007-05-29
There are 2 parts in Firestarter, the GUI, which is just a configuration tool, and then the Firestarter script that enables & configures iptables. The script should be running automatically and all the time, GUI is only needed for changing settings.

---

### Post by trak87 on 2007-05-29
Sorry, I wasn't clear. When I run the following after bootup, I see no chains/tables:

```
sudo iptables -L -n
```

To cope, I added "/etc/init.d/firestarter start" to /etc/rc.local and it now sets up iptables.

However, somethng is broken. On another computer running feisty, firestarter (the iptables stuff) starts fine. On mine I get empty iptables. My system has lots more libraries and progs installed though. Also, I see no firestarter or iptables errors mentioned in /var/logs/*

I'll remove the line in rc.local, retest and report back...

---

### Post by trak87 on 2007-05-29
I just remembered I installed pdnsd, a dns caching program. I had to change a line in one of the dhcp configs. Maybe that's the problem, because the link mentioned above describes a networking conflict with firestarter.

This statement (from the link above) catches my attention:

> What disturbs me is that nobody seems to care about this problem, or at least I have not seen anyone getting upset by this but this could be a security problem. Moreover, you are not warned that the firestarter daemon is not running. SO the only way you will find this out is when you actually install the GUI and check the status there.

I've been thinking the same thing ever since many people on these forums have been discouraging the use of firewalls while we're in a tremendous era of virii, trojans, spyware, etc. It makes no sense at all. Of course, we're encouraged to trust the router. That's ridiculous!

---

### Post by pseudonym on 2007-05-29
> **trak87 said:**
> I just remembered I installed pdnsd, a dns caching program. I had to change a line in one of the dhcp configs. Maybe that's the problem, because the link mentioned above describes a networking conflict with firestarter.
You may well have identified the source of your problem. Firestarter has something of a history of being fussy with dhcp in Debian-based distros.

Might I also recommend [Firehol]("http://firehol.sourceforge.net/") as another iptables frontend instead? There's no GUI, but the configuration language is very intuitive. It's also a lot less temperamental and more flexible than Firestarter, too - eg. it doesn't care what interfaces you have up at boot time (unless you want it to), which is good if you use things like USB ethernet adapters which you plug and unplug.

Just one proviso - you need to do a small hack to make sure Firehol starts in Feisty. Details are [here]("https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017") (see the post by scottmuz).

> **trak87 said:**
> I've been thinking the same thing ever since many people on these forums have been discouraging the use of firewalls while we're in a tremendous era of virii, trojans, spyware, etc. It makes no sense at all. Of course, we're encouraged to trust the router. That's ridiculous!
These 'debates' are raging all the time. It's the same with anti-virus in Linux. Pay no attention is what I say. Those who rail against the entirely reasonable and responsible step of installing firewall and especially AV usually do so for religious reasons rather than on the basis of reasoned argument.

I can see the Ubuntu devs point of view, though, in making bugs in packages like Firestarter less of a priority. The distro installs with no server programs installed by default which accept connections from the internet, and all ports are closed. This is secure enough for most home users. Firewall packages can 'stealth' your system, but their main value is in providing an easy way to control iptables for those who can't be bothered/don't have time to learn it ie. most people.

---

### Post by trak87 on 2007-05-29
Firehol is broken as-is, and needs tweaking. This is the same situation with Firestarter for me. And the recommendation to install Firestarter in the user Sessions area is strange. How do you have a system wide firewall then if it's only running for the current user? Or am I misunderstanding how Sessions works?

---

### Post by trak87 on 2007-06-01
As a follow up, for those having trouble with firestarter not loading the firewall rules via iptables properly, here's one solution that came from one of the links above. And btw, to see if Firestarter has properly set up the iptables chains, execute the following and you should see a bunch of text:

```
sudo iptables -L -n
```

Now the fix (for Feisty anyway). Go to /etc/NetworkManager/dispatcher.d/ and as root create a new empty text file called "50firestarter" with your favorite editor.  Cut and paste the following code:

```
#!/bin/sh

. /etc/firestarter/configuration 2>&1

# Check to see if the interface that changed is the one currently
# protected by firestarter. If not, quit.
[ "$1" != "$IF" ] && exit

# Check the current status of Firestarter
[ -e /var/lock/subsys/firestarter -o -e /var/lock/firestarter ]
fs_status=$?

case "$2" in
        up)
                [ "$fs_status" -gt 0 ] && /etc/init.d/firestarter start
        ;;
        down)
                ## Uncomment the following line to allow this script to
                ## turn off the firewall when the interface goes down.
                #[ "$fs_status" -eq 0 ] && /etc/init.d/firestarter stop
        ;;
esac

```

Save and exit.

Now give this file execute permissions:

```
sudo chmod 755 50firestarter
```

Now reboot and run the above iptables command ("sudo iptables -L -n") to test.

---

