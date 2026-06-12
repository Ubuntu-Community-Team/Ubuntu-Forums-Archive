---
title: "Removing Facebook app"
date: 2013-04-27
forum: General Help
---

### Post by ARooster on 2013-04-27
I have updated to 13.04 from 12.04 on the 25th and so far I am pleased with the experience. The changes don't seem to be too radical, thus not requiring much adapting and on this particular desktop things do seem to be running more smoothly, the default animated transitions looking quite well and do not seem to require as much hardware resources as the previous versions of Unity did. Upon installing 304 nVidia drivers Skype refused to start, but using the (somewhat clunky) temporary workaround I got that to work, too. No stability issues so far either.

Having installed everything I need, however, I went to check my Facebook account. Chromium offered to install an app for quicker access and so forth, however I find the Dash icon is quite useless (it just seems to open a full screen tab-free new instance of Chromium) and would like to get rid of it. Unfortunately I can't, for the life of me, find what to uninstall to get rid of the annoying blighter! Any suggestions?

---

### Post by ARooster on 2013-04-27
Right, having googled a bit, it seems to be Unity desktop integration of Facebook. It's a webapp of a supported site. As far as I can tell, Unity Tweak Tool will allow you to disable Amazon and Ubuntu One webapps, but how do you get rid of the non-preauthorised ones?

---

### Post by ARooster on 2013-04-27
It seems that disabling Amazon in unity tweak will not actually prevent it from popping up in the Dash Home search. Dash, when opting out of the record activity option, becomes quite useless.

Edit: Which is not to say that record activity should be left active! I think it's a foul idea and Richard Stallman is probably right!

---

### Post by ARooster on 2013-04-27
This is actually probably more of a Dash Home issue. I think Web pages (which Amazon, Facebook and Youtube are) should not be shown as applications, but I think this is more of a personal preference issue.

---

### Post by ARooster on 2013-04-28
Issue solved. For those interested, the answer is you have to delete files ending in  .desktop from ~/.local/share/applications/ to get rid of the desktop integration web app.

To remove the Facebook Unity web app

Code:> cd ~/.local/share/applications/
 rm facebookfacebookcom.desktop

---

