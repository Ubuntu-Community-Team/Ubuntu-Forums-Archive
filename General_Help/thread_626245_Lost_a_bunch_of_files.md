---
title: "Lost a bunch of files"
date: 2007-11-28
forum: General Help
---

### Post by BWF89 on 2007-11-28
I had a bunch of files of school projects and papers I've written throughout high school saved in my home folder. Yesterday they were all there. But today I go back and all of them are gone. The folders they were in are still there, but the actual files are missing. I password protect my computer and nobody really goes into my room anyway.

What could have happened to them? And is there any way I can get them back?

It's not a huge deal because I keep them backed up on my flash drive. But I'd really like to know.

---

### Post by BWF89 on 2007-11-28
Could it have anything to do with the unable to save bookmarks bug? I gave up on trying to fix it because every time I change my permissions to do some stuff outside of my home folder the bug comes back.

---

### Post by cwaldbieser on 2007-11-28
> **BWF89 said:**
> Could it have anything to do with the unable to save bookmarks bug? I gave up on trying to fix it because every time I change my permissions to do some stuff outside of my home folder the bug comes back.

Could you clarify this further?  

It is possible to change permissions on your home folder so you can't list the directory contents, but I am not sure if you accidently did that or if there is some other problem based on the limited information provided.

---

### Post by BWF89 on 2007-11-28
> **cwaldbieser said:**
> Could you clarify this further?
When I go to close Dolphin I get an error:

"Unable to save bookmarks; in <insert folder name> reported error was permission denied this error message will only be shown once the cause of this error must be fixed as quickly as possible which is most likely the hard drive"

I saw in another thread how to fix it by copy and pasting a line of text into the terminal. So I did that. But as soon as I use the kdesu dolphin command it changes my permissions and the error comes back.

I don't know whether this error is why it happened or not. I'm guessing it's not because it was only the contents of one folder and the subsequent folders inside it that got deleted. Nothing else in my home folder was touched. But I figured I'd mention it just in case it had something to do with it.

---

### Post by cwaldbieser on 2007-11-29
If you look at the permissions on the empty folder, how are they set?

---

### Post by BWF89 on 2007-11-29
> **cwaldbieser said:**
> If you look at the permissions on the empty folder, how are they set?
On the empty folders inside the folder the permissions are greyed out. But by going into "advanced permissions" you can set it to:
- owner and view and modify content
- group can view content
- others can view content

But even when you set it to this the missing files inside the folders don't re-appear.

---

### Post by BWF89 on 2007-12-02
bump

---

