---
title: "Spamassassin not working after upgrade to 7.04"
date: 2007-04-24
forum: General Help
---

### Post by guliver on 2007-04-24
Is there a fix for Spamassassin not working after upgrade to 7.04? I am using it with Evolution.

---

### Post by rbmorse on 2007-04-24
Are you piping to spamassassin via a message filter?  

If not, Is the Spamassassin box checked under edit/preferences/plugins?

(one assumes spamassassin is/is still installed).

---

### Post by guliver on 2007-04-24
It is checked under plugins section in Evolution.

It was working nice before I did upgrade.

---

### Post by AndrewB on 2007-04-24
I had the same problem, fixed it by re-installing spamassasin via synaptic. It picked up its setting from my /home  drive which is separate from my root.[http://ubuntuforums.org/showthread.php?t=99603&highlight=evolution+junkmail]("http://ubuntuforums.org/showthread.php?t=99603&highlight=evolution+junkmail")
and
[http://johnleach.co.uk/words/archives/2005/09/15/180/]("http://johnleach.co.uk/words/archives/2005/09/15/180/")

---

### Post by dcstar on 2007-04-24
> **guliver said:**
> Is there a fix for Spamassassin not working after upgrade to 7.04? I am using it with Evolution.

I had a similar issue and changed my Spam filter to Bogofilter (which is also natively supported by Evolution).

Once you get Bogofilter "trained" it seems to run a lot quicker than Spamassassin did, so I was forced into a change that actually improved things as I'm no longer using Spamassassin but my Spam filtering still works!

BTW, If you do change to Bogofilter, I found that I had to turn off the Spamassassin Plugin in Evolution (and make sure the Bogofilter one is enabled).

---

### Post by walovaton on 2007-04-24
Sorry but reinstalling spamassassin didn't work.  This is totally insane, I'm getting lots of spam and no matter what I do they don't get filtered.  I upgraded from 6.10 (which worked fine) to 7.04 and it's like spam hell.

I checked the evolution preferences, the plugin is activated and I have checked the spam checking in evolution.  Then I tried activating Spamassassin from the services tool (System -> Administration -> Services) but still dosn't work.

Please help us... what can we do??

---

### Post by Giorgio on 2007-04-28
Same problem here with evolution and spamassin after upgrading to feisty. Solved unchecking the bogofilter plugin in plugin preferences.

---

### Post by brickatius on 2008-04-18
Check that  'spamd' is running. There is a bug in that it is not enabled by default. Look at /etc/default/spamassassin fora line that says 'ENABLED=0' If it does you need to edit this line and change the 0 to 1.
Open a terminal (Applications>Accessories>Terminal
Give yourself root priviledges - type
sudo -s
Press Enter followed by your password
Type the following
gedit /etc/default/spamassassin
Change ENABLED=0 to ENABLED=1
Click Save and everything should work fine.

---

