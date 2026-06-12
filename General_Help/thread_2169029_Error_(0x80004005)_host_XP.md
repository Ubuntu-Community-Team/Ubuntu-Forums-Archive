---
title: "Error (0x80004005) host XP"
date: 2013-08-20
forum: General Help
---

### Post by lumaja2 on 2013-08-20
[FONT=Courier New,courier]Ubuntu 12.04 precise[/FONT]
 

 [FONT=Courier New,courier]After VM working properly for months I receive this error(0x80004005) [/FONT] 
 [FONT=Courier New,courier]I read some of the similar problems on Virtualbox forum and decide to remove VM,with Synaptic I remove it but not with “Mark Complete Removal” restart Ubuntu and from Synaptic install vbox-4.2.16 for precise.[/FONT]
 [FONT=Courier New,courier]Start VirtualBox window come up with this error:[/FONT]
 

 [FONT=Courier New,courier]Runtime error opening [/FONT][FONT=Courier New,courier]**'/home/luis/VirtualBox VMs/Windows XP/Windows XP.vbox'**[/FONT][FONT=Courier New,courier] for reading: -102 (File not found.).[/FONT]
 /home/vbox/vbox-4.2.16/src/VBox/Main/src-server/MachineImpl.cpp[725] (nsresult Machine::registeredInit()).
 [TABLE]
 	 	 	[TR]
 		[TD="width: 20%"] 			Result Code:  			
 		[/TD]
 		[TD="width: 80%"] 			[FONT=Courier New,courier]NS_ERROR_FAILURE (0x80004005)[/FONT]
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 20%"] 			Component:  			
 		[/TD]
 		[TD="width: 80%"] 			Machine
 		[/TD]
 	[/TR]
 	[TR]
 		[TD="width: 20%"] 			Interface:  			
 		[/TD]
 		[TD="width: 80%"] 			IMachine {22781af3-1c96-4126-9edf-67a020e0e858}
 		[/TD]
 	[/TR]
 [/TABLE]
 

 [FONT=Courier New,courier]Searching in Ubuntu for.OVA file it failed.[/FONT]
 [FONT=Courier New,courier]Please explain how to export VM to .OVA file and how to fix the error.[/FONT]
 [FONT=Courier New,courier]Thank you[/FONT]

---

### Post by Habitual on 2013-08-22
Luis:
.OVAs are exported appliances.
If the .vbox file isn't there, then you cannot export, however, to answer your question.
highlight the Appliance in Vbox and press Ctrl+E

To 'fix' the 'error' you'll need to re-install XP in Vbox or import an XP .ova from another host or from backup.

---

### Post by lumaja2 on 2013-08-23
Ubuntu 12.04 precise  Found that I lost all my VM, because I uninstall from synaptic, uninstall with Removal not with Complete Removal and I thick there still reference’s of the previous VM in System because of this gives me this error. The selected virtual machine is inaccessible. Please inspect the error shown below and press the Refresh button if you want to repeat the accessibility cheeck: Runtime error opening '/home/luis/VirtualBox*VMs/Windows*XP/Windows*XP.vbox' for reading: -102 (File not found.). /home/vbox/vbox-4.2.16/src/VBox/Main/src-server/MachineImpl.cpp[725] (nsresult Machine::registeredInit()). Result*Code:  NS_ERROR_FAILURE (0x80004005) Component:  Machine Interface:  IMachine {22781af3-1c96-4126-9edf-67a020e0e858} 0n the Virtualbox window there is ? Windows XP inaccessible. Checking System for VM reference’s found a few, my idea is remove the existent pieces of the old installation and start every thing fresh with the newer Virtualbox version 4.5.16 which is in Synaptic, my problem is I don’t know how archive this, can you please help and send instruction. Thank you

---

### Post by Habitual on 2013-08-23
Uninstalling Virtualbox will **not** remove anything in /home/luis/VirtualBox VMs
open a terminal and type 
```
find `pwd` -iname "Windows*.vbox" -type f
``` and 
```
find `pwd` -iname "*.ova" -type f
```
what does it find?

You want the VM back or not? I can't tell, you're so anxious to "start fresh"

However, if there is no windows*.vbox, or .ova file found in your /home/luis directory structure, then you will have to "start fresh" 

If you want to archive the current "/home/luis/VirtualBox VMs/" open a terminal and type
```
 cp -pr "/home/luis/VirtualBox VMs/" "/home/luis/VirtualBox VMs.back"
``` including quotes.
Then you can remove "/home/luis/VirtualBox VMs/" and "start fresh". I have ***never*** had to resort to this on any OS, so I am not advising to not do it, nor to do it.
but once you have made a valid backup, you are free to do as you like. ;)

You don't even have to use "/home/luis/VirtualBox VMs/", that can be 'configured' to use another directory. Personally, mine are in VboxVMs
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

```
find `pwd` -iname "Windows*.vbox" -type f
```
If there is NOTHING returned, you **will** have to re-install Virtualbox **and** Windows XP in it, or restore "/home/luis/VirtualBox VMs/" or the .vbox or the .ova from backup.

I hope that helps you Luis.

---

