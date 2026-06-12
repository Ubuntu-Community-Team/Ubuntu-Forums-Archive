---
title: "[SOLVED] 8.04   Empty the trash"
date: 2008-06-06
forum: General Help
---

### Post by thelugnut on 2008-06-06
When I click on "Empty Trash", it means I want to empty the trash. It does not mean I want a questioning dialog box to pop up and ask me if I want to empty the trash.

Is there a way around this?:confused:

---

### Post by bmac on 2008-06-06
Open your file browser (Nautilus, I hope) 
Select:
edit/preferences/behavior Tab
At the bottom of this tab under trash uncheck the "ask before emptying the Trash or deleting files..

Hope this helps....

---

### Post by thelugnut on 2008-06-06
Hi bmac,
I appreciate your response, but ...

I am afraid it didn't work. I selected and de-selected the appropriate boxes, but nothing changed. I still do not have a "delete" function, and I am still questioned as to rather I want to delete the file or not.

I performed the above actions a few times, and even restarted the system , but to no avail.

Arrrrghhh!  :confused:

---

### Post by Gallardo Spyder on 2008-06-06
If you go into configuration editor (I think it is part of the standard install - if not download it via synaptic) it is called gconfig-editor (officially).

Open it and do a find on trash (select search in keys and groups).

or you can go directly to /apps/nautilus/preferences/confirm_trash

This will make it "stick" when you uncheck the confirm delete box.

I just did it to make sure in 8.04.

Rich

---

### Post by bmac on 2008-06-06
[Gallardo Spyder]("http://ubuntuforums.org/member.php?u=245461") may be correct open your configuration editor.
Select apps/nautilus/preferences
Uncheck "confirm trash"
I did this and it eliminated the popup and continued to do so after reboot..

Hope this helps....

---

### Post by thelugnut on 2008-06-07
Gallardo Spyder wrote:
> if not download it via synaptic) it is called gconfig-editor

Well, I couldn't find it. Searching Synaptic yielded no results.

----------------------------------------------------------------------------
bmac wrote:
> open your configuration editor

Simpy put, I don't know how to do this.
-----------------------------------------------------------------------------
I appreciate the replies.:confused:

---

### Post by Gallienus on 2008-06-07
> **thelugnut said:**
> Gallardo Spyder wrote:


Well, I couldn't find it. Searching Synaptic yielded no results.

----------------------------------------------------------------------------
bmac wrote:


Simpy put, I don't know how to do this.
-----------------------------------------------------------------------------
I appreciate the replies.:confused:

Actually, it's 'gconf-editor' that you need to type. I'm always forgetting that too. :)

---

### Post by thelugnut on 2008-06-07
All Right! Gallienus,

> Actually, it's 'gconf-editor' that you need to type

That did it.

Again many thanks for the replies. I do appreciate them very much.
:guitar:

---

