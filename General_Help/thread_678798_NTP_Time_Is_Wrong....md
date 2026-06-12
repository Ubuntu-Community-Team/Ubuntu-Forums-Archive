---
title: "NTP Time Is Wrong..."
date: 2008-01-26
forum: General Help
---

### Post by CarlosinFL on 2008-01-26
I enabled / installed NTP on my 7.10 system and I set my Ubuntu PC to poll time from my local NTP server 192.168.1.1 however my time is like 5 hours off exactly. I don't know how to force a sync and I checked the time on my NTP box and my laptop and they're all correct.

Anyone know how I can force my PC to try to sync with the NTP server? Or simply make sure the time is correct?

---

### Post by danwood76 on 2008-01-26
it sounds like a timezone issue.
possibly your NTP is set wrong or your PC is, this would cause the +5 hours shift.

regards,
Danny

---

### Post by IcemanV9 on 2008-01-26
To check/fix the timezone issue, type this in the terminal:
```
tzconfig
```
There is a good [[COLOR="DarkOrange"]wiki[/COLOR]]("https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=ChangeTimezoneHowto") on timezone if you want to know more.

---

### Post by CarlosinFL on 2008-01-26
That command does not appear to work on my system...

When I go up to the clock and select **"Adjust Date and Time"** it asks me for my password and then shows **America/New York** which is EST (-5). Why would my time zone be messed up or why would that even matter if I tell it to sync with my NTP server which is set to the correct time. Any more suggestions?

```
root@tunafish:~# tzconfig
-su: tzconfig: command not found
root@tunafish:~# apt-cache search tzconfig
```

---

### Post by cprofitt on 2008-01-26
> **Carlwill said:**
> That command does not appear to work on my system...

When I go up to the clock and select **"Adjust Date and Time"** it asks me for my password and then shows **America/New York** which is EST (-5). Why would my time zone be messed up or why would that even matter if I tell it to sync with my NTP server which is set to the correct time. Any more suggestions?

OK...

Lets say your NTP server is 'set' to the correct time, but is set with a timezone of GMT. Then if your 'desktop' is set to GMT-5 and it syncs with your NTP server you would be five hours off. Is your NTP server set to sync to any other servers on the outside? What happens when you set your 'desktop' to sync to an outside NTP server?

---

### Post by CarlosinFL on 2008-01-26
As you can see from the attachement below, my NTP server is set with the proper time and shows that it is set EST. The NTP server is my Firewall and it connects to pool.ntp.org just fine. Then everyone on my LAN simply points to the Firewall which is designated as an NTP server.

I then removed my Firewall IP from the list of server to sync with on my Ubuntu PC and then added the following screenshot I provided. Time still shows wrong after waiting one minute...

---

### Post by fragos on 2008-01-26
NTP is probably not checked that freequently.  Reboot and it should synchronize then.  Your problem is that you've ajusted the time twice.  NTP assumes it's syncing at GMT which is then adjusted for local time.  Change your PC's to sync will the actual NTP servers.

---

### Post by CarlosinFL on 2008-01-26
Nah - I have rebooted and also reloaded the NTP service which in my opinion is better than rebooting. You should not have to reboot a Linux machine for one particular service to work unless you have a new kernel.

```
/etc/init.d/ntp restart
```

Something is not right with NTP however I don't what ...

---

