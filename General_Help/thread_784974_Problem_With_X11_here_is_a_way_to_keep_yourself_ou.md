---
title: "Problem With X11 here is a way to keep yourself out of trouble!"
date: 2008-05-07
forum: General Help
---

### Post by rabbitnightmare on 2008-05-07
My one niece was trying her hand on updating her graphic card drivers and got locked out of Kde, eg, she damaged her xorg.conf. LOL we all been there.

So I wrote this for her so she can at least get her desktop back.

How this works:

   1. sudo cp /etc/X11/xorg.conf xorg.conf.bak
   2. gksudo gedit Copy and paste the script found below into gedit or your favorite editor and save in /. I called hers "fix_xorg", call yours what you want.
   3. When you have a problem and you can't login due to xorg.conf problems you just get a command login, type your username <Enter> and then your password <Enter>.
   4. Next, just type sudo /fix_xorg or what ever name you called it, and in just a few seconds you should be in the desktop.
   5. You can now just end session and type reboot if you want and after reboot login to your user account.
   6. Each time you make an adjustment to your xorg.conf and you like the adjustment, and you can login, just delete your old xorg.conf.bak and make a new one from your current working xorg.conf.
   7. This way you always have a backup of your most current working xorg.conf, just in case something goes wrong, you can quickly fix it.

```


#!/bin/sh
filename=/etc/X11/xorg.conf.bak
if [ -f "$filename" ]
then
rm -f /etc/X11/xorg.conf
cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
sleep 2
startx
fi

```

I do this with every distro I use and I believe it should be included in Ubuntu as an option!

---

