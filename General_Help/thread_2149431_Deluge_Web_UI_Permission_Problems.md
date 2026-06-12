---
title: "Deluge Web UI Permission Problems"
date: 2013-05-28
forum: General Help
---

### Post by Samsicle on 2013-05-28
Hi All

I've got myself a HTPC that I would like to remotely download torrents to. So I recently followed the guide at [http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient](http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient)  to set up Web UI. I also followed the instructions for creating an init  script (but stopped before the section on logging hoping I wouldn't need it). I can download a file  just fine through the web interface (for example I download to  '/home/sam/Downloads') but when I actually go onto the computer running  deluge I have no permission to '/home/sam/Downloads/filename'

I  suspect it has something to do with the user i set up (deluge) and the  file being in my home directory (sam). But I don't know enough about permissions or to review the scripts that are used. I just straight copy and pasted the code provided at link above when I created the init scripts.

If I run
```
ls -lh
```
under the downloads directory, the file shows it belongs to the user and group 'root'. Currently to solve this I just run 
```
sudo chown sam:sam file/location
```

If anyone with a greater amount of knowledge than me has the solution it would be much appreciated.

---

### Post by Cheesehead on 2013-05-28
What do you want to do with those downloaded torrents?
Seed them? Download them to your local system?

If you want to download the files, how do you want to do it?
Local torrent client to transfer the files from the server via torrent?
SSH/SCP copy on the command line?
Have the server files show in a GUI file manager?

In theory, your torrent server should have several users on it, including 'deluge' and 'sam'.
Did you set both up? Or did you just create a sam directory without creating the user?

If you login to the server as 'deluge', the system should correctly deny you access to /home/sam/Downloads/filename
If you login to the server as 'sam', the system should permit you access to /home/sam/*
Which user are you logging is as?

---

### Post by Samsicle on 2013-05-29
> What do you want to do with those downloaded torrents?
Seed them? Download them to your local system?
I will be seeding them but mostly I just want them downloaded to my local system for use on my local system. Lets use an example for easier explanation: Say I'm at the office and I want to download the latest Ubuntu release. I start up the web UI at the office by going to my public ip and port 8112, then add the torrent by url to download to /home/sam/Downloads.
> If you want to download the files, how do you want to do it?
Through the Web UI that connects to the local deluge daemon. I only have the one computer at home which runs deluged and uses whatever I download. Continuing my example, when I get home from work I can make live usb for instance or upgrade my system. I just want to be able to download a file remotely then use it once I get home.
```
sudo adduser --system --group --home /var/lib/deluge deluge
```
This was the command I used to add the user 'deluge'. So I think this means the user 'deluge' should only be downloading to that file location '/var/lib/deluge'? Because from what I understood while going through the setup tutorial was that any files downloaded through the Web UI would belong to the user and group 'deluge' and since 'sam' is a part of the group 'deluge' I should have permission to do anything with these files. However, when I download a file to my home directory it belongs to the user and group 'root'. The guide says the user 'deluge' has no login access.
> If you login to the server as 'sam', the system should permit you access to /home/sam/*
I have permission to access /home/sam/* but not to /home/sam/Downloads/filename/*. It's just the file I'm downloading I don't have access to.
```
env uid=deluge
env gid=deluge
env umask=007
exec start-stop-daemon -S -c $uid:$gid -k $umask -x /usr/bin/deluged -- -d
```
This appears to be the meat an potatoes of the init script I created for the daemon (there is a similar one for deluge-web). Can I solve this issue by changing uid=sam and gid=sam? Will this cause some security issues? I'm not worried about security on the local side, I only have the one computer on my local network and I trust myself not to screw things up beyond repair, but I would prefer if people outside my local network could not find a way through.

I think that is a long enough post, hopefully made things a little more clear.

---

