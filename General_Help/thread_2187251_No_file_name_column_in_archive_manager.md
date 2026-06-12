---
title: "No file name column in archive manager"
date: 2013-11-11
forum: General Help
---

### Post by MDGM on 2013-11-11
Hi all,

I have a strange problem where there is no file name column when opening an archive with the default ubuntu "Archive Manager" program - see below screenshot:

[IMG]http://i145.photobucket.com/albums/r205/maxmumford/archive-manager-no-filenames_zpsddf6e0d5.png[/IMG]

I have checked all menu options I can find and can't find any options for bringing it back. I'm sure the solution is stupidly simple but I can't seem to find it. Any help?

---

### Post by pacmyc1 on 2013-12-17
> **MDGM said:**
> Hi all,

I have a strange problem where there is no file name column when opening an archive with the default ubuntu "Archive Manager" program - see below screenshot:

[IMG]http://i145.photobucket.com/albums/r205/maxmumford/archive-manager-no-filenames_zpsddf6e0d5.png[/IMG]

I have checked all menu options I can find and can't find any options for bringing it back. I'm sure the solution is stupidly simple but I can't seem to find it. Any help?

Hi there.
I got the same problem!
When googeling it seems like we are the only ones stupid enough not being able to see the filenames in archive manager..
I also tried uninstalling / reinstalling but without result.

---

### Post by pacmyc1 on 2013-12-17
> **MDGM said:**
> Hi all,

I have a strange problem where there is no file name column when opening an archive with the default ubuntu "Archive Manager" program - see below screenshot:

[IMG]http://i145.photobucket.com/albums/r205/maxmumford/archive-manager-no-filenames_zpsddf6e0d5.png[/IMG]

I have checked all menu options I can find and can't find any options for bringing it back. I'm sure the solution is stupidly simple but I can't seem to find it. Any help?


[COLOR=#000000]Hi there.[/COLOR]
[COLOR=#000000]I got the same problem![/COLOR]
[COLOR=#000000]When googeling it seems like we are the only ones stupid enough not being able to see the filenames in archive manager..[/COLOR]
[COLOR=#000000]I also tried uninstalling / reinstalling but without result.[/COLOR]

---

### Post by MDGM on 2013-12-20
Glad to find somebody else who has the same problem! I was beginning to think I'd be the only one stuck like this forever! Like you said, no luck on google, so ANYBODY with the slightest idea, you got 2 desperate people here :P

---

### Post by steeldriver on 2013-12-20
Just had a bit of a play with this one, I can reproduce this symptom by setting the name-column-width to a small non-zero value (e.g. 1) - if that's the issue, you should be able to reset it with

```

gsettings reset org.gnome.FileRoller.Listing name-column-width

```

---

### Post by pacmyc1 on 2013-12-20
> **steeldriver said:**
> Just had a bit of a play with this one, I can reproduce this symptom by setting the name-column-width to a small non-zero value (e.g. 1) - if that's the issue, you should be able to reset it with

```

gsettings reset org.gnome.FileRoller.Listing name-column-width

```


Well, that's beatiful, comfirmed solved :)

As a linux newbie I wonder how you found out that solution..

---

### Post by MDGM on 2014-01-07
Fixed for me too, thanks man!! It was beginning to be very very annoying :)

---

### Post by ShellfishGene on 2014-08-24
Archive Manager allows you to resize the Name column to a minimum width of 1 pixel, effectively hiding it. Double-clicking the separator between the Name and Size headers has the same effect. This may be how you ‘lost’ the Name column.

The GUI actually allows you to recover and show the Name column again. Just drag the left border of the Size column header to the right. In fact, all the columns behave this same way.

This way of hiding and showing columns is counter-intuitive to some people (myself included). It’s an unfortunate consequence of Archive Manager’s otherwise excellent, minimalistic design.

---

### Post by Yasser_Abdalkareem on 2015-01-04
> **MDGM said:**
> Hi all,

I have a strange problem where there is no file name column when opening an archive with the default ubuntu "Archive Manager" program - see below screenshot:

[IMG]http://i145.photobucket.com/albums/r205/maxmumford/archive-manager-no-filenames_zpsddf6e0d5.png[/IMG]

I have checked all menu options I can find and can't find any options for bringing it back. I'm sure the solution is stupidly simple but I can't seem to find it. Any help?


[SIZE=4][B]Try to just re-size column width by mouse over column header split and move with press mouse it will be appear again .

[/B][/SIZE]

---

