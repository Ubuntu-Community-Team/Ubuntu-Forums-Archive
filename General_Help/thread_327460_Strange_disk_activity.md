---
title: "Strange disk activity"
date: 2006-12-29
forum: General Help
---

### Post by schucki.be on 2006-12-29
Hello out there,
I switched to Edgy and am happy with that.
Except one thing....
Since a few days I see strange hard disk activity.
If that happens, my laptop become totally occupied. It is not frozen completely.
Just the reason I switched from that crap OS, XP, to Linux :twisted: 

Now I am looking for the cause of this semi-freezing.

Where can I start? I looked in the standard logs, but could not find anything...

Please advise!

Thnx,
Schucki.be

---

### Post by SuperMike on 2006-12-29
What output do you get from 'top' command if you sort on CPU utilization?

You can also do:

sudo apt-get install jnettop

...and see if it can show you any net activity with your PC even when you shut down your browser and aren't doing anything on the Internet. It might yield some clues.

And you looked in the event log with:

sudo tac /var/log/messages | more

...and don't see anything repeatedly being written into it?

---

### Post by schucki.be on 2007-01-02
Thank you Supermike.
Already tried it for the past days.
Is there a way to log the output from both commands?

Now I have to look at my laptop all night :-? .

I have not seen the peeks for 2 days now.

Thnx,
JSK

---

