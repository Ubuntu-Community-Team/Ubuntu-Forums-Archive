---
title: "advice needed, thanks in advance"
date: 2007-02-25
forum: General Help
---

### Post by tyk on 2007-02-25
i need some general advice on something i'm trying out. i have two comps, an amd64 with windows and ubuntu dual boot, which is also my main workstation. i cannot migrate completely to linux due to the software i need (cad/cam/3dstuff etc.) in any case all my old work is in windows based programs... and the other comp is a laptop (pIII thinkpad) which is not really fast/powerful enough for most of my work)

so i intend to set up a text only website on the laptop with links to my various work and personal files on some of the free webservers (savefile.com etc..) might even pay some place to keep it in order and all.. the laptop has a 20gig HD : P so i'll share some of it on /www or something. i left about 8-10 gigs free on my amd64 HD for an eventual linuxinstallation (wasn't expecting another comp). i want to change it to a fat32 so that i can share it as well and link it up to the laptop. i choose fat32 so that i cna effectively write to it from my amd64 as well as the laptop.. (tried ntfs-3g but it nearly killed my HD so am wary and will wait for some time)...
 
**major question** : is this all a decent idea considering i have a broadband (2mbps-supposedly ;) shared over three comps? considering i have about 5-6gigs on the laptop for a website and all its files, is it enough? i know it depends on no. of visitors but i don't realy intend it to be a website where eople can write stuff... what about any temp files and/or logs that might clog up the laptop HD? 

*minor question* : actually already asked somewhere else but i'll include it here as it is connected. i had already installed suse10.1 on the amd64 on the extra space i had. was quite happy with it. then i wanted to uninstall it and convert it to the fat32 i mentioned earlier. at the first attempt i sc**up and simply formatted it from windows. it created major probs with grub coz it wouldn't obviously find its config files and my comp generally froze on grub. then i installed ub6.06 and repaired grub and its kindof back on track, except its device mapping seems a little 'off'. so to boot to ubuntu on the amd64 i have to boot up from a linux or windows installation CD. this step bypasses grub and i get the 'correct' choices of OSs. would appreciate any help i terms of restoring MBR or even using ntldr to boot whichever OSs i might have..

i know its a long post but i really dunno who else to ask all this.. for i am familiar with some stuff but its not really my qualification, i am an architect.

muchos gracias : )

---

### Post by cronholio on 2007-02-25
Unless you also have 2 Mbps upload I wouldn't consider it a good idea. Why not run Samba and share folders this way? You can access Samba shares from Windows and Linux.

---

### Post by tyk on 2007-03-03
?? you mean, i still set up the webserver on the laptop and do samba sharing on it with whatever partitions/folders on it as well as th ntfs folders on the amd64 OR i should set up a server on the windows machine and share through it? and 2mbps is't good enough, is it? i dunno about the upload, but i'm assuming that when they say 2mbps download, it means that upload will be much faster...  thanks in any case :)

---

### Post by cronholio on 2007-03-04
If you have 2 Mbps download you will most probably have 128 kbps or so upload. You can test it [here.]("http://www.bandwidthplace.com/speedtest/")

---

### Post by tyk on 2007-04-07
ahh... and here i always thought 10/100Mbps LAN = download/upload bandwidth..
many thanks..)

---

