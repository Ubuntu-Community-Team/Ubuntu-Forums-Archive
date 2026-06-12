---
title: "Unable to mount Blank DVD-R Disc"
date: 2013-01-18
forum: General Help
---

### Post by comacaptain on 2013-01-18
Just switched to Ubuntu 12.10 and I'm no longer able to use my DVD burner everytime I place a DVD in the drive I get the following message "Unable to mount Blank DVD-R Disc" and I'm ubable to do anything with the disc. I had this problem in the past with other Ubuntu distro's but forgot how to fix it. Please I'm deseperate I need to use my DVD burner. It's crazy that Ubuntu continues to have this problem every distro. Please folks I'm still a bit of a noob with Linux but I need help.

---

### Post by comacaptain on 2013-01-21
Hey folks anybody please help me! I need to use my dvd burner hell USB sticks don't work anymore either all my data is stuck on my computer.

---

### Post by Nr90 on 2013-01-21
Ok, I'm no expert but I'll give it a try.

As the drive is empty it does not contain any partitions that you could mount.
Therefor I assume this is not really a bug.

If you put the disc in and open a DVD burner (brasero for example). Can you select the DVD as a burn target?

Regarding your problem with USB drives. Is this problem present with different USB drives?

---

### Post by sidzen on 2013-01-21
Here's something apropos I found from [*IBM*]("http://www.ibm.com/developerworks/linux/library/l-10sysadtips/")
and another from[* help.ubuntu*]("http://askubuntu.com/questions/186361/dvd-wont-mount-ubuntu-12-04")

Hope one will help!

---

### Post by comacaptain on 2013-01-25
Thank you so much Sidzen your help is much welcomed but my problem continues. Please guys and gals I'm a noob Okay I need your help but the communitty needs to finally admit this is a widespread problem affecting new users and we need an answer.

---

### Post by comacaptain on 2013-01-25
Yet again I beseech the Ubuntu Communitty to notice and acknowledge the obvious continued bug that shows everytime I attempt in anyway to use a DVD-R, CD, or USB Stick to transfer data to any media. This is the error message I get everytime I place a DVD-R, CD, or USB Stick in my computer.

"Unable to mount Blank DVD-R Disc"
   Location is already mounted


I was able to use my DVD Drive in all ways until upgrading to Ubuntu 12.10 then BLAM! nothing no burning of any sort after that. This has occurred in previous Distro's and yet the Ubuntu Communitty ignores it as a whole. I'm a huge advocate of Linux and Ubuntu but I'm not a programmer I need your help folks.

---

### Post by comacaptain on 2013-01-25
The following is the Error Save Log from trying to burn some data to a DVD-R using CD/DVD Creator. I hope this is of some help to solve this problem.


```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI burn:// URI found burn:///Alien%20Legion/Alien%20Legion%20-%20One%20Planet%20at%20a%20Time%20%2302.cbr
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20One%20Planet%20at%20a%20Time%20%2302.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - One Planet at a Time #02.cbr at /Alien Legion/Alien Legion - One Planet at a Time #02.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20One%20Planet%20at%20a%20Time%20%2301.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - One Planet at a Time #01.cbr at /Alien Legion/Alien Legion - One Planet at a Time #01.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2302.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #02.cbr at /Alien Legion/Alien Legion v2 #02.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2315.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #15.cbz at /Alien Legion/Alien Legion v1 #15.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2308.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #08.cbr at /Alien Legion/Alien Legion v2 #08.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20Tenants%20of%20Hell%20%2301.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - Tenants of Hell #01.cbr at /Alien Legion/Alien Legion - Tenants of Hell #01.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2320.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #20.cbr at /Alien Legion/Alien Legion v1 #20.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2308.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #08.cbr at /Alien Legion/Alien Legion v1 #08.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2312.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #12.cbz at /Alien Legion/Alien Legion v1 #12.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20On%20the%20Edge%20%2301.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - On the Edge #01.cbr at /Alien Legion/Alien Legion - On the Edge #01.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2301.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #01.cbz at /Alien Legion/Alien Legion v1 #01.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2318.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #18.cbr at /Alien Legion/Alien Legion v2 #18.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2312.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #12.cbr at /Alien Legion/Alien Legion v2 #12.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2315.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #15.cbr at /Alien Legion/Alien Legion v2 #15.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2304.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #04.cbz at /Alien Legion/Alien Legion v2 #04.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2307.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #07.cbz at /Alien Legion/Alien Legion v2 #07.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2304.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #04.cbz at /Alien Legion/Alien Legion v1 #04.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2318.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #18.cbr at /Alien Legion/Alien Legion v1 #18.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2307.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #07.cbz at /Alien Legion/Alien Legion v1 #07.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20On%20the%20Edge%20%2303.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - On the Edge #03.cbr at /Alien Legion/Alien Legion - On the Edge #03.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2301.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #01.cbr at /Alien Legion/Alien Legion v2 #01.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2317.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #17.cbz at /Alien Legion/Alien Legion v1 #17.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion
BraseroBurnURI Adding directory (null) at /Alien Legion/
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #14.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #15.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - Tough Enough.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #04.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - On the Edge #02.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #12.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #13.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #05.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - Grimrod.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - On the Edge #01.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - Binary Deep.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #19.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #20.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #03.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - Altered State.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #18.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #07.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - On the Edge #03.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #14.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #17.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #06.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #12.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #07.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Read-Order.txt at /Alien Legion/Read-Order.txt
BraseroBurnURI Graft already in list /Alien Legion/Torrent downloaded from Demonoid.com.txt
BraseroBurnURI Graft already in list /Alien Legion/Law Dog & Grimrod.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #02.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #13.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #01.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #02.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #08.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #03.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #04.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - One Planet at a Time #03.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - Tenants of Hell #01.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #05.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #01.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #09.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #10.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #16.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #17.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #08.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - A Grey Day To Die.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - Tenants of Hell #02.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #11.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #18.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v2 #11.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #06.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - One Planet at a Time #01.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion - One Planet at a Time #02.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #09.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #10.cbr
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #15.cbz
BraseroBurnURI Graft already in list /Alien Legion/Alien Legion v1 #16.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20Grimrod.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - Grimrod.cbr at /Alien Legion/Alien Legion - Grimrod.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2311.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #11.cbz at /Alien Legion/Alien Legion v1 #11.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2314.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #14.cbz at /Alien Legion/Alien Legion v1 #14.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20Binary%20Deep.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - Binary Deep.cbz at /Alien Legion/Alien Legion - Binary Deep.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2311.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #11.cbr at /Alien Legion/Alien Legion v2 #11.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2314.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #14.cbr at /Alien Legion/Alien Legion v2 #14.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2317.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #17.cbr at /Alien Legion/Alien Legion v2 #17.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2306.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #06.cbz at /Alien Legion/Alien Legion v2 #06.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2309.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #09.cbz at /Alien Legion/Alien Legion v2 #09.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2306.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #06.cbz at /Alien Legion/Alien Legion v1 #06.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20One%20Planet%20at%20a%20Time%20%2303.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - One Planet at a Time #03.cbr at /Alien Legion/Alien Legion - One Planet at a Time #03.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2316.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #16.cbz at /Alien Legion/Alien Legion v1 #16.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2310.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #10.cbr at /Alien Legion/Alien Legion v1 #10.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2309.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #09.cbr at /Alien Legion/Alien Legion v1 #09.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2303.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #03.cbr at /Alien Legion/Alien Legion v2 #03.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20Tenants%20of%20Hell%20%2302.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - Tenants of Hell #02.cbr at /Alien Legion/Alien Legion - Tenants of Hell #02.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2310.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #10.cbz at /Alien Legion/Alien Legion v2 #10.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2303.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #03.cbr at /Alien Legion/Alien Legion v1 #03.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Law%20Dog%20&%20Grimrod.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Law Dog & Grimrod.cbr at /Alien Legion/Law Dog & Grimrod.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20Tough%20Enough.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - Tough Enough.cbr at /Alien Legion/Alien Legion - Tough Enough.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2313.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #13.cbz at /Alien Legion/Alien Legion v1 #13.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20On%20the%20Edge%20%2302.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - On the Edge #02.cbr at /Alien Legion/Alien Legion - On the Edge #02.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20A%20Grey%20Day%20To%20Die.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - A Grey Day To Die.cbr at /Alien Legion/Alien Legion - A Grey Day To Die.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2316.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #16.cbr at /Alien Legion/Alien Legion v2 #16.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2305.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #05.cbz at /Alien Legion/Alien Legion v2 #05.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v2%20%2313.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #13.cbr at /Alien Legion/Alien Legion v2 #13.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2302.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #02.cbz at /Alien Legion/Alien Legion v1 #02.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2305.cbz
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #05.cbz at /Alien Legion/Alien Legion v1 #05.cbz
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20-%20Altered%20State.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion - Altered State.cbr at /Alien Legion/Alien Legion - Altered State.cbr
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Torrent%20downloaded%20from%20Demonoid.com.txt
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Torrent downloaded from Demonoid.com.txt at /Alien Legion/Torrent downloaded from Demonoid.com.txt
BraseroBurnURI Information retrieval for burn:///Alien%20Legion/Alien%20Legion%20v1%20%2319.cbr
BraseroBurnURI Added file /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #19.cbr at /Alien Legion/Alien Legion v1 #19.cbr
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_X50HRW.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs called brasero_job_set_current_action
BraseroLibisofs creating volume
BraseroLibisofs called brasero_job_get_data_label
BraseroLibisofs called brasero_job_get_flags
BraseroLibisofs called brasero_job_get_current_track
BraseroLibisofs Adding graft disc path = /.checksum.md5, URI = file:///tmp/brasero_tmp_X50HRW.md5
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/, URI = (null)
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Read-Order.txt, URI = /home/comacaptain/Comix/Alien Legion/Read-Order.txt
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Law Dog & Grimrod.cbr, URI = /home/comacaptain/Comix/Alien Legion/Law Dog & Grimrod.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #19.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #19.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #05.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #05.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #02.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #02.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #13.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #13.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #05.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #05.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #16.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #16.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #13.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #13.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #03.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #03.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #10.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #10.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #03.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #03.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #09.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #09.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #10.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #10.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #16.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #16.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #06.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #06.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #09.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #09.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #06.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #06.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #17.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #17.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #14.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #14.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #11.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #11.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #14.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #14.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #11.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #11.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #17.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #17.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #01.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #01.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #07.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #07.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #18.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #18.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #04.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #04.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #07.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #07.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #04.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #04.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #15.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #15.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #12.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #12.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #18.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #18.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #01.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #01.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #12.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #12.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #08.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #08.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #20.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #20.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #08.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #08.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v1 #15.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v1 #15.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion v2 #02.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion v2 #02.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - Grimrod.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - Grimrod.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - Binary Deep.cbz, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - Binary Deep.cbz
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - Tough Enough.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - Tough Enough.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - Altered State.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - Altered State.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - On the Edge #02.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - On the Edge #02.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - On the Edge #03.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - On the Edge #03.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - On the Edge #01.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - On the Edge #01.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - A Grey Day To Die.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - A Grey Day To Die.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - Tenants of Hell #02.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - Tenants of Hell #02.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - Tenants of Hell #01.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - Tenants of Hell #01.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Torrent downloaded from Demonoid.com.txt, URI = /home/comacaptain/Comix/Alien Legion/Torrent downloaded from Demonoid.com.txt
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - One Planet at a Time #03.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - One Planet at a Time #03.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - One Planet at a Time #01.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - One Planet at a Time #01.cbr
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /Alien Legion/Alien Legion - One Planet at a Time #02.cbr, URI = /home/comacaptain/Comix/Alien Legion/Alien Legion - One Planet at a Time #02.cbr
BraseroLibisofs Found parent
BraseroLibisofs called brasero_job_set_output_size_for_current_track
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs Finished track successfully
BraseroLibisofs stopping
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs called brasero_job_get_session_output_size
BraseroLibisofs output set (IMAGE) image = /tmp/brasero_tmp_0NUURW.bin toc = none
BraseroLibisofs called brasero_job_get_session_output_size
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs Entering thread
BraseroLibisofs called brasero_job_get_fd_out
BraseroLibisofs called brasero_job_get_image_output
BraseroLibisofs writing to file /tmp/brasero_tmp_0NUURW.bin
BraseroLibisofs called brasero_job_set_current_action
BraseroLibisofs Getting out thread
BraseroLibisofs called brasero_job_get_fd_out
BraseroLibisofs called brasero_job_get_image_output
BraseroLibisofs called brasero_job_get_session_output_size
BraseroLibisofs called brasero_job_add_track
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs Finished track successfully
BraseroLibisofs stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_CJTNRW.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /tmp/brasero_tmp_0NUURW.bin (size = 564447232)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) ae3e6bb085a1b2f44c29f139636943ca ((null) before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_tracks
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 0
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn Something went wrong
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 15
	message	= "An error occurred while writing to disc"
BraseroLibburn stopping
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2856)
```

---

### Post by comacaptain on 2013-01-25
NR90 thank you so much for your response all help is welcomed. But this is a bug all attempts to burn with Brasero fail and all attempts using DVD-R or placing data on a USB Stick illicit the same error response of "Unable to mount Blank DVD-R Disc"
Location is already mounted and failure to burn the data.

---

### Post by oldos2er on 2013-01-25
> **comacaptain said:**
> Yet again I beseech the Ubuntu Communitty to notice and acknowledge the obvious continued bug 

This bug has been confirmed: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1071739](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1071739)
It's now a matter of waiting for a fix to come through.

---

### Post by comacaptain on 2013-01-28
Thanks you for the help Oldos2er.

---

### Post by MoebusNet on 2013-01-28
Since this bug doesn't affect me, this may not be helpful but it looks like the bug description gives a work-around >  Each time I insert a blank DVD a window opens telling me that I just inserted a blank DVD and asking what to do with it. Immediately another window opens on top of it and reads "Unable to mount Blank DVD-R Disc Location is already mounted"

I can click OK to get back to the first window, but the error is really annoying and makes no sense.

This makes it sound like you can click 'OK', go back to the first window and continue as normal. Am I mistaken in that understanding?

---

