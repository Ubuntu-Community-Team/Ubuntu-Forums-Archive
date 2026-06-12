---
title: "Was hacked, and then bitcoin miner installed - need info on protection"
date: 2021-03-06
forum: General Help
---

### Post by archaeometrist on 2021-03-06
OK, a few things first.  I will ignore any "here's some links, start reading and start learning!" comments.  I want straight answers.  I spend all my time (working and working on my dissertation project) reading and researching and learning - I need quick and easy answers and don't have time to "read and learn".  (Linux and computers are NOT a hobby for me - they're tools and a way to get away from Microsoft's corporate greed and abuse!)  I'm also not new to computers or operating systems - I first learned to program in the early 70s!  I may not be a guru, but I AM rather old-fashioned when it comes to the attitude towards technology.  (I also prefer efficiency and not "the latest and greatest" - the newest fad in other words.)  The situation: Almost a month ago I upgraded from 18.04 to 20.04, due to concerns about security and problems with software (such as VPN to work/school).  I had to go through some headaches to get Ubuntu into a usable shape - for instance installing Gnome Flashback and making some other base changes (someone obviously has never heard the rule "Never fix that which isn't broken!").  Then I installed the VPN software from my school's IT department.  Less than a minute after installation, I had the first alert something wasn't right - a pop-up message about 'Stack Smashing detected'.  My system slowed to a crawl and became almost impossible to use.  I tried to figure out what was going on for a couple of days, and became suspicious when I found that my firewall had been deleted (after I'd installed GUFW and enabled it).  Then I actually watched as someone tried to move cursors around on my desktop - and deleting files.  I yanked the ethernet cable and did some scans - found that some programs I didn't recognize or want had been installed, including a bitcoin miner (which ate up most of the processors' time and resources).  I pulled that computer, and (a bit of a story) kludged together an older system so I could work and do my research/analysis.  (My good system is out in my shop - I'm hoping to find some agency that will investigate because what happened to me is a federal crime.)  Last night I went to a recommended website (for legitimate reasons) - which turned out to be a mistake.  This system slowed to a crawl and became unusable.  I had to enable Java for that website to work, and after that I found two bitcoin miners in my system.  I killed those, and ran rkhunter.  It found hidden Java directories which I deleted.  No more miners.  No return to that website either (I warned some others about it).  I really don't have a lot of time to do the 'recommended reading' and just need some simple, straight answers (and no snide or abusive comments please - if you aren't willing to help solve a problem, I don't want to hear about it).  I know apparmor is installed on this system and suspect it's misconfigured, but trying to get easy-to-do instructions on setting it up has been difficult at best.  I run Firefox and have noscript and ultimate adblocker installed (ads are bad for my health).  I'm careful about where I go - with the occasional mistake (like going to that website last night).    My setup: Ubuntu 20.04LTS, Gnome Flashback, I run Firefox (and Chromium for specific tasks), Thunderbird for mail. Firewall enabled, Virtualbox (for specific programs that won't run in Linux - which I need), plus a few others.  I try to get everything I can from the official repositories, and I'm careful about programs NOT from them.  Other programs include Google Earth (required for work and some research), VLC media player (I do try to relax when I can), Synaptic (preferred), XFburn (I prefer it), QGIS, GRASS, and so on.    Could someone (1) suggest software - I'd even pay a few dollars (typical grad student here - VERY tight budget), that would help protect against the hacking and so on - especially active/real-time malware protection?  (2) Point to easy-to-read and easy-to-follow instructions on setting up programs like apparmor and noscript (and software that will protect against outside hackers)?   (I do updates to Ubuntu daily and usually turn off my system when not in use.)  I will close by saying that since the days of BBS and so on (early 80s), there has been a terrible shift in attitude towards helping others - from being helpful and decent to being snobbish and insulting - that's why I try to stop the "YOU GOTTA LEARN WHAT I SAY YOU MUST LEARN!!!" attitude before it gets started.  I'm not trying to be insulting - I am quite tired of the "Big I, little U" attitude I keep encountering.  We're all equal, you may have more knowledge than I do regarding Linux, but I have my areas of expertise too.

---

### Post by DuckHook on 2021-03-06
None of us on these forums have anything to do with your miseries. Hence, your hectoring demands offend not only netiquette, but common standards of courtesy and decency. And this is not the first time: [https://ubuntuforums.org/showthread.php?t=2457987&p=14020819#post14020819](https://ubuntuforums.org/showthread.php?t=2457987&p=14020819#post14020819)

Desist.

[LIST=1]
[*]On these forums, you have neither the right nor the standing to impose conditions on what form help will be given. That is an arrogant presumption indicative of outrageous entitlement.
[*]Though some of us have security expertise, this is not a security forum. Seeking security advice here of the immediacy and efficacy that you demand is both misguided and foolish. You may as well go harangue a gardening site.
[*]Your general tone of aggrieved insolence is both stale and tiresome. It will win you neither friends nor support. If you cannot post respectfully, then kindly refrain from posting at all.
[*]If your security issues are as bad as you claim&#8212;of which you give us ample reason to be doubtful&#8212;then your first course of action is to report it to the authorities. Your second course, concomitant to the first, is to hire security professionals who can assess your danger on site and implement physical measures to counter your alleged threats. Your refusal to take such measures is an open invitation to treat the rest of your screed with the utmost scepticism.
[*]To borrow your phrasing: we are quite tired of your prosecutorial tone, your arrogance, presumption, hectoring, disrespect and, not least, your indigestible wall of text.
[*]
[/LIST]
Note that posting on these forums is a *privilege* not an entitlement. Do not continue to abuse that privilege.

---

### Post by SeijiSensei on 2021-03-06
I only hope you learn how to use paragraphs before writing your dissertation.

---

### Post by dragonfly41 on 2021-03-06
[COLOR=#000000]> I first learned to program in the early 70s! 
And I in the early 60s.

[/COLOR]> [COLOR=#000000]Then I installed the VPN software from my school's IT department. Less than a minute after installation, I had the first alert something wasn't right [/COLOR][COLOR=#000000]
Oh dear!
Let me suggest just one free VPN link at bottom of this page.
[/COLOR][https://protonmail.com/blog/what-is-cryptojacking/](https://protonmail.com/blog/what-is-cryptojacking/)

> [COLOR=#000000]I really don't have a lot of time to do the 'recommended reading' and just need some simple, straight answers[/COLOR][COLOR=#000000]
I will not do the reading for you.
But another suggestion.
Browse this site.
[/COLOR][https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

[COLOR=#000000]Good luck with studies.

[/COLOR]

---

### Post by GhX6GZMB on 2021-03-06
@DuckHook: You Rock! Thumbs up.

---

### Post by QIII on 2021-03-06
This thread is now closed. The original poster is encouraged to start over by composing an intelligible, reasoned, calm and respectful request for assistance.  That request will be free of demands born of a false sense of entitlement.  It will also be free from undertones of accusation directed at the Ubuntu Forums Community.

---

