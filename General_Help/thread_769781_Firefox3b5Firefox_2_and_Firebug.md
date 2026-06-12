---
title: "Firefox3b5/Firefox 2 and Firebug"
date: 2008-04-26
forum: General Help
---

### Post by darolu on 2008-04-26
First I'd like to rant about the decision to include Firefox 3b5 in Ubuntu hardy, it is glitchy (try to make work a xmlhttprequest calling it from local files) and no add-ons work on it which leads me to the reason I'm posting this:

The only reason I use Firefox (I really prefer Opera) is because of Firebug, which is extremely useful for web developing, but now my new (and great) Ubuntu 8.04 comes with Firefox 3b5 which is not compatible with most add-ons including Firebug.
The solution to this is pretty obvious, switch back to Firefox 2, which I did, but now I have Firefox 2 back (not in my language when installing with synaptic or apt-get btw) I can't install any add-on, big glitch going on, the message I get from the console says it can't find the installing location or something like that.
Does anyone know how to solve this?
Thanks in advance.

PS. I don't like the prefix thing.

---

### Post by FredB on 2008-04-26
About your *whining* on firefox 2 in hardy, just look at ubuntu release notes.

For firebug, an alpha version is available for firefox 3 beta 5. Something like a 1.2 version. Just wait a little to get it.

---

### Post by Rigrig on 2008-04-30
The Firebug in the Ubuntu repositories seems to work for me:
- In Firefox, uninstall the firebug extension (not sure if this is necessary, but better safe than sorry)
- Install the firebug package: either type *sudo apt-get install firebug* in a terminal window, or use 'Add/remove' from the menu and search for *firebug*

---

### Post by vexorian on 2008-04-30
You probably need to remove the firefox3 profile in /home/username/.mozilla before trying firefox2 again.

A lot of plugins do work in f3, the ones I am using are noscript, downloadhelper and stylish.

---

### Post by floydwilde on 2008-04-30
I'm needing to do the something similar, I need to use firebug for work, and I have a separate Linux user for doing work stuff, so I switch users. Do people actually call these profiles?  I actually switch users.  

So anyway, I don't want to uninstall the Firefox 3 package or anything. I didn't think that you could install both versions but I just went and installed this package, and apt didn't rip out version 3 or anything: 

 ```
 
root@satori:~# apt-get install firefox-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  firefox-2-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  firefox-2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.

```

hmm now how to start it?  I'll have to close my browser to find out.

---

### Post by tbrminsanity on 2008-04-30
I messed up my Firefox with 7.10 and it didn't fix till I updated to 8.04 and Firefox 3b5.  I like it much more then Firefox 2 and I've replaced Firebug with the developer's toolbar (not as powerful but same functionality).  Firebug will eventually be upgraded to 3b5, you just have to wait.

---

### Post by floydwilde on 2008-04-30
Yeah, I was suprised to find that firefox3, and firefox2 happily coexist.  Well, enough for me.  After I installed Firefox2, I moved the .mozilla directory to .mozilla3, and copied back my old firefox 2 .mozilla, removed the firefox3 shortcut icon on my toolbar and replaced it with the firefox2 one that appeared in the Applications > Internet menu, and it works fine, and I didn't even have to reinstall my plugins.  

Now theoretically, if I wanted to use Firefox 3 also, I could just move the .mozilla profiles around.  Why can't they just make an option, so you can modify the name of this profile directory or something?  Why do they still call it mozilla?

---

### Post by TimGS on 2008-05-25
I had this problem and also need Firebug for work.

Get rid of the .mozilla directory - then start Firefox 2. I suspect running two versions (esp as one is Beta) that read and write the same profiles is asking for trouble, so I'm getting rid of version 3.

-- Tim.

---

### Post by eindgebruiker on 2008-05-25
> **Rigrig said:**
> The Firebug in the Ubuntu repositories seems to work for me:
- In Firefox, uninstall the firebug extension (not sure if this is necessary, but better safe than sorry)
- Install the firebug package: either type *sudo apt-get install firebug* in a terminal window, or use 'Add/remove' from the menu and search for *firebug*

Works for me too. I indeed had to uninstall firebug in Firefox itself.

---

### Post by LeighT on 2008-05-25
I had the same problem with Firefox3, and found that it was so bug ridden it wouldn't even render some web sites. So I removed it and installed Firefox2, then came the fiddle to get my extensions going again, lost saved password in doing so.
Every thing was fine untill I installed the MPlayer plugin, which promptly indtalled Firefox3 again.
Given up untill they release the full version of Firefox3, untill then I am using Swiftweasle which reconises all of my extensions as well as my bookmarks.
I was taught many years ago you do not use Beta programs on PC's that are used as everyday machines.
It seems that lesson hasn't been heard by the Hardy devlopement team.
Anyhow try Swiftweasle it should get yopu out of trouble.

---

### Post by floydwilde on 2008-05-25
I've been living w/ both firefox 2 and 3 for a while now.   Some annoyances. I have two directories in my home directory:

.mozilla-2
.mozilla-3 

As you can guess, they are the .mozilla profile directories, for each version.  Say I've been using firefox3, and want to switch to using 2 for a while.  Well I just go:

rm -rf .mozilla-3 #(erase the old backup)
cp -a .mozilla mozilla-3
rm -rf .mozilla 
cp -a .mozilla-2 .mozilla   

So that works fine, but then I close that session, and forget what version I was using.  Then I go open Thunderbird and click on a link, and Firefox-3 opens up and destroys my firefox2 .mozilla profile.  Good think I've got a backup up, but whatever i did in my last session was lost.  Which is usually not much.  I changed the timezones in my foxclocks plugin, and had to reset.  No big deal, but still annoying.  Thinking about writing a script to backup the .mozilla profile, whenever I logout or something.  Also a simple script to just switch profiles would be nice.

---

### Post by Ameneon on 2008-05-25
I hope, hope, hope, hope FF3 is updated soon and fixes the ridiculous CPU/memory usage (near enough 50%, meaning one of my cores @ 100% and 250+mb) when opening certain sites and a certain amount of tabs. I'm still sticking with the browser out of laziness and habit (and because the browser otherwise is good) but being a live beta tester is pushing me ever closer to swapping FF out for one of the alternatives.

FF2 was a bit hogging too when the amount of tabs went higher than 35-40 or so, but in FF3 I can rarely have more than 10-15 before it starts chugging so much it's nearly useless. And even at that 35-40 in FF2 the slowdown was never so extreme as it is in FF3b5 :(

---

