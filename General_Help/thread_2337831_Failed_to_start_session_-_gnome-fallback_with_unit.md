---
title: "Failed to start session - gnome-fallback with unity disabled"
date: 2016-09-21
forum: General Help
---

### Post by ben5 on 2016-09-21
We have Ubuntu 14 on a bunch of old desktops.  Unity runs terrible so I use gnome fallback.  The people who use the PC's will mess around with stuff, so to try to prevent them from being able to switch it back to unity I do this

mv /usr/share/xsessions/ubuntu.desktop /root/xsessions-backup/ubuntu.desktop

This normally removes the unity option.  But recently some PC's are getting a "failed to start session" when user tries to login.  I suspect it is related to the whole unity thing.  I am remote to these PC's and there are hundreds.... but I have them dialing in to a central server so I can run scripts on them easily.   trying to figure out the best way I can fix these PC's.   And preferably prevent the issue, but if not, atleast be able to fix it easily with a couple CLI commands. 

Any suggestions?

---

### Post by TheFu on 2016-09-22
Use **ansible** to maintain the config you want.  Why is unity even installed on the machines at all? Purge it.  OTOH, if local people have completely open sudo on the machines, it will   never work. Lock down their sudoers to specific commands necessary and no more.

---

### Post by ben5 on 2016-09-22
The users have no sudo access. they are "Standard" users.   All they need is a web browser and ssh to our server.  They are call center agents and do surveys over the phone.  The surveys are either delivered in browser or terminal. 

It was a couple years ago when I first nailed down most of the config for these.... but Im almost sure I would have tried to just uninstall unity first.  No need for it.... so I would guess I ran into some sort of issue which drove me where I am... maybe not....

I think the login screen is still unity.... is that right?  what does that look like if unity is removed?

---

### Post by ben5 on 2016-09-22
ansible looks crazy expensive.... $10k/yr for self-support for 250 nodes!! (And we have 300+)   Unless I am looking at the wrong thing :-)

---

### Post by TheFu on 2016-09-22
> **ben5 said:**
> ansible looks crazy expensive.... $10k/yr for self-support for 250 nodes!! (And we have 300+)   Unless I am looking at the wrong thing :-)

Ansible is free - F/LOSS.  Sure, you **can** pay money, if you like, just like you can pay redhat for RHEL instead of using Fedora/CentOS.  I only know companies who insist on paying use that. Most of the world doesn't.  If you need them to come in and setup everything - you should pay.

The login manager is your choice. Pick one. Try gdm or lightdm.

In a situation like yours, I'd probably deploy **TinyCore** with only the required apps on the machine, nothing else.  There machines will be scary fast that way, assuming all the software will work with a minimal Linux.  Plus nobody will complain they need faster CPUs or more RAM or a larger HDD. TinyCore is 64MB in size. Call that a bonus.

BTW, I've designed and deployed call center systems in a prior life - inbound calls only. No outbound except to emergency services. Couldn't use Linux - proprietary, required, software.

---

### Post by ben5 on 2016-09-23
Thanks!  Sorry to be dense...  Am I not looking at the right thing here?  It looks like it is saying that the "self support" / "support not included" version still costs $10k+ for us.  [https://www.ansible.com/pricing](https://www.ansible.com/pricing)  

I'm guessing maybe there is like a different page for the actual open source/free version.  


How hard is this to set up?   I was briefly looking into Nagios for monitoring our few linux servers.... mainly just to monitor hard disk space so a full volume does not sneak up on me.  After a couple hours of toying around and practically a dozen people advising me that nagios is a huge pain to get setup, I abandoned it and decided to script the simple solution I needed myself.  All that extra monitoring would be nice but not necessary.


I digress - The point is that I'm trying to ask if this is similar to what I have been told nagios is like.  Not at all simple/intuative/quick?  Or is it more intuative/easy/quick to use?


I assume TinyCore would be a whole new install?   Not something I could deploy with a script?   


The very beginning of all this I was doing some investigation.... i rememter trying lubuntu and other various distros.... I forget exactly what my issues were with all of them, but in the end I settled on Ubuntu.  Im comfortable little and ask commandline, but working with desktop environments and getting into details about packages and dependencies, etc not so much.... 


The main criteria I needed to fill....
1.  Needs a web browser.... And preferably not some crazy light web browser.... but a good/reliable one that can handle whatever is thrown at it.   When we need the web browser it is for web surveys programmed by other companies.    Web surveys tend to be rather simple but every once in a while people do crazy stuff.... 
2. Needs to ssh to our main server and web links displayed in this need to be clickable.  
3. Needs good office app on the off chance they need to open a word doc for some job. 
4. I want to be able to access remotely via ssh or via vnc.  I think this is actually one of my biggest pain points....   I don't know why but it seemed like there are a dozen VNC options and none of them is turnkey as I'd like.
5. The actual set up should be as simple as possible.  I am remote to the call center so I am giving written instructions to the people actually doing these installs.
6. good driver support and runs OK on old PC's.  


Since we already have everything installed we are pretty unlikely we will embark on reinstalling all 300 of these anytime soon.... Unless perhaps you think I can get a TinyCore setup with a fully automated install.

---

### Post by TheFu on 2016-09-23
good driver support is unbelievably vague. I suppose, if the HW you choose has drivers built into the Linux kernel, then you would call that "good driver support."  Distros don't have "driver support." The kernel does.

"old PCs" is highly subjective. Ubuntu is planning to drop 32-bit releases. Are you prepared for that?

ssh works on every Linux I know. Non-issue. Not a distro question.
VNC - haven't used that in about a decade. x2go is 2-3x faster and uses ssh tunnels as part of the NX protocol.

You can load libreoffice on any Linux. This is NOT a distro question.

Don't think I've ever seen web-links not clickable inside a browser. Don't understand that question/issue.

None of the large browsers are safe. Seriously. NONE. Definitely not FF or Chrome or Opera. These things are so complex they are OSes with all the problems an OS has. If other companies are programming your web surveys, then you should be making the requirements.  Tell them - "must work with Dillo" and that will make them work with pretty much every browser made.  Dillo doesn't support javascript, which I consider a huge security feature.

I think your Microsoft background isn't helping. Unix has a very different way of working AND the community is very different.  Paid support isn't usually better than you'd get on forums, unless you pay for someone to fly in and setup stuff.  Heck, for $2500/day (8 hr max) + expenses, I'll help out on a week-to-week basis. I'm a little old and crotchety - don't like noobs much, so if you can keep those people away, that would be a big help.  If the work is remote, the price drops, slightly. ;)

I don't use nagios, but if you use ansible, there are pre-existing playbooks for setting it up.
Ansible takes about 30 minutes to understand and start using - they have a great into video.  The competition, puppet, chef, cfengine, and a few others takes about 2 weeks of training and 3 days to get going.  Ansible is GPL. [https://github.com/ansible/ansible](https://github.com/ansible/ansible) That's important.  F/LOSS software licenses are something you should learn ASAP so as to know when people are trying to sell something that is absolutely free already.  Nothing wrong with them "selling" it, provided it is a "reasonable" price - reasonable is not defined, however. All of this seems strnage to people with a Microsoft background. They've trained you to think that if someone doesn't require payment, then that software is crap.  That just isn't the case.

Ansible is on github.  You don't need their $10,000 GUI. I don't know anyone using it in the real world, but I suppose people do.  I find the CLI version extremely capable and can't see how a GUI would make it better.  I have that issue with most GUIs, though I'm starting to think that browsers with a GUI might be better than lynx ... not quite convinced yet. ;)  Ansible releases are named after Led Zeppelin songs. (Releases prior to 2.0 were named after Van Halen songs.) That sold me immediately!


TinyCore is a Linux OS. How you deploy it is up to you. You'll need to play in a lab to get familiar.  Spend the 20 minutes and see if it is something you can use.  It is definitely smaller.  I know that a large IT firm did many thousands of system deployments based on tinycore a few years ago. Lost contact with my friend there, so don't know if it is still going or not.

---

### Post by ben5 on 2016-09-23
Thanks!  To be clear the clickable links is in the ssh/terminal window.  i.e. so they can be looking at a terminal based survey that displays a web link and be able to click it instead of having to copy and paste into browser. 

To be clear, I don't have a windows background.  :-)  Well... I mean other than my desktop... just to many apps I want are windows only.  I prefer linux for servers though... so you don't need to sell me on open source software.... I know there is tons of great free stuff.... :-)

Unfortunately the business this is for accepts jobs left and right, even when we are overbooked, we accept jobs and figure it out.  (not the way I would run the company, but its not my choice)  Anyway, so the whole "do it our way or we won't run the job" thing won't fly well here.  Often we are working on a job that's already programmed, and has to finish in 2 days with hundreds of dialing hours needed, etc...  Other call centers may turn it down, but our niche seems to be taking all jobs... always... 

Anyway - thanks again for all the info - I will try playing around with this when I have some time.

---

