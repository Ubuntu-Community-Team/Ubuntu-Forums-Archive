---
title: "Consolidating servers"
date: 2008-03-05
forum: General Help
---

### Post by kameleon25 on 2008-03-05
Hello all,

     I am looking at consolidating 3 or 4 servers I have to help cut down on power usage and heat output. Basically I have the following machines that I want to consolidate:
1. web server running Ubuntu 7.10 server i386 with ISPConfig
2. stats/backup server running Ubuntu 7.10 server i386 with cacti, nagios, and custom backup applications dumping to 2 USB drives.
3. torrent/newsgroup server currently running Ubuntu 7.04 desktop i386 as this was my old desktop that I re-purposed. Running rtorrent, moblock, and hellanzb.
4. PBX server currently running pbx-in-a-flash (centos5) but thinking heavily about just installing asterisk on an Ubuntu system and flying with that.
Each of these is on separate hardware with the exception of the PBX as it is in a virtual machine running on my desktop until I can figure this consolidation deal out. So I am sure you can see my situation. I have 4 machines (not including my laptop, switch, and dual CRT monitors) in my little office :lolflag:. It can get quite warm in there so I need to do something here. But I also want to be security minded. 

The predicament I have is the web server could be rooted more easily than the others since I am testing out the ISPConfig (it already has been once) and have to have it open to the outside world. I need to have it separated from the rest so that if it were to happen again I don't lose all my stuff. The torrent machine needs to be able to run moblock without interfering with any of the other services (or adding many rules to moblockconf). And I also need the backup server (which also keeps copies of the other machines syslogs and such) to stay separate to keep it secure. I have been told that the pbx does really need it's own hardware for stability sake too. 


Here are the options I have thought about. Please let me know the pro's / con's of each or if there is something I have overlooked.
1. Take all the machines and load into virtual machines using vmware server. This option would require me to possibly buy a new setup. I have priced a dual core 2.1ghz amd w/ mobo, 4gb ram, and psu and it is reasonably priced. Each VM would have at least 512MB ram specifically for it with a max of 1GB leaving 1GB to the host machine.
2. running everything with chroot. I am not 100% positive this will work but I have been told by some local friends that it might. Of course I would not have to buy "new" hardware but possibly re-purpose some existing hardware.
3. Move just a few things around and don't worry about VM's or chroot. It will be fine.
4. Forget it all and just leave it all as is. Basically saying I am a wuss for whining about the heat and extra power consumption. ;)

The advantage of 1 and 2 if I can fit all the "machines" on one physical piece of hardware is I can run longer on a UPS than having 3 connected. Also if they all are running in VM's then if/when the hardware dies all I have to do is swap over the vmware guest os files and fire it back up as it does not "see" the host hardware change.

Any help/guidance is very much appreciated.

---

### Post by kameleon25 on 2008-03-06
Anyone? I am looking to try to do this consolidation this comming weekend if possible. Just looking for some opinions/insight of others. Thanks in advance

---

