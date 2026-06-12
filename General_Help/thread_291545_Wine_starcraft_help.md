---
title: "Wine starcraft help"
date: 2006-11-02
forum: General Help
---

### Post by brad1138 on 2006-11-02
I am having trouble with a couple things getting Starcraft to run. I successfully installed SC and I can run it by showing hidden files and double clicking Starcraft.exe. When I try to do it in terminal I am supposed to type 'wine "/wherever/starcraft.exe"' which for me is "/home/brad/.wine/drive_c/Program Files/Starcraft/Starcraft.exe" or shortened to "~/.wine/drive_c/Program Files/Starcraft/Starcraft.exe". When I type that I get "wine: cannot find '/home/brad/.wine/drive_c/Program'". I tried to cd to the SC dir but when I get into "drive_c" and type cd Program Files it says it doesn't exist(I also tried cd /Program Files-same prob). I have triple checked that all spelling & cases are correct. What am I doing wrong here? My other problem is that when SC did run it was slow and a bit choppy. I am running a Duron 1200 w/512 Mb ram and Nvidia Geforce 2MX. It was running about as fast as it should for a P166 or something (min req P90). I found in a post in these forums to try 'nice -n 20 wine "/wherever/starcraft.exe"' but that gives me the same problem ("wine: cannot find '/home/brad/.wine/drive_c/Program'"). Any ideas? also is that the correct solution for slow play? I do have the current Nvidia drivers loaded.

Thanks,
Brad

---

### Post by CatKiller on 2006-11-02
You're not taking account of the space in "Program Files". You can either use ```
wine "C:\Program Files\Starcraft\starcraft.exe"
``` or escape the space properly, ```
wine .wine/drive_c/Program\ Files/Starcraft/starcraft.exe
``` or, my favourite, use tab-completion to finish the path and filename for you. So > wine .wi<Tab>dr<Tab>P<Tab>St<Tab>starc<Tab>

Once you've got it working, you can start fiddling with the sound configuration to stop it being jerky. nice -n 20 has always worked for me.

---

