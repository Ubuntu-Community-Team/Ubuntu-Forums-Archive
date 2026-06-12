---
title: "How can I stop downloads temporarily"
date: 2024-12-07
forum: General Help
---

### Post by raleigh3 on 2024-12-07
I want to be able to stop downloading temporarily. 

I realize the updates do require it.

Is that possible?

---

### Post by grahammechanical on 2024-12-07
We can use Software and Updates>Updates tab to change

Automatically check for updates from Daily to never
When there are security updates from Download and install automatically to Display immediately
When there are other Updates - this function seems to be Display and does not include download but it will include checking for updates - change From Immediately to Every two weeks.

Regards

---

### Post by TheFu on 2024-12-07
Downloads of what?
You can delay snap updates to a specific day of the week.
You can turn off all automatic APT updates.
You can pause most torrents.
If you are in the middle of copying stuff between two systems, use rsync and it will pick up where it left off. If you use any other standard Unix tool that I can think of, it will start over from the beginning.  Some, nonstandard tools are smarter, like yt-dlp. It will pick up where it left off.

So, it depends on what and how you are downloading stuff.  If you pull the network cable, there will be a network timeout, usually in 30-90 seconds.  If that is "temporary" by your needs, that's an option too.

---

### Post by raleigh3 on 2024-12-07
> **grahammechanical said:**
> We can use Software and Updates>Updates tab to change

Automatically check for updates from Daily to never
When there are security updates from Download and install automatically to Display immediately
When there are other Updates - this function seems to be Display and does not include download but it will include checking for updates - change From Immediately to Every two weeks.

Regards

I am not talking about updates.

---

### Post by ian-weisser on 2024-12-07
Why do you wish to delay?

If, for example, due to a metered connection, there's a setting for that.

---

### Post by TheFu on 2024-12-08
> **raleigh3 said:**
> I am not talking about updates.

You can bring the network interfaces down, if you like.  That will stop downloads, but all other traffic too and a restart won't be automatic, unless the individual processes restart on their own. Some might not pick up where they left off, but most of the larger file downloading tools will.

---

