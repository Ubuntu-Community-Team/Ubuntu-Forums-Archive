---
title: "question about torrent clients"
date: 2007-05-04
forum: General Help
---

### Post by Angelbeast on 2007-05-04
On winXP i was using azureus and got great speeds. On Uuntu i have tried azureus and the BitTorrent client that comes with it and have gotten mostly very slow speeds. My question is...Is there one that works well and gets good speeds "out of the box" for Ubuntu 64?

---

### Post by kripkenstein on 2007-05-04
Azureus should get the same speeds as Azureus on Windows. And that should be about the same as utorrent (although a specific torrent might be faster on one rather than the other, depending on peers). So Azureus should work well - perhaps you haven't set all the options in an optimal way, upload speed, #connections, etc.? Post your settings and perhaps we can help.

Another option on Ubuntu is to run utorrent on Wine. This is actually quite easy to do, and works great. However, I am not sure if this works on 64-bit installations, Wine is 32-bit last I checked.

---

### Post by Angelbeast on 2007-05-04
> **kripkenstein said:**
> Azureus should get the same speeds as Azureus on Windows. And that should be about the same as utorrent (although a specific torrent might be faster on one rather than the other, depending on peers). So Azureus should work well - perhaps you haven't set all the options in an optimal way, upload speed, #connections, etc.? Post your settings and perhaps we can help.

Another option on Ubuntu is to run utorrent on Wine. This is actually quite easy to do, and works great. However, I am not sure if this works on 64-bit installations, Wine is 32-bit last I checked.

well this is my problem which i posted in aother topic and a couple of screen shots...

> **Angelbeast said:**
> i'm getting the two errors show in the screenshots...any ides how to fix them? doing anything with the router though is outof the question...if it can'tbe remedied is there any other bit torrent client that works better with ubuntu?

---

### Post by kripkenstein on 2007-05-04
It appears that Azureus is trying to use the port "3" for TCP and UDP. This is wrong, because ports under 1000 (or 1024?) require special privileges. But that is just for your general information. The thing to do here is to set a different port number. Go into the Azureus options (I don't have it installed so I can't say exactly where, sorry), and in one of the 'network options' or a similar name you can select the port. Try port 6881, that is generally standard for bittorrent.

---

### Post by Angelbeast on 2007-05-04
> **kripkenstein said:**
> It appears that Azureus is trying to use the port "3" for TCP and UDP. This is wrong, because ports under 1000 (or 1024?) require special privileges. But that is just for your general information. The thing to do here is to set a different port number. Go into the Azureus options (I don't have it installed so I can't say exactly where, sorry), and in one of the 'network options' or a similar name you can select the port. Try port 6881, that is generally standard for bittorrent.

hmmm...i reinstalled Azurues and now it shut down soon s it starts *LOL* ... is there any way to tweak the default bittorrent client?

---

### Post by kripkenstein on 2007-05-04
It shuts down immediately? No error messages?

If not, try to run it from the command line, and see if it prints error messages there.

---

### Post by unnes on 2007-05-04
If you are behind a router or firewall, you may have to forward the appropriate port in order to connect to peers and get good speeds. See [this site]("http://www.portforward.com/") for more information on how to forward ports on your specific router.

---

### Post by Angelbeast on 2007-05-04
> **kripkenstein said:**
> It shuts down immediately? No error messages?

If not, try to run it from the command line, and see if it prints error messages there.

It went into debug mode...other than that it's ll greek tome *LOL* ... it wouldn't let me paste it all so it's now an attchment...sort of...


[www.angelbeast.org/debug.pdf]("www.angelbeast.org/debug.pdf")

---

### Post by Angelbeast on 2007-05-04
> **unnes said:**
> If you are behind a router or firewall, you may have to forward the appropriate port in order to connect to peers and get good speeds. See [this site]("http://www.portforward.com/") for more information on how to forward ports on your specific router. 

well doing anything to the router is not an option...i don't really have 'access' to it if you know what i mean :popcorn:

---

### Post by kripkenstein on 2007-05-04
> **Angelbeast said:**
> It went into debug mode...other than that it's ll greek tome *LOL* ... it wouldn't let me paste it all so it's now an attchment...sort of...


[www.angelbeast.org/debug.pdf]("www.angelbeast.org/debug.pdf")

Wow, you crashed the Java VM, that's impressive ;) I haven't seen that for a while.

Sorry, but I don't think I have anything constructive to suggest... except to completely remove and then reinstall both java and azureus (make sure to do 'complete removal' in synaptic). This *might* help, but really, I have no idea what is wrong, I've never seen these problems before.

---

### Post by Angelbeast on 2007-05-04
> **kripkenstein said:**
> Wow, you crashed the Java VM, that's impressive ;) I haven't seen that for a while.

Sorry, but I don't think I have anything constructive to suggest... except to completely remove and then reinstall both java and azureus (make sure to do 'complete removal' in synaptic). This *might* help, but really, I have no idea what is wrong, I've never seen these problems before.

haha well you know...what can i say...when i do something i do it good :-)

so which one should i uninstall first, or would it make any difference?

---

### Post by kripkenstein on 2007-05-04
> **Angelbeast said:**
> haha well you know...what can i say...when i do something i do it good :-)

so which one should i uninstall first, or would it make any difference?

It shouldn't matter, you can uninstall them both at the same time.

---

### Post by stchman on 2007-05-04
> **Angelbeast said:**
> On winXP i was using azureus and got great speeds. On Uuntu i have tried azureus and the BitTorrent client that comes with it and have gotten mostly very slow speeds. My question is...Is there one that works well and gets good speeds "out of the box" for Ubuntu 64?

Did you make sure the proper ports on your router (if you use a router) are open?  If you dont opent eh port the download speed will suck.  I don't know if Azureus for XP and Azureus for Ubuntu have the same ports.  I personally prefer Ktorrent as it is very much like utorrent.

Also when you open the ports you need to specify it for a specific IP address.  I recommend doing a static IP for a machine you are going to use torrents a lot.  Make it the same IP as your XP OS.  Also use the openDNS numbers for your DNS if you can.

---

### Post by kalpik on 2007-05-04
try
```

rm ~/.azureus

```

---

### Post by Angelbeast on 2007-05-04
i can't do anything to the router settings...

i tried ktorrent....a 29mg file with 67 seeds started and went up to 22Kb/s then all the way down to 2Kb/s where it's staying...grrr

---

### Post by Angelbeast on 2007-05-04
> **kalpik said:**
> try
```

rm ~/.azureus

```

ron@ron-laptop:~$ rm ~/.azureus
rm: cannot remove `/home/ron/.azureus': Is a directory
ron@ron-laptop:~$

---

### Post by FakeOutdoorsman on 2007-05-04
To remove a directory with rm you need to add -r which stands for "recursive":

```

rm -r ~/.azureus

```

---

### Post by Angelbeast on 2007-05-04
> **FakeOutdoorsman said:**
> To remove a directory with rm you need to add -r which stands for "recursive":

```

rm -r ~/.azureus

```i uninstalled it from add remove apps

---

### Post by Angelbeast on 2007-05-04
okay i'm not a torent expert...i noticed all of the DHP collum had the red X's...that means they are blocked or something? are they supposed to be?

---

### Post by kripkenstein on 2007-05-05
Add-remove apps isn't enough, it might not delete the config dir in your home directory. So I think you should delete it as was suggested, if things still don't work.

I believe the X's only mean that you didn't get those peers through DHT, or that that particular peer doesn't support DHT. However, if you never see a peer without the X, then perhaps your own DHT isn't working. That might be a port problem.

---

### Post by Angelbeast on 2007-05-05
my downloads drift all the way down to ZERO and just stay there...i just don't get it...

---

### Post by kripkenstein on 2007-05-06
Post some data: what port are you using, is encryption enabled/forced, how many connections do you allow, how many connections do you see in your torrents (seeds/peers), etc.

---

### Post by Angelbeast on 2007-05-06
> **kripkenstein said:**
> Post some data: what port are you using, is encryption enabled/forced, how many connections do you allow, how many connections do you see in your torrents (seeds/peers), etc.

how do i get the info from the default torrent client?

---

### Post by kripkenstein on 2007-05-06
The poor results were using the default client? That is to be expected. Really, the only hope to get good results is if you use utorrent or Azureus, and to a lesser degree KTorrent.

---

### Post by Angelbeast on 2007-05-06
> **kripkenstein said:**
> The poor results were using the default client? That is to be expected. Really, the only hope to get good results is if you use utorrent or Azureus, and to a lesser degree KTorrent.

iwas getting poor results from all of them...everyone was telling me that i had to forward the ports on the router, which i don't have access to so i just went back to the default one...

---

### Post by kripkenstein on 2007-05-06
> **Angelbeast said:**
> iwas getting poor results from all of them...everyone was telling me that i had to forward the ports on the router, which i don't have access to so i just went back to the default one...

Well, if you are sure that the problem is port forwarding on the router, and you can't access the router, then I'm not sure there is much left for you to do. But then, I'm not an expert at port forwarding, perhaps someone else will have an idea.

---

### Post by Angelbeast on 2007-05-06
> **kripkenstein said:**
> Well, if you are sure that the problem is port forwarding on the router, and you can't access the router, then I'm not sure there is much left for you to do. But then, I'm not an expert at port forwarding, perhaps someone else will have an idea.

idon't know for sure that it was but that's whateveryone was saying *LOL* ... i put azureus back on to try it again and it'sshutting down soon as it starts again so i took it off but i'll have to wait till tomorrow to reinstall java coz i'm using it at the monent

---

### Post by flankker on 2007-05-06
> **Angelbeast said:**
> idon't know for sure that it was but that's whateveryone was saying *LOL* ... i put azureus back on to try it again and it'sshutting down soon as it starts again so i took it off but i'll have to wait till tomorrow to reinstall java coz i'm using it at the monent

i havent read all of this thread, but i would recommend deluge as a bittorrent client: [http://deluge-torrent.org/](http://deluge-torrent.org/)

i was having loads of problems with azureus, both related to java and to connection problems. i switched to deluge and now everything is good.

---

### Post by Angelbeast on 2007-05-06
i'll give it a try tomorrow...what kind of speeds do you get with it?

---

### Post by Angelbeast on 2007-05-06
man...it goes up to about 15Kb/s then all the way down to around 1 ... WTF ... this might make me go back to windows *LOL*

---

