---
title: "Enabling Strict Encryption in Torrentflux / BitTornado"
date: 2008-03-14
forum: General Help
---

### Post by Yfrwlf on 2008-03-14
[COLOR="Blue"]This guide  may enable strict encryption settings in versions other than the ones specified, since there is no telling when this setting will be added to Torrentflux.  But, this guide was built for the following versions:  Ubuntu 7.10 and installing from the repos Torrentflux version 2.3-2ubuntu1, which includes BitTornado version 0.3.18-4.  (If you have version 0.3.1.8, perhaps try what was mentioned [here]("http://www.torrentflux.com/forum/index.php/topic,2902.msg17490.html#msg17490") by dickswift.)[/COLOR]

Tired of not getting the speed you're paying your ISP to give you?  Don't have enough money to sue them for false advertising?  Then fight fire with fire by using encryption (and don't forget to drop your RST packets too using iptables).  Since it seems that even the latest version of Torrentflux does not have this enabled by default yet nor does it present these options in it's web interface, these are the instructions I have found for turning this on.  The reason for it not being in the web interface yet is most likely due to Torrentflux using BitTornado, which up until recently did not support encryption until it was implemented by The Shadow.

[COLOR="Blue"]**1.**[/COLOR]  You may need to install the python-crypto package from the repos in order for encryption to work, but haven't verified this.  Do this through Synaptic or the command line.```
sudo apt-get install python-crypto
```

[COLOR="Blue"]**2.**[/COLOR]  Install Torrentflux from the repos.  It will give you an error if there are any connection problems to MySQL or whatever database you are wanting to use, so make sure it's able to connect so it can use it.  When you install MySQL you are asked to create a root password, and Torrentflux will ask for this.```
sudo apt-get install torrentflux
```

[COLOR="Blue"]**3.**[/COLOR]  If you are running an upgraded 7.10 you can skip this step because you will have it unless you did a manual install.  You will need BitTornado 0.3.18 or greater for encryption.  If you do an updated install of Torrentflux from the Ubuntu 7.10 (and beyond) repos you should get it.  To check: If on a console-only box, you can check it's version after installing Torrentflux by doing a ```
dpkg -p bittornado
``` or you can look in Synaptic if it has a GUI installed.  Or just pay attention when you install it in the first place, geeez. :P

[COLOR="Blue"]**4.**[/COLOR]  IF you WERE to run the following...```
/usr/bin/btdownloadheadless

--crypto_allowed <arg>
          whether to allow the client to accept encrypted connections (defaults
          to 1)

--crypto_only <arg>
          whether to only create or allow encrypted connections (defaults to 0)

--crypto_stealth <arg>
          whether to prevent all non-encrypted connection attempts; will result
          in an effectively firewalled state on older trackers (defaults to 0)
```...you would notice those arguments for encryption.  Torrentflux needs to be told to use different defaults if you wish to only allow encrypted connections.  Doing so will prevent you from being able to communicate with unencrypted peers and may limit your available peers because of that, but your ISP will not start suspecting you are torrenting anywhere as easily.  After all, this is what you're wanting to prevent to begin with, these unencrypted connections so that your ISP (like Comcast) won't start throttling you.  If the only seeders available for a torrent aren't using encryption though and you set Torrentflux to only communicate with encrypted peers, you won't get any traffic at all.  So, play around with things and experiment, but hopefully, especially with the larger seeder/peer swarms, encryption should speed up your connection.  I don't know how much of an issue this is, but it should become less as/if encryption becomes a more standard practice if ISPs keep being nasty.

So, on the settings page under the admin user, put those options that you want into the "Extra BitTornado Commandline Options" field, for example:```
--crypto_allowed 1 --crypto_only 1
```...and then save the changes.

Here's some more information about the --crypto_only and --crypto_stealth options from The Shadow:> Encrypted connections only. This restricts the client to only connecting via encrpted links, and only via full stream encryption. This may drastically affect the ability of the client to connect to peers with a tracker that doesn't support the crypto extensions.

Full stealth encryption. Like the above mode, except it also modifies tracker communications so that (assuming peers are coded properly) the client will never receive any unencrypted incoming connection attempts. If the tracker doesn't support the crypto extensions, this will also effectively firewall the client.

[COLOR="Blue"]**5.**[/COLOR]  From GLGMarmot:> Modify line 254 of torrentflux2.3/html/index.php [COLOR="Red"](located in /usr/share/torrentflux/www/index.php in Ubuntu)[/COLOR] as below since the escapeshellarg function puts single brackets around any extra commandline options and no torrents work

- $command .= " ".escapeshellarg($cfg["cmd_options"])." > /dev/null &";
+ $command .= " ".$cfg["cmd_options"]." > /dev/null &";

-Go download a torrent and see how it works
-I also adjusted the rerequest interval from 1800 to 300 to try and get more peers. I suspect I wasn't getting many peers because some of them didn't support encryption.So for those who don't know, the "- $command" line needs to be replaced by the "+ $command" line.  So, where it has this```
$command .= " ".escapeshellarg($cfg["cmd_options"])." > /dev/null &";
```replace it with this```
$command .= " ".$cfg["cmd_options"]." > /dev/null &";
```

That should be it!

Also, The Shadow gave the following advice about ports.  I would recommend you try changing your ports and see if it helps.

> I recently had to help a person who was having problems seeding a torrent. After a lot of examination, I suggested he change his port range, and suddenly he was able to upload on remotely-initiated connections. Apparently his ISP was throttling his upstream on BT connections to nearly zero.

This is a serious development that affects the BitTorrent protocol's ability to function, and steps need to be taken to fix it.

I recommend all of you change your BT port range to a block of approx. 20 ports over 10000 but below 60000. Here's an example; min port 32681, max port 32699. Don't use this example, but instead choose your own range; if a lot of people use a particular range, that range may be targeted as well.

Future versions of BitTornado will have an option to choose its port in the available range randomly rather than searching linearly, and this option will be enabled by default. IF YOU CURRENTLY HAVE PORTS FORWARDED, YOU MAY NEED TO CHANGE YOUR PORT RANGE AND/OR FIREWALL SETTINGS TO ACCOMMODATE THIS CHANGE. The default port range on new installations will also be changed to a wide block of high-range ports.

Why this change will help:

BitTornado, and AFAIK most BitTorrent clients, open outbound connections using the standard temporary range (1024-5000), so an outbound BT connection can't be determined just from that port. The peer it connects to may still be using the standard 688x range, which would mean your ISP could isolate and throttle those connections. If your server port is opened on a non-standard port, and a client initiating a connection to you is using a port in its temporary range, then your ISP won't be able to determine whether the connection is for BitTorrent unless it monitors the protocol handshake.

---

### Post by elvis on 2008-03-28
Many thanks for this guide.  I've been meaning to chase this up for a while, and you've greatly simplified the job.

---

### Post by Yfrwlf on 2008-03-29
> **elvis said:**
> Many thanks for this guide.  I've been meaning to chase this up for a while, and you've greatly simplified the job.

Glad you found it useful, though I could have simplified it a lot more by just giving the command to use to encrypt all traffic. ;)

Fortunately now Comcast is under attack and are actually supposedly going to "let up" on capping torrents, or so they say.  Sad that they had to be attacked though in order to put an end to this if one does come.  I think a much more important problem is why isn't there more ISP competition in the U.S. for broadband?  Why are my only choices "Comcast or Crapcast."

Of course this problem effects a lot more than just Comcast customers, so it's still important, but I'm just saying.

---

### Post by samosamo on 2008-05-20
great work.  thanks.

---

