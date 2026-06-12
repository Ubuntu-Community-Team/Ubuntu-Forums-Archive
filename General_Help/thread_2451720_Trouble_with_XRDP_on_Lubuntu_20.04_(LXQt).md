---
title: "Trouble with XRDP on Lubuntu 20.04 (LXQt)"
date: 2020-10-09
forum: General Help
---

### Post by soundacct on 2020-10-09
Hi,
can anyone offer any help? I am new to linux. Please bear with me, I'm a lifelong windows user (trying to reform). I am still at the point where if there isn't a gui to interact with, I can do little more than  copy / paste commands from google searches.

I have XRDP installed and working (sort of) but the desktop looks different when i logon remotely, and I am not able to do certain things, such as install software or update software when connecting remotely. Does this mean XRDP is using a different "session"? I am not sure if i understand what that means.

I don't know what is the correct terms are in regards to linux. In windows, when I logon to a computer with a given username / password, everything looks and acts the same whether I am local or remote. This does not seem to be the case using XRDP with Lubuntu, so I am not sure how to phrase my question.

I have spent a few weeks asking google to no avail.

I have this machine nearly working - the idea is to have a plex server that I can deploy at my sister's house, but I need remote access to maintain it. My internet is not fast enough to stream 4k video remotely. I have the NAS at each location correctly file syncing, I have edited fstab to mount the NAS working correctly, and I have Plex Media Server working properly. It's been a steep learning curve, but if i can get past this last hurdle I can finally be done with windows.

thanks in advance for any help anyone can provide.

---

### Post by TheFu on 2020-10-10
There are 50+ different GUIs for Linux. About 10 are really popular.  Due to the way that remote desktops work, almost always the GUI and GPU heavy desktop used by default would make for a terrible remote experience, so some software automatically uses a "fallback" DE or GUI.  The differences between most GUIs are completely superficial, unless you change from KDE to Gnome3. Those can appear to be completely different and all the GUI settings will be different because they are not the same.

First, with every Linux release, some changes happen. Some are tiny and nobody notices, but others are large and completely in-out-faces.  It just depends.

Second, almost all Linux software is built in layers of other software created by different teams.  This applies most to GUI programs, because they add 3+ more layers than the CLI/Shell counterparts. As each layer changes over time, functionality changes.  If you want the fewest changes over time, get below the GUI and use the CLI versions.  Many commands I've been using since the early 1990s haven't changed and support all the same options today as they did back then.  Most have added a few extra options that make out lives easier.  
Typical layers for GUI software: [https://en.wikipedia.org/wiki/File:Schema_of_the_layers_of_the_graphical_user_interface.svg](https://en.wikipedia.org/wiki/File:Schema_of_the_layers_of_the_graphical_user_interface.svg)
For GUI programs, here's a diagram that shows the timeline of changes:
    [https://upload.wikimedia.org/wikipedia/commons/6/6e/X_window_system_desktop_environments_timeline.svg](https://upload.wikimedia.org/wikipedia/commons/6/6e/X_window_system_desktop_environments_timeline.svg)

Gnome is the main GUI library used today: [https://en.wikipedia.org/wiki/GNOME](https://en.wikipedia.org/wiki/GNOME)

"Session" is a generic term, just like "directory" is a generic term. Depending on the modifier, it can mean completely different things.  Usually, as you've used it, it is mostly about a login "instance" which holds dynamic data for the userid, for that session, to be used and available for all other programs that are started.  Understanding how a login begins, which initialization files are involved, how the GUI environment is selected, initialized, setup, run, and displayed wouldn't hurt.  But usually, it is easier to begin with a non-GUI login session and learn that first, because that all happens for both non-GUI and GUI logins.  And it is usually easier to begin with a what happens when you run a non-GUI program in a terminal first.

Basically, you seek a simple answer, without having the background to understand, yet.  None of this is hard, but there are lots of steps involved, even for how a non-GUI program runs from a terminal.  It is common in Unix/Linux for skills to build on prior skills and understand. That's why you don't find a book with every answer for how to do everything inside.  Unix systems don't have 1 way to do most things. They are extremely flexible and users are expected to learn the building blocks for how to use a few simple tools to build a more complex tool that exactly fits their needs. The system was designed for that purpose from the beginning.  The idea that a Word Processing program would be built and include 50,000 "features" was not part of the plan.  Unix systems have about 150 text processing tools on them today. Each with 5-20 options.  There are many more than 50,000 ways those tools can be used together to accomplish a goal.  The fact that YOU want to point-n-click doesn't matter to Linux/Unix.  
I used to teach Beginning Linux at a local University club.  I was always being asked "how to learn linux" [https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux) is my answer, mainly for Windows people who want to learn, not dabble.  Dabblers will never actually learn and will become frustrated.  
[LIST=1]
[*]The first link in that blog article is a "Linux for Windows Users" overview. It goes over the most important things that Windows people need to know from day-1 on a Linux system. Even being 6 yrs old, that article is still relevant.  
[*]The 2nd link is what minimal things are needed to maintain an Ubuntu Desktop system. I've been updating that article for years now. It has been republished.  
[*]The 3rd link is learning to think the Linux way. The Windows way of thinking is very, very, different than the Linux way. Until we learn to think differently, we'll forever be searching for some new tool that does 1 job, when we could used 2-3 existing tools on our systems to accomplish the same thing faster, automatically, and schedule it to run every day, once a month, every 5 minutes or whenever we like. It is a different way of thinking. Truly.
[/LIST]

> I have this machine nearly working - the idea is to have a plex server that I can deploy at my sister's house, but I need remote access to maintain it. My internet is not fast enough to stream 4k video remotely. I have the NAS at each location correctly file syncing, I have edited fstab to mount the NAS working correctly, and I have Plex Media Server working properly. It's been a steep learning curve, but if i can get past this last hurdle I can finally be done with windows.

Plex. I use that. It is available to me from anywhere in the world. Plex is really trivial to setup, actually. I don't have a plex account and never "login" with any plex client. When I'm remote, I use either a VPN or ssh-tunnel via a SOCKS Proxy to access all the plex media using the web-GUI.

For remote access, I use ssh.  ssh is how Unix systems communicate. There are probably 50 different tools based on ssh and it can be used as a Swiss Army knife to connect systems together in a secure way.  For text interfaces, distance doesn't matter. I've managed routers in central Asia from the USA using ssh, for example.  About 1% of the time, a GUI is handy, so I'll use x2go for remote connections over the internet. It has 1000x better security and performance than xrdp or any VNC.  People who switch usually say the performance of x2go vs whatever they used before is like comparing day to night.  On the same LAN where security can often be relaxed, there are more convenient and faster methods, but over the internet, x2go is the best answer I know today.

I don't know what you mean by "mount the NAS" at each location. That scares me a little from a security standpoint.  If this is just a local LAN mount, then I'm not scared.  If the storage is mounted over the internet, very few protocols are secure enough to be used in that way without a full VPN that you host on 1 end of the connection.

Copy/paste of terminal commands over the internet is very dangerous.  In my classes, I'd have students visit a webpage, copy some safe-looking commands, only to see those commands have about 50 hidden "bad" commands when they pasted.  I did that to make a point. Don't trust stuff you see on the internet.  If you copy/paste, always paste into an editor first, unless you know, 100% that you can trust the other person and trust the website. By pasting into the editor, those 50 "bad" commands would be seen, in addition to the 2 expected commands.  It doesn't take 50 commands to provide a back door into a Linux system that can be used remotely.

I wrote a bunch here and I'm pretty certain I didn't answer any questions above. Sorry.  There is a book, a free, no-hassle, book that teaches Linux stuff in a good order: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php).  Remember, that more advanced skills always build on less advanced skills in the Unix world, so we all have to start out like a baby growing up into an adult with our Linux skills.  In the beginning, we can't lift our heads or even roll over. Eventually, we'll be running, sprinting and doing parkour - ninja stuff.

Oh, and xrdp seems to be trouble for many users. That's what 2 minutes of google searches have taught me.

---

### Post by soundacct on 2020-10-17
Wow, thanks for taking so much time to write back and gather those links for me! Looks like that will take me a bit of time to digest.  

Sorry for the long delay in response, I started a new job on Monday and they have been pounding me with technical training. 

You’re quite correct - I am just dabbling and not trying to master Linux.  Of course I realize that is why I am having trouble in the first place, however that is not, as you suggested,  why I am frustrated. I mean no disrespect, but what’s frustrating is being told that I should go down some rabbit hole of reading countless articles with no earthly idea of how long that might take....or even if I am smart enough to ever understand.

I don’t expect help like I would at Microsoft’s forum (after all, I pay them to spy on me - that should be worth a little tech support), I am requesting help. If you can’t or won’t help, why clog the forum (and google) with unhelpful search results? With your detailed explanations and links, I do honestly believe you are trying to help and I am trying not to be ungrateful.

That said, I do have everything running properly except for remote access (to the desktop - plex remote streaming is working fine). 

I realize and appreciate that Linux is a community of mostly volunteers supporting each other for free, and that “windows people” often come off as entitled brats in these forums. I don’t want to be “that guy”.
 
I will humbly point out however that help requests such as mine usually result in at least one response with some variation of “Linux is not windows...you need to unlearn and relearn everything from the ground up...it’s actually easier than windows”, “actually, once you get used to the terminal everything is way easier”, etc.,.

it is objectively more difficult for a new user of any Linux distro to use effectively than say, windows, macOS, android, iOS, or chromeOS (yes, I know it’s Linux), and it is not everyone’s objective to become an expert with Linux. That doesn’t mean that some people might have a specific use case for Linux once in a while. There are many distros designed specifically to be beginner friendly, but when beginners get stuck and ask questions they invariably get unhelpful responses instead of actionable instructions. 


I am just trying to help out my brother-in-law so he can watch a little TV. And I am almost there.  He is a stay at home dad with a very, very bad back, and one of his kids is autistic, the other has ADHD. Also, my sister has been will be permanently working from home, so that dude must be some kind of Saint. Pretty much, TV and medical marijuana is all the guy has going for him.  Especially during COVID heading into the winter. 


Yes, I seek a simple fix for a one-time problem, if such a fix exists. I believe knowledge is good, but I have no use for Linux mastery, other than personal satisfaction I suppose. Such could be said for any field of study. I am already “good enough” with Linux to do whatever I can imagine wanting it for....except for this specific task, this one time. Can anyone help solve this specific issue? Any method of remote access would solve my problem. Does anyone know of a lightweight Linux distro that will run plex that already comes with a built in vnc server? If it is Ubuntu based, I am sure I could handle it from there.  

thx in advance.

---

### Post by ActionParsnip on 2020-10-17
If you are just running updates and installing software then install openssh-server on the Ubuntu side and use apt in a terminal. You don't need the full desktop to do this and it'll be much faster too

---

### Post by TheFu on 2020-10-17
If you want to know "what to type", then ... don't use xrdp or VNC for remote GUI connections, use **x2go** and **ssh**.  None of these will show what is on the desktop on the physical system. That is because of the security built into how login sessions work.  When you setup x2go, only the port used by ssh needs to be open. It is best if that port on the internet isn't 22/tcp. I'd use the router to perform port translation so ssh over the internet 
```
WAN-IP/63022/tcp --> LAN-IP/22/tcp
```
I don't know how clear that is, but basically, get ssh working and secured, then get x2go working. With x2go, using a lighter DE like mate or XFCE would help greatly. If the remote performance isn't pretty good, then tweak the compression and bandwidth settings. Regardless, you won't be watching videos over x2go over the internet, you'll need to use plex streaming for that.  x2go is 2-3x faster than the other options AND secure.

Once plex server is setup and registered with the Plex people, then you can use any plex client to access that media.  I don't use any plex clients, so I don't know how that works.

There are plenty of guides to setup ssh for internet use and how to secure it.
The x2go website has 3 command instructions to setup the server and 3-4 commands to setup the client. The x2go-client is a GUI. You'll figure it out quickly, I'm sure.

---

### Post by soundacct on 2020-10-17
thanks for the advice. I have a bunch of identical machines bought at auction that I use as plex servers for me, friends, and family. we have pretty slow internet around here, not fast enough for streaming 4k to each other - so everyone gets their own plex server at their own home. I don't actually need to use the remote servers, only access them to update software. 

. I'll try to implement this in the morning. Basically, i am trying to get remote access to look and behave exactly as though I was physically there, no matter how slow or poor the connection. I just need to apply system updates and occasionally upgrade plex media server, i don't plan to actually use it for anything else. 

I lack the skillset to do any of that via the terminal. I have an identical setup at home, I have no trouble keeping everything working, has been for years. it's only the remote access that doesn't work. 

thanks for your help

---

### Post by TheFu on 2020-10-17
Weekly system maintenance - all CLI commands
[https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

Much easier than setting up GUI access and wasting time when ssh is 100x easier.  Plus, you have to get ssh working first anyway.

---

### Post by soundacct on 2020-10-18
x2go & ssh quickly got too hard for me.

 is there truly no software that simply installs and works without having to hack commands into terminal? Plex server was cake - i downloaded it, opened it in package manager and everything installed and worked great. is there nothing that simple for remote desktop in linux?

---

### Post by soundacct on 2020-10-18
ok, the problem seems to be that xrdp does not log into the machine the same way as if i were standing in front of the computer. for example, when logged on remotely, i do  not have permission to install software or open folders as root.

is there some way to tell xrdp to log in the same way as it does when i am local?

---

### Post by soundacct on 2020-10-18
Solved it.
I just installed Ubuntu 20.04LTS and enabled desktop sharing

now from another linux machine, I can just use Remmina to connect to it. So I can't remotely administer from windows, but from any other linux machine is ok.

now plex, remote access, everything works correctly.

thanks everyone for all your help

---

### Post by TheFu on 2020-10-19
There are huge security implications between what xrdp does and what x2go does.  On the same LAN, it probably doesn't matter. Over the internet, there is a world of difference. [B][U]No way should anyone use xrdp over the internet.
[/U][/B]

---

### Post by ActionParsnip on 2020-10-19
> **soundacct said:**
> thanks for the advice. I have a bunch of identical machines bought at auction that I use as plex servers for me, friends, and family. we have pretty slow internet around here, not fast enough for streaming 4k to each other - so everyone gets their own plex server at their own home. I don't actually need to use the remote servers, only access them to update software. 

. I'll try to implement this in the morning. Basically, i am trying to get remote access to look and behave exactly as though I was physically there, no matter how slow or poor the connection. I just need to apply system updates and occasionally upgrade plex media server, i don't plan to actually use it for anything else. 

I lack the skillset to do any of that via the terminal. I have an identical setup at home, I have no trouble keeping everything working, has been for years. it's only the remote access that doesn't work. 

thanks for your help

If you are only updating software then use SSH. Its super slim. You don't need the full desktop to just run updates. SSH to the system and run
```

sudo apt update
sudo apt full-upgrade

```

The system is now fully updated.

---

