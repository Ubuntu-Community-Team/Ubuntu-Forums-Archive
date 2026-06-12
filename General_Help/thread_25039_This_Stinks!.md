---
title: "This Stinks!"
date: 2005-04-09
forum: General Help
---

### Post by Cougaram on 2005-04-09
THIS STINKS! NO REALPLAYER! I've tried searching the whole forum for a Realplayer howto but none of the post have enabled me to get realplayer installed and working? Is this an intentional oversight that it is not installed by default? Or at least an option in the synaptic tree? If not... WHY???? It's FREE from the Realplayer site but the thing will not link as a plugin for Firefox. C'mon folks... mplayer is *NOT* an adequate sub for rp!

---

### Post by bored2k on 2005-04-09
First of all lower your voice ( ^_^ ). Second, download the .bin extract it and install it. 
You did huh? Does it open? Oh it doesn't? Disable sound server @ startup.
Oh it doesnt link in firefox? ls /usr/lib/mozilla-firefox/plugins . Is the plugin there? no? create it with ln -s .

---

### Post by c_dog on 2005-04-09
[QUOTE=Cougaram]THIS STINKS! NO REALPLAYER! I've tried searching the whole forum for a Realplayer howto but none of the post have enabled me to get realplayer installed and working? Is this an intentional oversight that it is not installed by default? Or at least an option in the synaptic tree? If not... WHY???? It's FREE from the Realplayer site but the thing will not link as a plugin for Firefox. C'mon folks... mplayer is *NOT* an adequate sub for rp![/QUOTE]


Realplayer is not free as in FOSS (Free Open Source Software). It's just 'free' as in beer. Helix 
which is Open Source is there. The Linux version of RealPlayer 10 is based on Helix, but Real still keep the codec for RealPlayer. No big deal because just like Winbloze, which doesn't install RealPlayer, or FlashPlayer, or Java "by default" all's it takes is going to their respective website and downloading the Linux binary and install it. Takes even less time then time it took  for you to blow off steam. BTW, RealPlayer is available in Synaptic (or Apt) in multiverse. Just    turn the multiverse (the place for such 'non-free' free beer things) repository on and you'll see.

---

### Post by joshmachine on 2005-04-09
If you want realplayer10 (multiversion has realplayer 8) you can download it from here:

[https://helixcommunity.org/projects/player/](https://helixcommunity.org/projects/player/)

If you want braindead simple, download one of the *.bin files and install.

if you want it as a debian package do the following instead

Click on the Download link next to realplayer and select one of the non-distro specific rpms.

Download it to a local directory and use alien to convert it to a .deb pckage
>> alien Realplayer-XXX.rpm

This will produce a realplayer-XXX.deb packge.
install using dpkg

make sure you aren't running a different package manager.

>> sudo dpkg -i realplayer-XXX.deb 

You'll have to put the RealPlay directory in your path (wherever you installed it or /usr/local/RealPlay) and now you can run it from the command line. 

>> realplay

I'm not sure if you get it in your menu, but gnome menus are a whole other can of whoopass.

---

### Post by SFN on 2005-04-09
Just do this:

[HTML]sudo apt-get install helix-player[/HTML] 

and calm down.

---

### Post by nuopus on 2005-04-22
[QUOTE=SFN]Just do this:

[HTML]sudo apt-get install helix-player[/HTML] 

and calm down.[/QUOTE]

Yuh ... I would like to see helix-player play realplayer 10 content from the numerous news sites that I go to. Normally when people insist on RealPlayer 10 it is because of such content ... and people seem to keep suggesting helix-player. Helix-Player makes a good media player but will not play content that requires the real codecs.

IF you are going to argue back saying .... "Well they should not make content using those codecs if they want lots of people to view them" ... like I have seen before, this misses the point as the content I want to view is already in that format.

---

### Post by Leif on 2005-04-22
Am I the only one who suspects that this person is using the old trick to get easy answers instead of searching ? You know, where you go "linux blows, windows is so much better, I could do this in like 2 seconds in windows", and a hundred people will jump to prove him wrong ?

Here's a hint : the people here are friendly and helpful already, so just asking a question in a nice way will get you answers. No need to huff and puff.

---

### Post by jiyuu0 on 2005-04-22
[http://www.ubuntuguide.org/index.html#realplayer](http://www.ubuntuguide.org/index.html#realplayer)

---

### Post by XDevHald on 2005-04-22
[QUOTE=Leif]Am I the only one who suspects that this person is using the old trick to get easy answers instead of searching ? You know, where you go "linux blows, windows is so much better, I could do this in like 2 seconds in windows", and a hundred people will jump to prove him wrong ?

Here's a hint : the people here are friendly and helpful already, so just asking a question in a nice way will get you answers. No need to huff and puff.[/QUOTE]

Agreed fully.

[QUOTE=Cougaram] I've tried searching the whole forum for a Realplayer howto[/QUOTE]

Actually some really good deep investigating does do the trick by using the **Search **link in the navigation above, it's all in how you search the site and very carefully to find your answer to the question about Realplayer.

Also note that mplayer is a great application, yes it has it's ups and downs but it's very carefully used through httpheaders on mozilla/mozilla-firefox browsers. Download mplayer and see what you think.

---

