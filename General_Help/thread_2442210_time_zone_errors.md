---
title: "time zone errors"
date: 2020-04-30
forum: General Help
---

### Post by Skaperen on 2020-04-30
i was testing changes to the script i test new installs with to get ready to do a full install of 20.04.  i'm still on 18.04, so i'm running the tests of the script in 18.04 to be sure it runs right.  but it showed some problems with my system clock and time zones.  the time zones were still wrong and the system clock is off by one hour.  it shows UTC one hour behind (e.g. at 01:20 it showed 00:20).  the TZ environment variable was not set, so i changed things to set it to EST, where i am, and rebooted.  now i see that the system clock is behind by one hour, so i will need to see why *ntp* isn't getting that right (no idea why it would think UTC-1 would be right).  anyway, why i am posting here is another problem: time zone settings are acting goofy.  most of the time zones are giving incorrect times.  here is what i get:
```

lt2a/forums /home/forums 1> bash -c 'for z in UTC EST EDT CST CDT MST MDT PST PDT;do export TZ=$z;date;done'
Fri May  1 01:40:35 UTC 2020
Thu Apr 30 20:40:35 EST 2020
Fri May  1 01:40:35 EDT 2020
Fri May  1 01:40:35 CST 2020
Fri May  1 01:40:35 CDT 2020
Thu Apr 30 18:40:35 MST 2020
Fri May  1 01:40:35 MDT 2020
Fri May  1 01:40:35 PST 2020
Fri May  1 01:40:35 PDT 2020
lt2a/forums /home/forums 2>

```
well, at least MST gives me the correct time.  i used to live in Dallas, Texas and would be using CST, there.  maybe.  if it worked right.  is there something i need to reinstall?

**Feli&#265;a Tago de Majo**

---

### Post by norobro on 2020-05-01
Take a look at "man 8 tzselect"> The output is suitable as a value  for  the TZ environment variable.None of the values that you are using are valid except for UTC and MST.```
$ bash -c 'for z in UTC America/New_York America/Chicago America/Denver MST America/Los_Angeles;do zdump $z; done'
UTC  Fri May  1 19:14:02 2020 UTC
America/New_York  Fri May  1 15:14:02 2020 EDT
America/Chicago  Fri May  1 14:14:02 2020 CDT
America/Denver  Fri May  1 13:14:02 2020 MDT
MST  Fri May  1 12:14:03 2020 MST
America/Los_Angeles  Fri May  1 12:14:03 2020 PDT
```

---

### Post by Skaperen on 2020-05-01
why does EST work?

---

### Post by norobro on 2020-05-01
[COLOR=#000000]I stand corrected.

None of the values that you are using are valid except for UTC, EST and MST

[/COLOR]From the file 'backward' in the archive tzdata2020a.targz from here: [https://www.iana.org/time-zones](https://www.iana.org/time-zones)
> # From Arthur David Olson, 2005-12-19
# We generate the files specified below to guard against old files with
# obsolete information being left in the time zone binary directory.
# We limit the list to names that have appeared in previous versions of
# this time zone package.
# We do these as separate Zones rather than as Links to avoid problems if
# a particular place changes whether it observes DST.
# We put these specifications here in the northamerica file both to
# increase the chances that they'll actually get compiled and to
# avoid the need to duplicate the US rules in another file.


# Zone    NAME        STDOFF    RULES    FORMAT    [UNTIL]
Zone    EST         -5:00    -    EST
Zone    MST         -7:00    -    MST
Zone    HST        -10:00    -    HST
Zone    EST5EDT         -5:00    US    E%sT
Zone    CST6CDT         -6:00    US    C%sT
Zone    MST7MDT         -7:00    US    M%sT
Zone    PST8PDT         -8:00    US    P%sTYou can roll your own:```
$ bash -c 'for z in UTC UTC5 UTC-5  EST5 CST6 MST7 PST8 EDT4 CDT5 MDT6 PDT7;do zdump $z; done'
UTC  Sat May  2 02:04:24 2020 UTC
UTC5  Fri May  1 21:04:24 2020 UTC
UTC-5  Sat May  2 07:04:24 2020 UTC
EST5  Fri May  1 21:04:24 2020 EST
CST6  Fri May  1 20:04:24 2020 CST
MST7  Fri May  1 19:04:24 2020 MST
PST8  Fri May  1 18:04:24 2020 PST
EDT4  Fri May  1 22:04:24 2020 EDT
CDT5  Fri May  1 21:04:24 2020 CDT
MDT6  Fri May  1 20:04:24 2020 MDT
PDT7  Fri May  1 19:04:24 2020 PDT
```Threw in UTC-5 to show that "+" is implied but is really minus ;)

---

### Post by Skaperen on 2020-05-04
i can understand UTC being allowed and it is unique but why are EST and MST allowed but CST and PST not allowed?  did Boston and Denver pay a ransom that Dallas and Seattle refused to pay?

---

