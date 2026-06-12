---
title: "Mythtv Problems....newbie!!!!!"
date: 2006-08-17
forum: General Help
---

### Post by Lester_Burnham on 2006-08-17
Hi all,

This is my first post around here so please be gentle :)

I'm trying to get Mythtv up and running on 6.06 LTS (even tried on 5.10), but I keep getting tripped up by something along the way.

I've tried Hyams & Abarbaccia also and was very close on 5.10 server, but I couldn't get X loaded, so I trashed it again :)

A fresh updated install is now ready to go, so when I get a chance to start again in the next few days it would be great if you guys could point me in the right direction.

One thing I am curious about when running 6.06 is using the 5.10 repository's. I always seem to get dependency problems, which I sort of expected.

Thanks,
Lester

---

### Post by Titus A Duxass on 2006-08-17
You will get problems using Breezy repositories in Dapper!

Either change the repositories to Dapper or use Breezy.

Hyams Breezy install works well but you have to pay attention to the instructions.

If you are setting up a pure MythTV box for a HTPC have a go at MythDora, it's totally automatic and takes about 35 minutes to install.

If you still want to do an install based on ubuntu start with a clean install and have both / and /home as two partitions.

Follow the instructions to the letter, use the tab key to autocomplete commands.  This saves a lot of time and tailors the instructions to your machine.

Finally, come back to the forum for assistance.

---

### Post by Lester_Burnham on 2006-08-17
Hi Titus A Duxass :)

I'll have to get used to the TAB key thing. Most of what I've done so far has been copy and pasting with terminal or putty.
So, how does it help you? Does it auto complete the file name plus let you cycle through what versions are available?

I will give the MythDora a go...I've never heard of it.
I did have Knoppmyth up and running, but in natural progression, wanted to use Ubuntu next with it being easier to configure background stuff via GUI.

I would like to stick with Ubuntu, as the machine will most likely end up a backend and a server, then I can just run a dual boot knoppmyth or Ubuntu frontend with MCE maybe.

Would I be better off loading Ubuntu Server and then adding a GUI later, as LAMP is pretty much required anyway?

Thanks,
Lester

---

### Post by Titus A Duxass on 2006-08-18
It auto completes your file name / directory entries.

Cutting and pasting from Hyams guide will lead to trouble, that is why I recommend using the tab function.

I would do a normal ubuntu install, some of the things in Hyams guide are Gnome specific, if you know your way around the command line or around another WM then do a server install with the WM of your choice.

---

