---
title: "Is it wrong to &quot;sudo flock&quot; so I can use the update feature?"
date: 2006-10-26
forum: General Help
---

### Post by dpaint4 on 2006-10-26
I recently discovered that if I run Flock as root I can use the "Check for Updates" feature that is usually disabled. I don't want run Flock as root any other time, but I really like being able to do this one thing since it isn't in the repositories, and since it probably never will be.

I hate the pain of installing it, setting it to default, and then removing it by hand, and reinstalling every single time there's an update.

Am I doing something bad in this process? Is there a reason I shouldn't?

I know if you try to do this to Firefox, you get a warning in the command line not to run Firefox as root, and I know Flock is based on Firefox, so this is the basis of my question.

Thanks for your replies.

---

### Post by ThrobbingBrain66 on 2006-10-26
Lots of people install the mozilla version of Firefox to replace ubuntu's packaged version.  Some say it feels faster, others aren't so sure.  In any case, those people have to run Firefox as root to update it.  All other times they run it normally.  So to answer your question, what you are doing is perfectly fine...so long as you don't run Flock as root ALL the time.

---

### Post by AirRaven on 2006-10-26
If you absolutely *must* run it as root, it's a good idea not to use the [FONT="Courier New"]sudo[/FONT] command- it's not intended for graphical applications. Tends to mess stuff up.

If you want to run it as root, use the [FONT="Courier New"]gksu[/FONT] or [FONT="Courier New"]gksudo[/FONT] commands in GNOME, or [FONT="Courier New"]kdesu[/FONT] in KDE.

There shouldn't be any real problem with running it as root otherwise. Just run as root to get updates and run as normal the rest of the time.

---

