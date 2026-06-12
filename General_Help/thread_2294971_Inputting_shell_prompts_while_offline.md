---
title: "Inputting shell prompts while offline"
date: 2015-09-15
forum: General Help
---

### Post by Dave_Aoki on 2015-09-15
Hello everyone. I had a Dell mini with Ubuntu installed on it that I was using for school a few years back, but ran into the "configuration defaults for Gnome power manager.." issue and was unable to log in. I tinkered at it a bit but eventually gave up on it. Anyhow, I was talking about Linux systems with some co workers today and it made me think of the mini, so tonight I fired it back up and attempted to get it working. I won't go into too much detail just yet, but I did have a very general (possibly dumb) question:

Do I need to be connected to the internet to input commands in the shell? There were a few fixes I was trying out to rectify the power manager issue, and a couple of them came up as failed attempts; I'm not sure if it has anything to do with the fact that I am not connected to an internet source.. I run off of wifi in my apartment complex. If you do need to be connected I will take it somewhere where I can plug it in; at the moment I have no way of hard wiring it. 

Thank you much! :KS

---

### Post by TheFu on 2015-09-15
local shells do not require any networking.
Remote shells do - usually those connects are through ssh.

Every command has different errors. If the issue is that you cannot open a terminal, try a xterm or lxterm or aterm or ...  if none of those work, do you have a GUI loaded?

Other issues are probably specific to the attempted command - **command not found** means it probably isn't installed.

---

### Post by yancek on 2015-09-15
Failed attempts often give a reason for the failure.  Posting that information if you got a message would help.

---

### Post by efflandt on 2015-09-15
If you are trying to install or fix something that is not already on your system using **sudo apt-get**, like **sudo apt-get update**, **sudo apt-get install** whatever, you would very likely need an Internet connection to be able to fetch the update list or files to install.

---

### Post by Dave_Aoki on 2015-09-16
[SIZE=2][FONT=trebuchet ms]Well, I've found through 'df -h' command that my hard drive is maxed at 100%, which was why I was getting the power management error message. I read up a fix of uninstalling then reinstalling the gnome power manager with 'sudo apt-get --reinstall install ubuntu-desktop'; this apparently worked for some. Upon doing this however (following the successful uninstall of the gnome power manager), it first alerted me of what extra and new packages will be installed, as well as 10.8MB of additional space being used and would I like to continue. I hit yes, then it asks me whether I want to install these packages without verification. 

Next came a couple of 'Err along with what looks like URL's of ubuntu archives. Under each was 'Could not resolve 'us.archive.ubuntu.com'. This was what made me wonder if I needed to be hard wired to an internet source to allow these to be retrieved. It ends with 'Unable to fetch some archives, maybe run apt-get update or try with --fix missing?' 

I then tried 'sudo run apt-get update' as suggested, which then flooded me with a number of 'Failed to fetch' prefix followed by a URL. 

I hope this makes sense and apologize if it doesn't..

Is there a simple way to wipe the hard drive completely to free up the space? I'm not quite sure how I managed to load 6GB of anything onto this little guy, but that's what the directory is showing.[/FONT][/SIZE]

---

### Post by CharlesA on 2015-09-16
Correct. When you run apt-get update it fetches an updated index of the repositories. You need to be connected to the Internet to do that.

What does this return?
```
du / --max-depth=1 --human-readable 2> /dev/null
```

---

### Post by Dave_Aoki on 2015-09-16
Ok thanks, I'll try to take it into work with me to hook it up. 

As for the above code it looks like the space used along with the location to the right.. Is there any specific part of it you're looking for?

---

### Post by CharlesA on 2015-09-16
> **Dave_Aoki said:**
> Ok thanks, I'll try to take it into work with me to hook it up. 

As for the above code it looks like the space used along with the location to the right.. Is there any specific part of it you're looking for?

That is to hide any permission denied messages you'll likely get.

Should give you an idea of where your disk space is going.

---

### Post by TheFu on 2015-09-16
a) Please copy/paste programs AND error messages. Those are actually much clearer and easier for us to understand. Text, not pictures. We want to be nice to people reading here without high speed connections.

b) 6G isn't much space for a GUI install. Sure - for a server install, iwthout ANY GUI is it usually fine, but not for the bloaded DEs of today. I've been running an OpenBox install since around 2010 in 14G of space (actually less). It started as 10G, but I've added more storage as needed over the years. This is my main desktop and Perl development machine.
```
$ df .
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        17G   13G  2.6G  84% /
```

c) If the system will not be connected to the internet, ever, then you could just remove all the internet connections and networking everywhere. That would include the APT resources and just tell it to get packages from a DVD that you make.  There used to be a full install DVD - don't know if it still exists - that had all the top packages used by people and more.  If the system isn't connected, there isn't any security reason to patch.  However, if it is connected, even for 1 minute, then it must be patched ASAP when a connection is made and probably rebooted.

[https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline) will be helpful. **Keryx** looks interesting.  I've never used it and didn't know anything about it until reading that link.

---

### Post by Dave_Aoki on 2015-12-24
Hi Charles,

I got swamped with work and had to set the netbook aside for awhile.. but I have hooked it up to my router and am tinkering with it again. I entered:

du / --max-depth=1 --human-readable 2> /dev/null

It's listed a breakdown of what is utilizing all of my space which is currently maxed out, though I'm not sure how to show you since I'm on a different computer writing this post. I could submit a photo with my phone I suppose? 

Also, I have tried again to do the sudo apt-get update.. but it is still failing to fetch even though I'm hooked up. I also tried sudo apt-get --reinstall install ubuntu-desktop, which I've read from various threads will wipe the hard drive.. I get two yes/no prompts, one if I want to continue, and the second saying the packages cannot be authenticated and would I like to continue. I hit yes for both but still get error messages.

---

### Post by CharlesA on 2015-12-25
Does the other machine have internet access?

If it does, just pastebin it: [http://pastebin.com/](http://pastebin.com/)

I think both of those issues are due to the lack of space. If you can put the results of the du command up on pastebin, we should be able to get get to the bottom of it.

---

