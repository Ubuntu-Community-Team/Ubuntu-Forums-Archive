---
title: "Adding block lists to hosts file."
date: 2021-09-13
forum: General Help
---

### Post by Advait on 2021-09-13
[COLOR=#000000][FONT=Arial]Ubuntu 21.04. Linux newbie here. For a few months I’ve been thinking about setting up a pi-hole to block ads. But a few days ago I read about just adding a block list to the hosts file. I wasn’t aware of this option. It sounds a lot easier than setting up a pi-hole.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I found some ad block lists here [/FONT][/COLOR][[COLOR=#1155cc][FONT=Arial]_[https://winhelp2002.mvps.org/hosts.htm](https://winhelp2002.mvps.org/hosts.htm)_[/FONT][/COLOR]]("https://winhelp2002.mvps.org/hosts.htm")[COLOR=#000000][FONT=Arial] and here [/FONT][/COLOR][[COLOR=#1155cc][FONT=Arial]_[https://github.com/StevenBlack/hosts/blob/master/hosts](https://github.com/StevenBlack/hosts/blob/master/hosts)_[/FONT][/COLOR]]("https://github.com/StevenBlack/hosts/blob/master/hosts")[COLOR=#000000][FONT=Arial]. Other quality lists I should know about?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]When the block list is added to the hosts file, is that about the same as having a pi-hole? What is the advantage of a pi-hole over a block list in the hosts file?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Looks like adding the list to the hosts file is pretty easy. But I’m a newbie, so there may be some important things I don’t know. What do I need to know/do before adding a block list to my hosts file?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Yes, I’ll make a copy of my original hosts file before editing.[/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-09-13
Yes the /etc/hosts file is just text. If you want something like this and have many systems then you may want a PiHole system. You can edit the file with

```

sudo cp /etc/hosts ~/Documents/hosts_$(date +%F-%T)
sudo vi /etc/hosts

```

This makes the backup too (with the first command) then opens the file in vi. If you prefer a different text editor then use that.

---

### Post by TheFu on 2021-09-13
The problem with /etc/hosts is that wildcards cannot be used.  So, instead of blocking
*.facebook.com
we have to list the 500+ subdomains used by facebook.com directly.
A pihole, being the DNS for your internal network CAN use wildcards like *.facebook.com.

Some idiot wrote this: [https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279)
A slightly updated version: [https://blog.jdpfu.com/pages/hosts-for-security](https://blog.jdpfu.com/pages/hosts-for-security)

Pi-hole running inside an LXD container on Ubuntu: [https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454](https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454)
The pi-hole running inside an LXD container is pretty amazing.  I patch it weekly and run a set of update scripts weekly
```
$ more to-upgrade-pi-hole-sw 

# Update pihole software
echo "INFO: Update pihole software"
pihole -up

# Update tracking domain lists
echo "INFO: Update tracking domains "
~/bin/update-trackers

echo "INFO: Update pihole gravity block lists"
# Update gravity block lists
pihole -g
```
The ~/bin/update-trackers script pulls a few different tracker lists, tweaks them for my personal needs, and drops them into /etc/pihole/ as ".list" files.  Nothing too fancy, but my sensibilities are very different from what others use.

---

### Post by HermanAB on 2021-09-14
BTW, I use a hosts file by Dan Pollock on all my machines: 
[https://someonewhocares.org/hosts/zero/hosts](https://someonewhocares.org/hosts/zero/hosts)

It is pretty good and gets rid of about 99.9999% of all cruft on the net, your computer will react about 10,000 times faster and you will have about 1,000,000 times less problems with it... 
;)

---

### Post by Advait on 2021-09-14
> **HermanAB said:**
> BTW, I use a hosts file by Dan Pollock on all my machines: 
[https://someonewhocares.org/hosts/zero/hosts](https://someonewhocares.org/hosts/zero/hosts)

It is pretty good and gets rid of about 99.9999% of all cruft on the net, your computer will react about 10,000 times faster and you will have about 1,000,000 times less problems with it... 
;)

Here's my #<localhost> section

127.0.0.1    localhost
127.0.1.1    advait-Bravo-15-A4DDR
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

Here's Pollock's #<localhost> section

127.0.0.1    localhost
127.0.0.1    localhost.localdomain
255.255.255.255    broadcasthost
::1        localhost
127.0.0.1    local
::1        ip6-localhost ip6-loopback
fe00::0        ip6-localnet
ff00::0        ip6-mcastprefix
ff02::1        ip6-allnodes
ff02::2        ip6-allrouters
ff02::3        ip6-allhosts

Here's my guess at an updated version for me. This look correct?

127.0.0.1    localhost
127.0.1.1    advait-Bravo-15-A4DDR
255.255.255.255    broadcasthost
::1        localhost
127.0.0.1    local
::1        ip6-localhost ip6-loopback
fe00::0        ip6-localnet
ff00::0        ip6-mcastprefix
ff02::1        ip6-allnodes
ff02::2        ip6-allrouters
ff02::3        ip6-allhosts

---

### Post by Advait on 2021-09-14
> **TheFu said:**
> Pi-hole running inside an LXD container on Ubuntu: [https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454](https://ubuntuforums.org/showthread.php?t=2440863&p=13947454#post13947454)
The pi-hole running inside an LXD container is pretty amazing.  I patch it weekly and run a set of update scripts weekly

I went to the DLN pi-hole link with the step by step. The instructions don't look too complicated. I'll research it a bit more and try it.

Besides the wildcard ability, does the pi-hole have any other big advantage over using a modified hosts file?

I don't have any kind of network and I'm not on a network. Just a stand alone pc.

---

### Post by HermanAB on 2021-09-14
"I don't have any kind of network and I'm not on a network. Just a stand alone pc." - Except for a few billion other machines on the internet... ;)

You need not worry about the hosts file too much, just make a backup of the original file - I usually rename it to *hosts.original* - then save Dan's hosts file and name it *hosts* and Bob's your Uncle.

---

### Post by Advait on 2021-09-14
I backed up the original, added the block list and rebooted. Wow. Internet so much better without all the ads. This task should be added to all of those "N things to do after installing Ubuntu" lists.

How often should I check [https://someonewhocares.org/hosts/zero/hosts](https://someonewhocares.org/hosts/zero/hosts) for an updated block list? 1/month? More or less often?

---

### Post by TheFu on 2021-09-14
> **Advait said:**
> I don't have any kind of network and I'm not on a network. Just a stand alone pc.

If you don't have any network, then why do you care about block lists at all?  I take it this is for a different computer than you use to post here?  That must be true, because the computer you use to post here **is** on a network and your must HAVE a network to be using it.

Stand-alone PCs don't have ethernet or wifi or blue tooth.  Those are all forms of NETWORKING and need full firewalls, block lists and a careful user.

>  Besides the wildcard ability, does the pi-hole have any other big advantage over using a modified hosts file?

A pi-hole can provide DNS for all devices on the network - smart phone, media players, tablets, TV tuners, **and** computers.  Modifying the blocks in 1 location is nice.  Also, most smart phones don't allow modifying the /etc/hosts file, so controlling it outside the device, via your own DNS (that's what a pi-hole is), would be the only way to control which DNS lookups are allowed.

But it only works on the same network.  /etc/hosts files are specific to each device.  That means if you have a laptop and take it somewhere else - to a library, cafe, friends house, then your block list is still there, protecting you.  Of course, if you run the pi-hole inside a Linux container that is on the same laptop, then that would come with you.  It is a little more complexity and you'll need to patch the pi-hole OS and software. I do that weekly.  If it breaks, then the internet will seem to be unavailable. That can be confusing to people who don't understand what DNS does.

Neither of these will block links that don't use DNS lookups.  So, any URLs that point directly to an IP address will ignore DNS.  Eventually, the "bad guys" will be able to hide all their traffic in normal IPv6 address space because the number of IPs available is just so great as to make blocking them selectively just too hard.  For example, my ISP gives me a /54 IPv6 address space.  That's massively more IPs for my small business than the entire IPv4 internet has world-wide.

IPv6 drastically changes the internet.


With all that said, if you don't have any other devices - no smartphone, no tablet, no network TV tuners, no media stick players, then **using a /etc/hosts block list is an excellent step.**  

BTW, that lifehacker link above ... I wrote that article ... I'm the idiot.  At the time, I was pushing my tweaked /etc/hosts file to 5 different systems as needed through ansible (that's a DevOPS tool to do system administration on 5 - 5000 computers).

---

### Post by Advait on 2021-09-14
> **TheFu said:**
> If you don't have any network, then why do you care about block lists at all?  I take it this is for a different computer than you use to post here?  That must be true, because the computer you use to post here **is** on a network and your must HAVE a network to be using it.

Stand-alone PCs don't have ethernet or wifi or blue tooth.  Those are all forms of NETWORKING and need full firewalls, block lists and a careful user.

Good point. I should have said I'm on the internet but no ethernet, home or business network. I'm afraid I don't know all the correct terminology. But I'm slowly learning! :-)

---

### Post by TheFu on 2021-09-14
> **Advait said:**
> Good point. I should have said I'm on the internet but no ethernet, home or business network. I'm afraid I don't know all the correct terminology. But I'm slowly learning! :-)

I added a bunch above.

[LIST]
[*]Network - any connection between any two devices.
[*]LAN - a specific subset of a network that is typically "inside" your home.
[*]WAN - This can be connections to the Internet or just between different offices, not using the internet at all.  In a home environment, people would assume WAN = internet
[/LIST]

Two tin cans connected with wax-covered string held tight - that's a "network."

I think you have a network, just not a LAN.

```
PC --> Router --> Internet
```

Yes?
The PC connects to the router using ethernet.  Wifi is ethernet, just without a wire. That is a network.  If you care about this stuff, looking up the OSI Network Model on wikipedia 1 time could be helpful.  Don't worry about memorizing it. Just a quick look is probably useful. I bet there is a table, perhaps a diagram, of the layers in networking.

---

### Post by Advait on 2021-09-14
@thefu Thanks for the links. I've seen the OSI model diagram a few times over the years, but don't remember the details.

Is there a Linux hosts file GUI app? The app would allow the user to specify different hosts files (hosts_1, hosts_2, etc.). The GUI would allow the user to click on which hosts file to use and the app would make the switch by renaming the files. Ever heard of anything like this?

---

### Post by TheFu on 2021-09-14
No. No GUI.  
GUIs lie.  
GIUs provide 20% of what is possible.

You don't want to limit yourself from the power the other 80% of your computer OS can provide, do you?

Learn to use sudoedit along with your editor of choice.

No. I don't look for GUI programs for most things.  GUIs don't work on 95% of my systems.

---

