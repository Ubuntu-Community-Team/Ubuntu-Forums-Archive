---
title: "Crossover not creating menu entries in Gutsy!!!"
date: 2007-10-19
forum: General Help
---

### Post by SunnyRabbiera on 2007-10-19
I have a copy of crossover for easy installation of windows applications as i have other users on this computer who use windows apps...
sadly it is not creating menu entries on ubntuntu gutsy, I have a copy of crossover 6 left over from my transition days and I really need to get it working...
any help is appreciated...

---

### Post by SunnyRabbiera on 2007-10-19
come on I need help here, so I might bump this a few times till I get it.

---

### Post by grendelkhan on 2007-10-19
It's a known bug at Codeweavers, here's the fix:

In the meantime you can 
fix it by editing /opt/cxoffice/lib/perl/CXMenuXDG.pm and replacing the 
line:

     my $dir=dirname($self->{filename});

with

     my $dir=dirname($self->{menu});

then run /opt/cxoffice/bin/cxsetup 

That will get it installed and have the menu entries created for it.

If you are saying that when it installs windows software, it's not making menu entries when you install software, I've had this be an issue when doing unsupported software, but not when using their supported list.  I end up using the "Run windows command" function to create a new launcher for it.

---

### Post by SunnyRabbiera on 2007-10-19
> **grendelkhan said:**
> It's a known bug at Codeweavers, here's the fix:

In the meantime you can 
fix it by editing /opt/cxoffice/lib/perl/CXMenuXDG.pm and replacing the 
line:

     my $dir=dirname($self->{filename});

with

     my $dir=dirname($self->{menu});

then run /opt/cxoffice/bin/cxsetup 

That will get it installed and have the menu entries created for it.

If you are saying that when it installs windows software, it's not making menu entries when you install software, I've had this be an issue when doing unsupported software, but not when using their supported list.  I end up using the "Run windows command" function to create a new launcher for it.


nope, its a no show... i get the same error with regular wine...
what can I do??? I really need this to work.

---

### Post by Wiebelhaus on 2007-10-19
just a note , just in case , the bootleg torrent doesn't , that's why I paid for mine :)

---

### Post by SunnyRabbiera on 2007-10-19
I have a paid version....

come on I need answers people!!!!!

---

### Post by Wiebelhaus on 2007-10-19
> **SunnyRabbiera said:**
> I have a paid version....

come on I need answers people!!!!!

[HTML]I assume that you installed CrossOver as root. Then the CrossOver menu is
installed in a system-wide location so that it is automatically visible by all
users on the system. So the simplest way to hide it from the users is to remove
it from that system-wide location.

The simplest way to do so is to edit
/opt/cxoffice/share/crossover/data/crossover.menu and replace the

   "Mode"        = "Install"

with

   "Mode"        = "Ignore"

for the relevant menus (presumably 'Install Windows Software', 'Configuration'
and possibly 'Run a Windows Command').
Then run the following command:

/opt/cxoffice/bin/cxmenu --crossover --removeall --install

Note that this mean root will not see these menu entries either. But you can
still run CrossOver Setup from the command line:
/opt/cxoffice/bin/cxsetup

Also note that your users too will still be able to run CrossOver commands from
the command line and thus bypass the missing menu entries. You could remove
execute permissions on /opt/cxoffice/bin/cxsetup and /opt/cxoffice/bin/cxbottle
for non-root users, but even that would only make things a bit harder (they can
always get CrossOver themselves and install it in their account).

[/HTML]

---

### Post by grendelkhan on 2007-10-19
> **SunnyRabbiera said:**
> nope, its a no show... i get the same error with regular wine...
what can I do??? I really need this to work.
What's the problem exactly, I don't think I understand.  You don't have a meny entry for the Crossover tools, or when you install windows software with Crossover, you don't get a menu entry for it?

---

### Post by SunnyRabbiera on 2007-10-19
> **grendelkhan said:**
> What's the problem exactly, I don't think I understand.  You don't have a meny entry for the Crossover tools, or when you install windows software with Crossover, you don't get a menu entry for it?

I dont have a menu for crossover tool and when I install windows software... and no i have no unsupported stuff here, just apps like IE, adobe photoshop 7, MS office XP... ALL are supported.
I really need these programs to work

---

### Post by grendelkhan on 2007-10-19
You may want to contact Codeweaver's support then.  That's where I got my solution from and they said it would be fixed in an upcoming release.

---

### Post by SunnyRabbiera on 2007-10-19
well can someone at least tell how to get wine working for apps at least?
My subscription to crossover expired some while back and i lost my info so going there is no help...

---

### Post by SunnyRabbiera on 2007-10-19
folks???

Please???

I really need windows apps to work here... if this doesnt work then I will go back to PClinux and I will never use ubuntu again... I swear.

---

### Post by SunnyRabbiera on 2007-10-19
bump.....

---

### Post by SunnyRabbiera on 2007-10-19
double bump....

---

### Post by Wiebelhaus on 2007-10-19
> **sx66gns said:**
> [HTML]I assume that you installed CrossOver as root. Then the CrossOver menu is
installed in a system-wide location so that it is automatically visible by all
users on the system. So the simplest way to hide it from the users is to remove
it from that system-wide location.

The simplest way to do so is to edit
/opt/cxoffice/share/crossover/data/crossover.menu and replace the

   "Mode"        = "Install"

with

   "Mode"        = "Ignore"

for the relevant menus (presumably 'Install Windows Software', 'Configuration'
and possibly 'Run a Windows Command').
Then run the following command:

/opt/cxoffice/bin/cxmenu --crossover --removeall --install

Note that this mean root will not see these menu entries either. But you can
still run CrossOver Setup from the command line:
/opt/cxoffice/bin/cxsetup

Also note that your users too will still be able to run CrossOver commands from
the command line and thus bypass the missing menu entries. You could remove
execute permissions on /opt/cxoffice/bin/cxsetup and /opt/cxoffice/bin/cxbottle
for non-root users, but even that would only make things a bit harder (they can
always get CrossOver themselves and install it in their account).

[/HTML]

Just to reiterate , it's really simple.

---

### Post by SunnyRabbiera on 2007-10-19
that didnt work, otherwise I would not be griping right now.

---

### Post by Wiebelhaus on 2007-10-19
> **SunnyRabbiera said:**
> that didnt work, otherwise I would not be griping right now.

buy it then or run it from term.

---

### Post by SunnyRabbiera on 2007-10-19
I DID BLOODY BUY IT!!!!!!!!!!!

ugh this is impossible it seems

---

### Post by SunnyRabbiera on 2007-10-19
Alright this is seriously wierd, my issue has now been resolved and I have no idea how...
crossover is now on my menu's! I have no idea how it got on there but now its there on all the accounts I have on my compy...
but yeh this is seriously weird as I have no Idea how it fixed itself like that.

---

### Post by zivley on 2007-10-23
Hi, I had the same problem and it's important to summarize, I did manage to understand what's the exact way to fix this bug.
I'm based on what has been already posted on this thread, but on a more short and focused way.
I'm also on Gutsy and I installed Crossover from a .deb package, already during installation I could get a hint of where the problem is coming from, I've got an error about a configuration file that said it needs to get a valid filename path to work correctly, we're talking about the already mentioned file **/opt/cxoffice/lib/perl/CXMenuXDG.pm**
So, the first step will be editing that file (the error was in my case on line No. 254)
```
sudo gedit /opt/cxoffice/lib/perl/CXMenuXDG.pm
```
Then go to about line 254 (it may differ) and change
```
my $dir=dirname($self->{filename});
```
to
```
my $dir=dirname($self->{menu});
```
Save and exit and then you need to run the following command (IMPORTANT! Do it under your user! NOT WITH sudo!!)
```
/opt/cxoffice/bin/cxmenu --crossover --install
```
(Slightly different from what was mentioned before)
In some cases, you may still not see the changes on the menus (this is a Gnome bug perhaps) and the easiest way to refresh is to right click on "Applications" then "Edit Menus" and then, just by entering there and getting out, you suddenly see the new added menus. Of course you can always log off an log back in, but that's too long...
This is how I've got it solved in my Gutsy!
Thanks to all for the leads to the solution.
Ziv

---

### Post by fenderek on 2007-10-24
Zivley , Thank you, that worked perfectly.

---

### Post by adamsu on 2007-10-25
Kudos to zivley for that beautiful fix.:lolflag:

---

### Post by dajhorn on 2007-10-25
This menu bug was ticketed by CodeWeavers and fixed in the CrossOver 6.2.0 release.

---

### Post by uconvert on 2007-11-03
Thank you - thank you - thank you!

zively - you're my hero

---

### Post by zivley on 2007-11-04
Hey, the thanks and kudos need to go to **grendelkhan** and **sx66gns**, they gave those fixes previously in this thread, (look back at the first page) all I did was summarize their ideas and putting them together in an ordered way to make it work. So, my kudos goes to them...
In any case, I'm happy it helped you.
Ziv

---

### Post by ripperzane on 2007-12-06
> **dajhorn said:**
> This menu bug was ticketed by CodeWeavers and fixed in the CrossOver 6.2.0 release.

Question: There is a 6.2.0 release? I have purchased it and yet see no update (upgrade or for purchase). Interesting...

---

### Post by ripperzane on 2007-12-06
Oh and the fix worked :)
Go ppl go for the fix, as to you have allowed to to breath a sigh of relief :) :guitar:
RZ

---

### Post by skrote on 2007-12-20
fixed me right up.
thanks for posting this.:guitar:

---

### Post by junkyjunk on 2008-03-19
Thank You !!!):P)

---

