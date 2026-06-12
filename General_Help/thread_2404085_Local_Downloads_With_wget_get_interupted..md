---
title: "Local Downloads With wget get interupted."
date: 2018-10-19
forum: General Help
---

### Post by guillaumesoucy on 2018-10-19
Hi, 


I have several security cameras and I get the video streams from them using wget on a Ubuntu 18.04 vm running locally in my datacenter. The streams is downloading from midnight and get cut at 11:59 PM and get restarted again at midnight with a set of cronjob. But theses local streams get often interrupted randomly and one time on two doesn't start at all .  I get also stream from cameras installed in two other buildings in our town, the data pass by the internet, there absolutely no issues with them, only with locals ones. 

This is the cronjob file:

```

##
#
#
#The "Killer".
59 23 * * * pkill wget
#
#The "Recorders".
0 0 * * * cd /mnt/disk1/motions/camera-001-01/2018/ && wget -t 0 http://192.168.2.254/video.cgi --user=admin --password=*********
0 0 * * * cd /mnt/disk1/motions/camera-002-01/2018/ && wget -t 0 http://192.168.2.253/video.cgi --user=admin --password=*********
0 0 * * * cd /mnt/disk1/motions/camera-003-01/2018/ && wget -t 0 http://192.168.2.252/video.cgi --user=admin --password=*********
#

```

Even if I put a ```
-t 0
``` , the security camera streams refuse to be retried.

Thanks, 

Guillaume

---

### Post by TheFu on 2018-10-20
What do the system logs show?
Have you tried swapping the camera around to see if the problem follows the camera?
Any logs you can see on the cameras?

---

### Post by guillaumesoucy on 2018-10-23
Hi, 

The wget-log files are empty (0 byte), I do camera swapping one time because the foot who maintain one of the cameras on the wall was broken because of a drop. 

And also how I can see the logs on D-Link cameras?


Thanks,


Guillaume

---

### Post by HermanAB on 2018-10-23
Hmm, add a -c?

---

### Post by guillaumesoucy on 2018-10-23
This is the first thing I tried but it doesn't make any difference, unfortunately.

---

### Post by TheFu on 2018-10-23
So ... no system logs then?

---

### Post by guillaumesoucy on 2018-10-23
No the wget-log file appear to be empty, I understand this can help a lot. I will start the wget process manually to get a log and I will post the link here. 

I will run them for 24 hours or until they fail and get back to you. 


Thanks guys!


Guillaume

---

### Post by HermanAB on 2018-10-24
You could also run tcpdump to see what happens when things stop - are there retries - router errors...

---

### Post by guillaumesoucy on 2018-12-17
Hi Herman, 

But just a question, if the process ran for hours before getting interrupted and considering I'm not always at my desk to watch the activity captured in the terminal, I try to send the output to a .log file using this: ```
tcpdump port http -i ens18 -w capture-from-2018-12-17_18-12-00.log
``` 

But I obtain a capture-from-2018-12-17_18-12-00.log file with unreadable characters.
. 

Thanks, 

Guillaume

---

