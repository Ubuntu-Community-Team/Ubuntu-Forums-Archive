---
title: "scheduled speedtest through cron"
date: 2015-02-10
forum: General Help
---

### Post by TheVolamoot on 2015-02-10
I've moved to a new ISP where i am paying much more for much faster speed however I noticed that the speeds vary widely (often well below the minimum data-rate they claim I should always get.) I am looking for some way to schedule the output of a speedtest performed through cron to be emailed to me. I found a few scripts that allow for me to do a speedtest through command line but i am unable to store those results in an understandable way. Any help would be greatly appreciated.

---

### Post by ajgreeny on 2015-02-10
Use the command```
date >> speed.txt && wget -O - https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py | python >> speed.txt
```in your cron job to run as often as you want and the text file speed.txt will show the time of each execution of that command with incremental text entries for each one.  You can then show the output as evidence of the speeds you are actually getting and there is no need to email it to yourself as it will be sitting in your /home.

  Here's my text file having just done this at 5 min intervals.
```
Tue Feb 10 19:26:46 GMT 2015
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Orange Home UK (2.26.1.211)...
Selecting best server based on latency...
Hosted by RapidSwitch (Maidenhead) [57.94 km]: 22.843 ms
Testing download speed........................................
Download: 19.36 Mbits/s
Testing upload speed..................................................
Upload: 4.83 Mbits/s
Tue Feb 10 19:31:46 GMT 2015
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Orange Home UK (2.26.1.211)...
Selecting best server based on latency...
Hosted by RapidSwitch (Maidenhead) [57.94 km]: 20.829 ms
Testing download speed........................................
Download: 32.16 Mbits/s
Testing upload speed..................................................
Upload: 3.84 Mbits/s
```

Just out of interest, the speeds I get from running this command line version are nearly always slower than when I use the website in my browser which has just given me the results shown in my attachment.  I have no idea how or why.

---

### Post by TheVolamoot on 2015-02-10
thanks for the guide and easy install scripting... it works perfectly. I can't believe I didn't find out about it earlier... I noticed as well the speeds shown on the web version and this command line interfaces differ. Hopefully they fix it in the future but for the time being it works just as needed. Thanks Again!

---

