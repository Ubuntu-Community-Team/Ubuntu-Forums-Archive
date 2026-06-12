---
title: "Install Draftsight on Saucy"
date: 2013-10-16
forum: General Help
---

### Post by gmport on 2013-10-16
[FONT=Liberation Sans][SIZE=2]I am trying to install Draftsight on 64bit Ubuntu 13.10. After installing the i386 libraries as described at:
[URL="http://askubuntu.com/questions/359156/how-do-you-run-a-32-bit-program-on-a-64-bit-version-of-ubuntu"]http://askubuntu.com/questions/359156/how-do-you-run-a-32-bit-program-on-a-64-bit-version-of-ubuntu

[/URL][/SIZE][/FONT]   [FONT=Liberation Sans][SIZE=2]I then ran: [/SIZE][/FONT]   
```
[FONT=Liberation Mono][SIZE=2]sudo dpkg -i ~/Downloads/draftsight.deb[/SIZE][/FONT]
```[FONT=Liberation Sans][SIZE=2]
[/SIZE][/FONT]   [FONT=Liberation Sans][SIZE=2]The output in the terminal indicated that 'cdebconf:i386' was required so this was added.[/SIZE][/FONT]
[FONT=Liberation Sans][SIZE=2]The output when re-installing was:
[/SIZE][/FONT]```

[FONT=Liberation Mono][SIZE=2]~$ sudo dpkg -i ~/Downloads/draftSight.deb [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2](Reading database ... 165340 files and directories currently installed.) [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]Preparing to replace dassault-systemes-draftsight 2013.32.9 (using .../gm/Downloads/draftSight.deb) ... [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]access control disabled, clients can connect from any host [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]access control disabled, clients can connect from any host [/SIZE][/FONT] 

 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 

 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
  
 [FONT=Liberation Mono][SIZE=2](ShowLicence:16496): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine", [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]Gtk-Message: Failed to load module "canberra-gtk-module" [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]access control enabled, only authorized clients can connect [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]access control enabled, only authorized clients can connect [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]Unpacking replacement dassault-systemes-draftsight ... [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]Setting up dassault-systemes-draftsight (2013.32.9) ... [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]Set application as default for the user=gm [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]Set application as default for the user=gm [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]Set application as default for the user=gm [/SIZE][/FONT] 
 [FONT=Liberation Mono][SIZE=2]~$ [/SIZE][/FONT] 
  
```
[FONT=Liberation Sans][SIZE=2]Draftsight was partially installed because I had an icon and the splash screen opened but there was also an error message![/SIZE][/FONT]
 
 “[FONT=Liberation Sans][SIZE=2]Failed to load modules. The application will close.[/SIZE][/FONT]
 [FONT=Liberation Sans][SIZE=2]Please reinstall the application.”[/SIZE][/FONT]
 [FONT=Liberation Sans][SIZE=2]
I don't know what “murrine” is nor what to do about the warning.[/SIZE][/FONT]
 [FONT=Liberation Sans][SIZE=2]Also the line: [FONT=Liberation Mono]Failed to load module "canberra-gtk-module" [/FONT]has got me stumped.[/SIZE][/FONT]
 
[FONT=Liberation Sans][SIZE=2]Does anyone know how to fix this, I have been trying for about 2 weeks to install Draftsight. I've been using it on Mint 15 64bit where it installed with no problem but then I has access to 'ia32-libs'.[/SIZE][/FONT]

Regards gmport.

[FONT=Liberation Sans][SIZE=2]
[/SIZE][/FONT]

---

### Post by imagen99 on 2013-10-16
sudo apt-get install libcanberra-gtk-module:i386 libcanberra-gtk0:i386

---

### Post by gmport on 2013-10-16
Thank you imagen99,

Magic! I did: 'sudo apt-get install libcanberra-gtk-module:i386 libcanberra-gtk0:i386'.

Instant fix - Thank you very much.

Regards gmport.

---

