---
title: "Does Gutsy tzdata package include Australian daylight savings time (DST) updates?"
date: 2008-03-11
forum: General Help
---

### Post by Joel Duckworth on 2008-03-11
Hi I'm wondering if the current Gutsy tzdata package has the updated database for Australia/Sydney

The current released package is 2007f-3ubuntu1. The changelog for package makes no mention of the updates. From my understanding this package build indicates that it is using the Olson database (tz/zoneinfo database) version 2007f. I've checked the history of the tz database and the updates for Australia were not included until 2007g.

I've run the following commands and the DST change info appears correct 
```
zdump -v /usr/share/zoneinfo/Australia/Sydney |grep 2008
/usr/share/zoneinfo/Australia/Sydney  Sat Apr  5 15:59:59 2008 UTC = Sun Apr  6 02:59:59 2008 EST isdst=1 gmtoff=39600
/usr/share/zoneinfo/Australia/Sydney  Sat Apr  5 16:00:00 2008 UTC = Sun Apr  6 02:00:00 2008 EST isdst=0 gmtoff=36000
/usr/share/zoneinfo/Australia/Sydney  Sat Oct  4 15:59:59 2008 UTC = Sun Oct  5 01:59:59 2008 EST isdst=0 gmtoff=36000
/usr/share/zoneinfo/Australia/Sydney  Sat Oct  4 16:00:00 2008 UTC = Sun Oct  5 03:00:00 2008 EST isdst=1 gmtoff=39600
```

I also believe there is a bug with Gutsy showing 'User defined' in /etc/timezone instead of the correct zone. To solve this I ran 
```

sudo dpkg-reconfigure tzdata

```
...and reselected my timezone. I believe it may have been like that since I installed (gutsy server ed.) I also think this maybe updated with existing gutsy-proposed tzdata packages.

So... can anyone shed light upon why the tz database version wouldn't indicate that the update for Australian DST is in the package yet it appears to be there. AND can anyone else confirm that their gutsy server install left them with "User defined" in /etc/timezone?

See Olson/tz/zoneinfo database info here:
[http://www.twinsun.com/tz/tz-link.htm](http://www.twinsun.com/tz/tz-link.htm)

---

### Post by Joel Duckworth on 2008-03-11
Sorry my mistake here. I was using apt-cache show tzdata to show the package version which seems to just list the original package version. Doing a dpkg -s tzdata I see that the version is updated to the expected level.

I'm still curious about the /etc/timezone file though. How could it have got left with "User defined"?

---

### Post by dcstar on 2008-03-12
> **Joel Duckworth said:**
> Sorry my mistake here. I was using apt-cache show tzdata to show the package version which seems to just list the original package version. Doing a dpkg -s tzdata I see that the version is updated to the expected level.

I'm still curious about the /etc/timezone file though. How could it have got left with "User defined"?

My file is fine.

---

### Post by Joel Duckworth on 2008-03-12
Are you using Server edition too? What about anyone who's installed server edition?

---

### Post by apadula on 2008-03-29
I have a mix of server and desktop, and I've had mixed results this weekend.

DST is supposed to end here next week, but my desktop and one of my servers have both decided to set the time back a week early.  Two other servers are ok though.  Looking at the packages and files I've got:

Desktop (Hardy) - /etc/timezone doesn't exist, tzdata package is 2008b-1ubuntu1
Server 1 (Gutsy) - /etc/timezone says "User defined", tzdata package is 2008a-0ubuntu0.7.10

Both of the above incorrectly set the time back 1 hour.

Server 2 (Gutsy) - /etc/timezone says "Australia/Sydney", tzdata is 2008a-0ubuntu0.7.10
Server 3 (Gutsy) - /etc/timezone says "Australia/Sydney", tzdata is 2007k-0ubuntu0.7.10

Both of the above have done everything right so far, see what happens next week when the time does really change.

Interesting that the one with the oldest tzdata package got it right, I'm guessing the /etc/timezone file has more to do with it than anything else.

Cheers,
Anthony

---

### Post by dibble5504 on 2008-03-30
I had problems with a Gutsy server that was set to User Defined in /etc/timezone.  Not sure why it was set to this.  Running sudo dpkg-reconfigure tzdata resolved the premature time change.

The other problem was with a Gutsy desktop.  tzdata was not updated despite having all current updates.  A manual install from [http://launchpadlibrarian.net/12604249/tzdata_2008a-0ubuntu0.7.10_all.deb](http://launchpadlibrarian.net/12604249/tzdata_2008a-0ubuntu0.7.10_all.deb) fixed it.

My dapper server and trixbox server worked OK.

Paul

---

### Post by Funkdancer on 2008-04-01
FWIW, my Dell 9300 is running 7.1, fully up to date patch wise, and the only time related change I'd done was to auto install the NTP daemon - this is from when saying to synch automatically (added ntp.internode.on.net) upon clicking adjust on the time in the tray.

And... My clock is currently running 1 hour behind. It should read 12:29 but it is saying 11:29.

So my thinking is that it changed early i.e. the DST changes hadn't made it through in time in form of a patch/update. I'm not a terribly advanced Linux user so wouldn't know to check for what dibble5504 did above (unless I stumbled upon it via Google).

---

