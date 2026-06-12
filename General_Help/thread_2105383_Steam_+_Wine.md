---
title: "Steam + Wine"
date: 2013-01-15
forum: General Help
---

### Post by Juniorr on 2013-01-15
I know, this have been discussed before, but my question is a bit different:

I have Ubuntu 12.04.1 64bit and I'm running the native Steam client. However most of the games I play are not ported yet. So I decided to install Wine and give it a try, since I KNOW that nowadays it runs most games better even that Windows (at least for me).

So, I would just install Steam on Wine, nothing else, no programs or other software, just Steam.

Is Wine an open door for attacks, even with only original software installed, like Steam? If I ever get a virus (and I scan weekly my machine with avast and clamtk), could it do changes in my home directory or just the .Wine folder?

---

### Post by Petro Dawg on 2013-01-15
1st, not sure why you bother to scan your computer weekly :-s (or ever).

2nd, I can't imagine what person would bother coding a virus to hit Linux via Wine through a Steam download when all they have to do is create a file called naked-girlz.exe and they will instantly get hundreds of thousands of infected Windows computers owned by dirty old men.  

Other than, perhaps, the desire to be mildly annoying.

3rd, if there at any-time was a significant outbreak of Wine based viruses, Wine would most likely be repaired in short order to stop the problem.  Open source is a powerful enemy of viruses.

Oldie, but a goodie:  [http://archive09.linux.com/feature/42031](http://archive09.linux.com/feature/42031)  (I promise clicking the link doesn't download a virus.)

Since I couldn't find anything really current; I think, as a project this year, I may try to get one of my old computers up and running using an outdated Internet Explorer and maybe Outlook Express (if it runs) through Wine and try extremely hard to give my self a virus and see what happens.  When I get around to it, I will post the results.

---

### Post by Juniorr on 2013-01-15
1 - I scan my computer because I share files with my mom's/sister's/dad's phones, so I they have a virus it doesn't get to my PC, and if my PC already has one so it doesn't infect other Windows' machines as well. Even tho Linux is imune to Windows viruses I wouldn't like to infect other machines.

2 - Yes, there would be some non-intelligent people who'd actually click it.

3 - But if WIne gets infected in that short period of time I'd be the one losing it

But my question is about crackers. Mac got cracked in a matter of munutes. Windows in a couple of hours and Linux got out with no harm. So if I install Wine and someone gets my IP adress, would they be able to invade my machine? Is Wine an open door on the computer?

---

### Post by Petro Dawg on 2013-01-15
I suppose if you were really wanting to avoid Wine access to your folders, you could create separate Linux user login for just the installation of Wine and Steam.  Keep no personal records under that user name and use it only for gaming.  

From what I understand (and I could be wrong) it is theatrically possible for mal-ware to run in Wine and affect your home folder using user privileges.  But I do not believe it can get Root access to do much else unless you helped it along intentionally.

You may look at this security tip from Wine if you are interested.
> **11.2. How good is Wine at sandboxing Windows apps?**

 **Wine does not sandbox in any way at all.**  When run under Wine, a Windows app can do anything your user can. Wine  does not (and cannot) stop a Windows app directly making native  syscalls, messing with your files, altering your startup scripts, or  doing other nasty things. 
You need to use AppArmor, SELinux or some type of virtual machine if you want to properly sandbox Windows apps. 
That said, [winetricks]("http://wiki.winehq.org/winetricks") does have a sandbox  verb that does at least a partial job of isolating Wine programs from  the rest of your system. It protects against errors rather than malice.  It's useful for, e.g., keeping games from saving their settings in  random subdirectories of your home directory.

---

### Post by Juniorr on 2013-01-15
Your idea of creating a new user and putting the Wine folder there makes sense. I'll give it a try. Thanks

---

### Post by Petro Dawg on 2013-01-15
> **Juniorr said:**
> Your idea of creating a new user and putting the Wine folder there makes sense. I'll give it a try. Thanks

Hopefully someone with more experience than I will chime in and verify if that is truly a reasonable solution.  I am by no means a Linux guru, but from what I've read, it seems to be a logical solution.

---

