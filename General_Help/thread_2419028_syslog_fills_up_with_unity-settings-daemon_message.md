---
title: "syslog fills up with unity-settings-daemon messages"
date: 2019-05-15
forum: General Help
---

### Post by alain-de-feyter on 2019-05-15
Since a few days my syslog fills up with messages like the following:
```
  May 15 19:10:18 alan9 unity-settings-daemon[2572]: 15/05/2019 19:10:18      104.248.71.227
  May 15 19:10:18 alan9 unity-settings-daemon[2572]: message repeated 2 times: [ 15/05/2019 19:10:18      104.248.71.227]
  May 15 19:10:18 alan9 unity-settings-daemon[2572]: 15/05/2019 19:10:18      101.230.200.173
  May 15 19:10:18 alan9 unity-settings-daemon[2572]: 15/05/2019 19:10:18      104.248.71.227
  May 15 19:10:18 alan9 unity-settings-daemon[2572]: message repeated 9 times: [ 15/05/2019 19:10:18      104.248.71.227]
```
The size of syslog grows to gigabytes

Looks like 104.248.71.227 tries to connect? 
The main problem site is the 104.248.71.227. I cannot open it in a browser.
The 101.230.200.173 is less frequent, but that one can be opened in a browser. it says "f*** off".
I feel threatened, but I cannot stop the flood of messages. 
Any help?

---

### Post by Rubi1200 on 2019-05-17
Hi,

What version of Ubuntu are you currently using?

What event caused you to check syslog in the first place?

Are you using SSH or any other remote software, do you have ufw enabled?

The more information you can think of to help, the better we can advise you.

Thanks.

---

### Post by DuckHook on 2019-05-17
In addition to answering Rubi1200's questions (and please first answer all of them—they are important):

[list=1]
[*]Did you install anything from outside the repos around the time that your logs started getting spammed?
[*]Did you visit or were you redirected to any new, strange sites at this time?
[*]Did you receive any odd e-mail or other message at this time that you opened or looked at?
[*]Do you recall any other unusual computing event that coincided with this behaviour?
[*]What uncommon apps do you run? Example: do you mine crypto-currency, etc?
[/list]

---

### Post by alain-de-feyter on 2019-05-19
I am running ubuntu 19.04, using the unity desktop, because the gnome gets stuck in a login loop, but that is another problem to be addressed later.
I checked syslog, because there was no space left on my (separate) home partition. This was caused by the ever growing syslog.
I think the cause of this trouble was about a month ago. I experimented then with remote desktop and vnc. for that I opened port 5900. 
A few days ago some creep must have bombarded my port 5900. the attack was not successful sofar and of course I closed port 5900. This stopped the flood. 
I use ssh, but on another port. ufw is enabled and I have only a few ports open.
I am safe for now, but what if in the future I want to play with vino-server and vnc again?  
Yesterday I ran mtr on 104.248.71.227. The last line in the chain was digitalocean-ic-336107-palo-b22.c.telia.net. I filed an abuse report on the site of Digital Ocean, because I suspect that their site has been used as hub.
to DuckHook: I do know the risks you mention, so the answer to your 5 question is negative, but thanks anyway for the warnings. Even the best can make errors (proof of this: I have already made errors :) ).

---

### Post by Rubi1200 on 2019-05-19
I've never used remote software, SSH or anything even close (mostly because I see too many posts about hacks or potential hacks but also because I just don't need it with my setup).

That said, I believe there are plenty of guides out there on how to safely and securely use these programs.

Forum member TheFu has examples on his profile page:
[https://help.ubuntu.com/community/SSH/OpenSSH/Advanced?action=show&redirect=AdvancedOpenSSH](https://help.ubuntu.com/community/SSH/OpenSSH/Advanced?action=show&redirect=AdvancedOpenSSH)
[https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

And of course there are more.

As things stand, are you certain your system is now secure from threat?

I hope so :-)

---

### Post by DuckHook on 2019-05-19
You obviously know your stuff so no need to dwell on the basics.

VNC and its default port 5900 are infamous attack vectors for the hordes of scumbags looking to compromise the unwary. It is no surprise at all that your syslog got spammed so quickly. There must be thousands of robots scanning that port constantly. When a receptive IP is found, these robots will then try a brute force password attack that can get so intense that the deluge resembles a DoS attack.

The measures you have taken are good ones, especially reporting the suspect site. I wish more people were as network savvy as you. It would help police the Internet a bit better than it curently is.

Whois confirms two of your sites as hosted by Digital Ocean. It also shows one of your suspect sites to originate from China. Not that all China sites are bad, but a deluge of IP connection requests from this region is another red flag.

I no longer use VNC because of exactly these issues. I find that it is not that difficult to use alternate methods. Where VNC is absolutely necessary—say, as required for a remotely based teaching professional—the proper way to implement it is to tunnel your VNC connection through ssh. ssh itself must be set up properly with password disabled, a proper high-entropy key, and preferably on a high non-standard port. You could also implement port knocking, though things could get complicated for newbies and other users.

Instructions for ssh tunneling are all over the Internet, but a typical set is: [https://askubuntu.com/questions/304017/how-to-set-up-remote-desktop-sharing-through-ssh](https://askubuntu.com/questions/304017/how-to-set-up-remote-desktop-sharing-through-ssh)

It is unlikely that you have been compromised. You seem to be quite tech aware and security conscious. However, it would be a good idea to audit your system now. Keep an eye on your logs for the next few days, especially syslog and auth.log.

Good luck and Happy Ubuntu-ing.

---

### Post by DuckHook on 2019-05-19
It seems that Rubi1200 and I posted concurrently with almost identical advice. Great minds and all that&#8230;

---

### Post by alain-de-feyter on 2019-05-20
Thanks for your comment, DuckHook. I needed that confirmation of my suspicion of port 5900 and VNC. Next time I experiment with remote desktop, I will take your advice into account. My ssh connection is secure, and from the beginning indeed using a different port number than 22.
I will surely continue Ubuntu-ing happily. Being retired, I am a rather lonesome developer, but luckily, there is always the Ubuntu Forum!

---

