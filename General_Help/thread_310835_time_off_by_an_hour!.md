---
title: "time off by an hour?!?"
date: 2006-12-01
forum: General Help
---

### Post by mark2741 on 2006-12-01
Ever since doing a clean install of Edgy a month ago I have had this problem with my clock - it's always an hour behind my local time (I'm in Eastern USA - Philadelphia area to be exact). I have checked a hundred times and I have the time zone set to eastern us/new york. I have set it to both synchronize with an internet server and also manual and either way, once I reboot I get behind an hour! Makes no sense. This never happened with Dapper, just since moving to a clean install of Edgy.

Any help is greatly appreciated in trying to fix this.

---

### Post by ciscosurfer on 2006-12-02
Do you dual-boot, that is, do you have Windows installed as well?  I've heard of time issues just like this in dual-boot scenarios.  When you installed, did you set the time to include or exclude setting it via UTC?  Do you hae daylight saving time enabled?  Sorry if this wasn't any help, just some thoughts.

Do you use a router?  Do you have the router set up to sync with a time server as well?  If so, it may be conflicting with the time sync you've set up in Edgy.

And I seriously doubt this will help b/c I don't see how it would necessarily effect anything, but you can reset the sudo timestamp by issuing sudo -k and/or sudo -K (again, I think that fix is for future timestamp problems in the terminal, but thought I'd throw it out anyway).

I'm just throwing out guesses...

---

### Post by mark2741 on 2006-12-02
Although none of your suggestions were exactly the cause, it did get me to think about the issue more and I do recall it started right around the daylight savings time change.

So I rebooted the system and went into BIOS and sure enough, the system clock was off by an hour. I don't remember ever having to change it for daylight savings time before though so I'm a little worried perhaps my battery might be going on the motherboard? Anyways, after bumping the bios time up an hour and rebooting into ubuntu (I do dual-boot with windows but I haven't booted into windows in months) the time is right again.

So thanks!

However this shows me that Ubuntu's clock is hard set to whatever the BIOS's clock is set to at startup. So even if I change it in the time preferences in Ubuntu, the BIOS time overrides those settings, which is not a good way to do it IMO.

---

### Post by ciscosurfer on 2006-12-02
Ubuntu will set its internal system clock to your BIOS's hardware clock, so this makes sense.

Perhaps it's time to replace that battery?

---

### Post by wpshooter on 2006-12-02
I have noticed that the Ubuntu O/Ss seems to have some problems in that according to what I have experienced, they seem at times to alter the BIOS time set and you can have to correct time on the O/S and the incorrect time in the BIOS and also vis versa.  I think they still have some work to do in this area.

---

