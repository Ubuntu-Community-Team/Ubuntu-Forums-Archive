---
title: "NextCloud on 22.04.01 LTS and exposing ports"
date: 2023-03-05
forum: General Help
---

### Post by Tigera on 2023-03-05
I'm running Ubuntu 22.04.01 LTS on my machine and I'd like to set up a NextCloud server using my local ZFS encrypted storage exposed to my internal network, and eventually, the Internet.  I've tried setting it up in two ways.

The first thing I did was set up an Ubuntu 22.04.01 LTS virtual machine in QEMU with the NextCloud snap installed.  I was able to get that working and I can access it from the host machine, but not my internal network.  I followed the instructions at [https://www.cyberciti.biz/faq/kvm-forward-ports-to-guests-vm-with-ufw-on-linux/](https://www.cyberciti.biz/faq/kvm-forward-ports-to-guests-vm-with-ufw-on-linux/) to try to get port forwarding working on my NextCloud VM.  However, I'm unable to access it from outside of the host machine.

I searched Google and while I was looking for solutions, I found out about Multipass, which seemed really easy to set up.  So I followed the instructions at [https://multipass.run/docs/how-to-use-multipass-remotely-a-preview#heading--expose-multipass-to-your-network](https://multipass.run/docs/how-to-use-multipass-remotely-a-preview#heading--expose-multipass-to-your-network) to try to give other devices on my LAN access to the NextCloud instance.  Again, I can't access it from outside of the machine running the virtual machine.

The Multipass snap of NextCloud looks like it's running a different version of NextCloud, perhaps older.

So I have two questions: 
First, should I use the Multipass version of NextCloud or the Ubuntu virtual machine?
Second, how do I access that machine or appliance from outside of the host?

TIA

---

### Post by TheFu on 2023-03-05
I've never gotten multipass to work.

I switched to using an LXD/LXC container with the nextcloud snap running inside it a few weeks ago after running nextcloud with a custom install inside a KVM VM for the last 4+ yrs.  Maintaining nextcloud was always hit-or-miss with the 1-click update in the webapp. The last 3 yrs, I was forced to use the CLI method and it would routinely break NC-apps.

Even after all this time, there's no way I'd trust NC on the internet.  Setup a self-hosted VPN on a VM to access your NC instance through when away. Or you can use an ssh-SOCKS5 proxy for a web browser to have access over a secured ssh tunnel. That works well for Linux clients, but the VPN is so much easier for Android clients.

As for accessing the VM from other machines on your LAN, you'll want to setup a bridge to be used by the VM, not NAT.  I setup a bridge completely outside virt-manager or lxd, then just select the bridge name in those tools for the VM or LXC container.  

If you want to treat nextcloud like docker with a single IP for the host that has a port forwarded, I cannot help. The defaults for docker in related to security make me nervous, since they all use root-enabled containers and it is considered a special setup NOT to use root.  With lxd, root-less is the default.

---

### Post by Tigera on 2023-03-05
Thanks for the insight.  I'll admit I'm pretty new to LXC containers in general... those are like Docker containers, and not VM's, aren't they?  Does that have the same isolation as a KVM VM?  

If I understand your suggested setup, a VM would run the VPN server and then I'd forward that outside of my firewall, using a bridged network?  How then would I route traffic through the VPN to the LXC container?  Would that be two bridges then?

Any good tutorials you can point me towards?

---

### Post by DuckHook on 2023-03-07
There's a lot to unpack here:

Nextcloud
Networking
Containers vs VMs
LXD
Tutorials
Security

**Nextcloud:**

I don't like the snap version of NC… I run a custom install because I want to control all aspects of its configuration. If you aren't a control freak, you may find less heartache using some of the easier install methods.

The first time I installed NC, I did so using the snap. That's the easiest way. However I didn't like how overly easy it was. That sounds strange (in a way I'm being absurd) but I'm nervous about solutions that are too automated. I feel like I'm being forced to put my security/privacy/data in the hands of a platform that doesn't grant me insights into its inner workings and this sort of concession to ignorance bugs me.

My next foray was to install NC using the script on their website. This also went smoothly and gave me a working NC with almost no intervention no my part. More insights this way, but I didn't like some of its defaults. The script uses PostgreSQL, which is a poor choice—not because PostgreSQL is a bad DB—but because NC's own documentation defaults to MySQL/MariaDB, so there is limited support and documentation for PostgreSQL.

That's why I ended up spinning my own. I learned something about not only databases, but web servers and PHP and know how to tweak them to my own preference. Again, that's just me. Not a good choice for those who don't want to bother.

**Networking:**

Unlike TheFu, I do have NC set up for direct access from the Internet. This is the setup used by the vast majority of people. Mrs DH isn't about to hitch into a VPN just to get her calendar running so complexity is a non&#8209;starter. What most fail to do—but that I make sure to do—is to enforce security by isolating NC from my LAN. It is isolated on its own subnet with a separate physical NIC that is bound exclusively to the NC container only. This is the opposite of what you are trying to achieve. In my opinion, that detail is the key to basic acceptable security.

**Containers vs VMs:**

My NC instance runs inside a LXD container. I considered a VM, but ended up going with LXD because of several subtle reasons that just tipped the scale in LXD's favour: LXD is less resource intensive, easier to maintain and more versatile (see below), but VMs are more secure. I was sufficiently confident in LXD security that I placed my bet there. Note, however, that LXD defaults to unprivileged state. Docker does not. The choice of container matters. A lot.

**LXD:**

Unfortunately, LXD is not trivial. I wish it were. Documentation is sparse, scattered all over the Internet and involves assembling your own strategy from bits and pieces even when the info is found. It is firmly a geek platform for now, although once set up, it gives great rewards with minimal maintenance. If you are not comfortable with LXD, then a VM may be a better bet. I prefer LXD because once set up properly (which, again, is not simple) it is child's play to make redundant copies, sync to a backup machine, make snapshots and restores, etc.

My experience has been the opposite of TheFu's in another respect in that NC has only choked on an upgrade once. So far, the web based upgrade has performed flawlessly for over a dozen upgrades, both minor and major version releases. It hung on me only during one minor upgrade. But I always make a LXD snapshot before upgrading, so I simply restored the old image and tried again. It worked properly the second time. This illustrates the incomparable advantages of snapshots and restores.

**Tutorials:**

I've authored a LXD tutorial that you can find in my sig.
The Nextcloud tutorial that I used: [https://www.linuxbabe.com/](https://www.linuxbabe.com/)
The finer points of LXD networking: [https://blog.simos.info/](https://blog.simos.info/)
LXD lead developer blog—useful starting point: [https://stgraber.org/](https://stgraber.org/)
Online LXD documentation and home website: [https://linuxcontainers.org/](https://linuxcontainers.org/)

If you decide on a VM, I can't help, but it's a far more common technology so the Internet is full of tutorials.

**Security:**

I would never allow two bridges into my NC container. Never. NC will be exposed to the big bad Internet. No way am I going to bridge that into my LAN. No vlans either. It's a dedicated NIC that goes directly to my router with a subnet carved out just for NC. I also have fail2ban on my NC container to catch brute force password attacks. I have not yet implemented enforced 2FA, but that's because Mrs DH won't use it. Instead, I instruct her to put nothing sensitive on NC that she isn't willing to let the whole world see. That's the compromise we've reached for enforcing less security than I would like while still making it useful.

This means no LAN access. To reach NC from your desktop, you will have to go out into the Internet, then come back in again. Depending on the speed of your connection, this could be a pain, but that's the price we pay for proper security.

If you are *really* careful and *really* knowledgeable, you can define IP table rules in your router to redirect internal LAN packets to your NC subnet. These rules must be ironclad and only one&#8209;way so that nothing is open into your LAN. It goes without saying that this can only be safely done if you really know what you are doing. Most people don't. Not reliably anyway.

There is no such thing as easy security. Don't fall for the illusion of having your cake and eating it too.

---

### Post by TheFu on 2023-03-07
FYI, this is from 1 day ....
```

 Illegal users from:
    3.228.110.238 (ec2-3-228-110-238.compute-1.amazonaws.com): 5 Times
    8.208.100.2: 5 Times
    8.219.209.112: 6 Times
    8.222.131.130: 5 Times
    13.67.221.136: 10 Times
    18.133.75.43 (ec2-18-133-75-43.eu-west-2.compute.amazonaws.com): 5 Times
    34.142.82.98 (98.82.142.34.bc.googleusercontent.com): 10 Times
    35.207.98.222 (222.98.207.35.bc.googleusercontent.com): 8 Times
    43.128.233.179: 15 Times
    43.131.57.46: 15 Times
    43.134.74.183: 5 Times
    43.134.194.250: 5 Times
    43.153.62.34: 15 Times
    43.154.29.163: 5 Times
    43.154.54.104: 15 Times
    43.154.102.160: 15 Times
    43.156.27.23: 15 Times
    43.157.15.14: 8 Times
    43.157.31.78: 14 Times
    45.240.88.142: 5 Times
    46.101.110.253 (daiwer.sa): 14 Times
    46.191.141.152 (46.191.141.152.dynamic.ufanet.ru): 11 Times
    47.88.54.50: 5 Times
    47.91.95.228 (smtp.dynamica.no): 5 Times
    51.79.204.234 (hosting.mdhcom.com): 14 Times
    52.187.9.8: 15 Times
    61.216.131.31 (61-216-131-31.hinet-ip.hinet.net): 15 Times
    62.210.100.10 (62-210-100-10.rev.poneytelecom.eu): 15 Times
    64.225.56.228: 15 Times
    67.205.133.144 (abraj-alyawm.online): 5 Times
    80.253.246.237 (htb.jdsporst.com): 15 Times
    81.89.110.244 (81-89-110-244.blue.kundencontroller.de): 1 Time
    82.64.32.76 (82-64-32-76.subs.proxad.net): 15 Times
    82.141.237.225 (mail.mcmsecurity.com): 5 Times
    84.201.172.108: 15 Times
    85.253.29.212 (85.253.29.212.cable.starman.ee): 15 Times
    91.213.50.9: 15 Times
    96.78.175.41 (96-78-175-41-static.hfc.comcastbusiness.net): 15 Times
    103.14.8.100 (linebb.violin.co.th): 5 Times
    103.37.81.244: 1 Time
    103.38.4.238: 20 Times
    103.60.102.100: 5 Times
    103.250.11.82 (ip82.112.214.103.in-addr.arpa.unknwn.cloudhost.asia): 15 Times
    104.236.2.45: 7 Times
    104.248.242.125: 5 Times
    109.167.197.20 (109-167-197-20.westcall.net): 15 Times
    110.232.86.18: 5 Times
    112.217.207.26: 15 Times
    113.108.110.254: 5 Times
    115.240.206.194 (115.240.206.194.static.jio.com): 19 Times
    119.148.2.82: 5 Times
    124.160.96.249: 1 Time
    128.199.49.102: 15 Times
    129.126.119.71: 7 Times
    137.184.148.244: 14 Times
    138.91.110.181: 15 Times
    139.59.78.156 (vijayanand.me): 15 Times
    140.207.232.13 (ptr.not.exist): 5 Times
    142.93.178.37: 15 Times
    142.93.194.20: 14 Times
    142.93.241.93 (mobilia.com.pe): 9 Times
    143.198.83.146: 5 Times
    147.182.171.152: 15 Times
    147.182.188.81: 15 Times
    149.129.241.221: 5 Times
    152.89.46.156: 10 Times
    158.69.111.17 (s1.globalaliados.com): 15 Times
    158.69.168.3 (ip3.ip-158-69-168.net): 15 Times
    159.65.43.192: 14 Times
    159.203.136.174 (billfoldit.com): 13 Times
    160.251.96.65 (v160-251-96-65.rnfl.static.cnode.io): 5 Times
    162.43.5.169 (x162-43-5-169.static.xvps.ne.jp): 9 Times
    165.22.186.178: 10 Times
    165.227.122.248: 5 Times
    165.227.149.186: 7 Times
    167.71.56.110: 15 Times
    167.235.202.51 (static.51.202.235.167.clients.static.ip.clients.yourdomain.com): 15 Times
    172.22.22.5 (tivo): 3 Times
    174.138.27.246: 15 Times
    176.35.68.136 (176-35-68-136.xdsl.murphx.net): 15 Times
    180.64.115.229: 15 Times
    181.94.223.247 (host-247.181-94-223.personal.net.py): 5 Times
    181.224.253.233 (static253233.flx.com.pe): 5 Times
    185.57.164.159: 15 Times
    185.213.172.143: 5 Times
    186.147.129.110 (static-ip-186147129110.cable.net.co): 25 Times
    187.84.112.136: 19 Times
    188.121.102.135: 19 Times
    188.166.5.84: 14 Times
    188.166.58.96: 5 Times
    188.166.228.226: 5 Times
    190.104.25.214 (LPZ-190-104-25-00214.tigo.bo): 17 Times
    190.129.122.95: 16 Times
    190.242.104.110: 17 Times
    192.9.227.35: 23 Times
    193.70.88.163 (vps-d4dba05d.vps.ovh.net): 15 Times
    194.5.188.45: 5 Times
    194.195.117.57 (194-195-117-57.ip.linodeusercontent.com): 15 Times
    198.23.159.174 (198-23-159-174-host.colocrossing.com): 15 Times
    198.199.93.112: 15 Times
    201.249.204.178: 27 Times
    206.189.57.56: 15 Times
    206.189.114.49: 9 Times
    206.189.139.206: 15 Times
    208.109.12.76 (76.12.109.208.host.secureserver.net): 15 Times
    212.12.31.189 (rev-189-31-12-212.tula.net): 17 Times
    222.99.52.216: 5 Times
```

I just configured fail2ban to block attempts faster and for longer periods of time.  If we don't watch the attempts, we'll never understand the risks we are taking.  Previously, I allowed 5 attempts per hour, so any IP with more than 5 attempts wasn't an accident.  Show the appropriate amount of paranoia.  Please.

---

### Post by TheFu on 2023-03-07
I didn't want to use the NC snap either, but I was tired of upgrade failures.  As long as it wasn't going to be directly on the internet, I was willing to use lxd/lxc containers.
Sure, I use a few odd NC addons that may not be too popular. Those teams are doing the best they can.  I was worried about using the snap myself, so I spent a few days considering it and determining where the data and backups would actually be located.  For the snap, the nextcloud snap team did make creating backups pretty easy.  I did a few installs.  For years, I ran a custom install.

**/snap/bin/nextcloud.export** is the command.
It creates time-stamped directories in /var/snap/nextcloud/common/backups/
I wasn't thrilled with having a new directory created daily, so I force the name to be the same as part of every nightly backup.

```
# ##################[ Nextcloud Backup Data+Apps ]##################
NC_SNAP_BAK_TOP="/var/snap/nextcloud/common/backups"
echo "INFO: Export the nextcloud snap data, db, config.php and user data"
/usr/bin/rm -rf "$NC_SNAP_BAK_TOP/current.bak"
/snap/bin/nextcloud.export > /dev/null
/usr/bin/mv  $NC_SNAP_BAK_TOP/20* "$NC_SNAP_BAK_TOP/current.bak"
```
That just get the NC stuff in a place for rdiff-backup to grab a few seconds later, if that.

In my daily, versioned, backups, the /var/snap/nextcloud/common/backups directory is included.  I think the nextcloud.import command will import it ... hopefully asking which backup set to grab.  [https://help.nextcloud.com/t/snap-nextcloud-export-and-import-solved/85725](https://help.nextcloud.com/t/snap-nextcloud-export-and-import-solved/85725)

Most of my nextcloud data is on read-only NFS mounts, so there isn't much that can be harmed and the backups using rdiff-backup are fairly quick.  It changes daily mainly due to Notes and News. Both are small changes on a daily basis, but convenient in my work flow.

```
INFO: Backup Start:	2023-03-07-00:06:14
INFO:   Backup End:	2023-03-07-00:06:37
```
Under 30 seconds last night, thanks to versioning that rdiff-backup handles automatically.  I get an emailed backup report for all my backups every day.  Most happen beginning a 00:03am and finish by 00:14am.  That's 11 systems.  There are a few others that aren't on my "modern" backup solution yet.  Old OSes don't support the right version of rdiff-backup, so they don't work together.

The nextcloud config and DB and apps are aobut 500MB.
```
$ sudo du -hs /var/snap/nextcloud/common/backups
504M    /var/snap/nextcloud/common/backups

```
The system was setup about a week ago, so I only have 1 week of versioned backups.
```
/backups/nextcloud-lxd$ sudo rdiff-backup --list-increment-sizes .
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Tue Mar  7 00:06:30 2023          786 MB            786 MB   (current mirror)
Mon Mar  6 00:16:05 2023          979 KB            787 MB
Sun Mar  5 00:14:53 2023          128 KB            787 MB
Sat Mar  4 00:10:19 2023          293 KB            787 MB
Fri Mar  3 00:06:25 2023          165 KB            788 MB
Thu Mar  2 09:30:27 2023          580 KB            788 MB
Thu Mar  2 00:06:30 2023          227 KB            788 MB
Wed Mar  1 09:23:16 2023          468 KB            789 MB
```
Seems the versioning is working well from a storage efficiency perspective.  You can see that I tested/updated the backups last Thu a few times.  Adding less than 1MB/day is a big win in my book.  I'll probably have 120 days of versioned backups, since it uses minimal storage.  I did change where and what was backed up, so some stuff that wasn't needed was initially included which will work through the backup versions until it gets removed, eventually.  Still, less than 1GB - I call that a win!
From a raw storage standpoint, 
```
$ sudo du -sh backups/nextcloud-lxd/*
5.2M    backups/nextcloud-lxd/etc
164K    backups/nextcloud-lxd/home
22M     backups/nextcloud-lxd/rdiff-backup-data
128K    backups/nextcloud-lxd/root
60K     backups/nextcloud-lxd/usr
817M    backups/nextcloud-lxd/var
```

While I'd never put any php webapp directly on the internet hosted here, if I was going to do it, I'd get a VPS and use a custom install, not a snap.  Snaps have all sorts problems for servers that there isn't any great answer by default to mitigate short of versioned backups and preventing new snaps from being installed.  People have created scripts to stop snap updates [https://askubuntu.com/questions/1045542/how-to-stop-snapd-from-auto-updating](https://askubuntu.com/questions/1045542/how-to-stop-snapd-from-auto-updating) unless their script is run.  I'll probably implement that and add it do my apt-upgrade system scripts.  I'm not against updates. I'm against updates that happen without my explicit request.


BTW, if it isn't clear, I have a strong belief that if I can't backup AND restore a system, then it shouldn't be used at all.  The same applies to all storage. No backups means no use as primary storage either.

---

### Post by DuckHook on 2023-03-07
> **TheFu said:**
> FYI, this is from 1 day ....

--snip--

I just configured fail2ban to block attempts faster and for longer periods of time.  If we don't watch the attempts, we'll never understand the risks we are taking.  Previously, I allowed 5 attempts per hour, so any IP with more than 5 attempts wasn't an accident.  Show the appropriate amount of paranoia.  Please.
Is this from SSH?

I'm finding nothing in my Nextcloud log. I have SSH not only disabled but deleted from my NC container. I can only access it through the container host using lxc commands. The way I figure it, the fewer services running the better.

---

### Post by TheFu on 2023-03-07
> **DuckHook said:**
> Is this from SSH?

I'm finding nothing in my Nextcloud log. I have SSH not only disabled but deleted from my NC container. I can only access it through the container host using lxc commands. The way I figure it, the fewer services running the better.

Yes, that's from ssh to a public facing VM (my VPN server).  ssh on the internet is on a non-standard port, btw.
My nextcloud systems aren't on the internet. I do see a bunch of odd requests for a few other servers that are on the internet. Far too many to post here.  logwatch is a good tool for seeing which systems "probe your server" ... 
There are efforts to crash php and javascript clearly shown.  Normal people have no idea about the attacks. They are usually for wordpress and a few for myphpadmin, phpldapadmin, and webmin ... along with a few drupal and NC attempts just to see if they can get in.  I do see a bunch of webdav attempts, which NC supports.

Just think people need their eyes open to the attacks.

---

### Post by Tigera on 2023-03-08
I'll admit the backup options are a bit over my head.  I had a VM set up for NC, but from what I'm understanding, I should still get a dedicated NIC?

I'd prefer that this be on my desktop and not some other device.  The idea was that this was supposed to be the One True Device with all my stuff on it, including a blog and my passwords (following LastPass being hacked), and it was on my own hardware.  I even got a domain name so I could set up LetsEncrypt rather than a self-signed cert, but without network access, it doesn't work.

Now, though, it takes 15 minutes to boot, if it boots at all, and there are errors in my OpenZFS pool so it can't use all my drives.  But that's another thread.

If I did go the LXD route... how would that work?  Can I set up LXD to use my ZFS mount directly?  It seemed relatively simple using virt-manager, but I'm all for better capacity management.  I take it Multipass is pretty much useless then?  I should probably remove it...

---

### Post by DuckHook on 2023-03-08
You are asking for simple answers to complex questions. In no particular order:

[LIST=1]
[*]What is your risk tolerance? Mine is low. At least when it comes to computing. I don't like exposing any part of my LAN. I don't like having highly important or sensitive info on NC no matter how secure I think it is. By virtue of the simple reality that it is exposed to the Internet, it cannot be more secure than my LAN. You may decide that the convenience of NC is worth more than the risk. While that approach gives me the Willies, only you can make that determination. Everybody measures risk differently.
[*]What sort of data will be on NC? I allow innocuous photos, music, videos and non&#8209;sensitive documents (like news posts, users manuals and the like, which turn out to be the majority anyway). However, I draw the line at medical info, private correspondences, financial records, sensitive photos, bank statements, etc. Those remain on my internal servers, which are doubled for redundancy, then backed up every night. Very different approaches for very different security/privacy sensitivities.
[*]You have stated that you want NC to be your everything server. I suppose that if you are putting your whole life online, then it doesn't much matter whether someone hacks your LAN, so a double bridge is not much more of a risk. But think about that&#8212;your whole life online. Everything. Those intimate photos and videos, those love letters, those medical records, bank statements, financial records, the nasty email about your boss that you sent to your friends, passwords to everything, your&#8230; whole&#8230; life. Online. Because don't kid yourself. That's what it means to use Nextcloud. You are online. Just one hack away from having all of that posted on the dark web.
[*]You want to protect your password database after the LastPass fiasco. Good. You want to do so by duplicating the same exposures that got LastPass in trouble. Bad.
[*]NC is meant to be always available, always on, always exposed. Everyone I know runs it as a server on a dedicated machine. Mixing it with your desktop is irregular. It can be done, but I see compatibility issues. I shut my desktop down every night if for no other reason than to save electricity. My servers run 24/7 and are designed for redundancy and low power usage.
[*]You imply that you want to run your blog from inside NC. That not only gives me the Willies but the full&#8209;blown shakes. That means general access to strangers (unless you confine it to being a private blog). That in turn means opening up NC to very loose security, maybe amounting to none at all. You need to really rethink this one.
[*]Given what I'm seeing, and forgive me if this comes across as a bit presumptuous (I can't get a clear handle on your Ubuntu/Linux skills from postings so far), I would suggest that you start with a VM. If you want to use LXD, you should really play with it a lot before committing to it. The aim is to not only stress test the platform, but also to stress test yourself and your familiarity with the platform. When something goes wrong, you don't want to have to wrestle with both NC and LXD. That would be an overwhelming combo.
[*]LXD is at home with ZFS. ZFS is its preferred file system. To learn how to leverage an existing ZFS pool for LXD, read through the link in my sig: Sandboxing Apps with LXD. Tips and Tricks
[*]I don't use Multipass so cannot advise you on it one way or the other.
[/LIST]

---

### Post by TheFu on 2023-03-08
> **Tigera said:**
> I'll admit the backup options are a bit over my head.  I had a VM set up for NC, but from what I'm understanding, I should still get a dedicated NIC?
It depends on many factors, which haven't been answered.

> **Tigera said:**
> I'd prefer that this be on my desktop and not some other device.  The idea was that this was supposed to be the One True Device with all my stuff on it, including a blog and my passwords (following LastPass being hacked), and it was on my own hardware.  I even got a domain name so I could set up LetsEncrypt rather than a self-signed cert, but without network access, it doesn't work.
Desktops add all sorts of additional attack vectors that a server doesn't have. Perhaps 10x more.
Happy you got off cloudy password services.  That always seemed foolish to me.  But you should still use a password manager, just with local encrypted, db files that you backup many places.
Having a domain, doesn't make your ISP agreement invalid. Most residential ISPs don't allow running servers from their network.

> **Tigera said:**
> Now, though, it takes 15 minutes to boot, if it boots at all, and there are errors in my OpenZFS pool so it can't use all my drives.  But that's another thread.
15 minutes!  That's not good. I installed ZFS on with my first 20.04 trial long ago.  Performance was terrible, so bad that I only made it about 30 minutes before wiping the OS and loading LVM instead. Just sayin'.   Last month, installed Mint 21 with ZFS into a VM and it has been running fine. Don't know what relationship, if any, exists there. Just a data point for your consideration.

So you know, ZFS is a CoW - Copy on Write - file system and nearly all virtual machines don't like that. ZFS has a way to disable CoW, I believe, but I don't know. I've never used ZFS for block storage provided to VMs. You should do specific research on this aspect.

> **Tigera said:**
> If I did go the LXD route... how would that work?  Can I set up LXD to use my ZFS mount directly?  It seemed relatively simple using virt-manager, but I'm all for better capacity management.  I take it Multipass is pretty much useless then?  I should probably remove it...

LXD really wants a ZFS pool to create lxc containers inside.  The ZFS pool isn't mounted inside the host system.

Only you can decide if Multipass meets your needs.  But, it is usually a bad idea to have multiple hypervisors installed on the same system. Only 1 hypervisor can be in control of the virtualization hardware at a time. Conflicts will cause all sorts of issues. 

I get that you want easy answers. I don't have any, not really, except these strong suggestions.
* Don't expose your nextcloud to the internet. I get the feeling you aren't ready for that level of security.
* Virtual machines are easier to understand than linux containers.  Maybe stick with a single hypervisor for a few years first as your skills grow.
* There's nothing wrong with not wanting to become a Linux guru, but that choice needs to be clearly voiced, or advice will come assuming you plan on being a Linux admin as a profession.

---

### Post by DuckHook on 2023-03-08
> **TheFu said:**
> Desktops add all sorts of additional attack vectors that a server doesn't have. Perhaps 10x more.
&#8593; This &#8593;
I forgot to include this in my list. Super important!
> So you know, ZFS is a CoW - Copy on Write - file system and nearly all virtual machines don't like that. ZFS has a way to disable CoW, I believe, but I don't know. I've never used ZFS for block storage provided to VMs. You should do specific research on this aspect.
Interesting. Didn't know this.

My VMs are all on ZFS. So far, no problems. But I run very low&#8209;stress environments and don't push them, so maybe that's the reason I haven't had problems.
> I get that you want easy answers. I don't have any, not really, except these strong suggestions.
* Don't expose your nextcloud to the internet. I get the feeling you aren't ready for that level of security.
One of the few areas where you and I will continue to disagree. For the vast majority of ordinary users, not having a simple, unfettered, Internet&#8209;facing Nextcloud takes away the whole point in running it. The only remedy for the security exposure is to isolate, harden and use it sanely (no sensitive stuff), all of which has already been covered in our collective advice.

---

### Post by TheFu on 2023-03-08
> **DuckHook said:**
>  The only remedy for the security exposure is to isolate, harden and use it sanely (no sensitive stuff), all of which has already been covered in our collective advice.

Or setup a VPN like wireguard, which isn't very hard at all these days and has wide support on all popular client systems.  Secure access to your HOME LAN from anywhere in the world. 

These guides are all good, but the order would be my preference based on which I've used successfully.
[LIST]
[*][https://www.linuxbabe.com/ubuntu/wireguard-vpn-server-ubuntu](https://www.linuxbabe.com/ubuntu/wireguard-vpn-server-ubuntu)
[*][https://www.howtoforge.com/how-to-set-up-wireguard-vpn-on-ubuntu-22-04/](https://www.howtoforge.com/how-to-set-up-wireguard-vpn-on-ubuntu-22-04/)
[*][https://www.digitalocean.com/community/tutorials/how-to-set-up-wireguard-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-wireguard-on-ubuntu-22-04)
[*][https://www.linuxtoday.com/developer/set-up-wireguard-vpn-server-ubuntu-22-04/](https://www.linuxtoday.com/developer/set-up-wireguard-vpn-server-ubuntu-22-04/)
[*][https://peerchemist.medium.com/how-to-setup-wireguard-vpn-on-ubuntu-server-22-04-c329434aed12](https://peerchemist.medium.com/how-to-setup-wireguard-vpn-on-ubuntu-server-22-04-c329434aed12)
[/LIST]

If you prefer videos:
[LIST]
[*][https://www.youtube.com/watch?v=ZMqUyu53PbA&t=8s](https://www.youtube.com/watch?v=ZMqUyu53PbA&t=8s) Wireguard server setup on Ubuntu
[*][https://www.youtube.com/watch?v=3OkQpgIxhd8](https://www.youtube.com/watch?v=3OkQpgIxhd8)  Wireguard client setup on Ubuntu
[/LIST]

I like how the client setup for Android is accomplished using a QRcode.
BTW, a VPN server really should be on a separate VM and, if possible, have a dedicated NIC using PCI passthru provided by the hypervisor. The hardware is involved too with IOMMU and VT-d support which may need to be enabled in the BIOS and configured on the OS.  But if that isn't possible, then it is still better than using just nextcloud on the internet.  Use a VPN, please.  Make access to hacking your systems have a door with a lock to even get to a point where hacking attempts are possible.  VPNs are one of the things that should be run on a linux container, ever.

---

### Post by Tigera on 2023-03-09
Honestly, you have scared me enough that perhaps going with NC at all isn't a good idea.  

The whole point here was that I have a dozen services to keep track of - Wordpress.com for blogging, Google Drive for all of my files (I'm using an rclone crypt, and yes this includes personal, sensitive information), GMail, Yahoo, the list goes on.  I had hoped that I could consolidate all of that down to one place that lived on my own hardware where I had full control over it.  That was the reason I started out using a VM.  I have 8 cores and 7TB of storage (maybe more if I end up having to replace the hardware, which is looking increasingly likely since it won't boot in any reasonable time even with all the drives unplugged except the NVMe drives).  I could run Kubuntu as a VM also, and then run a separate VM for each server, but that sounds like it won't work either for the same reasons.

I actually haven't moved off of LastPass yet because I have somewhere in the neighborhood of 300 passwords to move and change, and it was a process I only wanted to go through once.  That and I was afraid that if I somehow lost a device, the KeepPassXC or whatever local database could be cracked just as easily, and now we're changing 300 passwords again.  It took me a month to change all that and I'm _still_ not done (you'd be amazed how hard it is to change passwords on some of these Mom-and-Pop websites).  Further that database has to stay in sync on all of my devices, which means every time I change a password, I have to go home, and sync the database again.  

When I saw from The Linux Experiment that there were apps for reading news, storing passwords, files, contacts, and other stuff on there, I had hoped that combined with my fancy hardware and a fiber connection, it would be a one-stop shop where I could be rid of Google, Microsoft, and the like, and that I wouldn't be putting a new NAS on the network, and a VPN server, and a NC server, and so on - it could just be that one machine, which has plenty of capacity for everything I need.

But you are right, and I am wrong.  So no NC for me, and I guess I'll stick with third-party services.  

Thanks for the help.

---

### Post by TheFu on 2023-03-09
> **Tigera said:**
> Honestly, you have scared me enough that perhaps going with NC at all isn't a good idea.  
NC isn't bad, but putting any system on the internet has liabilities, risks. There are mitigation strategies for most risks.
1. Have automatic, daily, versioned, backups that are stored on a different computer that isn't connected to the internet.
2. Limit access to any open inbound services, preferably to only the actual people and their devices who need access.  A VPN can do that as your portable devices move around the world.  If you are always accessing NC from home or work and work has a static subnet, you can setup firewall rules to block 99.999% of the internet, but allow the IPs from your work location. This wouldn't need a VPN.  Allowing 512 IPs access instead of 4B is a huge difference, right?

> **Tigera said:**
> 
The whole point here was that I have a dozen services to keep track of - Wordpress.com for blogging, Google Drive for all of my files (I'm using an rclone crypt, and yes this includes personal, sensitive information), GMail, Yahoo, the list goes on.  I had hoped that I could consolidate all of that down to one place that lived on my own hardware where I had full control over it.  That was the reason I started out using a VM.  I have 8 cores and 7TB of storage (maybe more if I end up having to replace the hardware, which is looking increasingly likely since it won't boot in any reasonable time even with all the drives unplugged except the NVMe drives).  I could run Kubuntu as a VM also, and then run a separate VM for each server, but that sounds like it won't work either for the same reasons.

Running email is more effort than most people would be willing to deal with.  I started running email servers in the mid-1990s for companies and still do that today.  For most people, it is too much hassle.  Every few years, when I have to migrate to a new OS to keep support, I sometimes think it is too much hassle for me as well.  I don't put anything on cloudy services. The idea of having my data on someone else's storage, on someone else's computer, at the end of someone else's network, inside someone else's building freaks me out a bit.  But I've worked as a programmer, admin, network admin, systems architect, storage architect, and enterprise architect for a Fortune 10 company. Also worked at some very small companies where we had to do everything. 

VMs are amazing and if you have sufficient hardware to do it that way, it isn't a bad idea.  Loaded my first OS into a VM around 1999. In 2002, the company where I was consulting mandated that all new deployments had to use VMs, not new hardware, whenever possible.  Around 2005, I started doing VMs at home. By 2008, I was running about 20 VMs on a single Core2 Duo desktop providing email, web, blog and lots of other services for clients.  That was before Linux became bloated, so 512MB of RAM was plenty for most VMs.  Today, even a little DNS server uses almost 1GB of RAM running on Ubuntu in LXC.

For someone seeking a hobby, this can all be overwhelming.  It is like the old question, how do you eat an elephant ... 1 bite at a time. The same goes for setting up all the things you seem to desire at home.  With VMs, you can setup migration points for each of the services you feel are needed.  In my world, the VPN is the most standard setup I have and usually ends up running the latest LTS release.  Some other things, like my enterprise email/communications server are multiple LTS releases behind.  Because this is likely to happen for anyone running stuff at home, I don't allow that email server to be directly connected to the internet.  To get to/from the internet, there's an email gateway system with the main purpose to block hundreds of inbound spam emails daily and to prevent anyone on my subnets from spamming the world.  Running email is much harder today than it was when I first started.  Thank all the spammers for the added complexity.

Running each service in a separate VM is a good idea. In the olden days, we'd load up 50 network services onto a single OS install, then fight with incompatible software stacks for each of those 50 services and when 1 of them was hacked, it would impact all the others.  The solution for that was to have 50 separate physical systems, which isn't realistic for a home.  Thanks to VMs and cheap RAM with fast CPUs and 2TB HDDs, almost anyone can run 20+ VMs inside their basement for $500 in hardware.  Ok, my "servers" aren't in a basement, but you get the idea.  Also, I avoid "server hardware" - don't need the noise or heat or expense.  A couple Ryzen desktop systems easily handle 40+ VMs.

> **Tigera said:**
> 
I actually haven't moved off of LastPass yet because I have somewhere in the neighborhood of 300 passwords to move and change, and it was a process I only wanted to go through once.  That and I was afraid that if I somehow lost a device, the KeepPassXC or whatever local database could be cracked just as easily, and now we're changing 300 passwords again.  It took me a month to change all that and I'm _still_ not done (you'd be amazed how hard it is to change passwords on some of these Mom-and-Pop websites).  Further that database has to stay in sync on all of my devices, which means every time I change a password, I have to go home, and sync the database again.  
I've used KeePass for a really long time.  Moved from v1 of the cross-platform DB to v2 and now to their .kdbx files.  These are encrypted using AES256 which still seems to be secure enough for USGovt use. I'm not worried.  I've blogged about password managers a few times:
[https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)
[https://blog.jdpfu.com/2010/04/24/keepassx-password-manager](https://blog.jdpfu.com/2010/04/24/keepassx-password-manager)
Don't remember when I switched to KeePassXC, but it has been a few years.  

The way I handle password DBs is simple.  I have 2 DBs - work and home.  They are sync'ed nightly from my primary desktop at home using rsync. The DB files are pushed to about 6 different locations, including inside nextcloud.  Inside nextcloud, they are sync'd with my android devices.  The nightly sync happens just after midnight, I know this, so as long as my desktop has the current kdbx file, it will be pushed everywhere needed nightly.  When I'm not traveling, my main desktop at home is my "system of record". I make any kdbx file changes on that system.  Simple.  I barely use a phone and don't have it connected to much - definitely nothing with any connection to money.  I don't trust phone security. I used to work in telecom for a huge world-wide telecom company with networking, internet, phones and cellular business around the world. If you care at all about privacy or security, your cell phone is the last thing you should take with you and don't think it is secure. Not ever.

> **Tigera said:**
> 
When I saw from The Linux Experiment that there were apps for reading news, storing passwords, files, contacts, and other stuff on there, I had hoped that combined with my fancy hardware and a fiber connection, it would be a one-stop shop where I could be rid of Google, Microsoft, and the like, and that I wouldn't be putting a new NAS on the network, and a VPN server, and a NC server, and so on - it could just be that one machine, which has plenty of capacity for everything I need.

Nextcloud has some great applications. Most are 1-click installs.  I have about 20 addons, but use just 3 most of the time - Notes, News and Files.  News isn't a 1-click install.  Files is part of the NC core and provides access to personal storage areas and file synchronization.  Notes are where I have different shopping lists for specific stores and little 'todo' lists.  Nothing too fancy.
Every time I tried to get NC calendar, contacts or email working, they didn't.   I run a standards compliant email, calendar, and contacts server. The standard protocols are all supported. Thunderbird hooks up to all of them, no problem at all.  Others in the company connect using their preferred email clients just fine ... much NC calendar, contacts, and email won't connect.  It should *"just work"*, but doesn't.  I have little desire to re-enter my hundreds of calendar entries (have about 5 separate calendars) or thousands of contacts stored in LDAP DBs. The system I use for email, contacts, and calendaring is pretty amazing.  They were owned by Yahoo previously, which added amazing search capabilities which are freakin' awesome and fast.  I'd drop nextcloud before dropping Zimbra, but I shouldn't have to choose. They should integrate.

Another tool I use is **Wallabag**.  It is a Read-it-Later replacement.  Simple, yet so very useful.  I wish wallabag had a nextcloud app so it would be completely part of nextcloud.

> **Tigera said:**
> 
But you are right, and I am wrong.  So no NC for me, and I guess I'll stick with third-party services.  

I would encourage you to pull as much local as you can. Only email would be something I'd suggest to be left to others.
Many things can be handled just by using ssh.  Learn all that ssh can do.  [https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)  ssh is how Unix computers connect to each other and securely connect and transfer data.  ssh using ssh-keys is secure enough for use over the internet even when inside countries that don't respect privacy rights.

For blogging, it really makes sense to keep that on public services, since the goal is to share it all with the world.  [https://thehackernews.com/2022/05/thousands-of-wordpress-sites-hacked-to.html](https://thehackernews.com/2022/05/thousands-of-wordpress-sites-hacked-to.html) and [https://jetpack.com/blog/what-to-do-if-your-wordpress-site-is-hacked/](https://jetpack.com/blog/what-to-do-if-your-wordpress-site-is-hacked/) On any day, over 1M wordpress blogs are hacked. I run blogging software, but not wordpress.  I should disclose that a niece lives with one of the WP founders.  We have very different ideas about security and I'm 100% positive that his php code is secure.  It isn't about the core wordpress code, it is about all the addons.

---

### Post by DuckHook on 2023-03-09
Once again, I'm in agreement with TheFu as to the following:

The way to look at the problem with cloud "solutions" like those offered by Google, Facebook and others is that you are ***already*** hacked. In fact, you are ***permanently*** hacked, 24/7, on all of your data, without surcease, with no possibility of reprieve, relief or mercy. It's just that they have made their hack so seductive that you have normalized it. The vast majority of people now treat being hacked by social media as part of the background of their lives.

The reason that NC scares you is because we are de&#8209;normalizing this hack. We are dragging it out of its hidey&#8209;hole kicking and screaming and back into the open. By showing you that NC can be hacked, we are forcing you to confront the problem and deal with it honestly rather than swallowing the social media delusion that we aren't being hacked at all.

What would you rather do? Wrestle with the problem and give yourself a decent fighting chance to triumph over it, or go on pretending that the problem doesn't even exist?

I'm not going to sugar coat the NC solution. It *is* a real solution. In fact, it is an *awesome* solution. But it requires some work and some learning. These are not that hard. The learning curve is surmountable. You just need to know where to start.

I'm going to try and simplify the picture for you:

You are being presented with two different approaches to a solution. Both of them work, but in different ways.

[list=1]
[*]TheFu's solution is to run NC within a private network that you must use a VPN to access.

TheFu's solution is a bit safer. But it buys this safety at the cost of inconvenience. If you can only access NC through a VPN, then the large majority of techno&#8209;phobic friends and family will just ignore it. In my opinion, there's no point in running NC if I can't post files on it that my family can retrieve, or that Mrs DH can't access her calendar if she forgets to VPN. Therefore, a VPN is too great an impediment to me. It takes away the reason that I want NC in the first place.

—Versus—
[*]My solution is to run NC as an Internet&#8209;facing service, but with enough safeguards to let you sleep at night.

My solution is not as safe as TheFu's. I freely concede that. However, it is far safer than using a cloud service. This is because we are already way ahead by clawing back control of our own data instead of letting some cloud service slurp it up for their own nefarious uses. By using NC, you transition from a state of already being hacked to one in which someone must make the effort to hack you before your data is at risk. Which state would you prefer?
[/list]
So, the decision tree is not difficult.

[LIST=1]
[*]First, decide whether you want the increased security but decreased convenience of TheFu's solution, or the decreased security but increased convenience of my solution.
[*]If you prefer TheFu's solution, then he has already given you detailed instructions for setting up a VPN.
[*]If you prefer my solution, then I will lay out the details in a post to follow.
[*]
[/LIST]
Either way, you will be better off than using cloudy services.

---

### Post by TheFu on 2023-03-09
100% agree with DuckHook.

There are other solutions to running your own NC too.

---

### Post by DuckHook on 2023-03-09
Keeping in mind that my knowledge of you is limited, here are my recommendations:

[LIST=1]
[*]Buy a new dedicated machine for NC. It doesn't have to be expensive. Some people run NC out of a Raspberry Pi, though I think that is foolish. There are many cheap thin clients that you can modify to work. They only have room for one HDD, but some HDDs are 16 TB these days.
[*]Running NC from your desktop machine is ill advised on so many levels, from security to stability to constraining upgrades to lack of versatility.
[*]Don't even consider containers. Run your Nextcloud in a VM. This will use a technology that you are already familiar with.
[*]Do not double bridge the VM. Have only one bridge to your router. Open the appropriate ports to allow NC to face the Internet. Make sure all other ports are firewalled.
[*]Configure router to open and forward only the required ports. These should only be 80 & 443.
[*]You can install NC any way you like: snap, script or bake&#8209;your&#8209;own. Ignore my earlier post about baking your own. In your case, the snap may be the best solution. It won't be as demanding and I'm sensing that fineness of control is not important to you—you prefer a painless and easy install.
[*]I don't recall if the snap version automatically sets up let's encrypt. If it doesn't, then you will need to install and configure it.
[*]Install fail2ban. Configure it properly and make a habit of watching its logs.
[*]Use only high entropy passwords for your NC account. I use a 48 character password with combined symbols, numbers and letters.
[*]Enforced 2FA is your call. It makes NC safer, but diminishes convenience again.
[/LIST]
That's really all there is to it. Ten steps. Some aren't even real steps but cautions and advisories. The details for each step require more instructions but can all be executed with a good websearch.

Next post: what NC can "safely" be used for…

---

### Post by DuckHook on 2023-03-09
Safety is a subjective judgment call. There is so much variation depending on context, risk tolerance, knowledge and skill that there is no "right" answer.

However, what gurus would almost universally agree on is that your expectations are too high. Many of the uses that you want are so risky that it would be very unwise to implement them. NC is an awesome platform, but it is not a magic unicorn. It won't solve all of your needs. Nor should it. I advise you to rethink your approach to data storage and security/privacy/data sovereignty.

Perhaps it would help if I gave you an idea of what I use mine for and, more importantly, what I ***won't*** use it for:

Uses:
[LIST]
[*]Calendar
[*]Contacts
[*]Tasks
[*]News feeds
[*]Photos & Videos (of a non&#8209;sensitive nature, mostly from auto back&#8209;ups of my mobile devices)
[*]Geomap of photos (since it's my very own, no social media giant can slurp it)
[*]Music (not my complete collection. Just copies of songs that I might want to stream on my mobile devices)
[*]Video chats
[*]E-books, users manuals, various non-sensitive PDFs, travel guides, etc.
[*]Bookmarks
[*]Notes (careful to keep them non&#8209;sensitive)
[*]Private shares with family and friends (secured with password and timed expiry/deletion. This is my only concession to sensitive data. I keep the risk minimal because of the timed deletion. That's as high as my personal risk tolerance goes.)
[/LIST]

Dangers:
[LIST]
[*]Blogging (NC has a blogging plugin. I consider this the height of folly to install. The last thing I want is to open my NC up to public access, which is what a blog is all about.)
[*]Public shares (same as above)
[*]Web server (again, same as above. If you want to run anything public, buy a VPS somewhere and run a strictly isolated server for that and only that service.)
[*]Sensitive files (I don't leave anything on NC that has financial, medical, personal or career implications. The important thing to note is that this restriction is even more important for cloudy services. So NC is no worse than 3rd party clouds and, in fact, far better because of its native privacy.)
[*]Passwords (If you want to put your encrypted passwords on NC, it's your call. Just realize that a password database on *any* public&#8209;facing server risks getting hijacked. If that happens, the bad guys will have all the time in the world to brute force its encryption.)
[*]E-mail (I have all sorts of sensitive stuff on my emails. Can't be helped. Even if I'm careful, others are not and will send me stuff. I don't want yet another copy floating around in a Nextcloud email client.)
[/LIST]

Although I've listed what I consider to be dangers, there's nothing stopping you from adding these modules to NC if you want. As has been repeatedly said: only you know your risk tolerance. If you have more faith in NC than I do, then perhaps you will judge that it's okay to have your bank statements on it. What freaks me out is not the standard you should use to define your own risk tolerance, so long as your judgment is based on real knowledge and not on wishful thinking.

I close with the following observation: even if you take big risks with NC, you are still way better off with it than doing the same things on the giant cloudy services.

---

### Post by MAFoElffen on 2023-03-10
> **TheFu said:**
> So you know, ZFS is a CoW - Copy on Write - file system and nearly all virtual machines don't like that. ZFS has a way to disable CoW, I believe, but I don't know. I've never used ZFS for block storage provided to VMs. You should do specific research on this aspect.

You cannot disable COW in ZFS. Though. you can tune the block size (and disable synch). Tuning the block size is what you do for performance tuning with databases on ZFS. RE: [https://www.oracle.com/technetwork/server-storage/solaris10/config-solaris-zfs-wp-167894.pdf](https://www.oracle.com/technetwork/server-storage/solaris10/config-solaris-zfs-wp-167894.pdf)

15 minutes to boot? I would really install and run bootlog to see what is going on there.

My ZFS-On-Root server comes up in seconds. I have compression tweaked, but no ZFS Native Encryption of pools. Not sure if you installed with encrypted pools.

---

### Post by #&amp;thj^% on 2023-03-10
> **MAFoElffen said:**
> You cannot disable COW in ZFS. Though. you can tune the block size (and disable synch). Tuning the block size is what you do for performance tuning with databases on ZFS. RE: [https://www.oracle.com/technetwork/server-storage/solaris10/config-solaris-zfs-wp-167894.pdf](https://www.oracle.com/technetwork/server-storage/solaris10/config-solaris-zfs-wp-167894.pdf)

15 minutes to boot? I would really install and run bootlog to see what is going on there.

My ZFS-On-Root server comes up in seconds. I have compression tweaked, but no ZFS Native Encryption of pools. Not sure if you installed with encrypted pools.

+1
Same here boots in seconds, (zfs-root)

---

### Post by TheFu on 2023-03-10
> **1fallen said:**
> +1
Same here boots in seconds, (zfs-root)

I have a Mint 21.1 system with ZFS.  Boots in seconds, I think. Let me check.
```
$ systemd-analyze 
Startup finished in 5.893s (kernel) + 3.998s (userspace) = 9.892s 
graphical.target reached after 3.993s in userspace

$ dft
Filesystem                                       Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_d0wbmk                         zfs    26G  6.6G   19G  27% /
rpool/USERDATA/root_5njgy6                       zfs    19G  384K   19G   1% /root
rpool/USERDATA/jp_5njgy6                         zfs    28G  8.9G   19G  33% /home/jp
rpool/ROOT/ubuntu_d0wbmk/usr/local               zfs    19G  256K   19G   1% /usr/local
rpool/ROOT/ubuntu_d0wbmk/srv                     zfs    19G  128K   19G   1% /srv
rpool/ROOT/ubuntu_d0wbmk/var/games               zfs    19G  128K   19G   1% /var/games
rpool/ROOT/ubuntu_d0wbmk/var/log                 zfs    19G  143M   19G   1% /var/log
rpool/ROOT/ubuntu_d0wbmk/var/lib                 zfs    19G   26M   19G   1% /var/lib
rpool/ROOT/ubuntu_d0wbmk/var/www                 zfs    19G  128K   19G   1% /var/www
rpool/ROOT/ubuntu_d0wbmk/var/mail                zfs    19G  128K   19G   1% /var/mail
rpool/ROOT/ubuntu_d0wbmk/var/spool               zfs    19G  4.4M   19G   1% /var/spool
rpool/ROOT/ubuntu_d0wbmk/var/snap                zfs    19G  128K   19G   1% /var/snap
rpool/ROOT/ubuntu_d0wbmk/var/lib/NetworkManager  zfs    19G  256K   19G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_d0wbmk/var/lib/AccountsService zfs    19G  128K   19G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_d0wbmk/var/lib/apt             zfs    19G   87M   19G   1% /var/lib/apt
rpool/ROOT/ubuntu_d0wbmk/var/lib/dpkg            zfs    19G   65M   19G   1% /var/lib/dpkg
bpool/BOOT/ubuntu_d0wbmk                         zfs   1.8G  265M  1.5G  15% /boot
/dev/vda2                                        vfat  512M   17M  496M   4% /boot/efi

deneb:~$ lsb_release -d
Description:    Linux Mint 21.1

```
That's with a default ZFS install. 21.1 is based on Ubuntu 22.04, just with the snaps removed. Since I run a different Window Manager, fvwm, anyway, the GUI doesn't matter to me.  So far, I haven't needed to know a thing about ZFS.

---

### Post by #&amp;thj^% on 2023-03-10
> **TheFu said:**
> I have a Mint 21.1 system with ZFS.  Boots in seconds, I think. Let me check.
```
$ systemd-analyze 
Startup finished in 5.893s (kernel) + 3.998s (userspace) = 9.892s 
graphical.target reached after 3.993s in userspace

$ dft
Filesystem                                       Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_d0wbmk                         zfs    26G  6.6G   19G  27% /
rpool/USERDATA/root_5njgy6                       zfs    19G  384K   19G   1% /root
rpool/USERDATA/jp_5njgy6                         zfs    28G  8.9G   19G  33% /home/jp
rpool/ROOT/ubuntu_d0wbmk/usr/local               zfs    19G  256K   19G   1% /usr/local
rpool/ROOT/ubuntu_d0wbmk/srv                     zfs    19G  128K   19G   1% /srv
rpool/ROOT/ubuntu_d0wbmk/var/games               zfs    19G  128K   19G   1% /var/games
rpool/ROOT/ubuntu_d0wbmk/var/log                 zfs    19G  143M   19G   1% /var/log
rpool/ROOT/ubuntu_d0wbmk/var/lib                 zfs    19G   26M   19G   1% /var/lib
rpool/ROOT/ubuntu_d0wbmk/var/www                 zfs    19G  128K   19G   1% /var/www
rpool/ROOT/ubuntu_d0wbmk/var/mail                zfs    19G  128K   19G   1% /var/mail
rpool/ROOT/ubuntu_d0wbmk/var/spool               zfs    19G  4.4M   19G   1% /var/spool
rpool/ROOT/ubuntu_d0wbmk/var/snap                zfs    19G  128K   19G   1% /var/snap
rpool/ROOT/ubuntu_d0wbmk/var/lib/NetworkManager  zfs    19G  256K   19G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_d0wbmk/var/lib/AccountsService zfs    19G  128K   19G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_d0wbmk/var/lib/apt             zfs    19G   87M   19G   1% /var/lib/apt
rpool/ROOT/ubuntu_d0wbmk/var/lib/dpkg            zfs    19G   65M   19G   1% /var/lib/dpkg
bpool/BOOT/ubuntu_d0wbmk                         zfs   1.8G  265M  1.5G  15% /boot
/dev/vda2                                        vfat  512M   17M  496M   4% /boot/efi

deneb:~$ lsb_release -d
Description:    Linux Mint 21.1

```
That's with a default ZFS install. 21.1 is based on Ubuntu 22.04, just with the snaps removed. Since I run a different Window Manager, fvwm, anyway, the GUI doesn't matter to me.  So far, I haven't needed to know a thing about ZFS.

Nice, I just knew we would convert you sooner or later.:lolflag:
BTW My pools are encrypted, trust me that's not bait to tempt you.....things are still in need of fixing and polishing 
```
systemd-analyze
Startup finished in 9.853s (firmware) + 12.072s (loader) + 23.533s (kernel) + 9.691s (userspace) = 55.151s 
graphical.target reached after 9.674s in userspace

```
And you could of guessed with me>>>>Zero Snaps
```
df -T
Filesystem                                       Type   Size  Used Avail Use% Mounted on
tmpfs                                            tmpfs  782M  2.3M  780M   1% /run
/dev/mapper/keystore-rpool                       ext4   437M   28K  404M   1% /run/keystore/rpool
rpool/ROOT/ubuntu_ebm2kz                         zfs    221G  6.6G  215G   3% /
tmpfs                                            tmpfs  3.9G     0  3.9G   0% /dev/shm
tmpfs                                            tmpfs  5.0M  4.0K  5.0M   1% /run/lock
rpool/USERDATA/oem_4fwxjg                        zfs    215G  256K  215G   1% /home/oem
rpool/ROOT/ubuntu_ebm2kz/usr/local               zfs    215G  512K  215G   1% /usr/local
rpool/USERDATA/root_4fwxjg                       zfs    215G  1.7M  215G   1% /root
rpool/ROOT/ubuntu_ebm2kz/var/games               zfs    215G  256K  215G   1% /var/games
rpool/ROOT/ubuntu_ebm2kz/srv                     zfs    215G  256K  215G   1% /srv
rpool/ROOT/ubuntu_ebm2kz/var/lib                 zfs    218G  3.2G  215G   2% /var/lib
rpool/ROOT/ubuntu_ebm2kz/var/mail                zfs    215G  256K  215G   1% /var/mail
rpool/ROOT/ubuntu_ebm2kz/var/log                 zfs    215G   14M  215G   1% /var/log
rpool/ROOT/ubuntu_ebm2kz/var/www                 zfs    215G  256K  215G   1% /var/www
rpool/ROOT/ubuntu_ebm2kz/var/spool               zfs    215G  256K  215G   1% /var/spool
rpool/ROOT/ubuntu_ebm2kz/var/snap                zfs    215G  256K  215G   1% /var/snap
rpool/ROOT/ubuntu_ebm2kz/var/lib/AccountsService zfs    215G  256K  215G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_ebm2kz/var/lib/NetworkManager  zfs    215G  384K  215G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_ebm2kz/var/lib/dpkg            zfs    215G   81M  215G   1% /var/lib/dpkg
rpool/ROOT/ubuntu_ebm2kz/var/lib/apt             zfs    215G  113M  215G   1% /var/lib/apt
bpool/BOOT/ubuntu_ebm2kz                         zfs    1.8G  376M  1.4G  21% /boot
/dev/nvme0n1p1                                   vfat   511M   13M  499M   3% /boot/efi
tmpfs                                            tmpfs  782M  168K  782M   1% /run/user/1000
/dev/sdb2                                        ext4   456G   37G  397G   9% /media/me/10353d0f-305c-4b90-91d9-97c3367fa974
/dev/nvme0n1p2                                   btrfs  238G   50G  187G  21% /media/me/KaisenLinux


```

---

### Post by TheFu on 2023-03-10
> **1fallen said:**
> Nice, I just knew we would convert you sooner or later.:lolflag:
BTW My pools are encrypted, trust me that's not bait to tempt you.....things are still in need of fixing and polishing 
```
systemd-analyze
Startup finished in 9.853s (firmware) + 12.072s (loader) + 23.533s (kernel) + 9.691s (userspace) = 55.151s 
graphical.target reached after 9.674s in userspace

```
And you could of guessed with me>>>>Zero Snaps 

I'd been planning to restart using ZFS again for the last 5 yrs, but it was never a good time. I used ZFS on Solaris a long time ago and tried with 20.04 but that was a terrible experience. It only lasted about 30 minutes on the system before I wiped it and ran back to LVM.

Mint is a new desktop VM for me. It isn't too-important, mainly used as a remote desktop and a place to run a few high-risk programs under firejail, where I have control over the constraints, unlike with snap packages.

---

### Post by #&amp;thj^% on 2023-03-10
> **TheFu said:**
> I'd been planning to restart using ZFS again for the last 5 yrs, but it was never a good time. I used ZFS on Solaris a long time ago and tried with 20.04 but that was a terrible experience. It only lasted about 30 minutes on the system before I wiped it and ran back to LVM.

Mint is a new desktop VM for me. It isn't too-important, mainly used as a remote desktop and a place to run a few high-risk programs under firejail, where I have control over the constraints, unlike with snap packages.
EDIT: @ Tigera I so did not mean to hijack your thread, i honestly thought this was in Chat area and not a support thread. Apology.
I kind of guessed you had experience with zfs, in your reply's to others over the past couple of years.
I also keep one running all "devel sources" to keep ahead of any future breakage, but that little machine just keeps ticking away like a fine watch.

---

### Post by Tigera on 2023-03-10
OK, there's a lot to respond here, but I'll try...

First off, thank you for trying to steer me in the right direction.  I know it's hard to try to explain all of this at once.  I'm trying to keep my questions simple and short so that I don't overcomplicate things too much.  That doesn't necessarily mean I feel like I need an easy solution.  Like you said, I just need to know where to start.  We can't go from 0 to perfect iptables rules running for LXD in one step.  Further, I'm a developer myself, so I'm able to understand a lot of what you're saying, but I just don't have experience with some of these things, particularly the backup conversation that happened earlier.  I've never backed up my Linux desktop before.  That was one thing I had hoped to learn to do.

Second, regarding the 15 minute boot time - that's 15 minutes to post, not 15 minutes for Linux to boot.  In other words, the thing doesn't even get to the bootloader in 15 minutes.  In fact, if I press the Delete key when it prompts you to push Delete to go into the BIOS, it doesn't recognize it - I have to keep pressing the key potentially for 15 minutes to get to the BIOS menu.  It's a hardware problem of some kind that I'm trying to nail down, and it is possible that I may need to replace multiple pieces of hardware.  Once it gets through the bootloader and I see the Kubuntu logo, we're ok.  The boot for Linux to the Kubuntu desktop is somewhat delayed, but that may be a configuration issue and I doubt it has anything to do with OpenZFS.  The OpenZFS cluster is encrypted, by the way; I just learned how to do that.  The hope was that the encrypted ZFS cluster would host my NC files.  Unfortunately, smartctl -a isn't working for one of the spinning drives, and ZFS is consistently reporting one drive or the other as unreadable, so both drives may need to be thrown away.

In terms of risk tolerance - yes, my risk tolerance is low.  I resisted for the longest time putting my files on Google Drive, and even then I'm using an rclone crypt.  The trouble is that my sensitive files are on my 10 year-old Mac (problem number 1), not backed up regularly (problem number 2), not accessible from anywhere but my Mac, and I live in an area subject to extreme weather events, so I decided an offsite backup was needed, or at least a redundant backup.  That's what led me to NC.  In order to look at my tax information, for example, I have to get up and go to my laptop, and when I'm out of town I have to bring my laptop with me to have access to those files, which means they risk being stolen with nothing but a password between me and a thief posting everything on the dark web (problem number 3).  

The original intention was to run NC in one virtual machine, whatever blogging software on another virtual machine, a web server on a third virtual machine, and so on.  I didn't even know NC had blogging capability until you mentioned it.  You are totally right that the ISP subscriber agreement may disallow me from running a server on my own connection.  I hadn't thought of that.  You are also right that it would be safest to run a web server or blogging software on a public-facing cloud machine.  That just means that I have to deal with pretty much the same situation I do now, with multiple services doing multiple things.

The desktop didn't have to function as the hypervisor - I could run my desktop on a separate VM.  It seemed like hacking the Kubuntu instance, then hacking hypervisor, then hacking another VM running on the hypervisor was a relatively low-probability attack, but as I recently heard from a friend in cybersecurity, that happens pretty frequently, so you're right there, too.    

It just seemed like a waste of capacity to have all this hardware just sitting around.  I thought maybe it would be fun to learn how to run these services myself, and in the process, it would run on my own hardware rather than me going through Linode or whatever and paying for someone else's hardware.  It would solve problems like how I handle backups, how I get access to my data out of town, how I handle passwords, how I share files with family, and so on.  What started this whole conversation was me trying to set up LetsEncrypt on NC, which apparently requires that I allow it access to the Internet.  I eventually went with a self-signed cert which just seemed wrong.  

Now, you are totally right, what I could do is OpenVPN to my home network, and then have access to an SMB share or whatever.  I like some of NC's other features and addons, and it allows me to get away from Google having all of my contacts, calendar information, and so on.  But that may be, as you say, a case of "having my cake and eating it too."  You are also right that it would be safest to run on separate hardware, but this is a potential pain point.  If I did run NC on separate hardware from the VPN, it would still need access to the internet at some point if I wanted to use LetsEncrypt rather than a self-signed cert, on top of needing to VPN into my LAN.  I would get annoyed very quickly at having to constantly tell Firefox, "Yes, I accept the risk" when I visited my own NC instance.  Then again, running a VPN on a Raspberry Pi is preferable to buying a whole new system to host NC.

So a couple of questions.  If I did run on a VPN to my LAN, would NC be an appropriate place to store passwords?  I'm guessing your answer to that will be "no," though I still thought I'd ask.  And if I did run a VPN to my LAN, how do we get around self-signed certificates on the NC instance?

---

### Post by Tigera on 2023-03-10
> **1fallen said:**
> EDIT: @ Tigera I so did not mean to hijack your thread, i honestly thought this was in Chat area and not a support thread. Apology.
I kind of guessed you had experience with zfs, in your reply's to others over the past couple of years.
I also keep one running all "devel sources" to keep ahead of any future breakage, but that little machine just keeps ticking away like a fine watch.

You didn't.  We're far afield of the original question now.  This thread should probably be moved.

---

### Post by TheFu on 2023-03-10
> **Tigera said:**
> OK, there's a lot to respond here, but I'll try...

Ok, so I'll try to stay away from the FUD - fear is mainly the tool and stick with reasonable, useful ideas, assuming you will not place NC directly on the internet ... for now.

> **Tigera said:**
> 
First off, thank you for trying to steer me in the right direction.  I know it's hard to try to explain all of this at once.  I'm trying to keep my questions simple and short so that I don't overcomplicate things too much.  That doesn't necessarily mean I feel like I need an easy solution.  Like you said, I just need to know where to start.  We can't go from 0 to perfect iptables rules running for LXD in one step.  Further, I'm a developer myself, so I'm able to understand a lot of what you're saying, but I just don't have experience with some of these things, particularly the backup conversation that happened earlier.  I've never backed up my Linux desktop before.  That was one thing I had hoped to learn to do.

There's a bunch of experience in these replies from everyone here. Everyone is providing "reasonable answers", based on our experiences and history. I don't think anyone is steering you wrong.
I was a professional cross platform C/C++ dev for a decade and before that I worked in realtime control systems using about 20 languages few people in the world have ever hear about, much less used.  Devs are smart and can figure almost anything out, but we are warped in the same way that auto mechanics have 3 cars that barely work in their yards. It is exactly the same issue.  It wasn't until I became a professional systems admin that I started doing things "the right way". For example, I learned why having 3 full copies of everything on 3 different systems created manually wasn't really a backup.  Backups need to be automatic, versioned, and placed on at least 2 other systems, beyond the master copy that sits on the "primary" source of the data.  Anything less is a failure for many reasons.

Backups are critical. I don't consider a system worthy of production data until backups are working and the restore has been tested on a system.  As a software developer, that always seemed like crazy talk, but when you have 10 - 1000 systems for which you are responsible, the focus changes completely. Other people are depending on the stuff those systems do, so when something bad happens, and it will, the time to recover and the age of the data that can be restored matters.  These are called RTO and RPO in the business.

> **Tigera said:**
> Second, regarding the 15 minute boot time - that's 15 minutes to post, not 15 minutes for Linux to boot.  In other words, the thing doesn't even get to the bootloader in 15 minutes.  In fact, if I press the Delete key when it prompts you to push Delete to go into the BIOS, it doesn't recognize it - I have to keep pressing the key potentially for 15 minutes to get to the BIOS menu.  It's a hardware problem of some kind that I'm trying to nail down, and it is possible that I may need to replace multiple pieces of hardware.  Once it gets through the bootloader and I see the Kubuntu logo, we're ok.  The boot for Linux to the Kubuntu desktop is somewhat delayed, but that may be a configuration issue and I doubt it has anything to do with OpenZFS.  The OpenZFS cluster is encrypted, by the way; I just learned how to do that.  The hope was that the encrypted ZFS cluster would host my NC files.  Unfortunately, smartctl -a isn't working for one of the spinning drives, and ZFS is consistently reporting one drive or the other as unreadable, so both drives may need to be thrown away.

Hardware issues don't get better.
If you are using encryption, you **must** have excellent backups.
If you are using clustering, you **must** have excellent backups.
If you are using RAID, you **must** have excellent backups.
Any one of those 3 things requires excellent backups.  Why?  Because with each, a tiny issue can result in a problem that cannot be solved, except by a complete wipe of the storage followed by re-creation of the array, and restoration of the data/files from backups. If your system has any hardware issues at all, it is just a matter of time before data becomes so corrupted as to be completely inaccessible.  I've seen this a few times.  It happened to me about 20 yrs ago, before I got backup religion.  Lost about 80% of my data.  Sadly, it took a few more years before I truly got it. "It" being backup religion.  Today any disk failure is a minor inconvenience, but they still happen.  It has been a few years, since I started buying better quality disks and have automated methods to monitor disk issues.

> **Tigera said:**
> 
In terms of risk tolerance - yes, my risk tolerance is low.  I resisted for the longest time putting my files on Google Drive, and even then I'm using an rclone crypt.  The trouble is that my sensitive files are on my 10 year-old Mac (problem number 1), not backed up regularly (problem number 2), not accessible from anywhere but my Mac, and I live in an area subject to extreme weather events, so I decided an offsite backup was needed, or at least a redundant backup.  That's what led me to NC.  In order to look at my tax information, for example, I have to get up and go to my laptop, and when I'm out of town I have to bring my laptop with me to have access to those files, which means they risk being stolen with nothing but a password between me and a thief posting everything on the dark web (problem number 3).  
Linux and MacOS are both Unix-based systems.  Why not use ssh/scp/sftp/sshfs to access files between the 2 systems. These should be 2nd nature to you.
All laptops need to be fully encrypted - all portable storage does. No exceptions.
No way would I put tax information into NC.  I have to say that were NC sucks is search.  You'd be better served by setting up a directory structure based on YYYY/MM/ for your documents and using a google-like local search tool to find things.  I use **recoll** and update the index daily for about 40TB of stuff. Recoll searches are google-fast and it can deal with metadata for most file types - html, email, pdfs, office documents, text, media files, epub, etc. For example, 
```
$ time recoll -b -t -q "Schember"  |egrep ebooks
:3:common/rclinit.cpp:353::Recoll 1.26.3 + Xapian 1.4.14 [/d/D2/recoll-index/recoll]
file:///d/D1/ebooks/Library/John Schember/Calibre Quick Start Guide (1)/metadata.opf
file:///d/D1/ebooks/Library/John Schember/Calibre Quick Start Guide (1)/Calibre Quick Start Guide - John Schember.epub
file:///d/D1/ebooks/Library/John Schember
file:///d/D1/ebooks/Library/John Schember/Calibre Quick Start Guide (1)/Calibre Quick Start Guide - John Schember.epub

real    0m0.117s
user    0m0.001s
sys     0m0.014s
```
So 0.1 seconds to find an epub book on a system with ...
```
$ inxi -d
Drives:    Local Storage: total: 37.13 TiB used: **22.56 TiB** (60.7%) 
```
Recoll has a GUI, if you prefer that.  I did a few other searches ... like for Heinlein, but the results were too long to post here.  The point is that recoll is an amazing search/indexing tool for finding things on your local storage.
In my experience with Nextcloud, it is unlikely to find what I seek and it never provides it in a way that is very useful. Sad, but try.


> **Tigera said:**
> 
The original intention was to run NC in one virtual machine, whatever blogging software on another virtual machine, a web server on a third virtual machine, and so on.  I didn't even know NC had blogging capability until you mentioned it.  You are totally right that the ISP subscriber agreement may disallow me from running a server on my own connection.  I hadn't thought of that.  You are also right that it would be safest to run a web server or blogging software on a public-facing cloud machine.  That just means that I have to deal with pretty much the same situation I do now, with multiple services doing multiple things.

As for blogging, I'd suggest running a static web site. That can be hosted almost anywhere - github - for example.  With a static website, you can use CSS to make it feel dynamic, but still mount it read-only, drastically reducing the security issues. There are plenty of static website generators, or you should create your own. I did with perl a few decades ago.  I've converted a wordpress site from a non-profit I help out into a 100% static website that looks the same (mostly) and has all the same links.  It was meant to be used as a failover for when WP was hacked.

Running different things on different VMs is how we all got started and learned.
As for running different webapps on a VPS, this is where learning linux containers can really help.  Websites really don't take much storage and most don't need much CPU or bandwidth.  If you have static websites and can't get them working on free places like github, you can prepay $10 for nearlyfreespeech.net. Most static websites there are $0.50/month or less.  They run BSD and don't handhold anyone, but they do autoscale. Basically, we pay just for bandwidth, so if you have a 20 page blog or a 200 page blog, the cost for that to be available all the time will probably be less than $10/yr, assuming you don't put huge files there.

> **Tigera said:**
> 
The desktop didn't have to function as the hypervisor - I could run my desktop on a separate VM.  It seemed like hacking the Kubuntu instance, then hacking hypervisor, then hacking another VM running on the hypervisor was a relatively low-probability attack, but as I recently heard from a friend in cybersecurity, that happens pretty frequently, so you're right there, too.    

I worked on the edge of IT security for decades and have attended many security conferences. It is scary what's possible, but the IT security guys aren't out to cause harm, generally.  I don't trust any cellular phone, however.


> **Tigera said:**
> 
It just seemed like a waste of capacity to have all this hardware just sitting around.  I thought maybe it would be fun to learn how to run these services myself, and in the process, it would run on my own hardware rather than me going through Linode or whatever and paying for someone else's hardware.  It would solve problems like how I handle backups, how I get access to my data out of town, how I handle passwords, how I share files with family, and so on.  What started this whole conversation was me trying to set up LetsEncrypt on NC, which apparently requires that I allow it access to the Internet.  I eventually went with a self-signed cert which just seemed wrong.  

You still need to know how to run these services, even if you get a VPS somewhere else.  Using a local VM to get a handle on that is a good thing.
As for accessing your data from anywhere in the world, there are many, many, many, ways.  Start with mastering ssh, scp, sftp, sshfs, rsync and tools based on them.  For example, with ssh, you can create a web proxy connection from your laptop into your home LAN that provides access to any internal webapps through the encrypted, authenticated ssh connection.
As for Let's Encrypt certs, the system requesting them needs to be on the internet during the time of the request, but not all the time.  Every 2.5 months, I put all my webapps on the internet for about 90 seconds as new LE certs are requested, then they are taken off the internet for the rest of the  time. There are other ways to get LE certs without putting systems on the internet. You just need to show control over the domain in a way that is approved by the let's encrypt process.  Inserting a TXT DNS record is one method to prove ownership.  

> **Tigera said:**
> 
Now, you are totally right, what I could do is OpenVPN to my home network, and then have access to an SMB share or whatever.  I like some of NC's other features and addons, and it allows me to get away from Google having all of my contacts, calendar information, and so on.  But that may be, as you say, a case of "having my cake and eating it too."  You are also right that it would be safest to run on separate hardware, but this is a potential pain point.  If I did run NC on separate hardware from the VPN, it would still need access to the internet at some point if I wanted to use LetsEncrypt rather than a self-signed cert, on top of needing to VPN into my LAN.  I would get annoyed very quickly at having to constantly tell Firefox, "Yes, I accept the risk" when I visited my own NC instance.  Then again, running a VPN on a Raspberry Pi is preferable to buying a whole new system to host NC.

For get openvpn, use wireguard.  Wireguard is much simpler and liked by Linus himself. It is smaller code, so less likely to have bugs and it is significantly faster.  OpenVPN has grown and grown and grown with new, more complex features over the decades, making it hard to maintain and next to impossible to audit.  [https://arstechnica.com/gadgets/2018/08/wireguard-vpn-review-fast-connections-amaze-but-windows-support-needs-to-happen/](https://arstechnica.com/gadgets/2018/08/wireguard-vpn-review-fast-connections-amaze-but-windows-support-needs-to-happen/) has been around since 2018, so it is well vetted by this point. See the links I provided above ... I think that's this thread.  Well worth your time.  Get wireguard working FIRST and you'll see why you don't need to have most of your other self-hosted services on the internet.

I wouldn't use a raspberry pi for anything important. The hardware isn't exactly designed for redundancy.  There are lots of things that can be done with a r-pi, but that doesn't make it a good idea. I'd rather see you running VMs.
> **Tigera said:**
> 
So a couple of questions.  If I did run on a VPN to my LAN, would NC be an appropriate place to store passwords?  I'm guessing your answer to that will be "no," though I still thought I'd ask.  And if I did run a VPN to my LAN, how do we get around self-signed certificates on the NC instance?
Password in nextcloud? No, unless you are talking about a .kdbx password DB file, then sure.
If your nextcloud isn't on the internet, just available through the VPN, then you don't need TLS.  But you can use DNS TXT records to prove to let's encrypt that you own a domain.  [https://letsencrypt.org/docs/challenge-types/](https://letsencrypt.org/docs/challenge-types/) check out the DNS-01 challenge.

---

### Post by Tigera on 2023-03-10
[QUOTE=TheFu]Hardware issues don't get better.[/QUOTE]
No, they don't.  I just upgraded this machine.  I wish I could get some more life out of it, but it may be time.  The dream was one box to do everything.  I guess my next one should not be as overkill on CPU.

[QUOTE=TheFu]Linux and MacOS are both Unix-based systems. Why not use ssh/scp/sftp/sshfs to access files between the 2 systems. These should be 2nd nature to you.[/QUOTE]

They are but I would need to Google how to do that from a mobile device.  I'd prefer not to have my laptop at all and have either my phone or my tablet.  I was hoping I could have a "web view" similar to what Office 365 does for web-based editing and never have the file physically on the device.  Granted, as you say, portable storage should be encrypted.  But if I want to stream music off of my desktop, then getting that to work on my phone over SSH seems like it might get a bit complicated.  I also don't want two copies of the data floating around and forgetting which one is the "real" copy I was working on, so I'm not sure SCP/SFTP is the right tool.  That's one reason that I went with Google Drive, because it auto-syncs copies of the data back to the source, though admittedly not with rclone.  It also allows me to have access from tablet or phone.

[QUOTE=TheFu]I wouldn't use a raspberry pi for anything important. The hardware isn't exactly designed for redundancy. There are lots of things that can be done with a r-pi, but that doesn't make it a good idea. I'd rather see you running VMs.[/QUOTE]

I agree, but for dedicated hardware running a wireguard or OpenSSH server, isn't it a bit of an overkill to run a VM?  

[QUOTE=TheFu]As for blogging, I'd suggest running a static web site. That can be hosted almost anywhere - github - for example. With a static website, you can use CSS to make it feel dynamic, but still mount it read-only, drastically reducing the security issues. There are plenty of static website generators, or you should create your own. I did with perl a few decades ago. I've converted a wordpress site from a non-profit I help out into a 100% static website that looks the same (mostly) and has all the same links. It was meant to be used as a failover for when WP was hacked.[/QUOTE]

I've thought of that, though the static website generators I've seen require that you rebuild the whole site every time you make a post, as opposed to having a WYSIWYG editor and just clicking "post."  Perhaps there's one out there that doesn't do this, and you're right, I should do some research to figure out what it is.

[QUOTE=TheFu]Password in nextcloud? No, unless you are talking about a .kdbx password DB file, then sure.[/QUOTE]

It sounds like the password addon in NC is pretty useless...

---

### Post by DuckHook on 2023-03-11
> **Tigera said:**
> …It sounds like the password addon in NC is pretty useless...
Not useless at all. In fact it's slick and dead simple to use.

I installed the browser extension with a few dummy passwords just to try it out. I can see why general users might like it.

But for the security conscious, the problem with it is that there is no challenge/response to ascertain if it's really you. If someone steals your laptop and hacks your login, then as soon as they open your browser, the extension just kicks in and every password is now fair game. It's like having no password manager at all.

With Keepassxc at least you must successfully respond to a challenge before you can decrypt the database each time. You can also set it to automatically close down after a set period of inactivity.

---

### Post by TheFu on 2023-03-11
> **Tigera said:**
> No, they don't.  I just upgraded this machine.  I wish I could get some more life out of it, but it may be time.  The dream was one box to do everything.  I guess my next one should not be as overkill on CPU.

Upgrading 10 yr old computers is seldom a good idea.  Computers double their performance every 2 yrs for the same price.  A computer 10 yrs old means that a new computer of the same price would be 5x faster.  Last fall, I replaced a Ryzen 2600 CPU/APU for a Ryzen 5600g for $120.  Went from 13,000 passmarks to 20,000 passmarks. the prior system was a Core i5 with about 3500 passmarks.  The switch from Intel to AM4 was a little more costly because it meant getting a new motherboard, new RAM and I was forced to spend $70 on a GPU I didn't want/expect to need.  OTOH, the 2600-->5600g upgrade was 1 thing, the CPU only, because the MB, RAM and everything else was reused. Future, I got to remove the GPU which was slower than the iGPU of the new Ryzen. Effectively, I have 1 more cheap Ryzen upgrade available that doesn't require moving to AM5, and DDR5 RAM.  I'm planning that for about 3-4 yrs, if I even bother. Both my Ryzens are 65W APUs with impressive performance. Basically, they are faster than a Cray supercomputer from 1990.  I know. I worked on a Cray back then.

> **Tigera said:**
> 
They are but I would need to Google how to do that from a mobile device.  I'd prefer not to have my laptop at all and have either my phone or my tablet.  I was hoping I could have a "web view" similar to what Office 365 does for web-based editing and never have the file physically on the device.  Granted, as you say, portable storage should be encrypted.  But if I want to stream music off of my desktop, then getting that to work on my phone over SSH seems like it might get a bit complicated.  I also don't want two copies of the data floating around and forgetting which one is the "real" copy I was working on, so I'm not sure SCP/SFTP is the right tool.  That's one reason that I went with Google Drive, because it auto-syncs copies of the data back to the source, though admittedly not with rclone.  It also allows me to have access from tablet or phone.

I care little about phones or tablets and care even less for them being connected except via wifi. I don't have any cellular plan for my smartphones.  I don't stream media outside the house to them. My phone has about 80G of my music on it. More than I can stand.  I use rsync to efficiently replicated files.  rsync uses ssh for any networked transfers. Generally, I'll pull the microSD, put it into a USB 3.2 adapter and connect it to a desktop, then use rsync for local -to- local storage xfers. I wrote a script, so it would be consistently mounted and music files xferred called music-sync-to-microSD.  Anything on a portable device is never the main copy to me.  That's a rule I have to keep things simple.  Applies to laptops, tablets and phones.

I never want to stream music outside the house. It is a waste of bandwidth. Not ever.  Around the house, I use M.A.L.P. on android to control playback to different rooms with speakers from my media server running mpd.
I use android to control video playback to different screens through jellyfin. Sometimes I use the jellyfin android app and sometimes I use a generic DLNA controller/renderer (vlc).

BTW, these work over wireguard.

> **Tigera said:**
> 
I agree, but for dedicated hardware running a wireguard or OpenSSH server, isn't it a bit of an overkill to run a VM?  

Who said anything about dedicated hardware?  Run a small VM for just wireguard and ssh access over wifi or over the internet. You know that multiple VMs can run concurrently on the same hardware, right?  I've run over 20 VMs on dual core systems in 2008.  Running 10 VMs on a 6-core Ryzen is nothing. Literally, nothing.  RAM is the main problem, not CPU or disk.  Right now, one of the Ryzens is running 5 VMs. Less than 3% of the available vCPU is used even if 12G of RAM is used by the bloated VMs.  My other Ryzen is running mostly lxc containers, but it also runs a Mint 21.1 VM that takes 25% of the system RAM. The containers are using:
```
$ lxc list --format=yaml|egrep 'peak|^  name:'
name: nextcloud-lxd
      usage_peak: 987521024
  name: pihole2
      usage_peak: 479211520
  name: publify
      usage_peak: 1338765312
  name: spam2
      usage_peak: 2933420032
  name: wallabag
      usage_peak: 407949312

```
I have redundant containers for some important services.

> **Tigera said:**
> I've thought of that, though the static website generators I've seen require that you rebuild the whole site every time you make a post, as opposed to having a WYSIWYG editor and just clicking "post."  Perhaps there's one out there that doesn't do this, and you're right, I should do some research to figure out what it is.

It takes less than a second to regenerate the entire static website, so what does that matter? Use rsync to push it to the target location and only the updated files will be changed.  As a developer, I assume you know how to use gmake, so only changed input files would update output files.  A static site with 50,000 source markdown files, but only 1 modified/new, would only need 1 modified/new html file xferred.  Even if you are lazy, pushing 50000 source files full of text using rsync would be just a few seconds, if that.

> **Tigera said:**
> It sounds like the password addon in NC is pretty useless...
That's my assumption. I've never bothered looking at it, because I don't consider php webapps secure.  Webapps are fodder for practice by cracking teams.  They spend lots of time figuring how to get in and have their way.  So, don't let them. Use a vpn and don't let them on the same subnet, because once they get inside, all bets are off.  That includes running a phone, tablet, or any browser with javascript enabled. Javascript runs code on the client system. Nothing says that code can't be used to run a network scan, then attack other devices on the same subnet.  Learn to think like an attacker. If you can imagine an attack vector, someone is using it already.

---

### Post by Tigera on 2023-03-11
Would something like [this]("https://www.newegg.com/bmax-b2/p/2SW-0029-00002?Item=9SIAW7DFGA7597&cm_sp=SP-_-1535807-_-Pers_ProductAlsoView+-_-4-_-9SIAW7DFGA7597-_-9SIAW7DFV01443-_--_-1") work for the dedicated wireguard/ssh server connected to the internet?  I don't think I need that much capacity.

---

### Post by Tigera on 2023-03-11
> **TheFu said:**
> Upgrading 10 yr old computers is seldom a good idea.  Computers double their performance every 2 yrs for the same price.  A computer 10 yrs old means that a new computer of the same price would be 5x faster.

The machine is only four years old.  It was a Ryzen 2700x with an X470 motherboard.  Now it's a Ryzen 5800X3D with triple the storage (that doesn't work).  This is looking more and more like a motherboard upgrade, but if I'm going to do that, and I've got two bad drives, I might just be tempted to get something faster.

> **TheFu said:**
> I care little about phones or tablets and care even less for them being connected except via wifi. I don't have any cellular plan for my smartphones.  I don't stream media outside the house to them. My phone has about 80G of my music on it. More than I can stand.  

My phone only has 32 GB of storage on it, 26 of which are filled up by music.  I couldn't move my whole library to it because I didn't have the space.  I was hoping streaming would be a cheaper option than buying a new phone.

> **TheFu said:**
> I use rsync to efficiently replicated files.  rsync uses ssh for any networked transfers. Generally, I'll pull the microSD, put it into a USB 3.2 adapter and connect it to a desktop, then use rsync for local -to- local storage xfers. I wrote a script, so it would be consistently mounted and music files xferred called music-sync-to-microSD.  Anything on a portable device is never the main copy to me.  That's a rule I have to keep things simple.  Applies to laptops, tablets and phones.

I can't pull the SD card out of this easily (they make storage so hard to replace these days), though I do have a microSD adapter around here somewhere.  Honestly, I'd rather use KDE connect and move stuff around that way via USB cable.  I suppose rsync is still an option though.

> **TheFu said:**
> BTW, these work over wireguard.

Which is looking like the solution I may settle on.  

> **TheFu said:**
> Who said anything about dedicated hardware?  Run a small VM for just wireguard and ssh access over wifi or over the internet. You know that multiple VMs can run concurrently on the same hardware, right?

Yes, but I thought your recommendation was to run the wireguard server or the ssh server on dedicated, isolated hardware.  If however I could use one machine and not have to use isolated hardware, that would make me very happy.  Was I misunderstanding, or are you suggesting that I could put the VM on the same hardware as my Kubuntu VM and run it that way?  That certainly would simplify things.

> **TheFu said:**
> It takes less than a second to regenerate the entire static website, so what does that matter? Use rsync to push it to the target location and only the updated files will be changed.  As a developer, I assume you know how to use gmake, so only changed input files would update output files.  A static site with 50,000 source markdown files, but only 1 modified/new, would only need 1 modified/new html file xferred.  Even if you are lazy, pushing 50000 source files full of text using rsync would be just a few seconds, if that.

Fair enough, but it's that extra step that bugs me rather than just having a "post" button.  But you are right, that's a small price to pay for the added security.

---

### Post by TheFu on 2023-03-11
> **Tigera said:**
> The machine is only four years old.  It was a Ryzen 2700x with an X470 motherboard.  Now it's a Ryzen 5800X3D with triple the storage (that doesn't work).  This is looking more and more like a motherboard upgrade, but if I'm going to do that, and I've got two bad drives, I might just be tempted to get something faster.

You have 2 beasts and the 5800 shouldn't need any upgrade for a decade - it can run 50 VMs if you put 64G of RAM into it.
> **Tigera said:**
> 
My phone only has 32 GB of storage on it, 26 of which are filled up by music.  I couldn't move my whole library to it because I didn't have the space.  I was hoping streaming would be a cheaper option than buying a new phone.

I don't like spending money on phones.  Usually wait 4-6 yrs between replacements.  All my phones, except company-provided blackberrys are still useful as wifi devices.
Last fall, I got an unlocked $140 Moto G Power 2020 with 64G onboard storage and a microSD that supports up to 256G.  That's a bunch of storage.  2 full days of battery life.  Back when I was forced to buy a Nexus4 with no external storage, I got a USB-powered wifi-storage device for $17 that would connect to the Nexus (only 16G local storage) and add 64G more storage - really it was a microSD card that could be swapped.  Streaming over a little, local, wifi network avoided the data charges. Generally, I left it in the car full of music and books on tape. It was a tiny Linux computer, about the size of my thumb.  Can't find the thing I bought anymore, but did see some apple compatible versions, complete with the _Apple tax_ for $70. 
Make your next phone have a microSD card or don't buy it.
> **Tigera said:**
> 
I can't pull the SD card out of this easily (they make storage so hard to replace these days), though I do have a microSD adapter around here somewhere.  Honestly, I'd rather use KDE connect and move stuff around that way via USB cable.  I suppose rsync is still an option though.

The drag-n-drop method may seem easier, but it isn't faster in the long run.  A script that does what you need, consistently will be faster over time.  Mine grabs all .ogg files and playlists with 'vorbis' in their names, replicates them to the microSD while maintaining the same directory structure.  
For Music, I use Genre/Artist/Album/Tracks&playlist.
For Photos, I use YYYY/MM-Event/{seq}-description.
For All other files, I use YYYY/MM/ and use descriptive filenames.  
I don't trust dates/times stored in the inode data, but use the directory structure to maintain that.  I do trust timestamps in exif data for photos, however.
I keep financial/tax files separate from project and personal files.  I don't scan receipts except for high-ticket value stuff and use a simple, paper, filing system that is just sequentially added to a folder.  Takes less than 30 seconds a month for filing and if I do need to look up a receipt, it is less than 30 seconds to find it, assuming I know the correct year and have an idea about the month.  People doing electronic filing are wasting so much effort when a simple paper file per year is sufficient.
I do keep lifetime warranties and receipts in a "forever" folder.  That's basically for anything with 10+ yrs of warranty. For example, the roof has a 30 yr warranty, so the paperwork for that is in this "forever" folder. Have another 10 yrs on it ... or so. Roof still looks great.

> **Tigera said:**
> 
Yes, but I thought your recommendation was to run the wireguard server or the ssh server on dedicated, isolated hardware.  If however I could use one machine and not have to use isolated hardware, that would make me very happy.  Was I misunderstanding, or are you suggesting that I could put the VM on the same hardware as my Kubuntu VM and run it that way?  That certainly would simplify things.

Isolated doesn't mean dedicated. I think that subtle difference was missed.  A $25 NIC added to the VM host and passed through from the internet to the VPN/ssh virtual machine would provide sufficient separation.  Now, I'd never do that for a WAN router/firewall. THAT does need to be on separate, dedicated, hardware.  I'd stay away from any Atom-based hardware myself.  Additionally, I wouldn't run a VPN on a WAN router either.  Even though router software comes with 100 extra services that can be enabled, that doesn't mean it is a good idea to use them.  Also, I'd avoid running a WAN router inside a VM.  I do run a router inside a VM for LAN segment firewalling, but that's very, very, different from the WAN router.

> **Tigera said:**
> 
Fair enough, but it's that extra step that bugs me rather than just having a "post" button.  But you are right, that's a small price to pay for the added security.
Only you can decide what security is sufficient.  I like to schedule my blog updates to go live at a specific time. I also like the idea of having 100% static files for the blog from a security standpoint. While I'm at it, I like using read-only NFS mounts to the blog website. I tested this at a security conference where they were playing capture the flag. That's basically a web-server takeover attack competition.  Over half the teams never noticed that the static files were mounted to a read-only file system from another box.  Of course, the ones that did new to just modify the web server base directory to point somewhere else to win the points.  If I were smarter setting that hackable server, I'd have set the quotas to prevent no new files from being added to the system, even on the read-write mounted areas.  Hummmm.  There's a local Defcon chapter meeting that just started here. I need to go join that video conference and ask about that from some buddies who compete in the CTF competitions.

---

### Post by Tigera on 2023-03-12
> **TheFu said:**
> You have 2 beasts and the 5800 shouldn't need any upgrade for a decade - it can run 50 VMs if you put 64G of RAM into it.

It does have 64 GB of RAM on it, making this all the more painful to think about an upgrade.  But that 7950X3D looks very tempting...

> **TheFu said:**
> I don't like spending money on phones.  Usually wait 4-6 yrs between replacements.  All my phones, except company-provided blackberrys are still useful as wifi devices.
Last fall, I got an unlocked $140 Moto G Power 2020 with 64G onboard storage and a microSD that supports up to 256G.  That's a bunch of storage.  2 full days of battery life.  

I've got the same phone, just the 2019 model.  I need to replace it though.  It's warped in a weird way...

> **TheFu said:**
> Make your next phone have a microSD card or don't buy it.

I'm sure mine does, but I have no desire to take it apart and replace it.

> **TheFu said:**
> Isolated doesn't mean dedicated. I think that subtle difference was missed.  A $25 NIC added to the VM host and passed through from the internet to the VPN/ssh virtual machine would provide sufficient separation.  

OK, that makes a lot of sense.  I can do that.  Then I can put NC on a separate VM, my desktop on another VM, and maybe a test server for the blog.

> **TheFu said:**
> Now, I'd never do that for a WAN router/firewall. THAT does need to be on separate, dedicated, hardware.  I'd stay away from any Atom-based hardware myself.  Additionally, I wouldn't run a VPN on a WAN router either.  Even though router software comes with 100 extra services that can be enabled, that doesn't mean it is a good idea to use them.  Also, I'd avoid running a WAN router inside a VM.  I do run a router inside a VM for LAN segment firewalling, but that's very, very, different from the WAN router.

I have to use the ISP's stupid router anyway since it's fiber.  Definitely not running anything but the firewall on that thing.

> **TheFu said:**
> Only you can decide what security is sufficient.  I like to schedule my blog updates to go live at a specific time. I also like the idea of having 100% static files for the blog from a security standpoint. While I'm at it, I like using read-only NFS mounts to the blog website. 

So is that done through a hosting provider like Linnode?  I'm missing something here... are those NFS mounts on your VPN at home?

---

### Post by DuckHook on 2023-03-12
> **Tigera said:**
> It does have 64 GB of RAM on it, making this all the more painful to think about an upgrade.  But that 7950X3D looks very tempting...
Your current box should make for a flexible and powerful server. To me, the long POST period indicates some HW issue other than MOBO or CPU, so replacing any of those is overkill. Try checking your RAM, video card and your HDDs. All of these can lead to slow POSTs.

Do a memory test (run memtest86+ from your grub menu)
Show us the HDD smartctl reports. If you suspect bad HDDs, then take them out to see if POST speeds up.

I think it is pointless to get a new MOBO CPU. You are better off with the current one being fixed to work as a good server, then using the money you save to buy a new, cheap and less powerful box for desktop use.

***Your current attempt to run everything out of one box is an insecure, inflexible and needlessly limiting strategy.***
> OK, that makes a lot of sense.  I can do that.  Then I can put NC on a separate VM, my desktop on another VM, and maybe a test server for the blog.
In my opinion, this is a poor strategy. See above.
> I have to use the ISP's stupid router anyway since it's fiber.  Definitely not running anything but the firewall on that thing.
I don't even trust them for firewall duties. I tell my ISP to bridge theirs so that it acts as a plain modem. Then I run a dedicated piece of gear for the real firewall with opnsense (pfsense is fine too). For most people it's a bit overkill, but just a thought.

---

### Post by TheFu on 2023-03-12
> **Tigera said:**
> I'm sure mine does, but I have no desire to take it apart and replace it.

It is just a slot on the side.  Hardly a big deal to open once a quarter. At least for me.

> **Tigera said:**
> 
OK, that makes a lot of sense.  I can do that.  Then I can put NC on a separate VM, my desktop on another VM, and maybe a test server for the blog.
You'd need 3 separate NICs, each in a different PCI or PCIe slot then.  PCI passthru is on the PCI slot level and provides exclusive use for the hardware in a specific PCIe slot to a single VM.  The point is that the network hardware IS NOT SHARED with the host or any other VM.  It is a risk level thing.

> **Tigera said:**
> 
So is that done through a hosting provider like Linnode?  I'm missing something here... are those NFS mounts on your VPN at home?
Static websites.  My home/business setup is very, very, different from what we've discussed here.  I have multiple public IPs, multiple subnets, multiple routers.  Different subnets are used to mitigate networking risks.  Since I don't trust wifi at all, all wifi connected devices are actually outside my main WAN router, but just inside the ISPs router on a 10.1.10.x/24 subnet.  That's also where IoT stuff goes and any house guests.  My static IPs are managed on my WAN router to specific devices in a heavily firewalled server LAN segment.  I have another LAN segment for internal servers and another segment for end-user wired devices. There are firewall rules between all these different segments.  Some internet facing systems are just gateways and reverse proxies.

For me, security begins with network architecture.

How many NICs do you put in your systems? For me, 1 is never enough.
```
$ inxi -N
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           Device-2: Intel 82575GB Gigabit Network driver: igb 
           Device-3: Intel 82575GB Gigabit Network driver: igb 
           Device-4: Intel 82575GB Gigabit Network driver: igb 
           Device-5: Intel 82575GB Gigabit Network driver: igb 
$ inxi -N
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller driver: r8169
           Card-2: Intel 82574L Gigabit Network Connection driver: e1000e
           Card-3: Marvell 88E8001 Gigabit Ethernet Controller driver: skge

```
A few dual-port Intel NICs are a good thing. ;)  I also have physically separate networks. VLANs aren't security in most small networks. A VLAN tag is just a suggestion, not a mandate.  This is just 1 of the many reasons I'm not a fan of raspberry pi computers.  No good way to have 3 NICs. ;)

Too many new ideas and concepts can muddy the water too much.

---

### Post by Tigera on 2023-03-12
> **DuckHook said:**
> Your current box should make for a flexible and powerful server. To me, the long POST period indicates some HW issue other than MOBO or CPU, so replacing any of those is overkill. Try checking your RAM, video card and your HDDs. All of these can lead to slow POSTs.

When I remove all the SATA drives, it still boots slowly.  None of this started happening before I added all those extra disks, though.  My next step is to take out the NVMe drive that I added.  If that doesn't work, it would have to be the motherboard, the RAM, or the video card.  In any of those cases, it's not worth it pouring more money into this thing.

> **DuckHook said:**
> Do a memory test (run memtest86+ from your grub menu)
Show us the HDD smartctl reports. If you suspect bad HDDs, then take them out to see if POST speeds up.

Haven't tried the memtest, but have tried removing all the drives besides the NVMe drives.  I'll see if I can get the thing to boot memtest.

> **DuckHook said:**
> I think it is pointless to get a new MOBO CPU. You are better off with the current one being fixed to work as a good server, then using the money you save to buy a new, cheap and less powerful box for desktop use.

***Your current attempt to run everything out of one box is an insecure, inflexible and needlessly limiting strategy.***


I'm confused here.  Are you saying to run each service on separate physical hardware?  NC on one box, wireguard on another, desktop on another, and everything else on separate, dedicated physical hardware?  That seems to be a lot of hardware to take care of.  Or are you suggesting running VM's for wireguard, NC, and everything but the desktop on other hardware, and having separate physical hardware for the desktop?  

Running off of one system *can't* be less secure than what I'm doing now with third-party services, right?

---

### Post by Tigera on 2023-03-12
> **TheFu said:**
> You'd need 3 separate NICs, each in a different PCI or PCIe slot then.  PCI passthru is on the PCI slot level and provides exclusive use for the hardware in a specific PCIe slot to a single VM.  The point is that the network hardware IS NOT SHARED with the host or any other VM.  It is a risk level thing.

I've confirmed which slots go to which IOMMU groups, so this should be doable.  This box was originally meant to be a "3 gamers, 1 CPU" machine, so I was really careful to read up on how the motherboard would assign virtual hardware.


> **TheFu said:**
> Static websites.  My home/business setup is very, very, different from what we've discussed here.  I have multiple public IPs, multiple subnets, multiple routers.  Different subnets are used to mitigate networking risks.  Since I don't trust wifi at all, all wifi connected devices are actually outside my main WAN router, but just inside the ISPs router on a 10.1.10.x/24 subnet.  That's also where IoT stuff goes and any house guests.  My static IPs are managed on my WAN router to specific devices in a heavily firewalled server LAN segment.  I have another LAN segment for internal servers and another segment for end-user wired devices. There are firewall rules between all these different segments.  Some internet facing systems are just gateways and reverse proxies.

O.o Let's start... eh, smaller, yes?  For static hosting, I'd have to use someone, or would you suggest using GitHub or a GCS bucket?


> **TheFu said:**
> For me, security begins with network architecture.

How many NICs do you put in your systems? For me, 1 is never enough.
```
$ inxi -N
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           Device-2: Intel 82575GB Gigabit Network driver: igb 
           Device-3: Intel 82575GB Gigabit Network driver: igb 
           Device-4: Intel 82575GB Gigabit Network driver: igb 
           Device-5: Intel 82575GB Gigabit Network driver: igb 
$ inxi -N
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller driver: r8169
           Card-2: Intel 82574L Gigabit Network Connection driver: e1000e
           Card-3: Marvell 88E8001 Gigabit Ethernet Controller driver: skge

```
A few dual-port Intel NICs are a good thing. ;)  I also have physically separate networks. VLANs aren't security in most small networks. A VLAN tag is just a suggestion, not a mandate.  This is just 1 of the many reasons I'm not a fan of raspberry pi computers.  No good way to have 3 NICs. ;)


Yeah, I probably need that if I'm going to host anything at home.  You are right, separate physical NICS is more secure.  This board has two of them, one of them wifi, but that isn't enough.

---

### Post by DuckHook on 2023-03-12
> **Tigera said:**
> I'm confused here.  Are you saying to run each service on separate physical hardware?  NC on one box, wireguard on another, desktop on another, and everything else on separate, dedicated physical hardware?  That seems to be a lot of hardware to take care of.  Or are you suggesting running VM's for wireguard, NC, and everything but the desktop on other hardware, and having separate physical hardware for the desktop?
Security is only one element of a robust system.

Consider the following:

**Scenario 1:**
You find that your new hardware won't work with an LTS release and you are forced to use a standard release. You are now on the six&#8209;month hamster wheel upgrade cycle using a less stable version that changes twice a year.

Why would you want to subject your servers to such instability? Instability is acceptable in your desktop, but not in your servers.

**Scenario 2:**
You decide that a great new service/utility/app is a must&#8209;have for your desktop experience. But it can only run properly on bare metal. You install it and it runs your desktop just fine. But it breaks your server VMs. You now have a still functional desktop, but no servers.

Why would you want to increase the fragility of your whole system in this way?

**Scenario 3:**
Bad guys compromise your desktop VM in such a way that they get to your bare metal install. In your setup, this means that they now automatically compromise all of your servers as well. If your servers were running on a different machine, you would have at least a fighting chance to isolate the threat and protect your server data. Your method means that as soon as your desktop sandbox is penetrated, the whole game is up.

**Scenario 4:**
Your one and only box goes down or gets corrupted. With your setup, you are dead in the water. But with a separate box for server VMs and another for desktop, you can leverage one to try and fix the other.

Why would you want to put all of your eggs in one basket?


How much and how finely you want to atomize your setup is a judgment call. There is no pat and easy answer to what is optimal. But there certainly are setups that are clearly sub&#8209;optimal, and yours has far too many eggs in one basket for my comfort.

For example, I buy really cheap fileservers for my important files. They are very reliable because I keep them dead simple. There is no other service running on them except NFS and SSH. They are also miserly when it comes to power, so running them 24/7 is dirt cheap. And because they are so cost effective, I can afford 2 identical ones for mirrored redundancy. If one goes down, I just reassign the DNS address in my DHCP server to the redundant machine and it's like nothing has happened. This is an example of the advantages that one can get by thinking more atomically. But I'm not suggesting that everyone do this. I've segmented my setup further than most people and this does require more maintenance and care. I've purchased safety and redundancy at the cost of more work. This is not a good solution for people who lack either the time, the training or the resources. It's a judgment call.

In my opinion, the best network strategies involve a combination of VMs on centralized servers and separate dedicated machines. It's a bit of an art determining which should be what, but working out a combo strategy yields a more secure, versatile and stable network.

I can't tell you what the best combo is for you. But I hear you toying with the idea of upgrading to a high&#8209;grade machine, or installing 64GB of RAM, or adding all sorts of pricey components, so money doesn't appear to be the primary concern. If cost isn't the issue, then why keep trying to shove everything into one box? It's like trying to use one chassis for a train, a submarine and an airplane. Different uses demand different HW platforms.

I suppose that you could combine similar VMs into one box: say, Nextcloud, a proxy server, a torrent server and a media server for example. But I would not put my sensitive files on that box, even in a VM. I would not even put my sensitive files on the same LAN. I would put such files on separate HW that is both physically and virtually isolated from the Internet facing VMs. But that's me.
> Running off of one system *can't* be less secure than what I'm doing now with third-party services, right?
Right. Of course. But this is like saying: "Russian roulette with one bullet has got to be better than it is with five bullets, right?" The point is that it's easy to make it even better. So much better. You don't have to settle for just a little better. A bit more work and a couple more devices and you're not playing Russian roulette at all. Only you can decide if the extra investment is worth it.

I've explained it thoroughly by now. I don't want to come across as flogging a dead horse, so now it's your call.

---

