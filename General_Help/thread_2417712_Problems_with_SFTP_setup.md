---
title: "Problems with SFTP setup"
date: 2019-04-26
forum: General Help
---

### Post by rafal3 on 2019-04-26
Hi.
I have a problem to setup a SFTP connection. 
My family is spread across a country so I need to setup just a SFTP connection for them. I have a Ubuntu Server 18.04. I have 2 SSD drives. First is 60GB mounted as /dev/sda just for a system, second 512 GB mounted as /dev/sdb1/media (this drive is for sharing media).
I have red and watched a lot of tutorials on internet, youtube but none of them working for me. I know that I making a mistake somewere but I dont know where and a request to you is to help me totally from scrach how to setup just sftp for my family. I will post all screens to you as needed but at this point I have lost to much time for setting this up and I want to just to have it work correctly. I must add that my family (will be 4 users) cannot have accesss outside a main folder so for example. I want to have on my SSD 5 or 6 folders: Movies, Photos, Programs, Kid1, Kid2. Those folders I want to share to my family (user1, user2, user3, user4) but they cannot go outside that folders to for example read other files like /etc folder. I know I messed up a little :) but help me with that please. Assume you have clean server with openssh installed.
Regards
rafal

---

### Post by TheFu on 2019-04-26
Please don't post images for server-related stuff ... ever.  Text is preferred. Copy/paste that, surrounded by "code tags"  - adv reply (#) or just use the "quote tag" and manually replace quote --> code in both the front and end.

To setup a normal sftp it easy.
**sudo apt install openssh fail2ban**
Be certain the "server" has a static IP on the LAN. Create userids for the people you want to provide access.  That's it.  
The ssh-server includes the sftp-server and it is enabled.  The userids have access to anywhere they would with normal ssh, including using normal ssh for all the remote stuff it can do.  There are sshd_config settings which can only allow sftp, block scp, rsync, ssh, and all the other 500 things ssh can do.
If you go with ssh, please don't allow passwords over the internet. I see thousands of attempted hacks every hour on my ssh ports. These have been happening for 20 yrs now. Because we don't allow any passwords to be used outside the LAN, they won't get in and after 3 attempts, fail2ban blocks that IP for a week.

On other systems, you might need to open a port on your WAN router - I like to use a non-standard high port - don't use port 22/tcp, since the entire world will attack that in about 3 minutes.  Leave the fault port on your server, let the router do port translation - say from {WAN-IP}:63099/tcp --> 192.168.55.31:22/tcp.  Doing this will drastically reduce your logs.

There are lots of other alternatives for your consideration.

Well, to limit where userids can see is hard, because they must have access to the /etc/passwd, /etc/groups and a few other files to even login. You can follow a guide to setup a chroot for sftp.  I've never done that.  I think it is built-into sftp now. [https://www.tecmint.com/restrict-sftp-user-home-directories-using-chroot/](https://www.tecmint.com/restrict-sftp-user-home-directories-using-chroot/) is a guide from a reputable source.

If you just want them to have read-only access to the files, I would setup a web server and lock it down using firewall and basic security.
Or use directconnect++ (usually called DC++)  or [https://github.com/RetroShare/](https://github.com/RetroShare/)  If you want security and control, RetroShare would be my suggestion.  Be cautious using tools like owncloud, nextcloud, seafile, Pydio, that claim to be like dropbox. Proper security on these setups is non-trivial.  I run a nextcloud server with lots of plugins - the video chat plugin is pretty freakin' awesome, I must admit.  Had 5 people on video chat last month.  Securing it is something I haven't been able to do enough to feel comfortable.  I block the internet and only allow access over https from extremely specific subnets - family member home subnets and a few cafe's that I commonly visit.  For access everywhere else, I use either openVPN or an ssh-tunnel.

Or since you seem to want to share only media files, you could use plex-server with the paid plex clients.  I don't know if there is any real security to prevent the kids from seeing adult content. I know DLNA doesn't have any capability like that. Plex Server is a DLNA server on a LAN.  I've been using Plex for multiple years, but don't share outside my LAN to others and do not using either a plex account, nor any of the plex clients.  I use both VPN and ssh-tunnel access to access the plex webserver and access the media - it streams nice, dependent on available upstream bandwidth.

Once setup, retroshare is the easiest to use. Only 1 of the locations needs inbound internet and shouldn't move. Assuming that is your box, everyone can share notes, email-like messages, forums, files, photos, whatever, for the entire family. It uses very strong, known, encryption.  I'm a little fuzzy about the setup, each client has to exchange gpg keys.

BTW, I hope you aren't using sda, but are using a partition on sda, like sda1 or sda2.  sda is the entire drive.  OSes don't run from the entire drive.

Only you can decide the best solution.

---

