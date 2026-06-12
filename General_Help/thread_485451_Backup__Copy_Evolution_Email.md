---
title: "Backup / Copy Evolution Email"
date: 2007-06-26
forum: General Help
---

### Post by gargo2000 on 2007-06-26
I'm looking to re-do my whole system.  Now that I am fully converted to using Ubuntu I need more space for it.  I was doing a trial run to see how much I like it...Well I love it.

I'm looking to backup my email in Evolution so I don't loose these emails.  Is there a certain command that I can use to back them up to my external hard drive?  Or is there a specific directory that I can go to and copy the directory to my external and once reloaded, I can re-copy them back.

Thanks for your time in advance who helps me

Gargo

---

### Post by jwh400 on 2007-06-27
From your user directory select "Show Hidden Files" from the "View" menu. What you're looking for should be in the .evolution directory. Copying the entire directory should also back-up  any calendar files you might have.

---

### Post by rbmorse on 2007-06-27
Also, don't forget 

file > backup settings

from the main Evolution menu, just in case.

---

### Post by BCtom on 2007-07-01
I too have tried doing a backup off all my personal files when doing a complete re-install, and found that it is not enough to just copy the file, like ".evolution" onto a disk, then copy back again. I found that to restore the program like Evolution, Firefox, etc..., I needed create archives for each folder I copied, i.g: rar. When I just copied the file, I found that I had change the CHMOD (file permission) for each individual file before the upgrade would accept it as my file. With an archived version, the CHMOD is automatically done when copied. 

I don't know if this is a problem that everyone experiences or not, but it was one, by doing the archiving trick, it made my files work with the new install of Ubuntu.

---

### Post by Razer_PcBg on 2007-07-03
Recently I did a successful backup/restore operation of my Evolution mail.  This included all mail, all folders and e-mail filters.  I did not have any calendar items so can't confirm if this is included though I believe it is.  Unfortunately your e-mail account settings do not get saved so it's a case of quickly setting up POP/SMTP again which takes 2 minutes.  Any e-mail signatures also have to be recreated.

After Ctrl+Alt+F1 -> Terminal, and logging in with my user account, I ran the following commands:

$gconftool-2 --shutdown
$evolution --force-shutdown
$tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution

The first 2 lines did nothing! :/

I did however get an error referring to the last bit but the compressed file was still created in my Home folder.  I then copied that to a flash disk drive, did a clean install of Feisty, copied the compressed file into my new Home folder, and ran the following commands from Terminal:

$gconftool-2 --shutdown
$evolution --force-shutdown
$tar xzf evolution-backup.tar.gz
$gconftool-2 --unload evolution_setting.xml
$gconftool-2 --load evolution_setting.xml

Again the first 2 lines did nothing as I got error messages.
The last 2 lines also generated errors and did not like the .xml bit so I thought the whole restore process was a failure.  But sure enough when I fired up Evolution, everything was there! :p

---

