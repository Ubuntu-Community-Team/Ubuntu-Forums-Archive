---
title: "HP Netbook and Ubuntu 9.10"
date: 2012-11-16
forum: General Help
---

### Post by zunebuggy on 2012-11-16
We have an HP Mini 311-1037NR netbook from Verizon and then my wife bought a laptop.  The netbook also had a nasty root-kit virus, so we decided to reinstall Windows 7 32 bit but Verizon never gave us a way to reinstall Win 7 32.  It has no CD Rom, and they never gave us a reinstall flash drive. 

I was able to make an iso of my Windows 7 32 and make a bootable flash drive from it, but when I went to read the key on the bottom of the netbook, the heat from the netbook had turned the whole MS key sticker black and unreadable.  I spend half a day with Verizon being transfered back and forth and hung up on.  I finally has enough and put Ubuntu 12 on it.  

My daughter wanted to use it for Club Penguin and it was incredibly slow.  So I read I could log in as Unity 2D to speed it up.  Well it was supposed to come with 12 but at the loging screen there is no cog icon and no way I saw to go to Unity 2D.  So I installed Unity 2D and it said it was installed but still no way to find it or to launch it.  

Then I read that Ubunutu 9.10 works very well on the HP netbook I have so I found the iso and installed it.

It's installed but so far I have these issues:

[B][LIST]
[*]No wifi driver
[*]No Flash Player for Club Penguin
[/LIST][/B]

I am currently connected via ethernet.

I go to adobe and it hangs when I click download.  

So I tried:

sudo apt-get install ubuntu-restricted-extras

and I get "Couldn't find package ubuntu-restricted-extras"

Then I tried 

sudo dpkg -i install flash_player_10_linux.deb

and get "No such file or directory"

I originally started Ubuntu with 9 and it was what I was most comfortable with and I could install almost anything from Synaptic Package Manager but it seems there is no more file support for Synaptic.  Is that the case?

Where can I get the wifi driver and flash player and any other drivers or software I'll need for 9.10?

Thanks,
Zune :guitar:

---

### Post by Impavidus on 2012-11-16
Ubuntu 9.10 is no longer supported, therefore the packages are unavailable. The latest Ubuntu version (I recommend 12.04 LTS) should run on that netbook without problem, that is, when the correct graphics drivers have been installed. That often happens with nvidia GPUs. Check for additional drivers.

Wifi drivers can sometimes be problematic as well, but first try to install 12.04 and see wat happens.

Synaptic still exists, but is no longer installed by default. You can install it via the command line or the software centre.

---

### Post by jerome1232 on 2012-11-16
I have that exact netbook running 12.04 LTS flawlessly, just upgraded it to 12.10 and it's working great, and faster than Win 7 SE.

Has an intel chip so graphics shouldn't be a problem.

I also wanted to mention these netbooks come with a recovery partition that allows you to reinstall Windows 7 SE, but if you've deleted it...


edit: whooops, mine is a Mini 110-3735DX, I'm not sure if there is a significant difference. Mine uses RTL8188CE chipset for wireless.

---

