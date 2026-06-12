---
title: "Help me swap to ubuntu :D"
date: 2005-07-27
forum: General Help
---

### Post by revs on 2005-07-27
So ive managed to at least swap from Windows to Linux at my workplace.

There are 2 main obstacles - Groupwise and NetWare Shares.

Currently im running SUSE 9.3 as its now novell owned and thus has a working groupwise app and a nice NetWare app and such.

I want to be on ubuntu tho!! :D who wouldnt.

so - can you help me run Groupwise - its a java app so should work. i have it on a test ubuntu system, but when i try and launch it i get "java/lang/NoClassDefFoundError: java/lang/Object".

And then theres the bigger and more importatn problem: Netware shares.
Has anyoen gotten the Novell Client Linux (the official one, not novel client linux) to work on ubuntu? its a load of rpms, and i gave it a shot with alien, but to no luck.

Ive used the unofficial novelclient linux, and have managed to make a connection - but have not then been able to mount any drives. I must be close tho - if ive made a connection, i cant see how i go and mount drives tho.

Any help is greeeeeeeeeeeeatly appreciated :D :D :D

revs

EDIT: Ok i managed to mount netware volumes with ncpmount - turns out i just had the username specified incorrectly - i didnt have the context, which it seemed to need.

kcik ass... now the Q is - do i want to go from my unbroke (kinda) suse to Ubuntu....

---

### Post by Zifnab on 2005-07-27
Why yes! I did GW just yesterday. Using this download:

[http://download.novell.com/Download?buildid=yV_WpnPZg5k~](http://download.novell.com/Download?buildid=yV_WpnPZg5k~)

It has installations for more than just Linux, so don't let the 90+ meg filesize fool you. Anyhow, untar it and browse to find the Linux .rpm file. I did: ```
alien <rpmfilename>
```to convert to a .deb. Then I su'ed and did: ```
dpkg -i <debfilename>
```This installs it to the directory /opt/novell/groupwise/client. There's a gwclient.desktop file in that directory that can be copied to /usr/share/applications to get a shortcut in your GNOME panel Applications menu.

Worked like a charm. Well, it's java-based and kinda slow compared to the Windows version, but it's still lots better than the only other Linux alternative - using the GroupWise web interface, provided that your mail server has that set up.

---

### Post by revs on 2005-07-28
[QUOTE=Zifnab]Why yes! I did GW just yesterday. Using this download:

[http://download.novell.com/Download?buildid=yV_WpnPZg5k~](http://download.novell.com/Download?buildid=yV_WpnPZg5k~)

It has installations for more than just Linux, so don't let the 90+ meg filesize fool you. Anyhow, untar it and browse to find the Linux .rpm file. I did: ```
alien <rpmfilename>
```to convert to a .deb. Then I su'ed and did: ```
dpkg -i <debfilename>
```This installs it to the directory /opt/novell/groupwise/client. There's a gwclient.desktop file in that directory that can be copied to /usr/share/applications to get a shortcut in your GNOME panel Applications menu.

Worked like a charm. Well, it's java-based and kinda slow compared to the Windows version, but it's still lots better than the only other Linux alternative - using the GroupWise web interface, provided that your mail server has that set up.[/QUOTE]
 cool.

now if only i could get netware shared sorted :)

---

