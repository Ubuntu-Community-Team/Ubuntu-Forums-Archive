---
title: "First day of ubuntu, a few questions"
date: 2005-11-01
forum: General Help
---

### Post by leg_of_pinguin on 2005-11-01
I've installed ubuntu 5.10. It looks great, and I would like to keep it.
However there are a number of issues I haven't found yet how to resolve.

Please kindly help me

1. Flash plugin is failed to install in mozilla. Manual install according to instructions on [www.ubuntuguide.org](www.ubuntuguide.org) fails either. (Probably they fit only for 5.04 version)

2. How to teach mozilla to process ed2k links automatically - add them to amule download list?

---

### Post by paddyg on 2005-11-01
as for flash plugin, just try here

[http://plugindoc.mozdev.org/linux.html#Flash](http://plugindoc.mozdev.org/linux.html#Flash)

(both download link and how to install)

---

### Post by Sionide on 2005-11-01
The latter can probably be done with a Mozilla Firefox extension.

[https://addons.mozilla.org/extensions/](https://addons.mozilla.org/extensions/)

A quick search on "ed2k" gives me [https://addons.mozilla.org/extensions/moreinfo.php?id=609](https://addons.mozilla.org/extensions/moreinfo.php?id=609)

---

### Post by leg_of_pinguin on 2005-11-01
I tried to install flash using 3 methods:

1) Automatic plugin install in Mozilla - failed
2) sudo apt-get install flashplayer-mozilla
   2.1) flash is absent in all ubuntu 5.10 repositories (while it seems that 5.04 repositories do have it)
   2.2) when I added 5.04 repositories to 5.10, it failed to install this package
3) I went to "[Macromedia Flash Player Download Center Linux]("http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4")", downloaded their linux package and followed intalling instructions. The installer script has started and failed.

Please advise how to proceed.

---

### Post by leg_of_pinguin on 2005-11-01
Probably this is ubuntu 5.10 issue. I installed Flash in Debian quite easily. People say that 5.04 works well with Flash.

Did somebody install flash on clean 5.10?

---

### Post by felix_stegerman on 2005-11-01
Please elaborate. What do you mean by "failed"? What error message did you get?

And what does your sources.list look like?

And just to make sure: you're not using a Mac or other non-x86 architecture,
by any chance, are you ? ;-)


Felix

---

### Post by lerrup on 2005-11-01
Have you enabled the universe/multiverse repositories?

See [here]("http://help.ubuntu.com/starterguide/C/faqguide-all.html") or System=>help

Flash is in there, follow the instructions and you should be fine.

---

### Post by codejunkie on 2005-11-01
[quote=leg_of_pinguin]Probably this is ubuntu 5.10 issue. I installed Flash in Debian quite easily. People say that 5.04 works well with Flash.

Did somebody install flash on clean 5.10?[/quote]
firefox is the same version in both ubuntu5.04 &ubuntu5.10 so flash should and does work just fine at least it does in my case. you need to open up synaptic and install the package flashplayer-mozilla if you can't find it in synaptic you need to add the universe & multiverse repo's to your /etc/apt/sources.list file

---

### Post by leg_of_pinguin on 2005-11-01
Thanks for response! I am not able to copy messages, since I'm at work now and linux stays at my home computer. But I remember them very well.

(Automatic way)
1. I use mozilla and go on some internet site where flash animation is used. Then I see a message "Install missing plugins" of mozilla, say "yes", it goes through an automatic process - download, set up, and then... "failed" on the last window. Mozilla doesn't give any additional info.

(Ubuntu natural way)
2. I go to ubuntu "Add programs", add all possible repositories that are part of clean 5.10 ubuntu, including "universe", "multiuniverse". Then I make search for word "flash" - no entries are found.

(Ubuntu ~natural way)
3. I edit sources.list manually, uncomment everything which is commented - still flash is not found.

(Ubuntu tweak way)
4. I edit sources.list manually and add all repositories of ubuntu 5.04 (taken from  [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories). Now flashplayer-mozilla package is found. However apt-get doesn't succeed. **Here I don't remember exact message, I will publish it today at evening.**

(Macromedia recommended way)
5. I download install_flash_player_7_linux.tar.gz, uncompress it and run their script. It asks for place of mozilla (/usr/etc/mozilla if I remember correctly), I type the path. Then the script does something. At the end it asks again for the path to mozilla, I type the path and everything repeats in infinite cycle. Finally I break it by Ctrl-C.

---

### Post by codejunkie on 2005-11-01
[quote=leg_of_pinguin]Thanks for response! I am not able to copy messages, since I'm at work now and linux stays at my home computer. But I remember them very well.

(Automatic way)
1. I use mozilla and go on some internet site where flash animation is used. Then I see a message "Install missing plugins" of mozilla, say "yes", it goes through an automatic process - download, set up, and then... "failed" on the last window. Mozilla doesn't give any additional info.

(Ubuntu natural way)
2. I go to ubuntu "Add programs", add all possible repositories that are part of clean 5.10 ubuntu, including "universe", "multiuniverse". Then I make search for word "flash" - no entries are found.

(Ubuntu ~natural way)
3. I edit sources.list manually, uncomment everything which is commented - still flash is not found.

(Ubuntu tweak way)
4. I edit sources.list manually and add all repositories of ubuntu 5.04 (taken from  [http://www.ubuntuguide.org/#extrarepositories]("http://www.ubuntuguide.org/#extrarepositories"). Now flashplayer-mozilla package is found. However apt-get doesn't succeed. **Here I don't remember exact message, I will publish it today at evening.**

(Macromedia recommended way)
5. I download install_flash_player_7_linux.tar.gz, uncompress it and run their script. It asks for place of mozilla (/usr/etc/mozilla if I remember correctly), I type the path. Then the script does something. At the end it asks again for the path to mozilla, I type the path and everything repeats in infinite cycle. Finally I break it by Ctrl-C.[/quote] the path to mozilla is /usr/lib/mozilla the one to firefox is /usr/lib/mozilla-firefox if that helps with the installer script you can also manually copy the flashplayer.xpt and libflash.so files from the macromedia installer to the /usr/lib/mozilla/plugins & /usr/lib/mozilla-firefox/plugins dir as root and flash will work also.

---

### Post by lerrup on 2005-11-01
[QUOTE=leg_of_pinguin]Thanks for response! I am not able to copy messages, since I'm at work now and linux stays at my home computer. But I remember them very well.

(Automatic way)
1. I use mozilla and go on some internet site where flash animation is used. Then I see a message "Install missing plugins" of mozilla, say "yes", it goes through an automatic process - download, set up, and then... "failed" on the last window. Mozilla doesn't give any additional info.

(Ubuntu natural way)
2. I go to ubuntu "Add programs", add all possible repositories that are part of clean 5.10 ubuntu, including "universe", "multiuniverse". Then I make search for word "flash" - no entries are found.

(Ubuntu ~natural way)
3. I edit sources.list manually, uncomment everything which is commented - still flash is not found.

(Ubuntu tweak way)
4. I edit sources.list manually and add all repositories of ubuntu 5.04 (taken from  [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories). Now flashplayer-mozilla package is found. However apt-get doesn't succeed. **Here I don't remember exact message, I will publish it today at evening.**

(Macromedia recommended way)
5. I download install_flash_player_7_linux.tar.gz, uncompress it and run their script. It asks for place of mozilla (/usr/etc/mozilla if I remember correctly), I type the path. Then the script does something. At the end it asks again for the path to mozilla, I type the path and everything repeats in infinite cycle. Finally I break it by Ctrl-C.[/QUOTE]


Weird, if you search in synaptic for flash under name and description and you find nothing?  Post your repositories list as I get about 10 entries of various levels of usefulness.

---

### Post by leg_of_pinguin on 2005-11-01
Thanks. I will check it today at evening and then write about results. Hopefully it will work in either way.

---

### Post by paddyg on 2005-11-01
no need of synaptic and reps for such a small issue as firefox flash plugin!

Just install it manually (leave the script alone---just do it yourself as root), just as codejunkie has said in comment # 10.

Then if you want to check, in firefox navigation bar type:

```
about:plugins
```

---

### Post by lerrup on 2005-11-01
[QUOTE=paddyg]no need of synaptic and reps for such a small issue as firefox flash plugin!

Just install it manually (leave the script alone---just do it yourself as root), just as codejunkie has said in comment # 10.

Then if you want to check, in firefox navigation bar type:

```
about:plugins
```[/QUOTE]

Maybe not, but if it doesn't turn up there, something is weird.

---

### Post by jeremy on 2005-11-01
Assuming that you have correctly enabled the universe and multiverse repos, do:
sudo apt-get update
followed by:
sudo apt-get install flashplayer-mozilla

If this does not work (and it should for breezy) then post your /etc/apt/sources.list here.

---

### Post by leg_of_pinguin on 2005-11-02
Thanks for everybody. I returned yesterday home, and flash just worked!(?) I swear, I did nothing.

As for ed2k automatic link proccessor, I still have no idea how to enable it.

**I would like to raise one more question**, utilizing your helping mood. There is one partition (out of 6 that I have) that ubuntu recognizes as required "root" privileges and doesn't allow me to see it.

BUT it is not a "root", and more then that - it is fully Windows Fat32 partition!!! Problem is that I copied all my previous linus files to that partition and now I would like to access them.

Now I copy the files back by Windows, using ext3 driver, which is humiliating.

What could be a reason for such phenomenon?;)

---

### Post by paddyg on 2005-11-02
[QUOTE=leg_of_pinguin]
**I would like to raise one more question**, utilizing your helping mood. There is one partition (out of 6 that I have) that ubuntu recognizes as required "root" privileges and doesn't allow me to see it.

BUT it is not a "root", and more then that - it is fully Windows Fat32 partition!!! Problem is that I copied all my previous linus files to that partition and now I would like to access them.

Now I copy the files back by Windows, using ext3 driver, which is humiliating.

What could be a reason for such phenomenon?;)[/QUOTE]

what does your /ect/fstab say ?

---

### Post by leg_of_pinguin on 2005-11-02
[QUOTE=paddyg]what does your /ect/fstab say ?[/QUOTE]
Should I type this in the terminal window? I will check it out.

---

### Post by lerrup on 2005-11-02
[QUOTE=leg_of_pinguin]Should I type this in the terminal window? I will check it out.[/QUOTE]

No, open in it a text editor and you will see priviliges for it there.  If you copy and paste them we can see what the prob is.

---

