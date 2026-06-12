---
title: "Menus &quot;behind&quot; windows?"
date: 2008-01-26
forum: General Help
---

### Post by SomeGuyDude on 2008-01-26
I'm not sure how to describe this, but hey.

I installed Banshee recently, and then installed some of the libmtp-dev packages (that's all I changed), and since then every so often when I click on the menu buttons on any window, they don't show up. They seem to be "behind" the window itself, so while "History" or "Tools" is highlighted like I clicked on it, there's no menu below it.

After a while, the problem seems to "fix" itself and they come back to the front, but I can't figure out what's doing it. Any ideas? Something else I need to explain?

---

### Post by DjBones on 2008-01-26
I had a problem similar to this that something to do with compiz,
(think it had something to do with it loading before some other things, and it would draw menus and such behind the windows like your saying)
i got around this by doing a
```
compiz --replace
```
in the run dialogue..
but i got a more permanent fix from adding 'sleep 10 &&' before the run command for compiz in the session manager.
hope that helps!

---

### Post by SomeGuyDude on 2008-01-26
Didn't change anything, sadly. I've had Compiz for forever, but this only started happening today and it's driving me bonkers. Tomorrow I'll start kicking off processes and see if anything fixes it, I'm too tired tonight.

---

### Post by SomeGuyDude on 2008-01-26
Anyone else?

---

### Post by SomeGuyDude on 2008-01-27
It seems like it's a problem with Banshee's "show track on change" plugin. I uninstalled that and everything was gravy. Weird.

---

### Post by DjBones on 2008-01-27
great!  odd that a plugin for banshee would affect other windows though lol

---

### Post by SomeGuyDude on 2008-01-27
Yeah, I'm not sure how to describe it. I think something weird happens when the little notification window is drawn. That ends up behind everything else, and then all menus in all windows are stuck behind.

It only goes away when a given window "changes". Meaning it's stuck like that until I load a new page in Firefox, for example. Then it all goes back to normal... until the track changes and the notification pops behind everything again.

---

