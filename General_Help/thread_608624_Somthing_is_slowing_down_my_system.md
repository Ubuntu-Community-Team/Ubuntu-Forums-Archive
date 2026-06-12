---
title: "Somthing is slowing down my system"
date: 2007-11-10
forum: General Help
---

### Post by robertriik on 2007-11-10
Hello
I'v recently installed Ubuntu for the first time, and upgraded from 7.04-> 7.10 a couple of days a go. But in the last 2 days ubuntun has been getting real slow, and bringing my computer to an absolute standstill, so i have to turn it of. I can't figure out which application is slowing it down so much, but it has to be a system application, since the whole system stops? I tried running top, but don't really get much out of it. Can anybody see anything, looking at the screenshot i'v attached from top?

---

### Post by disraeli on 2007-11-10
That top snapshot doesn't tell me much but in my experience when the system gets sluggish the first thing I think of is videocard drivers. Have you got an ATI or nVidia card as most people have?
I think anyway it would be best for you to start out with a fresh 7.10 install instead of upgrading from Fesity to Gutsy.

---

### Post by knutschr on 2007-11-10
Try
sudo apt-get remove xserver-xgl

---

### Post by Tyche on 2007-11-10
Another suggestion I might make is to go to System -> Preferences -> Indexing Preferences and shut everything down.  I noticed on my system (earlier, when running the Beta and RC of Gutsy) that indexing took a great deal of CPU time.  As I don't use the particular search function that it goes with at all, I just shut everything off.  If you were to do so, temporarily, you might see a marked improvement in your system.  If you then decide you want that search function enabled, you could go back in and decide what you want, and how much you want.

---

### Post by robertriik on 2007-11-15
Hey
Thanks a lot for all the answers. But they didn&#8217;t help. Except reinstalling and the drivers thing.  Any way to do that, without having to backup all my files, and loosing my settings? Never had to reinstall win xp before&#8230;When I shut down my HDD still keeps working like hell, all the way up to the point where the last "service" stops (or whatever it' s called in ubuntu) so I think it&#8217;s something with my system. I&#8217;ve also stopped all window effects, but that wasn&#8217;t the problem. The system just slows down so much that I can&#8217;t move the mouse. There is on thing dough. I have an Nvida Gerforce 4 MX 420,and i installed the "unfree" drivers for them. Can i "revert" back to old drivers maybe?

Sorry I can&#8217;t research this problem more myself, but I&#8217;ve recently started using Linux, because I&#8217;ve started a project called [Computers to Ave-Xevi project]("http://computeraid.zapto.org"). I&#8217;m gathering 200 computers that I and my friend are going to send to schools in Ghana! So I&#8217;m just trying out Ubuntu, but I&#8217;ll likely use Edubuntu or Edudebian, or Windows if all else fails :) I&#8217;m currently trying to find out what I&#8217;ll choose. Would be really cool if I could get Linux in the local language too. Any tips are more than welcome.
Sorry for this out of topic, but I felt it&#8217;s pretty important&#8230;

---

