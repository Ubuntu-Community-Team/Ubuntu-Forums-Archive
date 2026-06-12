---
title: "Samba service sometimes missing"
date: 2015-05-14
forum: General Help
---

### Post by ffonz2 on 2015-05-14
I have very odd behaviour on my Ubuntu 14.04 system. Since I have these annoying problems on an irregular basis, I first want to find the CAUSE of this problem. For the moment I am NOT interested in a SOLUTION.

I could see my samba shares flawless for over a year. Until about a month ago. Then, one day I couldn't see any share with Nautilus. When I double clicked Windows Network, I got the message:

```
    Unable to access location
    Failed to retrieve share list from server: No such file or directory

```
This lasted for about a week and then my shares where back again. Until this week... The shares have vanished again. Meanwhile I haven't done any exciting stuff: only some browsing in Firefox and accessing another system via ssh in a terminal. AND of course I installed Ubuntu updates. So I am suspecting this last process, since this is the only thing that is making changes to my system!

With smbclient I am able to see a share and download files. And on a Windows machine the shares are there, so the problem lies with Ubuntu.

I tried to restart the samba service, but it seems it's not there. I tried

```
    $ sudo service smb restart
    smb: unrecognized service

```
I also tried it with 'smbd', 'samba' and 'nmbd'. All give the same result: unrecognized service.

A few years ago I had the same behaviour on my previous PC: different hardware, different Ubuntu (12.04), same problem.

So where do I have to start to find out what is happening on my system? Maybe some logging? But I don't know which log files and what errors to look for. Any suggestion?

---

### Post by ffonz2 on 2015-07-18
Finally I found the cause of my problems. It al had to do with the "Master Browser". I could solve it in several ways, but I have chosen to connect to the network servers by hand ("Connect to Server..." -> Server Address: smb://<server-name>/ ).

If you are having similar problems then search for Samba and Master Browser and you will find all the information you need.

---

