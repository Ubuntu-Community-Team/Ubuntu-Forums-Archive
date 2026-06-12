---
title: "Accused by Network Admin of Having a Virus"
date: 2007-02-13
forum: General Help
---

### Post by troymcdavis on 2007-02-13
I've searched on the forums for threads about hacks and viruses, but all that seems to come up is threads where something happens and the user suspects it is a virus. I however, have a the opposite situation. I attend a university, so I use their network in my on-campus dormitory. However, when I tried to connect this morning, all my webpages directed a page that read thusly:
> We apologize for this interruption in your network service, but we have detected virus traffic from your computer. You are now isolated to protect other users with just enough access to get your computer fixed.
Now, I'm down with protecting the network, so this doesn't bother me (I don't want to be left without internet because someone opened an attachment in an e-mail labeled "Jessica Simpson wants to go on a date with you!"). Since I boot Windows to do homework for one of my classes and I'm confident in the lack of malware for Linux, I assumed it was on that partition, so I just did what the webpage told me on that partition (BTW: the web app that runs through these steps doesn't work with Linux or Firefox).

However, when they called to confirm everything, they said the activity occurred last night, while my computer was booted in Ubuntu. I really don't want to be responsible for such activity (plus, who wants to be on IT's bad side?).

I'm downloading and installing all available updates, and once I finish typing this, I will kill my apache server. But what else should I do? What processes should I look out for? Is there a list of normal/trusted processes (for instance, I don't know what esd is... where can I look that up?)? What steps can I take to ensure that this sort of activity is ended?

Last, I would like to add, this morning, when I turned opened my computer to unlock it, my password didn't work. The same also happened yesterday morning. I had to put in the liveCD, open the root shell, mount the partition, and change the password. Are these related? What could be causing this?

Thanks in advance for any/all help.

---

### Post by MCSE_Crossover on 2007-02-13
You could be potentially passing virii to Windows users if they are local on your machine and you email them - they could be attached to a forwarded email that you recieved and passed on...although they shouldn't be running as a process on your local machine. I would see if you can get some detailed information from your IT department. If they detected malicious traffic, there should be logs indicating what type of traffic is originating from your machine and why it got flagged. They should be happy to work with you.

Concerning your passwords, there are root compromises that can occur, although they are pretty rare if you are careful what you are installing and from what sources. There are some available in the respositories -- namely *rkhunter* and *chkrootkit* and possibly a few more. Also, you could try running ClamAV. I think that detects Windows virii that may be sitting dormant on your machine.

I would try to track your IT shop down though and see exactly what they detected.

---

### Post by troymcdavis on 2007-02-13
Thanks MCSE. They isolated my internet usage again, so I'm heading to their offices  tomorrow. The person I spoke with over the phone seemed pretty cool with the fact that I had Linux, but this campus is so anti-FOSS that it confuses me. Shouldn't our academic institutions be promoting intellectual freedom? End rant.

Any more advice/tips/info appreciated!

---

### Post by Arisna on 2007-02-13
I wondering about the Apache server.  Could IT have mistaken it for some kind of spamming/e-mail server somehow?  Most end-user Windows machines aren't going to be running many or any services.

---

### Post by nkassi on 2007-02-14
My guess is your are running a mail server or web server or that you installed a package such as rwho that is sending out packets asking for something. In dorm, you are pratically prevented from running anything suspect. Most universities will flag you for smtp traffic if you  are not a registered mail server.

Ask them for the details of what caused the alert. Also install firestarter and block all outgoing   connection (it will allow normal stuff through)

Nic

---

### Post by dcstar on 2007-02-14
> **troymcdavis said:**
> Thanks MCSE. They isolated my internet usage again, so I'm heading to their offices  tomorrow. The person I spoke with over the phone seemed pretty cool with the fact that I had Linux, but this campus is so anti-FOSS that it confuses me. Shouldn't our academic institutions be promoting intellectual freedom? End rant.

Any more advice/tips/info appreciated!

If you are running things like FTP clients, then the random ports they use can trigger bone-headed monitoring programs - likewise for a SMTP server that you may be using on your box.

The Ubuntu auto-update process could also be upsetting their assumptions of people only going to Microsoft for update traffic.......     :? 

You need to find out **exactly** what traffic is triggering their paranoia!

---

### Post by MCSE_Crossover on 2007-02-14
Waiting on users input from the IT department...then we can trouble shoot further. Great support everyone! A few ideas that I hadn't even thought of that could potentially be causing the issue.

---

### Post by troymcdavis on 2007-02-16
I'd like to thank you all for your input and give you a quick update:

I took the computer to ITS and I explained my situation to him. He made a face when I told him the virus was supposedly on my Linux partition (as in he knew of the lack of malware for Linux). He made it clear that I had two options:

1. I surrender my computer to ITS for **FIVE DAYS** while they sift through all my personal data to find the virus. Since they aren't too knowledgeable on Linux, they don't expect to find the virus and when they don't, they will reformat it and install Windows XP again. During this time, they will give me a loaner computer, but until my computer clears security (after they reformat) my network access will still be blocked.

2. I bite the bullet and let them reformat with a one day turnaround.

He explained he was a grunt and that the higher ups weren't going to be sympathetic to my plight, since we are required to run XP. Being without internet even this long has been near academic suicide, so I went with the latter. Sorry all your help fell by the wayside. I will take your considerations into account to make sure this doesn't happen again in the future.

---

### Post by nsleiman on 2007-02-16
I dont know why i had the feeling that IT pros will find out thats all a mistake and u continue on ubuntuing :) good luck.

---

### Post by troymcdavis on 2007-02-18
While I appreciate and laud your enthusiasm and optimism, nsleiman, my computer was returned to me about three hours ago with a clean install of Windows and some software. But I am posting from the Edgy liveCD (while reinstalling Ubuntu!). So have faith that I'm not discouraged and I'm sticking around. The community is just too great to go back to XP.

---

### Post by evilc on 2007-02-18
I have been reading your posts and agree with the responses you have been given, as far as the uni reformating your comp most uni's don't run Linux and all require you to use *Mickysoft. *Stickwith your principles and maybe add clamav to it (just for them):)

---

### Post by alan_daniel on 2007-02-18
I just ran across this thread and wanted to share a similar experience I had last year to maybe help you for the future. I was also in an on-campus dorm last year using the university's network, but unlike you I had two separate computers, one dedicated to windows and one for linux (we are also required to have windows). I woke up and checked my email one morning to find out that they had isolated my linux machine for what they called a virus. Immediately recognizing the slim chances that the computer actually had a virus, I went searching through logs in /var/logs/ and couldn't find anything. I finally decided to check the authorization logs (the logs of all attempted and successful logins), and I found SEVERAL thousand lines (i think it was 15,000) of failed logins.

I remembered that I had been running an ftp server (and ssh) on that machine so that I could easily and quickly transfer files between computers (it had its own public ip that stayed the same because the computer was rarely off). After about an hour of sifting through that log, I discovered that someone had tried many times to log in to my computer (I think via the ftp port), and had eventually succeeded. I did a dns lookup and found that the ip was from Korea. After emailing the IT department and sharing the log with them, they looked deeper into the problem and realized that I was right and that the hacker was using my computer to launch an attack on some computer up in Canada. That's where all the high traffic came from, and they assumed it was a virus because they are so common on windows machines (they didn't realize it was linux).

Just something to think about...I know it doesn't help now, but from what I read in your posts, it seems like it could be a possible explanation.

---

