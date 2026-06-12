---
title: "Need help getting Gutsy to run on my laptop"
date: 2007-11-01
forum: General Help
---

### Post by Mihasi on 2007-11-01
Hey everyone,

Here's my story: I just started my first year of college, studying electronics-ict. About a month ago I had my first Linux lesson. Before that I had only vaguely heard of Linux and I wasn't really willing to put effort into getting it to work on my system. After that first lesson, I figured it would really be worth the effort, so I decided to give Linux a chance. After messing arround with VMWare, I decided to just make a dual boot with Linux and Windows XP. My system specs are:

Intel Pentium M @2.13 Ghz
ATI Mobility Radeon x700    128 Mb
1 Gb Ram

Now, I started of with Fedora 7, because we were using Fedora in school. That didn't work, it wouldn't boot the X-server. I tried playing with the xorg.conf file a bit, but to no avail. Then I decided to move on and install Mandriva. All went fine untill I tried to use OpenOffice, which made the kde window manager crash. I then decided to give Ubuntu Feisty Fawn a try. But it didn't really appeal to me for some reason, so I went on to OpenSUSE. OpenSUSE installed fine, but then didn't do anything. It just showed a black screen after I booted up. Then Gutsy Gibbon came out, and I decided to give Ubuntu another chance. I installed it, and I was surprised to find it actualy worked. I really liked Gutsy for a time, but then I started to get those weird freezes everyone here is talking about and nobody knows a solution for. Now, I don't believe my system is too slow to run Gutsy and turning the visual effects down didn't help. I tried to install the official ATI drivers, but that didn't work. I tried changing the kernel to i368, no improvement. It can't be the heat, because my fans are on and my system works fine when I'm using XP. 

I came here to see if anyone of you could give me a hand. I'm trying to install Linux for more then a month now, and I'm really getting sick of browsing forums, looking for solutions for yet another error or bug. I really want to believe that Linux is more stable than Windows, but up to now I haven't seen any proof of that. As you can imagine, I do not have a lot of free time because of school. I really would like to spend that free time in another way then trying to fix my Linux. I've been more then patient trying to find solutions, but I've had it. Over the past few weeks I became known as biggest Linux fan of my class, but if I don't find a way to finally run Linux witouth this many errors, I think I'm gonna give up the fight and just go back to Microsoft. 

I will accept any solution, I really don't like the thought of going back to XP. If my system is too slow, please suggest some lighter distro, that still looks presentable. If it is my ATI card, please suggest some open source drivers I can use to fix it (since the official drivers won't work). If it's anything else, please let me know.

I know I can find most of this information myself, but I don't have the time anymore. Like I said: I have spent most of the past one and a half month looking for information to get all the distro's I tried out to work. I need to get back to my schoolwork and I need to be able to enjoy my free time instead of searching for fixes all of the time. I'm not saying that I'm not willing to put more effort into Linux. I really am. I just need someone who can give me a push in the right direction.

---

### Post by fjgaude on 2007-11-01
You might try Xbuntu, as it has a lighter desktop and using less memory. It should be faster than Ubuntu with its KDE or Gnome desktop.

---

### Post by Mihasi on 2007-11-02
Alright, thanks for the help. I don't really think it's my system specs though. I can run Vista fine (well, appart from it not finding my audio devices), so I don't believe that's the problem. 

Update: I made a distro-specific proprietary driver package for my ATI card. I was then able to use my laptop all through yesterday evening and this morning. I thought that had solved the problem, but for some reason it started freezing again and does that within 5 minutes after boot up. Could this perhaps be some memory problem? Or some kind of setting that get's changed without me noticing? I can't see why it would run fine for an entire evening and morning and then suddenly start to freeze after five minutes.

---

### Post by fjgaude on 2007-11-02
Could easily be memory... your laptop is pretty old, eh? Memory some years ago seemed to be not too reliable just like hard drives of five years ago.

Can't offer any suggestions. Good luck in achieving success.

---

### Post by Mihasi on 2007-11-02
My laptop is actualy about 10 months old. 

Anyway, thanks for responding.

---

### Post by nick_h on 2007-11-02
It would certainly be worth running memtest86+ from the Ubuntu grub menu.

---

### Post by lyndaj70 on 2007-11-02
Hi!

Have you tried Damn Small Linux, Puppy Linux, or Knoppix?  Knoppix and Damn Small are TERRIFFIC at detecting and installing hardware without much difficulty....  And Damn Small, when you install it to a hard disk, turns into a Debian installation, and Debian is the ancester of Ubuntu, so they use Synaptic and are both pretty easy to use.  

Puppy is built from scratch, so I don't think that there are a HUGE amount of apps, but the benefit to it is you can save back to CD/DVD and not change anything on the hard disk.

I hate that you're having troubles, I have ATI cards on all of my systems, and have had trouble with Gibbon as a result.  Have you tried installing Fawn, which from what I understand worked, then *upgrade* to gibbon?  I had to do that with this desktop cause while it would attempt to run the live cd, the video would mess up after install....

That's what I did and "thus far" it's working fine....  Newer laptops can be a pain.... What brand is it?  If it is a Dell, I hear that they are putting out Dell-specific ubuntu disks out for download for anyone wanting to put Ubuntu on their laptops.... You would have to google for the link as I discovered it surfing late one night and can't remember too many details (sorry).

Let me know how this resolves please.  I will keep an eye on this thread and help if I can..

~Lynda

---

### Post by Mihasi on 2007-11-11
@Lynda: thank you for you concern, but I am glad to inform you that my problem is now solved. I found that a possible solution for my problem was by disabling "dri" and "glx", by  adding 
        #Load "dri"
        #Load "glx"
        Disable         "dri"
        Disable         "glx"
to the "Modules" section in my xorg.conf file. This of course disabled 3D for me, but at least I had my laptop running on Linux. I ran it like that for a couple of days, then I accidently discovered System -> Administration -> Restricted Drivers. I found that my Ati driver wasn't checked. So I checked it and rebooted. And to my surprise, everything works fine now. I've been enjoying Ubuntu on full graphics withouth any kind of freeze for at least 48 hours now. So I believe something as stupid as chekcing the right driver off in Restricted Drivers resolved my problems. And again it's something very simple that I have wasted so much of my time on. 

It probably doesn't matter anymore, but my laptop is an ASUS W2000. Just for the record. :D

Well, I'm happy I can finally run Linux. It's such a great feeling knowing that almost every piece of software on my laptop is open source, and that almost none of it is Microsoft (dual boot for school and games). And that I can still achieve everything that my friends (who all refuse to put some effort into Linux) can, and sometimes better. 

I'll try to install Damn Small Linux on an old Pentium III I still have lying around here to see if I can get it to run again. 

@Everyone: thanks for the help. More people would switch to Linux if they realised what a great supportive community it has.

---

