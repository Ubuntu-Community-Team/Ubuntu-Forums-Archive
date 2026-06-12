---
title: "Updates"
date: 2014-07-17
forum: General Help
---

### Post by noel6 on 2014-07-17
tells me is is updating digital photo manager then goes on to unpacking shotwell then says the install or removal failed. not sure what to do. am thinking of uninstalling then reinstalling shotwell. any thoughts. thanks

---

### Post by plucky on 2014-07-18
> **noel6 said:**
> tells me is is updating digital photo manager then goes on to unpacking shotwell then says the install or removal failed. not sure what to do. am thinking of uninstalling then reinstalling shotwell. any thoughts. thanks

Get it to download the package again using from a terminal the command ```
sudo apt-get clean
``` and then ```
sudo apt-get update && sudo apt-get upgrade
```

If you get the same error,post the complete output of the "upgrade" command.

Good Luck

---

### Post by kc1di on 2014-07-18
if what plucky said does not work try this in a termial ```
sudo rm /var/lib/apt/lists/* -vf 
``` then run plucky's commands again.

---

### Post by noel6 on 2014-07-18
your suggestion worked [                                                      [IMG]http://ubuntuforums.org/customavatars/avatar317619_4.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=317619")                                                                                     [**[COLOR=#000000]plucky[/COLOR]**]("http://ubuntuforums.org/member.php?u=317619"). thank you very much. thanks for your input as well [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1839_3.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1839") 				 				 					 						 	[**[COLOR=#000000]kc1di[/COLOR]**]("http://ubuntuforums.org/member.php?u=1839")

---

