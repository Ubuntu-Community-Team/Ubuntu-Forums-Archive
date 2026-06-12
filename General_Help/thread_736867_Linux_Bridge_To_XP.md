---
title: "Linux Bridge To XP"
date: 2008-03-27
forum: General Help
---

### Post by ubtBaba on 2008-03-27
Hello,

I am inquiring about file sharing on Ubuntu.  I have successfully been able to do file transfers between my shared folders on my Ubuntu from my XP system.

My question is this, I have only one folder that I want my brother to access as a read-only folder from Vista [I am still figuring out how to use Vista's administrative functions ](*,)].  I have other folders that I am sharing for my personal use that I want only visible and accessible to me.  Is this possible?  Also, I am still new to the Linux world; if I need any other programs etc… please give me simple instructions.

Thanks In Advance

Also Linux Rocks :guitar:, it is more secure than my XP PC and I love it, but I still need to make a bridge to my other Windows systems.

---

### Post by renzokuken on 2008-03-27
this is all possible via **samba**. check out the samba wiki (google) or just google generally for guides on how to set permissions and access for folders via the smb.conf file

---

### Post by Xbehave on 2008-04-17
for the bridging you may want to try
[https://help.ubuntu.com/community/BridgingNetworkInterfaces?](https://help.ubuntu.com/community/BridgingNetworkInterfaces?)
& [https://help.ubuntu.com/community/NetworkConnectionBridge?](https://help.ubuntu.com/community/NetworkConnectionBridge?)
It can also be done with firewall configuration tool like guarddog or firestarer

and maybe vote for [this](http://brainstorm.ubuntu.com/idea/825/)
[[IMG]http://brainstorm.ubuntu.com/idea/825/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/825/)

---

### Post by bodhi.zazen on 2008-04-17
This kind of file sharing is quite easy and should work out of the box in a few short minutes.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

See the graphical configuration sections.

On windows, share a file.

On Ubuntu, go to places -> Network and you should see the share.

---

