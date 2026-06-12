---
title: "-HELP- Run Existing Windows Instalation On Ubuntu With Vmware player -HELP-"
date: 2007-04-05
forum: General Help
---

### Post by SDF-1 on 2007-04-05
Hi I have been using a website to run Windows XP on Vmware player as an existing partition. This is the website that I have been using to follow:

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

When I get into this section (Around 3/4 down on the webpage): 

[COLOR="Red"][I]Type "quit" in parted and make copy of MBR. Copy-paste this command into console:
"dd if=/dev/hda of=windowsxp.mbr bs=512 count=63"[/I][/COLOR]

The terminal won't allow me to make a copy of the master boot record. Does anyone have any ideas of why this does not work? 
[COLOR="Red"]
*Terminal says "Permission Denied"*[/COLOR]

[I]Another question I would like to ask is: is there another website which can explain it far better than this website? I seriously can't understand what this person types sometimes and it can get very confusing for me. I didn't understand this section as well.[I]

[I]Underlined values should be replaced with the values given by parted but there is a catch. Note that second RW value from vmdk file is not the same as the one you got from parted "Disk /dev/hda/". Thats because first partition on disk is master boot record or MBR which points to boot files of operating systems. It's lenght in this case is 63, and as far as I know, it is pretty standard value.[I]

[I]We will use copy of MBR so actual start point of Windows parititon is parted's value "Disk /dev/hda" 240121727 minus 63.[I]

[I]240121727 - 63 = 240121664 <- result goes to vmdk file[I]

Please help me if anyone can I am struggling to get this thing sorted out. :(

---

### Post by zvacet on 2007-04-05
This page same guide but maybe same extra explanations and help
[http://ubuntuforums.org/showthread.php?t=380699&highlight=windhttp://ubuntuforums.org/showthread.php?t=380699&highlight=windoows]("http://ubuntuforums.org/showthread.php?t=380699&highlight=windhttp://ubuntuforums.org/showthread.php?t=380699&highlight=windoows")

---

