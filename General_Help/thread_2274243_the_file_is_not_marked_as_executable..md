---
title: "the file is not marked as executable."
date: 2015-04-18
forum: General Help
---

### Post by abc-78 on 2015-04-18
Hi, guys.

Which distribution I'm using is elementary OS. It's based on Ubuntu 14.04.

I have installed a Minecraft client, its a jar file. Everything seemed all right, but after I clicked on it, I got &#8216;The file '/home/george/&#19979;&#36733;/MinecraftMagicLauncherMC1.8Edition.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.&#8216;

Then I did some search on Bing, got many solutions mostly like that Right click on it and go properties, then select permissions and check "Allow executing file as program".

Everyone that have tried that said that worked out, but when I right clicked on it and went properties, I didn't see any content like "Allow executing file as program".

So, my question is, is there any way else to solve this like using command. (sorry for my poor poor poor English...)

---

### Post by kerry_s on 2015-04-18
in elementary file manager its, click properties-> more, then click on the 3 boxes that say "execute".
or
in terminal:
chmod +x /home/george/&#19979;&#36733;/MinecraftMagicLauncherMC1.8Edition.jar

---

### Post by abc-78 on 2015-04-18
I just did as you said, it worked! Thanks, dude!

---

