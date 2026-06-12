---
title: "4 copies of same file corrupted"
date: 2015-08-01
forum: General Help
---

### Post by marc43 on 2015-08-01
(...not sure where to post this exactly, and it's already posted at Libreoffice forums with no response.)

Hi. I have a calc file filled with important information. Everyday, multiple copies are made to external drives via cron. I also have one that I uploaded to storage online about 2 weeks ago… so the online one is an archived version.

I have used the original of this file just today. About 4 hours ago. Now, on all four files, including the one I have online that I haven’t touched in a while, I get the following error:

Read-Error.An unknown error has occurred.

I have no idea what is going on. I’ve purged libreoffice, manually deleted all corresponding folders, and reinstalled. But this error keeps happening.Has anyone else had this trouble, and do you know what to do about it?

---

### Post by vidtek on 2015-08-01
> **marc43 said:**
> (...not sure where to post this exactly, and it's already posted at Libreoffice forums with no response.)

Hi. I have a calc file filled with important information. Everyday, multiple copies are made to external drives via cron. I also have one that I uploaded to storage online about 2 weeks ago… so the online one is an archived version.

I have used the original of this file just today. About 4 hours ago. Now, on all four files, including the one I have online that I haven’t touched in a while, I get the following error:

Read-Error.An unknown error has occurred.

I have no idea what is going on. I’ve purged libreoffice, manually deleted all corresponding folders, and reinstalled. But this error keeps happening.Has anyone else had this trouble, and do you know what to do about it?

Marc-

Nobody seems to be helping here so I'll put my bit in.
Try looking at the file with another system/programme.  If you have access to a windaz machine, check it out with Excel, or online via an internet cafe using google calc (or whatever the online google spreadsheet app. is called.)  I wouldn't persevere using your normal machine until you have successfully accessed your data.

Tony.

---

### Post by marc43 on 2015-08-01
Thanks Tony. I've got some advise on how to crack this thing and I'll try that. Unfortunately, Google docs doesn't open ODS files.

---

### Post by amanchesterman on 2015-08-01
When you purged LO and deleted 'all corresponding files', did you delete the **hidden** LO profile folder?
More info here: [https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)
Just a thought.

---

### Post by tgalati4 on 2015-08-01
I would check the SMART status of your hard drive.  Normally, when something like this happens, I suspect hardware first.  If your disk checks out, then look at your cronjob.  Did it make copies within the last 4 hours?  If so, then it perhaps propagated a bad file.  It happens.

Look through your *dmesg* for errors.  Open a terminal:

```
dmesg | more
```

Spacebar to page forward.  "q" to quit.

---

