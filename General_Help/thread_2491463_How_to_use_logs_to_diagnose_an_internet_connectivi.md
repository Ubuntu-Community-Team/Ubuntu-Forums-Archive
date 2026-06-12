---
title: "How to use logs to diagnose an internet connectivity issue?"
date: 2023-10-10
forum: General Help
---

### Post by Advait on 2023-10-10
I'm a tech noob and know nothing about the command line. But I can copy and paste commands like a champ. 

I'm using Ubuntu 22.04, Gnome, Wayland and Firefox and Pihole installed on my AMD laptop. I have no network. I use a wifi hotspot to get all my internet, mostly 5G. I don't have a stand alone router. If I do have a router I don't know where it's operating from. I have a VPN but normally it's turned off. Pihole automatically turns on when I boot up. (I did not install Pihole, I paid someone to do it. I have zero idea how he configured it but it's been working fine for 3 years.) 

Here's the problem that often happens: I'll boot up my laptop and when it gets to the Enter Password screen I'll check to make sure the wifi is connected to the hotspot. Then I'll log in and then Firefox automatically starts and loads all my main sites. Then I'll go to another website and it says something like "Error, Unable to load page." Then I'm unable to do any browsing at all. I then start Chrome and Edge and both of them are unable to load any web page. When I do a reboot the problem is gone.

If I remember correctly, one time I did a ping and the ping was successful, lots of successful approx 60ms ping times. I'll try this ping test again when the problem happens again. 

Is there someway I can diagnose this problem? Can I capture some log files to diagnose?

---

### Post by MAFoElffen on 2023-10-10
For basic diagnostics of network connectivity, I do these in succession. I gear this towards wifi...

Check the wifi icon. Select the System Tray and make sure wifi is connected to a Network.
```

ip a
# I look at the output and make sure the device says it is "up" and has an assigned IP address. Say it was 10.0.0.7
ping -c 10.0.0.1
# use the output of the IP address and use "1" as the IP suffix. That is the usual for a Gateway IP. If fail, reboot your gateway. If yes, go on. 
ping -c 4 8.8.8.8
# ping Google public DNS server via it's IP address. If fail, restart networking. If yes, go on.
ping -c 4 www.google.com
# ping Google using it's name. If fail, DNS is not work (resolvd). If yes, go on
traceroute ubuntu.com
# see the steps to the website that is failing, See if it makes it there...

```
That is a logical flow chart. Before going to logs.

You can restart your networking based on which network renderer you are using, or if ytou just need to restart resolvd, using systemdctl, without having to reboot your computer.

---

### Post by Advait on 2023-10-12
Perfect. Thanks! I'll do these steps next time the problem happens.

---

### Post by Advait on 2023-10-12
> **MAFoElffen said:**
> You can restart your networking based on which network renderer you are using, or if you just need to restart resolvd, using systemdctl, without having to reboot your computer.

* I have no idea what a "network renderer" is or how to restart my network. I'll google to learn more.

* I have no idea what resolvd is or how to restart it. I'll google to learn more.

* I have no idea what systemdctl is or how to use it. I'll google to learn more.

(No one believes me when I say I'm a noob. :lol: ;) )

---

### Post by MAFoElffen on 2023-10-12
That is why we are here...

Ubuntu uses two different network renderers, called NetworkManager & networkd. It only basically uses one at a time. So configuration for networking depends on which one is used. Most Desktop Editions, by default, use Network Manager, and change the settings of it, in the GUI Settings > Network Settings. networkd is the default renderer for Server Edition.

resolvd is the SystemD service that helps with DNS, or Domain Named Services. The command to restart it is
```

sudo systemctl restart resolvd

```
To check it
```

sudo systemctl status resolvd

```
Since you are "New", I assume that you are usig the Desktop Edition, so your renderer would most likely be Network Manager... To restart it
```

sudo systemctl restart NetworkManager
sudo systemctl status NetworkManager

```
With the second command there checking the status of it...

'systemctl' is a utility (as seen in the above commands) that your can use with SystemD to control system daemons., like enabling/disabling, starting/stopping, restarting services...

---

### Post by SeijiSensei on 2023-10-12
Traceroute is a good place to start. It's not included out of the box with Ubuntu, so install it with
```
sudo apt install traceroute
```

Point it at some remote server, like 8.8.8.8 which is Google's DNS server. Run it with the "-n" option so it won't spend time trying to identify the names of each intermediate host.
```

$ traceroute -n 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  192.168.100.1  5.108 ms  4.986 ms  4.783 ms
 2  173.48.81.1  13.988 ms  14.883 ms  15.602 ms
 3  100.41.27.152  16.947 ms  16.359 ms  16.857 ms
 4  140.222.1.43  20.257 ms 140.222.1.81  22.686 ms  23.267 ms
 5  204.148.20.6  21.457 ms  22.081 ms  21.368 ms
 6  * * 108.170.248.65  24.284 ms
 7  142.251.65.115  23.735 ms 8.8.8.8  14.092 ms  13.262 ms

```
Each entry is the IP address of an intermediate router. Entry six shows that 108.170.248.65 is pretty busy, but eventually the packets went through.

If you see entries with just stars or long delays, you'll know that the problem is upstream from you and cannot be solved on your end.

---

### Post by MAFoElffen on 2023-10-12
I mentioned 'traceroute' in Post #2, as my goto as what I do as a step 4... LOL

Good explanation for them on how to use it. I only summarized. By the time I get to traceroute, if I find something, then I contact where is stops and start contacting someone to see what their problem is. LOL

---

### Post by Advait on 2023-10-12
> **SeijiSensei said:**
> Traceroute is a good place to start. It's not included out of the box with Ubuntu, so install it with
```
sudo apt install traceroute
```

Done! Just installed it. Gassho, Sensei.

---

### Post by Advait on 2023-10-12
> **MAFoElffen said:**
> That is why we are here...

Ubuntu uses two different network renderers, called NetworkManager & networkd. It only basically uses one at a time. So configuration for networking depends on which one is used. Most Desktop Editions, by default, use Network Manager, and change the settings of it, in the GUI Settings > Network Settings. networkd is the default renderer for Server Edition.

resolvd is the SystemD service that helps with DNS, or Domain Named Services. The command to restart it is
```

sudo systemctl restart resolvd

```
To check it
```

sudo systemctl status resolvd

```
Since you are "New", I assume that you are usig the Desktop Edition, so your renderer would most likely be Network Manager... To restart it
```

sudo systemctl restart NetworkManager
sudo systemctl status NetworkManager

```
With the second command there checking the status of it...

'systemctl' is a utility (as seen in the above commands) that your can use with SystemD to control system daemons., like enabling/disabling, starting/stopping, restarting services...

Very clear explanation and instructions. Thanks. I'll try these next time the problem happens. Is there an app where I can run these admin commands from a GUI? It's been a long time, but I remember that Windows and Windows Server both have a very extensive GUI that allows you to do almost all admin tasks in the GUI. Is there something like that for Ubuntu?

Yes, I'm using the Desktop Edition.

---

### Post by Advait on 2023-10-12
So can I mark this thread as "Solved"? Or is there anything else I should know or other troubleshooting steps I should know?

You guys provided clear, noob-friendly instructions. Gassho.

---

### Post by MAFoElffen on 2023-10-13
Where to run from?

Go to the Activity Icon in the left of the top bar. When it toggle to the Switcher, start typing in "terminal". Select the Terminal app. Enter the commands into the Terminal Window at the command prompt.

---

### Post by Advait on 2023-10-13
> **MAFoElffen said:**
> Where to run from?

Go to the Activity Icon in the left of the top bar. When it toggle to the Switcher, start typing in "terminal". Select the Terminal app. Enter the commands into the Terminal Window at the command prompt.

Yes, I can run those commands in the terminal. I'm good with starting the terminal and running basic commands. My terminal app auto-starts and is always in my Taskbar. I was just wondering if there's an Admin GUI app for Ubuntu. Looks like there isn't one.

Thanks for your help and, unless there's anything else, I'll mark this thread as Solved.

---

