---
title: "Why does Flash always stop working with firefox 3?"
date: 2008-06-29
forum: General Help
---

### Post by sonicb00m on 2008-06-29
THis is quite frustrating, I just reinstalled Hardy from scratched and ran all the updates and then decided that I would start with a totally clean profile in firefox 3 and recreate everything from hand, instead of copying over my old profile.

Flash was working ok but as usual now I just get a great big grey box and nothing works. I am getting so tired of this.

x64 edition, how do i get it work again? Reinstalling flash doesn't solve it.

Also, installing gnash or the the free flash doesn't work either. All i get is the missing plugins message despite installing god knows how many times. What a load of ****.

---

### Post by entropy_ on 2008-06-29
There is no 64bit version of the official flash player
Either install the [32 bit version of firefox]("http://ubuntuforums.org/showthread.php?p=1174435") or use [nswrapperplugin]("http://ubuntuforums.org/showthread.php?t=341727") to use the 32bit version of flash player

---

### Post by sonicb00m on 2008-06-30
That's not the problem. The problem is it just stops working out of the blue.

Neither does installing the gnash etc. They are not registered with Firefox 3 as usuable.

No problems with FF2 on x64.

---

### Post by danwood76 on 2008-06-30
Its an issue with npviewer, though on my 64 bit system flash runs fine now.
With the initial release of hardy there were issues, update firefox to the official 3.0 release as thats what I'm using and its fine.

---

### Post by sonicb00m on 2008-06-30
I am using the latest, unfortunately, but problems persist. It's a fresh install with all the updates. All my machines are the same.

---

### Post by jualin on 2008-06-30
Using Firefox 2 solves the FLash problems?

---

### Post by sonicb00m on 2008-07-01
Yeah, flash also works in Opera just fine too. It's jsut with FF3 (final) that I get this white box. It's happened on all my machines at some point,.

---

### Post by sonicb00m on 2008-07-01
Actually, it seems to be pulse audio . I removed that completely and reinstalled the flash stuff and it's working again now.

Pulse Audio in Ubuntu final is a disaster. It's outrageous this has been added to Ubuntu.

---

### Post by vipseixas on 2008-12-02
I have the same problem, sometimes flash just stops working on FF3. If I restart FF it comes back for a while.

The question is, uninstalling PulseAudio really did the job for you? And if a remove PulseAudio, what can I use instead? Or I do not really need PulseAudio? 

Besides that problem, I am very disappointed with FF3 on Linux because I have a bunch of problems with it. FF3 on Win just works fine for me (I use both systems). I thinking of moving to Opera on both systems, but I sure will miss some add-ons.

---

### Post by vipseixas on 2008-12-03
For the record: I wiped out PulseAudio from my system and the gray box problem persists...

---

### Post by danwood76 on 2008-12-03
With the latest version of flash (64bit from adobe) I have had no issues.
It works completely with pulse and everything.

WHat version of flash are you using and are you on 64bit or 32?

---

### Post by vipseixas on 2008-12-04
I am using 64 bits: flashplugin-nonfree_10.0.12.36ubuntu1_amd64. It's the last version available from the multiverse repository.

It's strange that Opera uses the same plugin without problem. I think the problem is on FF, when the problem arises I can't see the plugin running (ps xa | grep flashplugin shows nothing).

I think I will try to use the 32 bits FF version...

---

### Post by danwood76 on 2008-12-04
Use the latest version of the plugin available from adobe labs.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
Its in the alpha stage but it works perfectly and is actually 64-bit.

The one in the repos uses nspluginwrapper to launch the 32 bit flash plugin in a 64 bit browser, this is where all the issues come from.
You will need to uninstall the one from the repos and install the one (un-tar) from adobe labs into ~/.mozilla/plugins/

---

### Post by lifeofcannabis on 2008-12-04
i just fixed this problem on my laptop like min ago with some googling, if your using firefox, uninstall all flash packages in add/remove in apps menu.

im not sure the terminal commands but someone here can help you or google sudo uninstall flashplugins-nonfree

and those other packages from gnash, and the other player, (google the packages name to uninstall) because not all show up in add/remove apps

need more help just message me, so i can google the commands for you,

now once you do this download this:
[http://contribsoft.caixamagica.pt/trac/browser/packages/cm12/FlashPlayer/current/SOURCES/install_flash_player_10_linux.tar.gz?rev=1171&format=raw](http://contribsoft.caixamagica.pt/trac/browser/packages/cm12/FlashPlayer/current/SOURCES/install_flash_player_10_linux.tar.gz?rev=1171&format=raw)

once all packages are uninstall run the install in that archive for installing flash,
this will install flash in the right area, now flash will work perfect, no greyed out click play buttons.
goodluck let me know if you need help

---

### Post by robobot on 2008-12-04
I had problems with Flash and Firefox 3, too; specifically, Hulu wouldn't work. I installed the alpha version of x64 Flash from Adobe, and everything works fine now. I'm surprised it works so well for an alpha version.

---

### Post by vipseixas on 2008-12-04
Thanks a lot guys! The alfa version from Adobe is working fine. Just tested a lot of flash sites and no gray boxes anymore!

Thanx again!

---

### Post by danwood76 on 2008-12-04
Where it says alpha.
Its the same as the actual v10 flash, just compiled with the alpha version JIT compiler.
It should work the same as the 32 bit in theory but could have some issues as the compiler is new.

---

