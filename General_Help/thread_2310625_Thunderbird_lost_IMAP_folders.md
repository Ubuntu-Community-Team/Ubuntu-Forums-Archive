---
title: "Thunderbird lost IMAP folders"
date: 2016-01-20
forum: General Help
---

### Post by tuuk on 2016-01-20
I am an Ubuntu 15.10 and Thunderbird 38.5.1 user. I connect to my employer's Outlook/Office 365 servers via IMAP and SMTP. 

This morning (20 January 2016), right after receiving a set of updates to some  of the installed packages, my Thunderbird client lost all the subscribed  IMAP folders (except Inbox and Deleted). Furthermore, even though I can  see my folders in the "Subscribe" dialogue window, I cannot seem to  resubscribe to them by just ticking folders and hitting "OK". Nothing  happens when I do that. When I check again, no folder is subscribed to. I  can still receive and send emails, even though I cannot copy messages  into my Sent folder, which normally used to happen automatically. 

As a workaround, unticking "Show only subscribed folders" in  Server Settings > Advanced shows all folders on the IMAP server  (after a restart), subscribed or not, which is not quite desirable as  many unwanted folders pollute the folders list.

This happened to me on two separate machines running Ubuntu 15.10. 

I cannot immediately spot a connection between the updated  packages and the problem I described, but I am including the list of the  updated packaged below in case it helps. There was also a Thunderbird  update six days ago (14 January), but it has been working fine until the  updates this morning. 

Please let me whether I can provide any further information to diagnose the problem. Or, if you have any suggestions for me... 

Thanks, 
Tugkan 

linux-image-generic (4.2.0.25.27) ... 
linux-headers-4.2.0-25 (4.2.0-25.30) ... 
linux-headers-4.2.0-25-generic (4.2.0-25.30) ... 
linux-headers-generic (4.2.0.25.27) ... 
linux-generic (4.2.0.25.27) ... 


libisc-export95 (1:9.9.5.dfsg-11ubuntu1.2) ... 
libdns-export100 (1:9.9.5.dfsg-11ubuntu1.2) ... 
libisccfg-export90 (1:9.9.5.dfsg-11ubuntu1.2) ... 
libirs-export91 (1:9.9.5.dfsg-11ubuntu1.2) ... 
libxml2:i386 (2.9.2+zdfsg1-4ubuntu0.3) ... 
libxml2:amd64 (2.9.2+zdfsg1-4ubuntu0.3) ... 
libisc95 (1:9.9.5.dfsg-11ubuntu1.2) ... 
libdns100 (1:9.9.5.dfsg-11ubuntu1.2) ... 
libisccc90 (1:9.9.5.dfsg-11ubuntu1.2) ... 
libisccfg90 (1:9.9.5.dfsg-11ubuntu1.2) ... 
libbind9-90 (1:9.9.5.dfsg-11ubuntu1.2) ... 
liblwres90 (1:9.9.5.dfsg-11ubuntu1.2) ... 
bind9-host (1:9.9.5.dfsg-11ubuntu1.2) ... 
dnsutils (1:9.9.5.dfsg-11ubuntu1.2) ... 
libavutil-ffmpeg54:amd64 (7:2.7.5-0ubuntu0.15.10.1) ... 
libswresample-ffmpeg1:amd64 (7:2.7.5-0ubuntu0.15.10.1) ... 
libavcodec-ffmpeg-extra56:amd64 (7:2.7.5-0ubuntu0.15.10.1) ... 
libavformat-ffmpeg56:amd64 (7:2.7.5-0ubuntu0.15.10.1) ... 
libavresample-ffmpeg2:amd64 (7:2.7.5-0ubuntu0.15.10.1) ... 
libpostproc-ffmpeg53:amd64 (7:2.7.5-0ubuntu0.15.10.1) ... 
libswscale-ffmpeg3:amd64 (7:2.7.5-0ubuntu0.15.10.1) ... 
libavfilter-ffmpeg5:amd64 (7:2.7.5-0ubuntu0.15.10.1) ... 
libavdevice-ffmpeg56:amd64 (7:2.7.5-0ubuntu0.15.10.1) ... 
ffmpeg (7:2.7.5-0ubuntu0.15.10.1) ... 
linux-libc-dev:amd64 (4.2.0-25.30) ... 
libav-tools-links (7:2.7.5-0ubuntu0.15.10.1) ... 
libavcodec-extra (7:2.7.5-0ubuntu0.15.10.1) ...

---

### Post by lisati on 2016-01-20
Don't panic, you are not alone.

Not sure if it's related, it might turn out to be unrelated, but I had something similar happen recently, but with just one email account. I use Thunderbird 38.5.1 on Ubuntu 12.04.

I can't recall exactly what I did, including refreshing the subscribed folder list, unchecking and rechecking "Show only subscribed folders", closing Thunderbird then restarting, but it seems to have come right. The only thing out of the ordinary I've noticed is that it happened with an Outlook.com email account which recently seems to be having intermittent issues with outgoing email not being delivered as expected.

---

### Post by tuuk on 2016-01-21
Thanks Lisati.

I have tried some combinations of the steps you mentioned. If there is a correct one, I have not found it.

When "Show only subscribed folders" is unchecked, I see all the folders. I can subscribe to the ones I want and my choices seem to stick. However, in the "Folders" pane, all folders are displayed because of the unchecked option. As soon as I check "Show only subscribed folders" and restart Thunderbird to see the effects, all subscriptions are lost and it is not possible to subscribe to any folders.

---

### Post by sebastian_buettrich on 2016-01-21
Experiencing the exact same, since Jan 19. 
Thunderbird 38.5.1
Version: 1:38.5.1+build2-0ubuntu0.14.04.1
and Outlook/Office 365.
Other mail clients (Evolution) work fine.
I have not found an explanation or cure yet - will keep digging.
Grateful for any pointers!

---

### Post by sebastian_buettrich on 2016-01-22
Answering my own post,
i can confirm that steps described above ("unchecking "Show only subscribed folders") " solve the problem for me -
it remains unclear though what caused this behaviour.

All folders are subscribed to, so they should be visible with option "Show only subscribed folders" checked.
[SOLVED, sort of, but no ...]

---

### Post by tuuk on 2016-01-22
When I go back to checking "Show only subscribed folders" and restart Thunderbird, I lose my subscribed folders again. Somehow, the subscription information is lost.

---

### Post by tuuk on 2016-01-23
It looks like the cause of the problem was Microsoft making "updates" to its IMAP implementation. It appears that they are working on a fix.
See [http://www.o365dash.com/](http://www.o365dash.com/).

---

### Post by Vighnahara on 2016-04-30
I'm having this problem as well.

What triggered it was I created a new sub-folder (sub-sub-sub-folder actually) and moved an email into it. Then the sub-folder disappeared, so I went to re-subscribe to it only it wasn't listed in the subscription list. So I un-subscribed to its parent folder, thinking that might trigger a refresh. Only that made the parent disappear!

When I deselect "show only subscribed folders" *and* delete my ImapMail contents, the folders re-appear but with every folder I've ever created. If I do either of these steps alone, I get problems (e.g. not listing folders and/or listing phantom folders). I have folders that still exist for archival purposes, but I don't refer to them ever and prefer them to be hidden.

For the time being, the only way I can see the folders I need is by including the folders I want to hide. FYI, this is a microsoft exchange account provided by my university.

The strange thing is that it's affecting multiple computers. This problem started on my Linux machine, and I went to my Windows machine to see if I could export the folders in question to my Linux machine... but they were gone from the Windows machine as well! Only the folders I'd touch were affected on the Windows machine, everything else worked as expected.

I'm tempted to go to my office, unplug the network cable, boot up the computer and back up the folders before the server gets a chance to break them.

---

