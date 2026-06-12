---
title: "Install for grandparents to get email"
date: 2007-03-28
forum: General Help
---

### Post by jakev383 on 2007-03-28
I am thinking of setting up an Ubuntu box for my grandparents. They're old (hence, grandparents - soon to be great-grandparents) and not technically inclined at all. 
What I'm thinking is a small PC with a video-out card/adapter to let them use it on their TV set. Wireless keyboard and mouse. I'm envisioning a script setup that will call at 2am and retrieve their email and send any email that is waiting to be sent. I'm also thinking of having it wget a script from my webserver and run the script. Since they'll be on dial-up and only connect at 2am, I need a way to do things on their system. The best I can think of without flying there (1100 miles away) is to have it grab a script and run it - in the script I can bash out whatever changes I need to make to the system and cross my fingers that it worked.
What prompted it is my bill from the post office. About once a month my Grandmother will call and ask me to find her information on "that intraweb thing". This month it was about MSG (like in your foods). $8.20 to ship the paperwork up to her. And this is a monthly thing. No, I won't stop doing it - they're my grandparents and the least I can do is send them information when they want.
Anyway, does anyone have any ideas to make this easier for them? I have a few months before I go back up there, so there is plenty of time to get a machine working for them. I'll probably get 2 machines so I have a solid base to test with before I send them my update script. Has anyone set anything similar up?
What dial-up Internet service works best with Ubuntu/Linux in general? What email client do you think will be best for grandparents? (Big buttons, and very few of them. NEW, REPLY and that's about all). Anything else to make this easier that I'm not thinking of?
Thanks!

---

### Post by Chappy7777 on 2007-03-28
Jake,
I can't help you at all w/the tech part of your question. WAY over my head at this stage in my Linux life (about 3 mos old). 
However, I am using an ISP called [www.dialupatcost.ca](www.dialupatcost.ca)  I live in a Canadian backwoods village w/no hispeed available. I get download speeds between 45K and 75K on this Linux box. Faster than on my XP machine. They have an online webmail program that works quite well, is secure, ez, etc. I got in the habit of using online webmail since I figured it was safer re:malware, hackers, viruses and all the joys of MS. Since I have had the account for a number of years, I haven't bothered changing just because I am now using Ubuntu. Tho I am playing w/Evolution abit.

Oh, dialupatcost is cheap. $9.99/mo CDN, which is about 8.50 US. I pay $31 every 3 mos. I see nothing in their literature barring use of the ISP to you yanks. Actually, do a Google because methinx I saw a US version for 6.95/mo or so.

Chappy

---

### Post by jakev383 on 2007-03-28
> **Chappy7777 said:**
> Jake,
I can't help you at all w/the tech part of your question. WAY over my head at this stage in my Linux life (about 3 mos old). 
However, I am using an ISP called [www.dialupatcost.ca](www.dialupatcost.ca)  I live in a Canadian backwoods village w/no hispeed available. I get download speeds between 45K and 75K on this Linux box. Faster than on my XP machine. They have an online webmail program that works quite well, is secure, ez, etc. I got in the habit of using online webmail since I figured it was safer re:malware, hackers, viruses and all the joys of MS. Since I have had the account for a number of years, I haven't bothered changing just because I am now using Ubuntu. Tho I am playing w/Evolution abit.

Oh, dialupatcost is cheap. $9.99/mo CDN, which is about 8.50 US. I pay $31 every 3 mos. I see nothing in their literature barring use of the ISP to you yanks. Actually, do a Google because methinx I saw a US version for 6.95/mo or so.

Chappy

Thanks for the ISP. They're actually in mid-Michigan so they're neighbors! :)  A cheap dialup service that worked with Linux in general would be great. I could set up another number for their area and pipe it into my Asterisk box to allow them dial up, but I'm not 100% sure that would work well - I know faxing is a pain. Might be something that I should look into though.
Webmail probably wouldn't be the best thing. It could be done though. I run email, webmail, DNS, etc. servers so I can customize quite a bit for them and could probably skin Squirrelmail to make it easy for them, but then they would have to be connected to use it. I'd prefer for them to just poll my email server to get their messages late at night when they're sleeping.
Thanks again!

---

### Post by jakev383 on 2007-10-27
It's been a while, but I've found a couple dial-up companies in my grandparent's area that are inexpensive and can be used with Linux. I've decided to have the machine poll email at 3am-ish, and also grab a script (if it exists) to run maintenance. This is so I can use their existing phone line, but not have to worry about keeping the line busy all the tie or anything but still be able to run maintenance scripts on their machine in the event I need to do anything.
Anyway, I need an email client for them. As few buttons as possible. Thunderbird would work, but I'd like to find a theme (I'm not into making my own) that basically had write, reply-all, and delete on it. Maybe even remove the close/min/max buttons as well.

---

### Post by _duncan_ on 2007-10-28
Hi Jake,

Dial-up can be a bit difficult to set up in Ubuntu, particularly if the modem is a software modem (generally called winmodem). These require the OS to do part of the work of a true hardware modem, and most of the available drivers are for windows OS.

You may want to browse through the Dial-up wiki (2nd link on my signature) for an overview of what you have to do to get it working.

---

