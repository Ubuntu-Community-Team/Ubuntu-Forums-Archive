---
title: "using NodeJS with Ubunutu 15 and folder permissions"
date: 2018-10-24
forum: General Help
---

### Post by zerocool99 on 2018-10-24
I've been doing JS development on a Windows PC for a while and have gotten the Linux bug and started doing more JS development on a Linux box I set up with Ubuntu 15. 

I was building a site using GatsbyJS which has an auto reload feature along with Visual Studio Code for my IDE. Anytime I was creating ReactJS components with terminal commands, VS Code would say the new component in a folder doesn't have the right level of permissions to save. This happened pretty much anytime I was saving anything, or dropping assets in an images folder, etc. The same thing happened with I was working with AngularJS as well. 

I am logging in as Root on the terminal when I'm working so its def. not that.

I had to continually stop, open Nautilus or try and set the whole directory permissions by using 
```
sudo chown -R $USER ~/.blabla
```

Then I'd go back into VS Code and it would work, until I had to save again and the folder permissions would be reset again.

I'm just wondering how I can do this without constantly having to fix the folder permissions. 

I searched on google for a while and I have yet to find anybody else with this issue. I posted something on Stack Overflow and nobody really helped so this is kind of my last chance to try and fix this. I love the dev eco system, but this folder permission thing is a serious buzzkill so I'm hoping someone knows what's going on.


Any help is greatly appreciated. 

Pete

p.s. since this is a development specific topic, I posted it in General. If this is the wrong forum, let me know and I'll move it to the right forum.

---

### Post by TheFu on 2018-10-24
Welcome to the forums.

Ubuntu 15.xx only had 9 months of support. Basically, it ended when 16.04 was released.  The forum rules frown on helping with unsupported releases.  
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  shows the currently supported releases with their end of life dates, EOL.  If you cannot reinstall a new Ubuntu every 6 months (or won't), choosing an LTS release would be smart.   16.04 or 18.04 are the current LTS releases.

The use of root for anything other than specifically admin purposes is not advised on any Unix-like system.  Don't.
And it is a terrible idea to use sudo with any GUI for a number of reasons.

Use your normal userid and only use Linux storage, not NTFS, for programming.  If you have issues writing to Linux storage with your normal userid, we can help with that as a general question. It is unrelated to whatever version of any Unix-like system you use.  You could be on SLS from 1992 or Ubuntu 19.04 Alpha-alpha - same answer.

---

### Post by DuckHook on 2018-10-24
> **TheFu said:**
> …The forum rules frown on helping with unsupported releases…
It's not so much forum rules as it is practical considerations. Who still has obsolete versions on their computers? I certainly don't. So it becomes basically impossible to recreate the conditions of the problem or test anything.

---

### Post by zerocool99 on 2018-10-25
Interestingly enough, I fired up my Linuix box today to get the exact version and upgraded to 18.04 (Bionic Beaver) so I have the latest version. However, it sounds like I won't be able to use NodeJS or WebPack or any other modern tool set because of the folder permissions issue?

I'll check into the Linux Storage and see if that works.

---

### Post by TheFu on 2018-10-25
> **zerocool99 said:**
> Interestingly enough, I fired up my Linuix box today to get the exact version and upgraded to 18.04 (Bionic Beaver) so I have the latest version. However, it sounds like I won't be able to use NodeJS or WebPack or any other modern tool set because of the folder permissions issue?

I'll check into the Linux Storage and see if that works.

What?  Node.js runs fine.  Whether YOU can use it or not is a personal issue.   

Using root for non-root stuff is the easiest way to cause a self-inflicted issue.

Don't use NTFS for Linux software development.

---

