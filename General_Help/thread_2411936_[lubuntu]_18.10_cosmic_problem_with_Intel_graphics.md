---
title: "[lubuntu] 18.10 cosmic: problem with Intel graphics after sudden black screen boot"
date: 2019-02-05
forum: General Help
---

### Post by scragnoth on 2019-02-05
Hi, I'm running a rather old Lenovo machine:

Intel Pentium Dual CPU E2140
4 GB RAM
82946GZ/GL Integrated Graphics Controller (An Intel GMA 3000)

A few hours ago I did shut down the system as usual. The black desktop background was weird, but I didn't care about it, normally I have the standard background image (that purple one).
When I wanted to use the system again, it booted to a black screen.
I followed the procedure to get into GRUB and hitting "e" when my ubuntu installation was highlighted in the menu. I replaced "quiet splash" with "nomodeset", followed by "CRTL+X"

(found that here: [https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it))

Text was scrolling on the screen, but it did stop at "Started Update UTMP about System Runlevel Changes" - waited a few minutes and then hit power off, it then scrolled more text after that (received power-off or sth) and then the machine was silent. I did power it on again, did the nomodeset fix again, then first nothing, but low and behold, my login screen reappeared, weirdly stretched tho (my display's native resolution is 1680x1050 - also an older display). I can't change it. Then I tried a few things, but nothing worked (re-installing the intel graphics drivers.

I always have to go the nomodeset route now to boot my machine. Otherwise I have the black screen boot issue back. When I had the idea to look for updates with Discover,  It alwys shows me "The PackageKit daemon has crashed" (that wasn't the case when I ran Discover the last time before today). When it showed me X updates, after that it said I'm up to date. Did hit "check for updates" manually, the PackageKit error reappeared, but then it showed me the 42 updates which I all installed (was running a Linux Mint installation on a more powerful machine before, that machine died, but there he told me about new updates in the status bar, I didn't have to start sth. like Discover manually to check for updates. Is there a way to notify me about new updates automatically like it was in Mint on the other machine?).
After that, again 12 new updates, which I also installed. That didn't fix it.

My "sudo apt-get update" output looks like this

```
Ign:1 http://ppa.launchpad.net/ubuntu-x-swat/intel-graphics-updates/ubuntu cosmic InRelease
Hit:2 http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu cosmic InRelease                                                
Hit:3 http://archive.ubuntu.com/ubuntu cosmic InRelease                                                                     
Get:4 http://security.ubuntu.com/ubuntu cosmic-security InRelease [88,7 kB]                                                 
Err:5 http://ppa.launchpad.net/ubuntu-x-swat/intel-graphics-updates/ubuntu cosmic Release                                   
  404  Not Found [IP: 91.189.95.83 80]
Get:6 http://archive.ubuntu.com/ubuntu cosmic-updates InRelease [88,7 kB]                                                   
Hit:7 http://repo.steampowered.com/steam precise InRelease                                                            
Get:8 http://archive.ubuntu.com/ubuntu cosmic-backports InRelease [74,6 kB]                                           
Reading package lists... Done                                 
E: The repository 'http://ppa.launchpad.net/ubuntu-x-swat/intel-graphics-updates/ubuntu cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target DEP-11-icons-large (main/dep11/icons-128x128.tar) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4                                                                                                                    
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:1 and /etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-intel-graphics-updates-cosmic.list:4
```

[ATTACH=CONFIG]282409[/ATTACH]
[COLOR=#000000]Sorry I had to use the more awkward screenshot option, but I never figured out how I could copy text from a terminal (using uXterm every time, tried it with regular Xterm as well tho) on this installation. In Mint, it worked with CRTL+SHIFT+C. What do I know... and what to I know why there's more than one terminal anyways... 
I don't have the motivation to try to find out (I treid, I read Shift+PrintScreen should work but it wasn't usable in the browser then, just within the terminal I could have inserted the text with Shift+Insert) what's that about when I'm already pulling my hair out with that graphics issue. [/COLOR][COLOR=#ee82ee]

[/COLOR][COLOR=#ff0000]Edit: qterminal which I recalled that I also have on here worked as usual with SHIFT+CRTL+C - at least that's something...[/COLOR]

I think the line starting with "Err:" a few lines in is the culprit in my case. I tried to add that Repository again (maybe that caused those W: lines in the end which weren't there when I started trying to fix the issue).
As told here: [https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates)
and here: [https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/intel-graphics-updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/intel-graphics-updates)

Hope someone can help me, until then I have to live with weirdly stretched graphics display and a more complicated booting routine...

---

### Post by scragnoth on 2019-02-07
Update: Tried / Found out a few things. The ppa  ubuntu-x-swat/intel-graphics-updates/ubuntu cosmic Release                                     gives a 404 because it's packages are incompatible with 18.10. The W:  messages were caused by myself, I added the x-swat repositoreis again,  wheile they were still there. The error messages in Discover  disappeared, once I removed all x-swat ppas. It still booted fine when  using the nomodeset fix.

I wanted to fix it tho, so I searched a  bit and found this PPA, which claims to offer Intel Graphics support on  18.10 - [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)
Added the PPA, installed the packages, tried a normal boot - still a black screen.
But  now, the nomodeset route would always get stuck at "Started Update UTMP  about System Runlevel Changes" and I never got rid of this issue. Tried  everything I could - recovery mode, pkg option (repair broken  packages), that installed something, but no effect, removed the oibaf  ppa and purged the packages, still no effect, wanted to try boot repair  unless I realized that it needs a GUI - didn't work using the root  shell.

Then I realized I could try one more thing: Putting that  ATI Mobility Radeon 5430 back in, which never seemed to work for me  before since no video came from it's VGA port, so I removed it and used  the machine without it.
Again, low and behold, now the internal VGA  was deactivated and it did boot first try. Full resolution again, but  ABYSMAL performance. Scrolling and moving windows are laggy, YouTube  480p (which was fluid with the GMA 3000) lags as well.
So, I added the oibaf ppa back in, but the performance is just as bad as before.
At  least I can use the machine again, I let boot repair do it's thing  once, and then even tried removing the dGPU again and see if it would  still boot: black screen, and nomodeset still gets stuck on "Started  Update UTMP about System Runlevel Changes" every time.

So, is  there any chance the GMA 3000 will receive a compatible package for  18.10? Good dGPU drivers seem to be a rarity tho, as I saw several  questions regarding the issue of iGPUs outperforming them by far in  ubuntu. What a shame - I wouldn't hold my breath for that getting  better, forever.
Or, is there another driver I could use? The official one was outdated, for an older version of ubuntu, so I didn't bother.

---

### Post by scragnoth on 2019-02-09
Kinda weird but working solution for my machine especially: Found this by digging around... [https://www.overclock.net/forum/74-graphics-cards-general/1498649-so-i-put-pcie-gpu-into-my-old-lenovo-thinkcentre-m55e-one-pcie-1x-add2-r-slot.html](https://www.overclock.net/forum/74-graphics-cards-general/1498649-so-i-put-pcie-gpu-into-my-old-lenovo-thinkcentre-m55e-one-pcie-1x-add2-r-slot.html)

That riser board provides PCIe X1 and a proprietary function for an DVI upgrade board (which just adds DVI in addition to the onboard VGA through the GMA 3000, that's still no dGPU) and PCI. So my Mobility Radeon 5430 uses PCI then? So weird! I didn't found that card for sale, nor another (maybe more powerful one) for that slot. There's PCIe X1 dGPUs for sale but they're crazy expensive, not worth it considering their power.

So, I had that PCIe X16 GeForce 8600 GT lying around which I found laying on the street some time ago... So I tried that from above. I just did it differently (don't know how he pulled it off his way tbh). There's plastic bridges between the populated contacts on that connector, the proprietary DVI board has breaks in it's connector in those spots. So you can't insert a PCIe X16 card there, since that one doesn't have those breaks. So... I just broke the proprietary part off with brute force. I'm never going to use that DVI board anyways. Added the 8600 GT (which is a very low-power card fortunately, only a small fan, no external power required), it's a bit wobbly in there since it's only held by that short part of the connector and it booted right away, no frills.

And what should I say... it's a bit louder, but it doen't make me mad, it surpasses what the GMA 3000 was able to do. YouTube 720p ist possible now, and scrolling and stuff is as fluid as before.

I'm glad it works, but I honestly don't know how... How could that run when most of the 8600 GT's connector isn't connected to anything? But, of course I'm not complaining.

Do you think reinstalling everything could fix that GMA 3000 issue? Or is it true that support for that will never come back? Or hadn't the support been dropped at all, but it just fried a little bit? It's hard for me to research if support has been dropped, I found no list or anything similar in the release notes of 18.10, listing older hardware where there's no compatible drivers anymore...

---

