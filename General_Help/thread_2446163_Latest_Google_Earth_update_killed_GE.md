---
title: "Latest Google Earth update killed GE"
date: 2020-06-25
forum: General Help
---

### Post by WB0HYQ on 2020-06-25
Google Earth has always run just fine on my XFCE/XUbuntu 18.04 but today, GE announced there was an update, and I downloaded and installed it. Now, when I start it from a terminal, I get this:

bill@bill-UBU:~$ google-earth-pro
/usr/bin/google-earth-pro: line 21: 10494 Illegal instruction     (core dumped) "$(dirname "$(readlink -f "$0")")/googleearth-bin" "$@"

If I start it from Cairo Dock, I get nothing. Using System monitor, I see it trying to start, then it turns red and dies (probably from the illegal instruction). Is this something messed up in the version they offered, or some other underlying problem? I use GE extensively and can't be without it for long.

Bill

---

### Post by WB0HYQ on 2020-06-25
More info: I have since downloaded 7.3.2 and re-installed it after completely removing version 7.3.3. Older version runs just fine, so this is a problem for the Google People I guess.

Bill

---

### Post by Yellow Pasque on 2020-06-26
[https://support.google.com/earth/thread/48368936?hl=en](https://support.google.com/earth/thread/48368936?hl=en)
There doesn't seem to be a resolution yet. Good luck...

---

### Post by lvm on 2020-06-26
I also have this problem and it seems to be related to older AMD CPUs - mine is AMD Phenom(tm) II X4 975. Probably compiled using modern CPU instruction set unsupported by older CPUs.

ps until this is fixed, any advice on how to avoid 'new version available' nagging is welcome.

---

### Post by WB0HYQ on 2020-06-26
LOL. I have the "new version available" nag screen as well. I've scoured the Options, but there isn't any "don't check for updates" option I can find. It is apparent from the Google forums that they are aware of the problem, but aren't inclined to fix it. But, since no Google employees are present on any of the forum panels, one never knows. My system CPU is: AMD Athlon(tm) II X3 460.

Bill

---

### Post by pqwoerituytrueiwoq on 2020-06-26
7.3.3.7721 on xubuntu 20.04

[LIST]
[*]Works for me on
[LIST]
[*]Ryzen 5 3600 / RX 580
[/LIST]

[*]Does not work
[LIST]
[*][Intel Pentium Processor B970]("https://ark.intel.com/content/www/us/en/ark/products/63915/intel-pentium-processor-b970-2m-cache-2-30-ghz.html")
[LIST]
[*]Opens but fails to render anything
[/LIST]
[/LIST]

[*]Need to test (should be able to do this this evening)
[LIST]
[*]Phenom II 965 / GT 430
[/LIST]
[/LIST]

---

