---
title: "Help! Need recommendation for a office network setup."
date: 2022-10-19
forum: General Help
---

### Post by nosyarutnubu on 2022-10-19
Good day, I'm new to the forum and hoping to find recommendations here.


I'm a new IT in a small enterprise here in the Philippines, planning to improve our network setup.


We have 2 offices, a main with 50 PCs and a branch with another 50 PCs located to another city. Currently using NAS as file sharing on each branch and connected thru a VPN. I want to implement an Ubuntu Server with Samba to be used as the file sharing server, and use the current NAS as the backup.


Is this okay? Any disadvantages? I also want to improve the security but I don't know where to start. Please leave some suggestions. Thank you very much!

---

### Post by ian-weisser on 2022-10-19
What are the problems that your enterprise is encountering that these changes are intended to solve?

"Security" is a very broad topic. What security concerns do you have?

---

### Post by nosyarutnubu on 2022-10-19
Hello sir, the reason why I am planning to improve our security here is because recently we got hacked. The attacker got our files and wants some money for it. The company declined since we have a backup of the files that was compromised. I don't want that to happen again that's why I want to improve the security here.

---

### Post by QIII on 2022-10-19
Hello.

The first step in determining how to "improve your security" is to understand how you "got hacked", by which I assume that someone was able to gain access to your network, either from outside or from the inside, and gain access to your data.  What do you mean by having compromised files?  What happened to your files?  Were they corrupted?  Were they deleted?  Were they encrypted? What sort of data was it?  What sort of files?

What security is it that you want?  Keeping someone with physical access to one of your machines from doing something wrong?  Securing your backup files from tampering?  Keeping your network safe from external intruders?  As ian-weisser said, security is a big, extensive subject that many of us have been working on for many, many years and we still find ourselves surprised from time to time. Books are written about "improving security".  We can't possibly cover it all.  We can give you a few slices if you will tell us exactly what you want.  After that, you will need to do a LOT of study and research.

Unfortunately, security is not achieved at a snap of the fingers.  It is not a five-step method that fixes everything for all time.  Security as a continuous process of improvement in many, many areas of your enterprise.

---

### Post by ActionParsnip on 2022-10-19
What OS are the clients using?

---

### Post by nosyarutnubu on 2022-10-19
Hello sir @QIII, I apologize for the late reply.

I was not here when the incident happened, it occurred a month before I was employed here. The management told me that we were hacked from the outside, they didn't really knew it immediately until they noticed that some files were missing. They thought at first maybe the NAS was at fault since the files are just there. Until they got a text saying if we want the files back we need to provide some chunk of money, you know like some television drama. The management didn't really tolerate the attacker since we have a backup of the files offline, it's not updated tho but can rebuild some of the missing files from there. The type of files that were compromised was composed of normal office files, like sales report, probably the employees record from the human resources, company financial report etc.

A month later I was employed here. All the user's computers was re-installed with new windows OS, saying the attacker could still have access somewhere. They bought a new NAS and that's it. There is no firewall or whatsoever. Does Cisco's router's count as firewall? I'm not really sure. The reason why I don't know a lot of things about networking is because I focused on hardware troubleshooting in this past few years, just technical support jobs and basic network troubleshooting, that's it. 

Now, I want to learn about security. Colleagues told me to study Linux that's why I got the idea of having an Ubuntu. But how do I keep outsiders from accessing our network? Where do I start? A few slices of suggestions is all I need sir, then I'll study all the way from there and will keep improving. Thank you very much.

---

### Post by nosyarutnubu on 2022-10-19
Hello sir @ActionParsnip, everyone is on Windows 10.

---

### Post by ActionParsnip on 2022-10-20
NFS4 or Samba will give you an easy way to share to Windows clients.

---

### Post by ian-weisser on 2022-10-20
For folks diving into security who can understand rapidly-spoken english, the [Ubuntu Security Podcast]("https://ubuntusecuritypodcast.org/") is a great starting point.

Episodes [152]("https://ubuntusecuritypodcast.org/episode-152/"), [153]("https://ubuntusecuritypodcast.org/episode-153/"), and [154]("https://ubuntusecuritypodcast.org/episode-154/") in particular are an excellent beginner's guide to server security.

Don't be fooled by the patient-schoolteacher tone of the tutorial -- Camila is a professional security engineer who is clearly a real-deal expert. She has cleverly arranged the material well for beginners in a non-interactive environment. I've been following Ubuntu security for almost 10 years, and she taught this old dog a few new tricks.

---

