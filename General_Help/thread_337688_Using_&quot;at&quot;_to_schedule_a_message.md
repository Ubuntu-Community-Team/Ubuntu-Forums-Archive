---
title: "Using &quot;at&quot; to schedule a message"
date: 2007-01-13
forum: General Help
---

### Post by cookfromfrozen on 2007-01-13
Hi

I'm trying to use the "at" command to schedule a message to pop up at a certain time later in the day.

I am currently doing this:

```

tim@desktop:~$ at 1701
warning: commands will be executed using /bin/sh
at> zenity --info --text "put the dog out"
at> <EOT>
job 1 at Sat Jan 13 17:01:00 2007

```

The time comes and goes and no message pops up.  Typing "at -l" shows nothing, so I assume the job was run.

Where am I going wrong?

---

### Post by dcstar on 2007-01-13
> **cookfromfrozen said:**
> Hi

I'm trying to use the "at" command to schedule a message to pop up at a certain time later in the day.

I am currently doing this:

```

tim@desktop:~$ at 1701
warning: commands will be executed using /bin/sh
at> zenity --info --text "put the dog out"
at> <EOT>
job 1 at Sat Jan 13 17:01:00 2007

```

The time comes and goes and no message pops up.  Typing "at -l" shows nothing, so I assume the job was run.

Where am I going wrong?

Do a forum search for specifying the X server screen when using cron jobs, you should find something useful......

---

### Post by cookfromfrozen on 2007-01-14
Got it thanks, it somehow slipped my mind that cronjobs ran silently in the background :)

This is how you specify which display if anyone comes across this:

```

at> DISPLAY=:0 zenity --info --text "put the dog out"

```

---

