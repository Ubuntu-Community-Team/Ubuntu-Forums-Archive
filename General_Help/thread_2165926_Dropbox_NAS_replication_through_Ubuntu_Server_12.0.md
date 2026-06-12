---
title: "Dropbox NAS replication through Ubuntu Server 12.04"
date: 2013-08-07
forum: General Help
---

### Post by snowtr on 2013-08-07
**Background**
[COLOR=#333333][FONT=UbuntuRegular]I have a D-LINK DNS-320 NAS which works well to provide SMB shares but not much else. I have mounted the volumes on my NAS to my Ubuntu Server 12.04 VM which runs as production for me for several internal and external sites.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My own Documents, Pictures, etc... I moved to the NAS some time ago to a folder on my own name.
[/FONT][/COLOR]
**Dropbox**
[COLOR=#333333][FONT=UbuntuRegular]I have since installed Dropbox and made it into a daemon by following another article and this resulted in my user's home folder having a new folder called Dropbox inside which replicates without issue.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My problems comes from that inside that folder I created a soft link called Documents to the folder named after me on my NAS through the mount. i.e.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]/home/user/Dropbox/Documents -> /mnt/nas1/vol1/Files/user
[/FONT][/COLOR]
**Problem**
[COLOR=#333333][FONT=UbuntuRegular]Now whenever I reboot it seems to me like the NAS is not mounting before Dropbox kicks in because rebooting the Ubuntu Server causes Dropbox to wipe all my files. Then if I SSH in and run their python script to restart Dropbox then it finds everything (almost everything) again and starts to upload it. This back and forth is causing me issues and to loose some of my files.
[/FONT][/COLOR]
**Current status**
[COLOR=#333333][FONT=UbuntuRegular]I have for now disabled the Dropbox daomon on my Ubuntu Server and I am currently working with Dropbox to try to restore all of my files.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Once I have done this, I need to come up with a better method.
[/FONT][/COLOR]
**Original Idea**
[COLOR=#333333][FONT=UbuntuRegular]My original idea was that Dropbox would simply replicate all of my Documents and allow not only everything to be synced between smart phones, tables, laptops, and desktops, but for me to also keep a synced copy on my NAS for backup purposes.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Clearly at this point I cannot do this if I cannot fix the above issue so I am reaching out for some help and I would welcome ideas.[/FONT][/COLOR]

---

