---
title: "can't connect to MSN network"
date: 2006-08-23
forum: General Help
---

### Post by precinto on 2006-08-23
Hello everyone.

It's been a week or so since I can't connect to my MSN IM accounts. It doesn't work neither with gaim nor aMsn nor Kopete. And I really don't know where to look in order to solve it. I don't think I've changed or updated anything related to that for a while.

I'm using aMsn and Kopete versions from the dapper repositories and gaim (beta 3) from debuntu repository.

Thanks for your help.

---

### Post by ThrashJazzAssassin on 2006-08-23
Can you log-in here [http://webmessenger.msn.com]("http://webmessenger.msn.com")?

If that works then Gaim/Kopete/etc are probably getting blocked with a firewall. Do you have a router or a firewall app installed?

---

### Post by precinto on 2006-08-23
Yes, I can use Web Messenger. I also tried using http method in the gaim configuration.

I have a router, but I never had to set it up for msn connection. As for a firewall... just moblock, but it has always let me connect as well.

---

### Post by William the Conquerer on 2006-08-29
> **precinto said:**
> I have a router, but I never had to set it up for msn connection. As for a firewall... just moblock, but it has always let me connect as well.

well, I haven't been able to connect either for a week or so but I was too lazy to do anything about it ;).  Funny you should mention moblock though...  I stopped it and tried to reconnect on gaim and as long as I don't use the http method (it was fixed in the newest gaim, but it's not gonna be in the dapper repositories of course...) I can connect fine =).  SOOO...  obviously moblock is...  blocking it, so maybe if there's a way to flag messenger.hotmail.com as being ok we could have our cake and eat it too (moblock and msn)...  I'll post if I find anything else helpful.

oh, and to stop moblock open gnome-terminal and type this:
```
sudo /etc/init.d/moblock stop
```

---

### Post by William the Conquerer on 2006-08-29
actually, it's pretty easy to fix...

> **pelle.k said:**
> There is a blocklist updater in /etc/cron.daily/moblock-nfq (moblock-ipq if that is what you installed...)

1. 'sudo nano /etc/cron.daily/moblock-nfq'
go to line 34 where you will find > BLOCKLISTS="ads-trackers-and-bad-pr0n level1 level2  **Microsoft**  spyware " < add remove what you see fit.
Check this out [http://www.bluetack.co.uk/modules.php?name=FAQ&myfaq=yes&id_cat=6&categories=Blacklists+FAQ](http://www.bluetack.co.uk/modules.php?name=FAQ&myfaq=yes&id_cat=6&categories=Blacklists+FAQ)

2. ctrl + x to save it. Wait for cron to update, OR if you are in a hurry, just do 'sudo /etc/cron.daily/moblock-nfq' :)

when you have /etc/cron.daily/moblock-nfq open and are at line 34 take out "Microsoft" run ```
sudo /etc/cron.daily/moblock-nfq
``` and that should be it...

---

### Post by dyntryx on 2007-10-20
I know this post is old, but just as future reference in searches, etc...

If moblock is blocking MSN messenger, there is no way to whitelist by ip *and* port.  You can only whitelist the port or remove the ip from the blocklists.

The simplest way to allow MSN messenger would be to whitelist the port.  To do this, open the file
```
/etc/moblock/moblock.conf
```
in your favorite text editor.  Find the line that reads
```
#WHITE_TCP_OUT=""
```
... or perhaps it may be something like ...
```
WHITE_TCP_OUT="80 443"
```
If there is a *#* at the beginning of the line remove it.  Then add the number (port) *1863* somewhere between the quotes, so the line looks more like
```
WHITE_TCP_OUT="80 443 1863"
```
This is the port MSN uses to connect.  This will allow you to connect to MSN messenger--using Pidgin or Kopete or your messenger or choice--while still blocking Microsoft on all the other ports.

Hope that helps someone.

**Edit:**
I forgot to mention that after you edit your moblock configurations, you--of course--have to restart moblock.  Type this at the console:
```
sudo moblock-control restart
```
Now the settings will take effect. :)

---

### Post by MemoryDump on 2007-10-23
I can't seem to connect to any IM network using aMSN.. but I can with Pidgin.. any other possibilities as to why it wouldn't work? I don't have moblock installed.

---

### Post by MemoryDump on 2007-10-23
> **MemoryDump said:**
> I can't seem to connect to any IM network using aMSN.. but I can with Pidgin.. any other possibilities as to why it wouldn't work? I don't have moblock installed.
hmm.. now it's working remotely when I'm connected via a NX client.. could it be an issue with the visual enhancements conflicting with aMSN?

---

### Post by AimarZar08 on 2007-11-16
I found this very helpful, thanks!

---

### Post by jonwe195 on 2008-01-19
I can't even connect to [http://webmessenger.msn.com](http://webmessenger.msn.com)! It seems as though MSN blocked me or something...Pidigin alternates between saying that I was disconnected (reading error) and that the service is not available. webmessenger.msn.com doesn't load anymore either...and I don't understand why everybody is talking about moblock, 'cos it's not even in the default repositories of Ubuntu (I don't have it anyways...).

If anybody has the slightes idea what could be my problem, I would be grateful for any help! I think (but I'm not sure) my problems started when I installed KDE 4.0 (by using the ppa repositories as explained at the [kubuntu site]("http://kubuntu.org/announcements/kde-4.0.php"))

---

