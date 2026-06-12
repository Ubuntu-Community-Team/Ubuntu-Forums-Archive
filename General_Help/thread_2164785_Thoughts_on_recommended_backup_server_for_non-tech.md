---
title: "Thoughts on recommended backup server for non-techie friends?"
date: 2013-08-01
forum: General Help
---

### Post by Roasted on 2013-08-01
Hello! I'm on the fence between 3 different ideas and I am curious what other users may think. Long story short, two (married) friends of mine have had some bad luck with their computers lately. Between a 2 year old causing the premature death of one laptop and a brand new one dying within 3 weeks, they're interested in a backup solution. I offered to set up one of my spare boxes at their place as a backup server. This will literally be a Samba box. Nothing more.

1st idea - Ubuntu Server 12.04. Install Samba, configure shares, and be done with it.
Pros - Simple. Not a lot to go wrong. Simple instance. 5 year support.
Cons - If the system needs attention, a CLI interface is a scary place for non-techie users. That said, I've never had the need to maintain my parent's backup server, which is Ubuntu Server 12.04, CLI only.

2nd idea - Regular install of Ubuntu. 
Pros - GUI in case I need to walk them through how to get in and do things. That can be a bonus, but I can't see the need of a GUI that much since if anything goes wrong, they'd call, and I could probably walk them through forwarding port 22 through their router to let me SSH since I can likely SSH in quite a bit quicker than having them check various things in the GUI.

3rd idea - FreeNAS. 
Pros - Web UI. More functionality in the standard install.
Neutral - The added functionality that FreeNAS web UI would provide is somewhat meaningless (I doubt they even know what torrents are), since the one and only goal is to have files backed up.
Cons - Relatively unfamiliar to me. That SSH thing keeps coming to mind as the gleaming way for me to remote in if need be... 

I'm leaning heavily towards option 1, but I want to think this through in as much as possible. This system won't have RAID - just a single drive that provides them with Samba shares. Their systems (Windows) would have some sort of software on it (still trying to figure out which... I'd welcome suggestions) that would control the syncing capabilities. 

Thoughts?

---

### Post by newbie-user on 2013-08-01
I'd just stick to samba. You wouldn't want your non-techie friends getting into a gui and messing up all the settings. For the most part, the file server can just sit doing its thing without any administration. I would recommend having at least a software raid 1 to guard against hard drive failure, especially if you're using consumer drives.

---

### Post by Roasted on 2013-08-01
> **newbie-user said:**
> I'd just stick to samba. You wouldn't want your non-techie friends getting into a gui and messing up all the settings. For the most part, the file server can just sit doing its thing without any administration. I would recommend having at least a software raid 1 to guard against hard drive failure, especially if you're using consumer drives.

I was thinking about that... but to get started, I'm not thinking it'll be an option. This system is basically a gift from me, so whatever drives I have available are what I have available. I don't think I have anything bigger than a 250, so we'll use that to get the box running. I'm going to advise they invest money in some bigger drives, something like 1-2TB WD Reds, then I'd be happy to set up a RAID for them. If nothing else, the fact that their data will be stored on a separate system, even if it's a single drive, is still better than nothing. 

I do like the idea of setting up a RAID, likely with mdadm (love that, never had an issue with it). Then I could rig it up to email me if a drive fails. That way that's one less thing for them to worry about.

It pays having a tech nerd as a close friend, eh? :P

But anyway, yeah I'm leaning more towards option 1. It's simple, robust, longer term, etc. I just wanted to make sure I wasn't missing a key point that would advocate option 2 or 3 more heavily than what I was seeing.

---

