---
title: "Unable to update via apt-get, aptitude, synaptic or update manager"
date: 2012-11-12
forum: General Help
---

### Post by oxman on 2012-11-12
All of a sudden my connections to the repositories are being refused. I have changed various settings in the repositories etc. No joy. Fire wall is off in the router. Unable to update via apt-get, aptitude, synaptic or update manager. Did searches on the problem and found nothing that helped. I just don't know where to go from here.


Any help is appreciated.

---

### Post by Mr_JMM on 2012-11-12
Have you tried changing servers under Software Sources? Could be the current one is down.

---

### Post by oxman on 2012-11-12
Yes, I changed servers also. No joy. Thanks for the reply.

---

### Post by ibjsb4 on 2012-11-12
Any corruption going on in your sources list?

cat /etc/apt/sources.list

---

### Post by gerowen on 2012-11-12
Tried

sudo apt-get -f install

in the terminal to make sure nothing is broken?

---

### Post by oxman on 2012-11-12
cat /etc/apt/sources.list  No irregularities that I can see.

sudo apt-get -f install No fixes needed according to cli.

Thanks for the replies.

---

### Post by thirnick on 2012-11-12
did you try bypassing your router?

---

### Post by ibjsb4 on 2012-11-12
When you do an apt-get update are you getting error 404?

---

### Post by raja.genupula on 2012-11-12
> **oxman said:**
> All of a sudden my connections to the repositories are being refused. I have changed various settings in the repositories etc. No joy. Fire wall is off in the router. Unable to update via apt-get, aptitude, synaptic or update manager. Did searches on the problem and found nothing that helped. I just don't know where to go from here.


Any help is appreciated.
  This information can't help us much to have a better look on your issue . give us the results of ```
sudo apt-get update
```

---

### Post by oxman on 2012-11-17
My apologies for the delay. I was seriously sidetracked. I am still unable to update upgrade my system.

---

### Post by oxman on 2012-11-19
I just found out that Hughes net Gen 4 users in my area are having this same problem. Any help is appreciated

---

### Post by arpanaut on 2012-11-19
Post to the forum the output from the terminal of
```
sudo apt-get update && sudo apt-get upgrade
```

Those results may give us a clue as to what the problem is,
otherwise people here will just be guessing.

Is your internet connection working correctly otherwise?
Are you connected through a proxy?

---

### Post by oxman on 2012-11-19
Thank  you for the reply. I believe the issue is definitely my new hughesnet Gen4 satellite hookup. I am currently at another location and the update went quite smoothly. I will do some further checking on this. The problem isn't solved since I have two PCs at home that are behaving the way this laptop did.

---

### Post by illuminaughty50187 on 2012-12-03
+1 my hughesnet doesn't let anything work (relating to updates or installs) in ubuntu. Im gonna start a new topic.

---

### Post by Neon John on 2013-01-06
> **illuminaughty50187 said:**
> +1 my hughesnet doesn't let anything work (relating to updates or installs) in ubuntu. Im gonna start a new topic.

The problem is with the web accelerator in the new Gen4 modem.  After days of research, I finally found the definitive answer:

[http://community.myhughesnet.com/hughesnet/topics/can_i_enable_disable_my_web_acceleration_myself](http://community.myhughesnet.com/hughesnet/topics/can_i_enable_disable_my_web_acceleration_myself)

My initial problem was that the upgrade broke SubVersion.  Later I found that it broke Synaptics and Update service. The thing all three have in common is using HTTP on port 80.

turning off the accelerator make SubVersion Synaptics and Update work but now the web is sloooow.  This is my short term solution.  My long term solution is to cancel my contract and go to Vianet.

John

---

### Post by RogerInMD on 2013-02-14
Just found out the same thing after pulling my hair out for days.  Switched off Web Acceleration on the HN1000 and the failed fetch (111 Connection refused) disappeared.  After switching on some debug settings for **apt**, I think it's due to the fact the the HughesNet proxy does not properly allow HTTP keep-alive connections for port 80 fetching.  Or that's my best guess.

Seen other issues with Gen4 in loading multi-content pages that likely also use the keep-alive feature.  Though so far general browsing doesn't seem too bad.

Upgrade from 10.04 to 12.04.1 finally seems to be working. :D

Roger

---

### Post by Neon John on 2013-02-14
> **RogerInMD said:**
> Just found out the same thing after pulling my hair out for days.  Switched off Web Acceleration on the HN1000 and the failed fetch (111 Connection refused) disappeared.  After switching on some debug settings for **apt**, I think it's due to the fact the the HughesNet proxy does not properly allow HTTP keep-alive connections for port 80 fetching.  Or that's my best guess.

Roger

An update from my end.  I raised enough hell both on the web and off that I got the attention of someone at Hughesnet.  A lady from executive customer service contacted me.  After several phone calls and emails, I got to talk to an actual developer.  I sent him a tcpdump of a refused session.  He admitted that the accelerator is broken and that fixing it is a fairly high priority task.  The lady told me she'd notify me when the fix is in.

Roger, thanks for doing your debugging.  I'm about to ping the lady at executive customer support for a status report and I'll pass this along.

Meanwhile I'm green with envy at my next door neighbor.  I didn't have a shot at the Exede bird (trees) but she did.  She had it put in and is consistently getting 13Mbps download and 1.2Mbps upload.  Twice what I've ever seen with Hughesnet.  This is using [http://testmy.net](http://testmy.net).

I still have an open ticket for slow upload speeds, about 128kbps but that's for another post :-)

John

---

