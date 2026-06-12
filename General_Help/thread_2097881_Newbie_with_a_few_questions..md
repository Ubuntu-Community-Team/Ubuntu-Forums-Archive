---
title: "Newbie with a few questions."
date: 2012-12-24
forum: General Help
---

### Post by xreyuk on 2012-12-24
Hey guys, 

I'm looking to use Ubuntu on my NAS box, which will be doing a couple of other tasks. As I'm a complete newbie, I'm in need of some help. 

I have one hard drive with all of my stuff in, and another spare hard drive of the same size. How should I format these drives for a NAS, and how do I go about setting them up in RAID 1? How can I do it without losing my content already on the disk? (Ubuntu is running off a USB stick)

Secondly, how do I go about sharing them on the network, what do I use?

I would like to use the Wake on Lan feature, and wondered if you could tell me how to set this up?

Finally, how should I go about securing the box correctly, as I want to have remote access to it. The box will running the network share for the NAS, an SFTP server and Sabnzbd+, other than password protecting what I can, and setting up my router ports, what else can I do to keep it secure?

Thanks in advance!

---

### Post by chadk5utc on 2012-12-24
Not sure exactly your setup but I suggest before attempting to create raid backup backup backup. Honestly what Im going to suggest is to get new drives create the raid you want then copy your files to it. Here is a great link with lots to read about security, server guide, firewall Etc

---

### Post by xreyuk on 2012-12-26
Thanks for the information.

Unfortunately I'm unable to get new drives, and will have to do it this way for now.

Can you suggest what to do?

Do you have any information about my other questions?

Thanks in advance.

---

### Post by bodhi.zazen on 2012-12-26
You are asking a lot of questions in a single thread, some of which are more detailed then others.

See:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)

You can use Samba to share files. Alternates would be nfs, ftp, scp, sftp, etc etc ...

For ssh, use keys

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

After reading a bit, post specific questions and we can help a little more.

---

