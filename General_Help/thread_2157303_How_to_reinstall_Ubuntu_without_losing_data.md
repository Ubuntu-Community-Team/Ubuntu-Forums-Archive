---
title: "How to reinstall Ubuntu without losing data?"
date: 2013-06-24
forum: General Help
---

### Post by TimothyLinux on 2013-06-24
I am reinstalling Ubuntu and I want to do so without losing data. I turned on the installer and chose "Something Else". I chose the partition I installed Ubuntu on and tried to untick the "Format" box. It won't let me do that, so how do I do it?:confused: I can't risk this data, and I can't lose Ubuntu. Any help would be appreciated. Thx in advance!

---

### Post by snowpine on 2013-06-24
Back up your data to at least 2 external devices or network services, one of which is off site (for example, an external hard drive and dropbox). Then you will not risk losing your data. **Please stop installing Ubuntu** until you have made these backups, I cannot emphasize this enough!!!

Now that your backup is complete, here is some good advice on setting up a separate /home partition so you can keep your user data separate from the OS: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) (Note: this is not a substitute for proper backups! but it will make administration/reinstallation easier in the future.)

(edit: actually that tutorial looks a little out of date, anyone got a newer one?)

---

### Post by Irihapeti on 2013-06-24
You can't untick the "format" box on the main partition, because Ubuntu has to format it as part of the install process.

There is a way of getting it to leave the home (user) directory alone, but it's been too long since I used the install to be able to remember reliably. Someone else may be able to help you here.

However, I strongly recommend you to back up your data before you reinstall. No matter how good the instructions, and how careful you are, there is always the possibility of a catastrophic mistake.

There are lots of thread around the forum from people who this has happened to. It's heartbreaking, because there's often nothing much we can do for them. :(

---

### Post by BBQdave on 2013-06-24
> **snowpine said:**
> Back up your data to at least 2 external devices or network services...

Now that your backup is complete, here is some good advice on setting up a separate /home partition...

+1 Back up your data :D

You could do a separate home partition, but in my experience, backing up your data to different drives is a good way to go.

I back up weekly or more often, depending on the project I am working on, to an external hard drive. Monthly, I back up my data to a home server - an old eMac that I use as an FTP file server. And once a year I copy my data to DVD's - to archive that year's data.

It may sound like a lot of backing up, but it is easy to do - and I have not lost any data, going on a decade :)

---

### Post by Ranko Kohime on 2013-06-24
Pretty much what the 3 replies before me have said, but I'll add just a little more:

"Any data that you **CAN'T** afford to backup, you **CAN** afford to lose"

In other words, you should be making backups whether or not you're re-installing your OS.

---

