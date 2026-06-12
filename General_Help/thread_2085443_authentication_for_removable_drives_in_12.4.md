---
title: "authentication for removable drives in 12.4"
date: 2012-11-18
forum: General Help
---

### Post by harreid on 2012-11-18
Can anybody please help me to authenticate for removable drives. I have tried the following but none of the file listed seem to be in my file system. I'm using Ubuntu 12.4


First of all, backup the file. Open a terminal and run:
 	Code:
 	cd /usr/share/polkit-1/actions/ sudo cp org.freedesktop.udisks.policy org.freedesktop.udisks.policy-backup cd 
then open the file:
 	Code:
 	gksu gedit usr/share/polkit-1/actions/org.freedesktop.udisks.policy 

An entry in the file looks like this:
 	Code:
 	  <action id="org.freedesktop.udisks.filesystem-mount">     <description>Mount a device</description>     <message>Authentication is required to mount the device</message>     <defaults>       <allow_any>no</allow_any>       <allow_inactive>no</allow_inactive>       <allow_active>yes</allow_active>     </defaults>   </action> 
The description of each entry is self-explanatory, it's in human readable format.

Now if you want password authentication by an admin user in order to  mount an external drive, then change the authentication mode from **yse** to **auth_admin** or **auth_admin_keep** (it's like auth_admin but the authorization is kept for a brief period):
 	Code:
 	  <action id="org.freedesktop.udisks.filesystem-mount">     <description>Mount a device</description>     <message>Authentication is required to mount the device</message>     <defaults>       <allow_any>no</allow_any>       <allow_inactive>no</allow_inactive>       <allow_active>**auth_admin_keep**</allow_active>     </defaults>   </action> 
You can change the authentication mode in other entries in a similar way.

Save the file and close the editor & you're done.

The above was for  ubuntu 9.10 so maybe things have changed since then.

Thanks for any advise.

---

### Post by mc4man on 2012-11-18
Your path is wrong - it's this, you were leaving out the red /
> [COLOR="Red"]/[/COLOR]usr/share/polkit-1/actions/org.freedesktop.udisks.policy 
So to edit the proper file
```
gksu gedit /usr/share/polkit-1/actions/org.freedesktop.udisks.policy 
```

In **12.04** not all usb drives are treated as such so you may find that some like SanDisk drives won't be affected by your edit. In that case you need to edit a .pkla that allows active admin/sudo user to mount, check internal drives. If needed ask..

---

### Post by harreid on 2012-11-19
[COLOR=Black]Thank you for taking the time to help me [/COLOR][COLOR=Black][memc4man]("http://ubuntuforums.org/member.php?u=320715")[/COLOR].
I now have my usb external drive mounted and I can read from it, problem is now I can't write to it, I get the message "you are not the owner"  and I can't edit permissions. I'm hoping you can help me again.

Many thanks.

---

