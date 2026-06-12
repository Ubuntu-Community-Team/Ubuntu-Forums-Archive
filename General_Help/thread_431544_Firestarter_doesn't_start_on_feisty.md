---
title: "Firestarter doesn't start on feisty"
date: 2007-05-03
forum: General Help
---

### Post by musther on 2007-05-03
I've installed firestarter, set it up, and now it should be running as a service when I boot, /etc/init.d/firestarter is there and I can run /etc/init.d/fiestarter start as root, and it works.  I've run update-rc.d remove and than run update-rc.d to put the rc scripts back, but still no luck.

but according to /etc/firestarter/firestarter.sh status it's still not running after a reboot.

Is it something to do with me using a wireless interface and it not having come up in time?

---

### Post by zvacet on 2007-05-03
Your firewall is runing be sure about that.Firestarter is just GUI for iptables wich are your firewall installed and runing by default.Because of GUI Firestarter makes it easyer to make changes if you want to.In Ubuntu all ports are closed by default,so you don´t have to worry too much.

---

### Post by musther on 2007-05-03
But surely /etc/init.d/firestarter is the deamon which should be running?  If not, then why does it try to load on boot (the scripts are in the rc directories).  

Also, I don't believe that Ubuntu has all ports closed by default as VNC, FTP and SSH (to name just a few) work straight away, no modification needed.

---

### Post by rich.bradshaw on 2007-05-03
Ok

Firestarter sets up iptables. YOU DONT NEED IT RUNNING ALL THE TIME! In fact, it's a security risk to have it running, as it runs as root.

Those ports are not open by default, only if you install openssh, and enable remote desktop and ftp.

Once firestarter is on, then it's on. You can check your firewall logs by going to system/admin/system logs.

Try blocking all ports in firestarter (default) close firestarter, reboot or whatever you want, then try and connect to you computer - it won't work. Then you can be sure that it's working. I used to think I needed it running as well - we are all used to Windows, where you can't trust it unless you can see it actually working - it's hard to accept that Ubuntu just works - you don't have to be able to see open software for it to be working it's magic!

---

### Post by musther on 2007-05-03
It's not that I expected the firstarter GUI to be running all the time, I don't want that at all.  But I looked on the firestarter website, specifically this page:

[http://www.fs-security.com/docs/persistence.php](http://www.fs-security.com/docs/persistence.php)

Which clearly gives the impression that there are two parts to firestarter, the GUI (which I don't want running all the time) and the deamon.  It gives the impression that you need the deamon running.  

And if it's the case that it simply modifies the iptables, then why does it try to start the firestarter deamon (which is not the gui)?

If I run:
```
/etc/init.d/firestarter start
```

The deamon starts, this IS NOT the GUI, so if it isn't needed for the firewall (which is handled by iptables), and it isn't the GUI, then what is it doing, or not doing?

Sorry, this is just a little confusing, it seems redundant.

---

### Post by fragos on 2007-05-03
Once you run firestarter once the iptables firewall is configured.  When you run firestarter you can monitor the firewall results in real time in a GUI display.  If you terminate firestarter I believe that special logging function is also terminated.  You need not run firestater for other than GUI configuration.  If you wish to run it by default do System-> Preferences-> Sessions and in the startup tab you may add firestarter and it will start with Gnome.

---

### Post by musther on 2007-05-04
That makes sense, and I'm not trying to be annoying, but that only seems to explain the firestarter GUI, what does the deamon do, does it log those real time events even if the GUI isn't running?

Thanks for you help.

---

### Post by zvacet on 2007-05-04
[http://www.grc.com/stevegibson.htm#projects]("http://www.grc.com/stevegibson.htm#projects")

Click on shields up to test if you have any port open.

---

### Post by heatpumpcontrol on 2007-05-04
> **musther said:**
> I've installed firestarter, set it up, and now it should be running as a service when I boot, /etc/init.d/firestarter is there and I can run /etc/init.d/fiestarter start as root, and it works.  I've run update-rc.d remove and than run update-rc.d to put the rc scripts back, but still no luck.

but according to /etc/firestarter/firestarter.sh status it's still not running after a reboot.

Is it something to do with me using a wireless interface and it not having come up in time?

I found a solution and apparently is has to have the GUI up and running. 

[Solution]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_Firestarter_start_automatically_at_startup")

Good luck
HPC

---

### Post by musther on 2007-05-04
I don't really want a solution, I just want to know what the deamon does as I apparently don't need to have it running?  Very odd, nobody seems to know the answer!

---

### Post by nick1 on 2007-05-04
Greetings,

I believe Firestarter is not enabling my firewall rules on system bootup.

First, some information:

I am using Ubuntu Feisty Fawn 7.04 desktop edition
I have Firestarter version 1.0.3 installed
I have a fairly strict policy setup:
inbound traffic policy:  default (meaning all inbound traffic is blocked)
outbound traffic policy:  restrictive by default, whitelist traffic (only allowing HTTP/S and Samba(SMB) out)

The reason I believe Firestarter is not enabling my firewall rules on system bootup is because when I issue the following command...

```
sudo iptables -L
```

...I do not see any of my firewall rules listed.  This command is used to list the entire set of firewall rules.  It's as if Firestarter did not implement my firewall policy.

Only when I manually startup Firestarter (System > Administration > Firestarter) is my firewall enabled.  Reissuing the previous command displays my firewall rules.

Is this a bug? What is the resolution to this problem?

Thanks,

*Nick*

---

### Post by musther on 2007-05-04
I still think the issue is that the firestarter DEAMON (I AM NOT TALKING ABOUT THE GUI HERE) is not starting on boot, IT SHOULD BE, it's in the init directories, it just isn't working.  Try issuing

```
sudo /etc/init.d/firestarter status
```

after a clean boot.  If it tells you that it's not started, try

```
sudo /etc/init.d/firestarter start
```

and then try looking at your iptables output.  

This is the command that is supposed to be executed by the init system, but for some reason it isn't working on boot.  I think this must be a bug.

---

### Post by fragos on 2007-05-04
> **musther said:**
> I don't really want a solution, I just want to know what the deamon does as I apparently don't need to have it running?  Very odd, nobody seems to know the answer!

The daemon gives you a way to look at the firewall results as they occur with better presentation and summaries than available by looking at a text log.  Terminate firestarter and the daemon will be terminated.  The firewall however continues to work according to the iptables rules.  You can leave firestarter running in the background and only see the firestarter icon in the applet bar until you click on the icon to return the window.

---

### Post by musther on 2007-05-05
Um, I'm sorry, but that doesn't seem to be true.  If I open firestarter (the GUI) and then close it, the deamon continues to run.  And the deamon is supposed to be running.  I don't know how many times I'm going to have to point out that it's in the rc directories, it should be started by init, and yet it's not starting.

And besides, if the deamon was just for monitoring the firewall, that doesn't explain why unless it's running none of the nick1's rules are being implemented.

I think the firestarter deamon is the important bit, it should be running as it IS the firewall (this is how the firestarter website makes it sound).  Now I've checked that ubuntu has all the ports closed by default (presumably by iptables), that's fine, but there is some bug with firestarter, the deamon NEEDS TO BE RUNNING in order for any firestarter rules to be implemented.

---

### Post by fragos on 2007-05-05
You may be correct on that.  The understandings that one aquires on the web are sometimes flawed.  My observ ations may have only been patialy correct.  I'll have to fiddle with it a bit and become better informed.

---

### Post by fragos on 2007-05-05
> **fragos said:**
> You may be correct on that.  The understandings that one aquires on the web are sometimes flawed.  My observations may have only been partialy correct.  I'll have to fiddle with it a bit and become better informed.

I checked it and proved you were correct.  Firestarter rules are only used if firestarter has been started in that session.  I used System-> Administration-> Sessions and added firestarter to the startup list.  For a command I used "gksudo firestarter" and now the daemon runs.  I still have to start firestarter again when up and running to get the GUI and icon in my applet bar.  Thanks for placing me back on the strait and narrow.

---

### Post by musther on 2007-05-06
Yes, but the deamon is supposed to start on system boot, you shouldn't need to start the GUI at all, you (as the user) shouldn't need to do anything.  Init should start the deamon, it should run as any other deamon does - in the background, no user interaction (unless you want to).

---

### Post by rai4shu2 on 2007-05-06
I don't get it...

```
$ sudo /etc/init.d/firestarter status
Password:
 * Firestarter is running...
```

Works fine here.

EDIT: No, wait. I just rebooted and noticed it was stopped.

Might be something to do with this: [https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/42759)

---

### Post by rai4shu2 on 2007-05-06
I just tried this and it fixed the problem (for now):

sudo nano /etc/firestarter/firestarter.sh

Comment out the part where it says this:

```
if [ "$MASK" = "" -a "$1" != "stop" ]; then
       echo "External network device $IF is not ready. Aborting.."
       exit 2
fi
```

---

### Post by musther on 2007-05-06
Well done! I think it's a network manager issue.  If you're using network manager the firewall won't start because your network interface isn't ready.  I'll file a bug report.

---

### Post by flayspray on 2007-05-13
Hi all,

Having the Firestarter service running from startup is important for me as well because I use my linux box as a router and the internet sharing doesn't work until I start Firestarter after logging in. I would rather that it started automatically so that my flatmates don't have to have me log in before they can use the internet on their Windows machines. I'll try the hack mentioned above but it would be nice if the developers would address this because I seem to remember that it worked alright in Dapper and Edgy...

Thanks for the advice all...

---

### Post by musther on 2007-05-13
I did post a bug report, but it doesn't seem to be getting much attention!

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/112924](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/112924)

---

### Post by fragos on 2007-05-13
Perhaps a bug but easily handled.  In the applet bar, System-> Prefferences-> Sessions-> "Startup Programs tab"-> "New button".  Name: something meaningful like "Firewall".  Command: "sudo firestarter -- start-hidden".  You will be prompted for password when X starts.

---

### Post by musther on 2007-05-13
Firstly the command you have to have it run is not:

```
sudo firestarter -- start-hidden
```

You will need:

```
gksu firestarter -- start-hidden
```

Otherwise you wont get a prompt for your password in X, and anyway, this isn't technically starting the deamon, it's starting the firestarter program, you'd be better with something like:

```
gksu /etc/init.d/firestarter start
#I hope this is the correct file, I'm at work and not on an ubuntu machine right now.

```

And besides, this is a very messy 'fix', I don't want to have to type my password twice (I know there are ways around thins, but nice, not to mention secure, ways), and what about when other users log on, then it wont start.

The fixes discussed on the bug page are much better, and one of them should be implemented and released.

---

### Post by fragos on 2007-05-13
> **musther said:**
> Firstly the command you have to have it run is not:

```
sudo firestarter -- start-hidden
```

You will need:

```
gksu firestarter -- start-hidden
```

Otherwise you wont get a prompt for your password in X, and anyway, this isn't technically starting the deamon, it's starting the firestarter program, you'd be better with something like:

```
gksu /etc/init.d/firestarter start
#I hope this is the correct file, I'm at work and not on an ubuntu machine right now.

```

And besides, this is a very messy 'fix', I don't want to have to type my password twice (I know there are ways around thins, but nice, not to mention secure, ways), and what about when other users log on, then it wont start.

The fixes discussed on the bug page are much better, and one of them should be implemented and released.

"sudo firestarter --start-hidden" does start the daemon and does ask for a password.  "gksu" or "gksudo" may be more proper in this case but the daemon nad not the GUI are started as verified with "sudo /etc/init.d/firestarter status".  I try everything I recommend to insure that it works and despite what you claim, it dose work.  Feel free to offere alternatives but don't call something wrong which you haven't verified.  In my original post I made a typo and added a space after the "--" which of course doesn't work -- my apologies.

---

### Post by musther on 2007-05-13
I'm sorry, I didn't mean to offend you, I just assumed you had made a genuine mistake, and wanted to get in quickly to help anyone who wanted to follow the advice.

But this fix is still quite a crude work-around (and I don't mean that as an insult), the issue shouldn't be there in the first place, it's a simple bug in the package.

The reason I suggested calling /etc/init.d/firestarter start was simply that if /usr/bin/firestarter (or whatever files is called by 'firestarter') is in turn calling the deamon, it is possible that it would terminate when the user logs out, starting the deamon directly would leave it running for other user.  This may well be a non-issue, but it seems 'cleaner' to me to call the deamon directly.

Anyway, the bottom line is I didn't mean to offend, and apologise for it.

---

### Post by fragos on 2007-05-13
Apolgy accepted.  I came to my solution by trial and error which doesn't always yield the most elegant solution.  I thought about placing the command in /etc/rc.local but wasn't sure the Internet connection required would be started at that phase.

---

### Post by musther on 2007-05-13
I think the solutions on the bug page work, have you tried those?

---

### Post by MadMac on 2007-05-17
> **zvacet said:**
> [http://www.grc.com/stevegibson.htm#projects]("http://www.grc.com/stevegibson.htm#projects")

Click on shields up to test if you have any port open.

Sorry to jump into an old thread, but I think I may have a problem.  When I run the shields up test, all but 6 (six) ports are showing as being open (red color).

Could this be because of the NAT firewall in my router?  Firestarter is running, even after a reboot.

Thanks!

---

### Post by musther on 2007-05-17
Yes, that test will be running up against your outermost firewall, which will be the NAT on your router.  If you want to test your machine, you'll have to set up DMZ on your router to direct all traffic to the machine you want to test, then run the test.

It's your routers NAT firewall which has lots of open ports.

Jon

---

### Post by MadMac on 2007-05-18
> **musther said:**
> Yes, that test will be running up against your outermost firewall, which will be the NAT on your router.  If you want to test your machine, you'll have to set up DMZ on your router to direct all traffic to the machine you want to test, then run the test.

It's your routers NAT firewall which has lots of open ports.

Jon

Yeah, but the IP address that shows up in the test is not the IP address that shows up when I check System -> Administration -> Network and click on the DNS tab.

I do have WPA2 and the firewall running on the router, too.

Any ideas on this?  Though I have a sneaking suspicion that it has to do with the IP address that I get from my satellite internet service?

Thanks!

---

### Post by musther on 2007-05-18
Your router has an IP address, assigned by your ISP, via this address your router is visible to to the world, it is the router that the test will test.

Your router also has an internal IP address, visible to your local area network (LAN).

Your computer has an IP address, either chosen by you or assigned by your router's DHCP server, this is only visible on your LAN.

Your computer could be getting its DNS info from your router (the internal LAN address), or it could be getting it from some server on the net.  

I hope that clears things up a little :-), but if it doesn't, let me know.

---

### Post by Wim Sturkenboom on 2007-05-18
Maybe I will create more confusion, but having a script in /etc/init.d does not mean that it's started at boot. Therefor a link is needed from one of the rc.x directories.

Or am I mistaken here?

---

### Post by musther on 2007-05-18
That's right, but I think it's safe to assume that if there's a script in init.d, it's supposed to start on boot (or am I wrong here?), and with firestarter, the links are there in the rc directories, they just don't work on boot because the network system isn't started when firestarter tries to start.  If you change it so that firestarter loads later in the process, apparently it works.

---

### Post by fragos on 2007-05-18
Starting firestarter as part of starting X works every time for me.

---

### Post by MadMac on 2007-05-18
Thanks folks, I think I got it, now.  It's hitting the IP address at the entry/exit for the ISP, not the router or computer.  Router and computer are sittin' pretty - no entry from what I can tell.

I just wonder which entry is for Firestarter under System -> Preferences -> Sessions.  When I use System -> Administration  to start up the desktop gui for Firestarter, I get an entry named "gksu" started, but nothing else is started.

Thanks again for all the help!

---

### Post by musther on 2007-05-18
Assuming you just want your machine to be safe, and don't want to do anything clever with your firewall, don't worry about firestarter, in fact, you can uninstall it.  By default, Ubuntu has all ports closed, and they'll stay that way unless you do something to change it, such as enable remote desktop access.  If you remove firestarter, all you ports will be close and you'll be safe.  Firestarter is useful to do other things with the firewall (specific things) and also to monitor firewall activity.

---

