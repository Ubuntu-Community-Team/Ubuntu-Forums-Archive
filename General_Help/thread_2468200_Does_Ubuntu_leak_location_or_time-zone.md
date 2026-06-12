---
title: "Does Ubuntu leak location or time-zone?"
date: 2021-10-21
forum: General Help
---

### Post by erosman on 2021-10-21
On an Ubuntu installation video, it was suggested to set the location to USA during the installation and the reason was hinted at youtube facilitation.

The question is whether the location and/or time-zone gets leaked by the OS?

*PS. The remote_addr IP is not the subject of this question.*

---

### Post by mIk3_08 on 2021-10-21
> **erosman said:**
> On an Ubuntu installation video, it was suggested to set the location to USA during the installation and the reason was hinted at youtube facilitation.
The question is whether the location and/or time-zone gets leaked by the OS?
*PS. The remote_addr IP is not the subject of this question.*
I don't think of this leak. The Linux key is now 1024-bit to 2048-bit keys. I don't think there's a leak in their. Even the fastest computer can't break the Linux key in a few hours. It takes a lot of years/decades before it cracks the key. 
I don't think so.

---

### Post by ActionParsnip on 2021-10-21
The location is used to set locales like the keyboard and set the package source to something geographically closer for faster updates. It also sets the time zone.
What do you mean with this YouTube idea? Is this on a video you have watched? If so can you please give us the link.
Thanks

---

### Post by erosman on 2021-10-22
> **mIk3_08 said:**
> I don't think of this leak. The Linux key is now  1024-bit to 2048-bit keys. I don't think there's a leak in their. Even  the fastest computer can break the Linux key in a few hours. It takes a  lot of years/decades before it cracks the key. 
I don't think so.

Encryption relates to hacking. I was enquiring about leaking which means pass data e.g. via HTTP headers.

> **ActionParsnip said:**
> The location is used to set locales like  the keyboard and set the package source to something geographically  closer for faster updates. It also sets the time zone.

I also noticed that. I was trying Ubuntu 21.10 (I am still on Win, and looking for a new laptop to install Ubuntu).
In my case, my preferred language is en_GB, my keyboard layout is usually en_US and I also write in at least 2 other languages so I usually use 3 keyboard layouts. My time-zone is in totally a different location as I am not in UK currently.
When trying Ubuntu, I set the location to London but then didn't find a place to change the clock.

> **ActionParsnip said:**
> What do you mean with this YouTube idea? Is this on a video you have watched? If so can you please give us the link.
Thanks

I saw it on a non-English-language video tutorial on Ubuntu installation on YouTube. It was surprising to me and thus I asked here to verify.

---

### Post by ActionParsnip on 2021-10-22
Do you have the link to the video please?

---

### Post by mIk3_08 on 2021-10-22
> **erosman said:**
> Encryption relates to hacking. I was enquiring about leaking which means pass data e.g. via HTTP headers.
Linux don't really uses http they only uses https. meaning its http  secured. This https always carries out unique encryption meaning, it also  carries keys an encrypted keys. Now if you are asking about https they are encrypted in a tunnel. the tunnel are solid encrypted. And it can't easily be broken. as what I've said that "Even  the fastest computer can't break it"

---

### Post by erosman on 2021-10-22
> **ActionParsnip said:**
> Do you have the link to the video please?

Which languages do you speak? 
The video is not in English.

> **mIk3_08 said:**
> Linux don't really uses http they only uses https. meaning its http  secured. This https always carries out unique encryption meaning, it also  carries keys an encrypted keys. Now if you are asking about https they are encrypted in a tunnel. the tunnel are solid encrypted. And it can't easily be broken. as what I've said that "Even  the fastest computer can't break it"


HTTP was a reference to internet connection. What you are referring to is man-in-the-middle which not the subject here.

Leak refers to source computer sending unwanted data to the target server.
Hack refers to  3rd party reading the data in transit between source & target (which is not the subject of this topic).

I am enquiring about leak in data sent from source computer to the target server i.e. the data exchange between source and target server.  The headers are read by the target server or else connection can not be made.

---

### Post by TheFu on 2021-10-22
> **erosman said:**
> On an Ubuntu installation video, it was suggested to set the location to USA during the installation and the reason was hinted at youtube facilitation.

The question is whether the location and/or time-zone gets leaked by the OS?

*PS. The remote_addr IP is not the subject of this question.*

Leaked by the OS?  All browsers leak this data, not the "OS."  It is amazing all the data that browsers leak. A few things normal people don't realize that browsers leak:
resolution
battery level
screen rotation
window size
and, yes, the timezone and local time too.

Location data is only as good as geolocation services.  Mine is usually about 50 miles off from being correct.  One service actually got about 2 miles away - which was pretty impressive.  Because I never use wifi at home, google can't mix the wifi SSID with their driving around for streetmap data to figure out where I'm located.  Be careful using BT or any other RF stuff too. It reaches farther than most people know.

If you have webRTC or javascript enabled, it is crazy how much extra data those make accessible. Disable both of those ... but all those web-based video meetings will stop working.  I run those in a highly constrained browser, in a sandbox, using a different user-account.

If you want privacy, there are many more things that can be done. Too long to list here and someone interested in a step-by-step process will be disappointed since every new browser release modifies what is needed.  NEVER trust incognito modes in browsers.  You've been warned.  I'm not saying those don't work, but they have a long history of failure - and when they fail, they tend to fail badly. Best just not to trust them at all and use outside tools to ensure a browser bug isn't all you are hit with from a privacy standpoint.

---

### Post by mIk3_08 on 2021-10-23
> **erosman said:**
>  HTTP was a reference to internet connection.  What you are referring to is man-in-the-middle which not the subject  here.
Leak refers to source computer sending unwanted data to the target server.
If you don't specify your target machine, of course it will leak. Like for example; you are sending script to a specified (static) ip and that ip belongs to a circle for dynamic cycle. here in Philippines our ISP uses dynamic IP cycle for distribution of course it will leak because there are multiple users in a few dynamic ip cycle. All users in that dynamic ip can be affected and this can lead to a catastrophe because it may possible affect to other ip's in a circle. To be specific what kind of a server your are talking here?

---

### Post by erosman on 2021-10-23
> **TheFu said:**
> Leaked by the OS?  All browsers leak this data, not the "OS."  It is amazing all the data that browsers leak.... 

Exactly ... browser or any software that connects to the internet which includes OS (during updates, downloads, etc).

One point was that I couldn't change the clock, without changing the location.
For example:
I want 3 different keyboard ..... (no problem)
Set location to London ..... (no problem)
Set time zone to Kathmandu ;)

I could add additional clocks.. but the main time display was tied to the location chosen on installation/try-out
It even changed my Windows clock.. when I restarted in Windows (so it is system wide I guess)

On Windows I have:
- Format: English (UK) .. e.g. time & date format
- Location: UK
- Keyboards: English (US) + 2 others
- Time zone: not GMT ... ;)

---

### Post by TheFu on 2021-10-23
I'm not worried about software updates giving away my location. That's because I stay within the Canonical Repos for all the software that I can with very, very, few exceptions. Many of those exceptions are using PPAs hosted by Canonical.  Let's be serious, if we don't trust Canonical, then we shouldn't be running Ubuntu, right?
Your ISP knows where you are better than anyone else. That pesky "service address" in their records.  Whether your ISP shares that information with 3rd parties or not is a crap shoot. [https://www.pogowasright.org/a-look-at-what-isps-know-about-you-examining-the-privacy-practices-of-six-major-internet-service-providers/](https://www.pogowasright.org/a-look-at-what-isps-know-about-you-examining-the-privacy-practices-of-six-major-internet-service-providers/)

KTM TZ is odd (to me).  I spent some time there. It is 15 minutes off from the Indian TZ, just to be different. It is one of the few places in the world where I never worried about taxi drivers padding the meter or being unhappy with the price.  Some cities, it just isn't safe to drive for non-locals. KTM is one of those. They have an entire language of car horn beeping.

BTW, you do know that you don't need to use any GUI to control the TZ for your system.
Use **tzselect** to pick one.  Of course, the DE can choose to ignore this - I don't use any DE, so it isn't an issue.  An easy way to set the TZ for the entire system is:
```
echo "TZ='Asia/Kathmandu'" | sudo tee /etc/timezone
```

If you want to look at cities around the world, /usr/share/zoneinfo/Asia/Kathmandu is an example, but all for the OS are under /usr/share/zoneinfo/. 
There's a wikipedia article on timezone data that could be interesting for some people.  There are mainly 2 people who maintain these files for everyone else.  
GPSd has a similar story.  There is 1 guy in Nebraska that maintains the gpsd code ... that will fail tomorrow if it was updated during a bad 2yr period.  Older versions are find.  Newer versions are fine.  [https://www.theregister.com/2021/10/19/gpsd_bug_reset/](https://www.theregister.com/2021/10/19/gpsd_bug_reset/)  And the requisite XKCD cartoon: [https://www.explainxkcd.com/wiki/index.php/2347:_Dependency](https://www.explainxkcd.com/wiki/index.php/2347:_Dependency)  Just think of all the cars on the roads with GPS that haven't been updated, but got the bad code.

---

### Post by TheFu on 2022-03-15
So, due to some other time related issues, I've learned much more about browsers and time zones.
Firefox has anti-fingerprinting settings, part of which include setting the timezone to UTC for all queries by webservers.  The setting is accessible through the about:config controls.  A browser restart is required whenever the value is toggled.

If we want more protection, we can set our systems to use UTC all the time, but that is a hassle most people wouldn't like.

I've also noticed that firefox behaves different between 20.04 and 18.04, even running the same firefox version.  Ran firefox inside a restricted container and outside it and with new userids on both OSes to check. 20.04 worked as expected, but 18.04 always failed.  I'm still researching the issue, but think the locale setting for LC_TIME could be the issue.

The output of the default date command is slightly different between 18.04:
```
Tue Mar 15 11:13:13 EDT 2022
```
and 20.04:
```
Tue 15 Mar 2022 11:13:06 AM EDT
```
These were both run using **$ \date** to ensure any of my aliases weren't involved. I've check my locale settings too.

---

### Post by dragonfly41 on 2022-03-15
Try here ..

[https://www.grc.com/shieldsup](https://www.grc.com/shieldsup)

Also try Brave browser.

---

