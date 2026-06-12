---
title: "Can not delete a file from Trash"
date: 2016-01-28
forum: General Help
---

### Post by Marc_Massart on 2016-01-28
I plugged a removable disk in a foreign computer running ubuntu. I deleted some files on that disk through this foreign computer. Once back home I plugged this USB disk in my computer running Lubuntu 15.10.
I immediately saw the previously deleted directory in my trash folder. I remembered I forgot to expunge the trash on the foreign computer.
Now I am unable to delete the directory and file from trash. Even tried Windows.

It looks as if I don't have enough permission to do that (rm, rmdir; chmod, chattr). All give access denied as a result.

How can I solve this without reformatting the disk (contains more than 1.5 TB of data !)

Thank you.

---

### Post by Bucky Ball on 2016-01-28
Welcome. Try using 'sudo' before your commands. 'super user do'. That is why you are getting permission errors.

Be warned: be careful! If you are using rm and rf commands, one false move if you're unsure what you're doing (and as you were unaware you should be using 'sudo' for this I'd say might be good to avoid those commands right now) and you could end up re-installing anyway. Perhaps better to launch the file manager as root, navigate to the trash folder and delete that way. 

> gksudo nautilus

Again, be careful. You have the file manager open as root and can cause some real damage. Delete the file you want from trash folder in the file manager and close the file manager window straight away is best.

---

### Post by Marc_Massart on 2016-02-01
Tried sudo, and it failed. The files are on the SAMBA share mounted disk in :
[email]marc@marc-VirtualBox:/mnt/BBOX3/.Trash[/email]-1000/files/autorun$ ll
totaal 1024
dr-xr-xr-x 1 root root   0 apr  8  2011 ./
drwxrwxrwx 1 root root   0 jan 24 22:37 ../
-r-xr-xr-x 1 root root 766 okt 13  2002 wdlogo.ico*

BBOX3 being the SAMBA share.

Even tried sudo -i and then rm *, still fails.

[email]marc@marc-VirtualBox:/mnt/BBOX3/.Trash[/email]-1000/files/autorun$ rm *
rm: normaal bestand &#8216;wdlogo.ico&#8217; (schrijfbeveiligd) verwijderen? y
rm: kan &#8216;wdlogo.ico&#8217; niet verwijderen: Toegang geweigerd

translation: rm:normal file 'wdlogo.ico' (writeprotected) delete? y
                rm: can not delete 'wdlogo.ico' access denied.
chmod or chattr with sudo does not change anything.
rm with force option uder sudo does not work. The file seems to be welded on my harddrive.

---

