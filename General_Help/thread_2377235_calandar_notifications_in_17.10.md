---
title: "calandar notifications in 17.10"
date: 2017-11-10
forum: General Help
---

### Post by bob brazie on 2017-11-10
I am using Thunderbird for my e-mail and calendar. I have the calendar set to sink with Google calendar too.
When clicking on the date at the top the calendar opens and it is not showing any notifications.
Is there a setting I am missing somewhere or maybe this is not working in 17.10 yet?
I did Google this but couldn't find any answers to the way I was posing the question.
Thanks in advance. Bob.

---

### Post by walts48 on 2017-11-10
When clicking on the Date at the top of Thunderbird or the one that shows in Ubuntu where the sound icon, mail envelope and other items reside?

Do you see the Today Pane in the Thunderbird Mail window, the Calendar tab next to the Mail tab?

I'm pretty sure you need Thunderbird running to get notifications.

---

### Post by bob brazie on 2017-11-10
Yes the today pane is showing and Thunderbird is running.
There is no "mail" icon in 17.10. It is now the date at the top center when clicked it opens to show a calendar and notifications. Though mine shows no notifications.

---

### Post by walts48 on 2017-11-11
> **bob brazie said:**
> Yes the today pane is showing and Thunderbird is running.
There is no "mail" icon in 17.10. It is now the date at the top center when clicked it opens to show a calendar and notifications. Though mine shows no notifications.

That date at the top center isn't associated with Thunderbird AFAIK, and adding an event to that calendar doesn't provide any notification options that I can see. I am using Ubuntu 16.04 LTS.

Maybe when I have time I'll run my 17.10 Live CD and test.

---

### Post by bob brazie on 2017-11-11
A screen shot of what I am talking about.
Thanks. Bob

---

### Post by ajgreeny on 2017-11-11
That calendar is not linked to thunderbird as far as I'm aware, and I do not know if it can be made to link.

For the calendar in Tbird you need the lightning add-on, and I recommend that you install that from the repos by installing xul-ext-lightning package, not from the thunderbird add-ons site as the two can get versions out of sync with each other.

---

### Post by bob brazie on 2017-11-11
I do have the lightening add-on installed. Have for years.
I didn't know about not installing from the add-on site though.
Would that be a command in terminal? If so what would the full command be?
Do you know the current version of the one in the repos?
So, Thunderbird and Lightening are not made to link to the new notification area in 17.10?

---

### Post by ajgreeny on 2017-11-11
Yes, the usual ```
sudo apt install xul-ext-lightning
``` should do it.
You may need to remove the T'Bird lightning extension first if you have it installed that way direct from T'Bird add-ons.

The current repository version in 17.10 is **52.4.0+build1-0ubuntu2**, exactly the same as the T'Bird version.

---

### Post by bob brazie on 2017-11-11
Thank you.
Still wondering if there is a way to make it work with the gnome notifications.

---

