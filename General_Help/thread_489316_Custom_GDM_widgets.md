---
title: "Custom GDM widgets"
date: 2007-07-01
forum: General Help
---

### Post by Houlala on 2007-07-01
Hi,

I would like to know if we can add some custom buttons to GDM Login Window : 
In the official doc, you can add widgets (button, list, ...) but you can't connect it to custom command (like custom reboot on other kernel or OS).

I try to find where the command are defined and I just found RebootCommand and other in the /etc/gdm/gdm.conf... But nowhere to add custom command connected with custom widget :(

Someone has solution to this ?
Thanks. Bye

---

### Post by Houlala on 2007-07-01
So, 

I find a way to solve the problem : 

- Add these lines to the GDM theme (/usr/share/gdm/themes/<theme>/<theme>.xml) : 
> <item type="rect" id="custom_cmd_button0" button="true">
 <show type="reboot" modes="console"/>
 <pos y="50%" width="box" height="box" anchor="w"/>
 <box xpadding="0" spacing="2" orientation="horizontal">
	<item type="pixmap">
	   <normal file="icon-reboot.png"/>
	   <prelight file="icon-reboot-prelight.png"/>
	   <active file="icon-reboot-active.png"/>
	</item>
	<item type="label">
	   <normal font="Sans 9" color="#666666"/>
	   <prelight font="Sans 9" color="#ffffff"/>
	   <active font="Sans 9" color="#dc292b"/>
	   <pos y="50%" anchor="w"/>
	   <text>Windows</text>
	</item>
 </box>
</item>

- Launch "gksudo gdmsetup"
- Click on "Command Edition"
- Edit the first custom command and that's it...

But, my command is a script that does :
/usr/sbin/grub-set-default 1 && /sbin/shutdown -r now "Rebooted to Windows from gdm menu."

Then, when I click on my Windows Button in my GDM Theme, my computer doesnt reboot...
Anyone have solution ?

---

### Post by Houlala on 2007-07-01
Ok, got it !

So, in fact, we cant execute script, but just command, so we have to create a C program in order to launch the script to reboot : 
> #include <unistd.h>

int main()
{
	return execlp("/sbin/windows", 0) == -1;
}


Compile, copy and modify the custom command in the gdmsetup.

And put in the script /sbin/windows : 
/usr/sbin/grub-set-default 1 && /sbin/shutdown -r now "Rebooted to Windows from gdm menu."
(1 because the grub entry of windows is the second ;))

That's all folks

---

