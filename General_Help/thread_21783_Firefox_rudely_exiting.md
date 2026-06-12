---
title: "Firefox rudely exiting"
date: 2005-03-23
forum: General Help
---

### Post by AhYup on 2005-03-23
Hi

I just got started with Ubuntu yesteray. So far I like it but I'm havingt a lot of trouble with Firefox.

Its just randomly exiting without warning. It just blinks off the screen.

I can't find any error messages on it in xerrors or in the various logs in /var/log

Where else can I look to start getting an idea where the problem might be?

And does anybody know of any Firefox bug that does this?

---

### Post by kiddo on 2005-03-23
From **what I've experienced so far**, that's the way Linux apps crash in general. Does it happen often in your case? Maybe too much tabs open? It happened ~10 times or less since january for me. That's 10 times too much, but oh well...

Hmm maybe a tiring idea would be running the "firefox" command from a terminal and see the output when it crashes? Hope my comment can be of some help.

---

### Post by dude2425 on 2005-03-24
I've been having this problem too, but I hadn't really cared much about it. I constantly have tabs open. I use TBE cause I love my tabs so much. I only ever need 1 browser window.
Anyways, back to the problem at hand. I usually crash the most on that inquirer site or something like that. I was linked to it through Digg, but after I tryed it after opening firefox again, it wouldn't crash. Maybe it's just a bug with firefox when rendering certain things. I'll check more into it now that I know I'm not the only one.

---

### Post by bnutting on 2005-03-24
Several people have been reporting this issue. Have you guys updated firefox through apt? I know I saw an update yesterday for it. I don't know if it resolves it or not.  I have also seen suggestions to downgrade your version of firefox because this is a known issue.

Bryan

---

### Post by AhYup on 2005-03-24
Its crashing on my 2-3 times a day right now. Since I'm taking online classes its a real show stopper. 

I am considering going back to 1.0. My immediate guess is that it has something to do with running mouse gestures under 1.1. Are any of you guys running mouse gestures when it crashes?  

Although its stable enough on my SUse machine its having trouble with slackware and now Ubuntu.

---

### Post by gmc on 2005-03-24
Why not run firefox from a termial window and if it's reporting any problems when it exits, you should see them in the terminal window?

Just a thought

Gord

---

### Post by bsherman on 2005-03-24
I'm seeing similar behavior. 

After running apt-get update; apt-get upgrade this morning, Firefox is now 1.0.2. Some websites are working, but when I get a "Accept this certificate..." dialog box and click any of the radio buttons on it, Firefox segfaults.

---

### Post by AhYup on 2005-03-24
Well when I ran it in a terminal I got the sole comment "segmentation fault". And then I realized that I was having a few other problem that bad RAM could account for. 

So I rebooted into memtest and am running tests.

---

### Post by ngolian on 2005-04-28
I think it's Ubuntu's version of Firefox. I've migrated 3 boxes from Debian recently, including one Athlon 64, and Firefox is unstable on all of them. Try [http://www.zalman.co.kr](http://www.zalman.co.kr). Crashes every time here. It would display on Debian, but with the fonts a bit screwy IIRC: like some monospace serif font I hadn't configured with extra spacing between the letters. I'll try a self-compile tomorrow.

---

### Post by ryanrad on 2005-04-28
I'm not sure if this will help you or not, but have a partial solution to one of my bugs.

Firefox kept freezing every time I went to a particular site.  So, I downloaded Epiphany and tried it.  I noticed a popup with Epiphany at about the same time Firefox kept freezing during the page load.

So, I went into Firefox and enable popups.  It worked, the page loaded just fine!

However, I have tried a couple other sites where I remember having problems as well, but at least one of them still freezes Firefox.

---

### Post by ngolian on 2005-05-11
In my case it seems to be the free Flash plugin. Installing the commercial one has helped my 32-bit laptop, but there doesn't seem to be an alternative for 64-bit.

---

