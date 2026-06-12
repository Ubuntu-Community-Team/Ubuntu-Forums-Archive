---
title: "speech recognition for young student"
date: 2007-12-04
forum: General Help
---

### Post by gobbles414 on 2007-12-04
Hi all,

I have read some other threads in these forums regarding speech recognition in Ubuntu. But I have a specific question that I don't think has been asked yet... A young friend of mine recently switched from Windows to Ubuntu Linux. :guitar: My friend is currently in junior high school (a.k.a. middle school). It seems that it is difficult for my friend to type on a computer -- even with word-prediction enabled in OpenOffice. He can use a keyboard and mouse. But he has difficulty with handwriting and typing. My friend's mother called me yesterday on the phone and **asked if Dragon Naturally Speaking 9 will work in Linux.** She wants to get my friend Dragon 9 as a Christmas gift. I have read some encouraging reports at the [Wine Application Database]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077"). But my friend is not very good with computers. So any solution that you help me to design must be able to survive system updates, including updates to the kernel.

**Some questions and comments**
Is there a native Linux alternative to Dragon that works well with OpenOffice? Or, are there any other commercial speech recognition programs besides Dragon that might work well in Wine? My friend is using an older Dell desktop. The maximum RAM is either 512MB or 1GB. Surely the RAM is 533MHz speed or slower. Can dragon run well at those specs even in Windows? If a virtual machine or dual-boot setup is required for speech recognition, my friend may switch back to Windows.

Thanks in advance for your advice!

---

### Post by gobbles414 on 2007-12-05
bump

---

### Post by Sef on 2007-12-05
In [Wikipedia]("http://en.wikipedia.org/wiki/Dragon_NaturallySpeaking"):

> In addition, certain versions of NaturallySpeaking (7,8,9) can be run on Linux operating systems using the WINE open-source implementation system. The implementation does not give full Windows functionality, concentrating instead on text-recognition capability using the included DragonPad.

[Ubuntu Howto]("http://ubuntuforums.org/showthread.php?t=168711"): Naturally Speaking and 6.06.   This may or may not work on Gutsy.

---

### Post by gobbles414 on 2007-12-06
Hi Sef (and everyone),

Thank you for your comments. Do you or someone you know have any personal experience with Dragon in Ubuntu? I cannot advise my friend's mother to spend the more than 100USD it costs to purchase Dragon 9 if it is not even going to work. It would be nice if there were a free trial of Dragon 9 available for testing! My friend is currently using Ubuntu 7.04. I doubt that he would be willing to downgrade to Ubuntu 6.x. But he probably wouldn't care about upgrading to 7.10.

I just got an email from my friend's mom with a system model number. My friend is using a [Dell Dimension 4600]("http://reviews.cnet.com/desktops/dell-dimension-4600-pentium/4507-3118_7-30529709.html?tag=sub"). Here is a link to [Dragon 9 system requirements]("ftp://ftp.scansoft.com/pub/datasheets/ds_DNSPref9.pdf") (requires a PDF reader). As you can see from the links, my friend's computer technically meets the system requirements for Dragon 9. But I am concerned that the slow RAM speed (333MHz) might be a problem. Incidentally, PC World has rated the Dell Dimension 4600 as one of the 10 worst PCs of all time.

I look forward to reading your replies.

---

### Post by Steveway on 2007-12-06
Doesn't IBM have something called ViaVoice for Linux?
You should take a look at Linux-natives first.

---

### Post by gobbles414 on 2007-12-06
Hi all,

Would Philips SpeechMagic work in Ubuntu?

---

### Post by gobbles414 on 2007-12-07
Steveway,

Thank you for your reply. Everything that I have read suggests that ViaVoice for Linux is old, unsupported, the recognition is not as good as Dragon, and as I recall it is necessary to purchase a license. Am I incorrect? If so, please tell me so that I can investigate further.

---

### Post by gobbles414 on 2007-12-08
Hi all,

I think that my friend's mom is going to need to order Dragon or some other speech-to-text software sometime in the next few days. Otherwise my friend may not get the software on Christmas Morning. My friend's mom has the following opinion: "why should I get this program if only parts of it will run in Linux?"** It is a minor miracle that Dragon's speech-to-text features are working in Linux!** But due to the price of Dragon software, my friend's mom also wants vocal commands to control mouse movement, window behavior, and program launching -- like they would in Microsoft Windows.

It is starting to seem like my friend will have to switch back to Windows. That is really unfortunate because the last time I talked with my friend, he was very excited about being a Linux user.:( **Any additional ideas before I make one last report to my friend's mom?**:confused:

---

### Post by rvk on 2007-12-11
If your friend really needs good-quality speech recognition, then perhaps he should switch back to Windows.  However if someone helps him with installing DNS under Linux then that could be a solution, especially because not having to type can already be enough help for him.

You can also try if it's possible to combine DNS and
[Gnome-Voice-Control](http://live.gnome.org/GnomeVoiceControl).  That might be an ideal solution, but I don't know if the two can be combined (I don't see why not, but I've never tried to install DNS under Linux myself).

Whatever option you advise, I think both you and your friend should consider donating some speech to the [ open-source speech recognition project VoxForge](http://www.voxforge.org). That will eventually help projects such as Gnome-voice-control to become a good substitute for proprietary software.  Perhaps even superior!

---

### Post by gobbles414 on 2007-12-12
Hi rvk,

Thank you for the VERY informative links. I really don't think that my friend's old Dell is going to be powerful enough to run Dragon 9 in any operating system. It technically meets the hardware requirements. But the RAM -- and probably hard drive as well -- runs at a very slow speed compared to more modern hardware. Regardless, I think that my friend's mom will not be satisfied with the current limitations of Dragon in Linux. I have encouraged her to ask my friend if Ubuntu or Dragon is more important.

---

### Post by rvk on 2007-12-12
Glad that I could offer some help.  I think you're right about the specs being a bit too meager to run DNS 9.  At work I run it under Windows XP, but my office computer is very decent (2 GB & duo core).

If your friend really needs speech recognition (and it sounds like he does) he should probably consider a new system or an old version of DNS.

On a new system he could also consider using Windows vista, since that offers speech recognition built-in and I think regarding command and control it might be better than DNS (assuming that it's available in his language).

Naturally I would rather recommend Linux, but I don't want your friend's life to be awkward.

Please consider donating some speech to the VoxForge project so this injustice will one day cease to exist (and help me spread the word).

---

### Post by gobbles414 on 2007-12-12
rvk,

Of course, I will do anything that I can to help Linux compete with Windows! You can count on my support of open source speech recognition projects. Question: Isn't the built-in speech recognition in Vista really bad? Click [here]("http://www.youtube.com/watch?v=2Y_Jp6PxsSQ") for the infamous Vista speech recognition video. How accurate is the DNS 9 that you use at work and how does it compare with the accuracy of Vista's speech recognition?

---

