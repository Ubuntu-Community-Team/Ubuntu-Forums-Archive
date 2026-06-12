---
title: "Chkdsk replacement"
date: 2017-12-10
forum: General Help
---

### Post by strixtux on 2017-12-10
Dear Foristi, as I have de-microsofted all my machines, of course I keep on running into problems. One concerns an external hard disk which now has an inconsistent file system. NTFS, usuallyworked like a charm. When I try to mount it, the system response is that the file system is inconsistent and I have to run chkdsk/f on Windows. Then reboot twice.
Anybody able to meke head and tail of this?
As I am a new kid in tux, I sort of feel in trouble. Although the transition up to now was not too painful at all.
Is there any Linux app which can do the same for me without having to reinstall Windows on one of my machines?
 ^ ^   ^ ^
(QQ)(QQ)
(  v ()  v  )
--"-"---"-"--

---

### Post by coffeecat on 2017-12-10
*Thread moved to **General Help**.*

Quick answer: no, there isn't a comprehensive Linux app which does everything chkdsk does. ntfsfix is the nearest, but is not enough for what you want. From man ntfsfix:

>  ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.


You'll need to attach your external hard drive to a Windows machine - I suggest you prevail upon a friend, rather than install Windows - and then run chkdsk.

After that, back up all your data from that drive, and reformat it with a Linux filesystem. Using ntfs for data storage when you don't have immediate access to Windows is asking for inconvenience, or worse.

---

### Post by strixtux on 2017-12-10
Thank you for fast response.
I'll have a Windows system on a spare HD just for emergencies in the future.

---

### Post by ian-weisser on 2017-12-10
NTFS is *owned* by Microsoft. It's not an open format or standard.
The lack of good NTFS tools in Linux is not due to laziness, it's due to an active Microsoft policy to protect their property.

---

### Post by oldos2er on 2017-12-10
> **strixtux said:**
> Thank you for fast response.
I'll have a Windows system on a spare HD just for emergencies in the future.

You don't say which version of Windows you're using, but if you have Windows 10 with fast startup, you'll need to disable it, or not mount the relevant partition in Ubuntu.

---

### Post by strixtux on 2017-12-11
I used to run a Win 10 upgrade from win 7 on both 32 and 64 bit machines.
After both types would screw up during updates, all failed fatally. No way to rebuild the machines, no way to retrieve an upgrade from 7 again - too pissed to spend more money on instable systems.
I installed UbuntuStudio 17.10 then on all machines and after a few stumbles I am quite content with it. Much less failure prone than Windows.
When things don't work, well, they don't. That's life. I do not assume laziness here, as much as I see proprietary issues must be taken serious.
So if it must be, I'll take a spare disk, install 7 again and use it as fallback tool in the transition process.

---

### Post by Quarkrad on 2017-12-11
In ubuntu world versions with a .10 end have limited life support.  For day-to-day operation many people use a version with a .04 ending - these are called LTS (long term support) versions.   The next LTS is due April 2018 (18.04) - I would consider doing a reinstall* sometime in May/June - have a look at this *[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)* - it details the life cycle of different versions. * There is normally an upgrade option from one version to another but many people do a *backup* followed by a *reinstall* to the new version - if you get to that point (in May/June) and need help post another thread on this forum and people will talk you through it.

---

### Post by strixtux on 2017-12-11
If a reonstall is due every six months it's still easier than any Windows trouble. No problem as long as I can prepare for that.

---

### Post by Quarkrad on 2017-12-11
Long Term Releases are stable and have a life of about 5 years - many of us use a LTR for day to day working and for those who like to see 'what is coming up (and other things)' run a .10 release in something like Virtualbox as well.  E.g. I am currently running 16.04 but like a lot of people have 17.10 and 18.04 on Virtualbox as well.  So ....  there is no need to re-install every 6 months - very few people do this. Wait until May/June and enjoy 18.04 for many years to come - it will not be that much different to what you have at the moment.

---

### Post by strixtux on 2017-12-11
Sounds good.

---

### Post by vasa1 on 2017-12-11
> **Quarkrad said:**
> Long Term Releases are stable and have a life of about 5 years - many of us use a LTR for day to day working and for those who like to see 'what is coming up (and other things)' run a .10 release in something like Virtualbox as well.  E.g. I am currently running 16.04 but like a lot of people have 17.10 and 18.04 on Virtualbox as well.  So ....  there is no need to re-install every 6 months - very few people do this. Wait until May/June and enjoy 18.04 for many years to come - it will not be that much different to what you have at the moment.

[LTS]("https://wiki.ubuntu.com/LTS") is the more common term.

The main flavor has support for five years. Most of the other [official flavors]("https://www.ubuntu.com/about/about-ubuntu/flavours") may offer support for only three years.

---

### Post by strixtux on 2017-12-11
If 17.10 is an unstable version, I can live with that. Works much more reliable than any 'doze.

---

### Post by ian-weisser on 2017-12-12
Interim (6-month) releases of Ubuntu are NOT unstable. Not beta. They are fully tested and supported. They are simply supported for a shorter period of time, because this community cannot support 10 releases of Ubuntu simultaneously.

---

### Post by strixtux on 2017-12-12
Anyway, it does what t's meant to do and that's the way i like it. No updates which run over three hours (16 MBit DSL) and then screw up the machine.
What troubles I experienced in my short Linux career look like a vacation trip compared to the 'dozer.

---

### Post by leunam12 on 2017-12-12
You don't have to have Windows installed to run chkdsk, use the Windows Rescue Disk. You can also go to your disk's manufacturer 's web page and download their diagnostic and repair tools.

[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)

---

### Post by leunam12 on 2017-12-12
> **strixtux said:**
> I used to run a Win 10 upgrade from win 7 on both 32 and 64 bit machines.
After both types would screw up during updates, all failed fatally. No way to rebuild the machines, no way to retrieve an upgrade from 7 again If  you have a Windows 7 installation disk or recovery disk that came with your computer you can re-install Windows 7, activate it, and then run the Windows 10 upgrade, it is free, you don't need a separate Windows 10 License.

---

### Post by strixtux on 2017-12-12
That used to be free. Ain't no longer. Been there, tried that skipped postcard and t-shirt ;-)Guess what motivated me to rid my machines from all 'doze...
And thanks a lot for that link, I'll try that!

---

### Post by leunam12 on 2017-12-12
It is still free, I upgraded one a couple of weeks ago from Windows 7. But who wants Windows 10 anyway. I downgraded mine to Windows 8.1 because 10 was so buggy. I wish I could downgrade my computer at work; it's giving me a lot of headaches.

---

### Post by strixtux on 2017-12-13
i am a freelancer and I am using all my machines for work. I am glad I have the option to chose.

---

