---
title: "Can I use Deja Dup on Kubuntu???"
date: 2015-10-14
forum: General Help
---

### Post by Alcidious on 2015-10-14
I have been using the default installation of Deja Dup on my Ubuntu laptop and Desktop to make backups for several years. I am trying to synchronize all my data from various backups, so I have partitioned my hard drive and installed Kubuntu.

Can I use Deja Dup to restore a backup to a clean installation of Kubuntu?

If not, do I need to just restore a backup to Ubuntu only? Is there another tool I can use?

Thanks!

I have Ubuntu LTS 14.04 installed on my desktop and laptop. On my desktop, I've partitioned the Hard Drive and installed Kubuntu 15.04. All my backups are on an External Hard Drive.

---

### Post by mastablasta on 2015-10-15
of course you can use. why wouldn't you be able to?

you can also use some KDE apps in windows. as well as some Gnome apps.

just know that it will pull in it's gnome dependencies. not an issue as long as you have disk space. most disks these days have plenty of space, so even if you installed both DE side by side you would have less space taken than installing windows 8.

---

### Post by Alcidious on 2015-10-15
Is the only difference the KDE Desktop? Does that have different files associated with it, that would be stored during backup?

I couldn't find Deja Dup in the Kubuntu Software App, so assumed it wasn't inlcuded for a reason. I just want to make sure I get all my old files, documents, and photos and such so I can clear my external hard drive and "restore" them to Kubuntu ....

---

### Post by deadflowr on 2015-10-15
deja dup is simply a user interface for the duplicity backup program.
As far as I know all the backups are marked as duplicity files, so any file should work with any duplicity frontend or command.
One would think.

But I would also agree that I can't see any serious reason, outside of adding gnome bloat, that it won't work on KDE.
The only thing about it is it might be what you could call crippled as deja-dup has some integrated functions to it that makes it work with various components of gnome.
(An example of this is it is integrated into the file manager, nautilus)
But those would be more feature crippled than usability crippled, imo.


Here's gnome's howto restore when dejadup goes bust
which might be of use
[https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase](https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase)

Food for thought, I guess.

---

