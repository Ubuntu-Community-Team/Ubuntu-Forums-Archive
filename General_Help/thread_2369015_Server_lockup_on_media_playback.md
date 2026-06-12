---
title: "Server lockup on media playback"
date: 2017-08-17
forum: General Help
---

### Post by JDAIII on 2017-08-17
I've been experiencing an issue where my server locks up when I'm streaming media from my server remotely to my workstation at work. I'm also tracking as a plex issue since that is what I'm using to stream but whether or not plex has an issue, there should be no locking up of my server.

I do a hard reboot and if I play the same media file, it will lock up at the same time in the playback. 

I checked my syslog and saw some smart errors with sde1 so I physically removed the drive, but the issue returned so that was not the cause. One thing that I saw that I have never seen before is at the exact time of the lock up, the syslog stops and places some characters in the file. Then I see syslog picking back up after my reboot.

Please ask anything, but I have no idea where to go from here. pastebin of the last 17 lines of the syslog is below.

I do see that the drive temp is a bit high, but shouldn't be maxed out.


[https://pastebin.com/raw/iaq4TS7n](https://pastebin.com/raw/iaq4TS7n)

---

### Post by Autodave on 2017-08-17
What version are you running?  I see 14.10 and 15.04 both in your post. Neither is supported any longer. That could be your problem.

The media you are streaming: is this stored on your HD or are you getting it online and then resending it online? That takes a HUGE amount of resources to do that and I wouldn't be a bit surprised if something is overheating. Especially if it is high def.  Just sending a high def video takes a lot of machine.

---

### Post by JDAIII on 2017-08-17
This is my home server which is on 16.04 right now. I have not taken the time to test 16.10 or 17.04 before upgrading.

The files are stored on the hard drive. Or rather A hard drive. I cannot imagine that the CPU is overheating as I have liquid cooling and it has been at a reasonable level, but I've been planning to move to a larger case with more cooling built in along with more airflow and empty space. I guess that I will try a remote thermometer and monitor the temps on the drives and so forth.

---

### Post by JDAIII on 2017-08-17
Strange, on a drive in a USB/SATA dock on my desk, I run hddtemp on it and I see two different messages for it. I'm guessing that the higher one is in fact not correct. It has been working without issue for a few months now. I'd have to imagine that the open air of a 72 F room would not fully allow of that kind of temp. I have to assume that it is wrong. But an overheating drive would not cause a server to crash. This is the drive holding the files that I am streaming.

jd@FileServer1:~$ sudo hddtemp /dev/sdf
/dev/sdf: ASMT 2105:  drive supported, but it doesn't have a temperature sensor.
jd@FileServer1:~$ sudo hddtemp /dev/sdf
 /dev/sdf: ASMT 2105: 155°C



I started streaming a 1080 file and I'm monitoring the CPU temp. I see the temps after 5 minutes hovering around 62C. This is a little high, but not high enough for me to start freaking out. It is transcoding to 3Mbps 720p.

---

### Post by Autodave on 2017-08-17
First off, keep the 16.04 release on there: that is a long term release. The next LTS will be 18.04. In between, there are short term releases that are ONLY supported for 6 months until the next release comes out.

Obviously, that "/dev/sdf: ASMT 2105: 155°C" has to be wrong. I cannot imagine a HD still operating at anywhere close to that temp.

Having said that, your water cooled CPU beats mine, but let me tell you what I have seen here. I have an 8 core overclocked to 4.0. Streaming an HD via Teamviewer, I have all 8 cores running between 90 and 100%. I have a huge cooler and 2 5" case fans, but I still see 150F degrees. The desktop feels like a space heater. :-) The HD temp stays rather normal, however.

---

### Post by JDAIII on 2017-08-17
I was tracking it up until it locked up. 60C for CPU and drives never got over 45C and that was peak. So not temp.

Any other ideas? I'll have to reset the server tonight. Frustrating. I also forgot to mention that I did an apt upgrade this morning which obviously didn't affect it.

---

### Post by TheFu on 2017-08-19
Transcoding doesn't take a high-end CPU.  My plex-server is on a $50 G3258 and easily transcodes 2 1080 streams concurrently - stock cooler.

What does **dmesg** say about HW issues?

I don't see anything alarming in the syslog.  

Have you forced an fsck on all storage?
Have you tried reinstalling the running packages?  Sometimes bitrot will create a different instruction that is valid, but not desired.  Doing backups for everything is preventative, since it forces all the bytes to be read on a disk and gives the disk hardware a chance to relocate failing sectors.

Oh ... and are you certain the media file isn't corrupted?  In theory, no bad data input (media file) should ever cause a program to crash and in no way should a crashing program ever cause the OS to segfault, but ... there have been segfaults with the new Ryzen CPUs the last 6 months on Linux.  AMD is working it.

I'm just throwing out ideas.

But the best advice is to check ALL the log files for issues.

---

