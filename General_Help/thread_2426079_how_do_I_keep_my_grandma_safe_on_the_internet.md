---
title: "how do I keep my grandma safe on the internet?"
date: 2019-09-04
forum: General Help
---

### Post by ardouronerous on 2019-09-04
After my grandma's Windows XP laptop got infected with a virus and since Windows XP was no longer supported anyway, I installed Lubuntu 18.04 on it.

Now, what security addons can I put on Firefox to keep my grandma safe on the internet, but also wont break the websites that she visits. She lives in a assisted living and I can't be around to watch her 24/7.

I've already installed: Decentraleyes, HTTPS Everywhere, Privacy Badger, uBlock Origin, I've considered putting NoScript on there, but I've decided against it since it would confuse the hell out of her.

---

### Post by Autodave on 2019-09-04
You have probably done way too much already.  13 machines that I either have here or in use elsewhere.  2 of them are pretty much open to the public.  Never had a virus on any of them in the 10+ years that I have used Linux.

Linux is not Windows: quit thinking like a Windows' user.

Without knowing the specs on grandma's machine, but knowing that it came with XP, I would delete all that extra stuff and give grandma a little extra speed out of all that old hardware.

You may even consider putting Xubuntu on there and give her something a little nicer to look at.  Without that extra stuff on there, Xubuntu will probably run just as fast if not faster.

I run Xubuntu on every machine.  No anti-virus at all.  The ONLY thing I used is uBlock on Firefox to block all the extra ads from appearing.

Grandma on Linux with nothing else, will be 1,000 times safer than you on Windows with all of you extra stuff running.

---

### Post by ardouronerous on 2019-09-04
> Without knowing the specs on grandma's machine, but knowing that it came  with XP, I would delete all that extra stuff and give grandma a little  extra speed out of all that old hardware.

It's a Dell Inspiron E1505, originally it had 1GB RAM, so I upgraded it to 2GB RAM, which is the max already on this machine. I'm not sure what you mean by deleting all the extra stuff, since I've wiped out all of Windows XP to install Lubuntu.

> You may even consider putting Xubuntu on there and give her something a  little nicer to look at.  Without that extra stuff on there, Xubuntu  will probably run just as fast if not faster.

Xubuntu's UI resembles MacOS, since she's never used a Mac before and since she's more used to Windows XP's UI, Lubuntu's UI kinda resembles XP's, the taskbar being on the bottom, I think it's a good fit for her, since I don't want to confuse her.

> I run Xubuntu on every machine.  No anti-virus at all.  The ONLY thing I  used is uBlock on Firefox to block all the extra ads from appearing.

So uBlock Origin alone will protect her on the Internet then?

---

### Post by Frogs Hair on 2019-09-04
Ublock is a good ad-blocker and I also us [HTTPS Everywhere]("https://addons.mozilla.org/en-US/firefox/addon/https-everywhere/")  and [Privacy Possum.]("https://addons.mozilla.org/en-US/firefox/addon/privacy-possum/") When extensions update they may require some setup or interaction is grandma able to do this?

---

### Post by Tadaen_Sylvermane on 2019-09-04
When I had my grandparents old laptop on Ubuntu I didn't do anything special. I didn't get a call for help for near 2 years as opposed to the bi-weekly Windows calls. Ultimately no amount of addons or customization can protect someone from lacking simple common sense though. All these addons are fine but they will make it harder for her, not easier.

---

### Post by TheFu on 2019-09-04
My mother got hacked about 10 yrs ago on XP.  She recognized it immediately and powered off the computer.  I couldn't get there for a few months, so she paid bills at another relative's nearby home.  I'd moved her over to using Firefox, Thunderbird, and other F/LOSS programs a few years earlier.
When I finally go there, she new the plan was to install Lubuntu.  I setup a left-hand set of icons for the 5 things she used, setup remote ssh access from my home with the router and Linux, setup an external backup disk, with hourly backups using Back-in-Time and weekly replication backups for critical data to my house using rsync.  She had an old Pentium4 at the time.

With remote **ssh**, I could setup or configure anything needed, as she needed it.  For example, Firefox was the main browser with NoScript, but I wasn't able to explain to her the working of it. Instead, I installed a 2nd browser without any real security settings that she could use on airline and bank and brokerage websites, as needed.  I was very clear to only use that browser for non-trivial money reasons.  She understood and it worked.

ssh also allows **x2go** remote desktop to be used securely. Installing ssh and **fail2ban** has been sufficient to handle any attacks. I use the router's port translation from some random high-port into the default ssh part on the Linux machine.

Initially, she was scared of Linux, because I don't run with much of a GUI at all.  When her Lubuntu install was setup, she smiled and said everything was almost the same as under XP. She'd been using the same programs already, so that wasn't too different. The buttons on an iconbar were easier for her.  Actually, the hardest part was to remember to leave the computer on every Friday night so I could backup the files and patch for her.  I was already managing 20 other systems for a few clients, so adding 1 more wasn't any issue.  Patching her system never caused any issues. Wish it was so easy for some of the others.

She moved into assisted living and the Pentium4 died, was replaced by a Core i7.  Because Lubuntu was already fast enough on the P4, she didn't notice the difference in performance at all, but she could see how important it was to me that it was a little faster. 

Mom died a few yrs ago, so that all ended.  I've offered to do the same for anyone in the family, provided they ran Linux.   I don't push. I don't sell.  It is just an offer to about 40 people. Two houses have switched to Linux for their home servers, but I don't manage those. The chief nerd in each location does by their choice.  Usually during a visit, someone will be told that I work in the computer field and ask for help.  I'm pretty clear - I'll help with anything that isn't Apple or Windows. I won't touch those OSes for family.

Browser addons can be security/privacy problems, BTW.  That includes some privacy/security addons.  Sometimes addons change ownership and policies. TNSTAAFL.

---

### Post by Autodave on 2019-09-04
One other thing you may consider: TeamViewer.  It is very simple to install and use.  I remotely access 3 different machines with that.  I can log in, check that updates are current, fix things that they have somehow managed to change.  It is a free program and quite simple.

---

### Post by HermanAB on 2019-09-04
I gave my mother in law a MacBook Air.  Once a year, I run the updates, if she didn't.  That's it.  No issues ever.

For the other fandamily, I simply say that I don't do Windows.

---

### Post by Autodave on 2019-09-04
I have Win10 on this machine only for one game.  Nothing else has been installed in Windows.  When not playing the game, it is booted to Xubuntu.

---

### Post by haplorrhine on 2019-09-04
No expertise, but in my experience he had no will and/or ability to learn NoScript.  He only browsed.  I think the basic browser ports--were they http, https, and ssl?--worked until he needed to do an FTP download.

---

### Post by 1clue on 2019-09-04
I like your original group of plugins. Without NoScript.

Unlike (apparently most) other Linux users, I know that security on Linux is a big deal. Software that is written for a cross-platform tool (web browser, ms office compatible, many other variants of scripts) can affect Linux as well. If you follow the recommended API for many things that we think of as Windows-only, they will work on Linux too. Including malware. I have been pwned several times, and most of them I would almost certainly not have recognized had I not modified the original install based on some sort of security best practices list, and paid attention to CVEs and patches. Unlike the early days, malware authors aren't just trying to trash your system anymore, they have an interest in preventing you from having noticeable problems so they can own your system longer for whatever their purposes might be.

Let me reinforce the difference between a virus (a specific subset of malware which Linux is not really susceptible to) and malware (the entire group of software written with the intent do do you or your hardware harm, or to do harm to another computer or entity using your computer as an attack point). Also let me draw attention to the most common type of "malware" which is phishing. Convincing somebody to enter valid credentials to an unauthorized entity. That's not software at all, and you can't really protect against it.

Viruses, you don't really need to do anything about. Word documents/excel/whatever MS documents you may need to do something about. Every time I install a box I review one or more Linux Security wikis because each installation is different and the advice changes over time anyway. It's a moving target, so to speak.

Unfortunately keeping your grandma safe is going to require some sort of education and caution on her part, with the phishing part. Email integrity and caution about clicking links in emails and electronic documents. That can only work with education and caution and a healthy sense of paranoia.

---

### Post by HermanAB on 2019-09-04
BTW, bear in mind that your Grandma's generation are the people who invented computers and most everything else. Even if she does come from a simpler environment, she probably worked with cash registers, accounting machines, electric type writers and the like in shops and offices, for more years than you may know.  For most people, a laptop computer is just a glorified electric typewriter.  Therefore, don't treat her like a dummy, she may know much more than she lets on and may be able to teach you a thing or two!

---

### Post by uRock on 2019-09-05
> **1clue said:**
> I like your original group of plugins. Without NoScript.

Unlike (apparently most) other Linux users, I know that security on Linux is a big deal. Software that is written for a cross-platform tool (web browser, ms office compatible, many other variants of scripts) can affect Linux as well. If you follow the recommended API for many things that we think of as Windows-only, they will work on Linux too. Including malware. I have been pwned several times, and most of them I would almost certainly not have recognized had I not modified the original install based on some sort of security best practices list, and paid attention to CVEs and patches. Unlike the early days, malware authors aren't just trying to trash your system anymore, they have an interest in preventing you from having noticeable problems so they can own your system longer for whatever their purposes might be.

Let me reinforce the difference between a virus (a specific subset of malware which Linux is not really susceptible to) and malware (the entire group of software written with the intent do do you or your hardware harm, or to do harm to another computer or entity using your computer as an attack point). Also let me draw attention to the most common type of "malware" which is phishing. Convincing somebody to enter valid credentials to an unauthorized entity. That's not software at all, and you can't really protect against it.

Viruses, you don't really need to do anything about. Word documents/excel/whatever MS documents you may need to do something about. Every time I install a box I review one or more Linux Security wikis because each installation is different and the advice changes over time anyway. It's a moving target, so to speak.

Unfortunately keeping your grandma safe is going to require some sort of education and caution on her part, with the phishing part. Email integrity and caution about clicking links in emails and electronic documents. That can only work with education and caution and a healthy sense of paranoia.
I agree with most of this. I only use one add-on in Firefox. Facebook Container. I disabled ad blockers, NoScript, and Ghostery after they kept borking websites and irritating me with having to either allow something or close the tab and find another source. I don't visit many sites and I never use links in emails to get to a site's login page, unless working through a PW reset.

---

### Post by sudoranger on 2019-09-05
1. Let her do gardening.
2. Spend more time with the grandchildren instead of Internet.
3. Teach her how to curl.
4. Ask her to minimize technology/gadget as she doesn't have much time left. Go vacation, enjoy the beach or champagne.
5. Use VM, install Windows XP within Ubuntu and if things got out of control just reformat and reinstall (or clone) the VM again.
6. Repeat 1-5.

Extra Tips: Avoid Google Chrome at all cost, install Adblock extension/plugin. Uncheck "Show hidden files" in Nautilus. For more extreme precautions, disable JavaScript, location, notification, do not track traffic in her browser.

Edit: An oh, use Snap or flatpak (although I recommend the earlier). The jailed/contained environment is safer than those of the traditional apt though might be a bit slow when launching + some gtk theme issues on some apps.

Hehehe.

---

### Post by SeijiSensei on 2019-09-05
I've switched from Firefox to [Brave Browser]("https://www.brave.com/") which is based on Chromium.  It has built-in ad blockers.  Very quick, too.  Rather than Firefox plus a bunch of add-ons, you might give Brave a try.

---

### Post by GhX6GZMB on 2019-09-05
Just use Opera and enable the adblocker. She'll be fine. Uninstall Firefox.

---

### Post by TheFu on 2019-09-06
> **ml9104 said:**
> Just use Opera and enable the adblocker. She'll be fine. Uninstall Firefox.
FYI [https://www.engadget.com/2016/07/18/opera-browser-sold-to-a-chinese-consortium-for-600-million/](https://www.engadget.com/2016/07/18/opera-browser-sold-to-a-chinese-consortium-for-600-million/)

---

### Post by uRock on 2019-09-07
> **TheFu said:**
> FYI [https://www.engadget.com/2016/07/18/opera-browser-sold-to-a-chinese-consortium-for-600-million/](https://www.engadget.com/2016/07/18/opera-browser-sold-to-a-chinese-consortium-for-600-million/)

That's good to know. I think I'll stick with Firefox.

---

### Post by GhX6GZMB on 2019-09-07
Interesting. Doesn't change the fact that Opera IMO is the best browser around. I'll keep an eye on it, but the company is still Norwegian, investors or not.

---

