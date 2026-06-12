---
title: "update-manager error crashed with SystemError in open():"
date: 2019-01-20
forum: General Help
---

### Post by Gnusboy on 2019-01-20
Hi all

I've been having a lot of trouble trying to update 16.04.  The other day I noticed I wasn't getting regular updates as usual. I opened the system & updates and there was a very long list of various updates I had not done. I did not D/L right then and went looking for some what or why information, but I didn't find anything on-point.

I went ahead and starting the updates. I can't say exactly how many there were, but them my system started having multiple crashes. It seemed to start the updates and then crashed time after time. It kept asking me to send an error report, but then crashed before it was submitted.

I went looking for anything I could find, but no luck.

Prior to this incident I had another problem. I'm not sure if they are related. For a long time (months) I had a error notice in the top right menu bar. It is a red circle with a white line. I did not have time to deal with it and my system continued working. A right click showed "Ubuntu Error Package manager - "right click or Apt-Get in terminal . 
```
"error: opening the cache (E: could not read from /var /lib /apt/lists/us.archive.ubuntu.com _dists_xenial-updates_in release-get line (21: is a directory) E: the package lists or status file could not be parsed or opened.) : this is usually means that your installed packages have unmet dependencies
```
I did not really understand the message, but I tried entering the entire string in the terminal which did not work. Then I tried fsck /dev/sda9
hoping that would solve this problem. I've sometimes done this and it seemed to work in the past.
But it must have been the wrong thing to do because then I started having the multiple crashes etc.

So, now I am so far in the weeds I can't find a way out. Aside from the error messages and the general gumming up of my system, I can boot and use my machine. But I still have not done the long list of updates to make my system stable. I think there were a few other things I've done, but I can't recall them.

If the screenshot is not readable I'll post the full image if necessary.[IMG]file:///home/jess/Desktop/Ubuntu%20error%20Screenshot01-12-2019.png[/IMG]

[IMG]file:///home/jess/Desktop/Ubuntu%20error%20Screenshot01-12-2019.png[/IMG]
My most recent attempt to update failed and I got the error message showing in the attached screen shot. I'd like to get this fixed. If anyone can guide me through it, I'll appreciate it.[ATTACH=CONFIG]282253[/ATTACH]

---

### Post by Gnusboy on 2019-01-22
Can manyone help me fix this problem??

---

### Post by Gnusboy on 2019-01-25
Bump

---

### Post by again? on 2019-01-25
Run an update and upgrade in terminal and post your output to aid people to evaluate what's happening.
```
sudo apt update
sudo apt upgrade 
``` 
Copy terminal output and paste your results between code tags.
eg
[noparse]```
paste results here
```[/noparse]

which will display as 
```
paste results here
```

---

### Post by Gnusboy on 2019-01-26
guber2

I tried both commands and they came back as bus erroe (core dumped). 0%

P.S. If it matters, I also have 14.04 dual boot in a separate partition.

---

### Post by again? on 2019-01-26
You said "Then I tried fsck /dev/sda9 hoping that would solve this problem. I've sometimes done this and it seemed to work in the past."
Is it a possibility you have a failing hard drive?
[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en)

---

### Post by Gnusboy on 2019-01-27
guber2

> **guber2 said:**
> You said "Then I tried fsck /dev/sda9 hoping that  would solve this problem. I've sometimes done this and it seemed to  work in the past."
Is it a possibility you have a failing hard drive?
[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en)

I checked my HDD with Smart test I ran several short self tests which  came back as "self -test fail,"  I've attached a screenshot of the test.  
Although the short test failed, the assessments came back as OK except  for "spin up time" and "reallocated sector count" which show as  pre-fail. There are also 7 bad sectors. From what I see, it seems like  the disk is performing as expected, but there is a potential for  failure.

What is weird is that when I did the test yesterday the short test also  failed, but reported only 5 bad sectors and all of the comments read as  OK. I have seen the 5 bad sector notice at other times, but did not  appear to be a problem. Now there are 7 bad sectors. Does this change  make a difference? 

Also:
Is there a problem to running fsck to fix my system problems?
P.S. I tried to send attachments, but could not figure out how post screenshots. Sorry,
If you can figure a solution it would be a great thing. Thanks.

---

### Post by again? on 2019-01-28
I have little knowledge of the tell tale signs of a failing disk or how to interpret disk diagnosis errors.
You should copy and paste the exact error messages you get with the apt update/upgrade commands.
Failing disk was just a suggestion because of your use of fsck and googling "bus error (core dumped) ubuntu" returns this could be seen when hardware is failing.

Do some tests in your 14.04 install to see if you get similar results
[https://askubuntu.com/questions/291570/mark-bad-sectors-on-hard-drive-without-formating/490549#490549](https://askubuntu.com/questions/291570/mark-bad-sectors-on-hard-drive-without-formating/490549#490549)

---

