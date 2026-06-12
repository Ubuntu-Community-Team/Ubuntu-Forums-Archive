---
title: "Cron fails to execute"
date: 2008-03-22
forum: General Help
---

### Post by mag3966 on 2008-03-22
I have read the man pages on cron and have googled around, but could not seem to get cron right.  
My crontab looks like:

37 11 * * * echo "Good Morning My Fair Feathered Friend"

This is to print the quoted material in the terminal screen at 11:37 am every day.

I setup the crontab by typing crontab -e and edited the file using my default editor gedit. (I have also switched the editor to nano and also vi, but the same results happen).  I have typed crontab -l and it shows that the cron is set.  I have also checked /var/spool/cron/crontabs/myusername (as root in init 1 as it appears locked otherwise) and it also shows that the crontab is set to run.  Yet when the time comes, it never runs and never does anything.  

I have tried other commands to test cron in the crontab such as 45 14 * * * ping google.com.  However, cron never seem to run at the time requested.

Any thoughts are appreciated.  Thanks,

mag3966

P.S.  I am a bit of a newbie to ubuntu.

---

### Post by mag3966 on 2008-03-22
Any Ideas?

---

### Post by munkyeetr on 2008-03-22
I am by no means any expert either, and I tried something like you did:
```

33 20 * * * echo "Good evening."

```

and it did not print to the terminal, however when I changed it to output into a file:
```

34 20 * * * echo "Good evening." > ~/Desktop/greeting.txt

```

it worked fine, creating the file and outputing the text into it.

I also tested using ping:
```

38 20 * * * ping www.google.ca > ~/Desktop/ping.txt

```
and it worked fine also, outputting into the file:
```

PING www.l.google.com (209.85.173.103) 56(84) bytes of data.
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=1 ttl=244 time=23.6 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=2 ttl=244 time=23.4 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=3 ttl=244 time=23.7 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=4 ttl=244 time=23.3 ms

```

There may be an issue (or other way to) print(ing) to the terminal, as I said, I am also no expert, but if you are just trying to make sure that crontab is working at the right time, test it outputting to files.

---

### Post by mag3966 on 2008-03-26
Thank you Munkyeetr for your reply.  I was able to output the command to a file.  Apologies for not responding sooner, but I had a bit of a crisis here at the house.

However, I am having an additional issue.  What I am attempting to do is to ssh into a remote machine (a vista box running cygwin) and then to run a command on that box for it to rsync its files to the linux box from which I have just run the ssh command.  Essentially, I can ssh into the vistabox from the linuxbox, but do not know how to structure the commands on the linuxbox to be actually running commands on the vistabox.

I know a burning question may be why don't I just go to the vistabox and set up a script callable from cron which rsyncs its files over to the linuxbox.  I tried this but it does not appear that I can get cron working at all on the vistabox.  

Any help from anyone is appreciated.

---

### Post by munkyeetr on 2008-03-26
ssh(ing) into remote mchines is beyond my current knowledge. I'm sure someone else who finds this thread can help you.

---

### Post by thedarkwinter on 2008-03-26
Hi

I have never used cygwin nor rsync :) but can i suggest that you post some of the code you are trying to run and we can have a look at what the problem may be. You may also start a new question, as this thread's title is not really the current issue.

---

