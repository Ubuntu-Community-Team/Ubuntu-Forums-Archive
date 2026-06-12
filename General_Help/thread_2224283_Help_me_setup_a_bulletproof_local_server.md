---
title: "Help me setup a bulletproof local server"
date: 2014-05-15
forum: General Help
---

### Post by yoshimitsuspeed on 2014-05-15
I need to set up a local server for my business. It will have one primary purpose. I will be buying a high end CAD program with a floating licence. This means any computer on the network will need to be able to access the license and I will need to be able to VPN in to access it remotely. 
The big issue is that their annual support is like $1000/year which I will try to avoid. This means that if the server crashes and say I needed to set up another computer to host it I would be SOL and looking at huge fees to get their help so I want to do everything I can to make sure this doesn't happen. I am hoping to use an old Dell tower that I have and wanted to set it up in RAID so that all data was backed up on multiple drives. 

I have been using Linux for over a decade so I am pretty comfortable from a personal user perspective but I don't have a lot of experience with networking, RAID or servers. I did setup a couple basic localhosts back in the day when I was doing basic web design but it's best to figure I don't know much at all lol. 

I would prefer a server with a GUI to make things easier. It seems to me this should be a decent way to go for a local server. The question then becomes, should I install something like Ubuntu Server? Or should I just install something I am familiar with like Kubuntu LTS and install the rest of LAMP and whatever else I might need? 

Will I need to setup a backup style RAID through the bios or can I just set that up in Ubuntu while formatting and creating my drives? 
I have 2 500 GB hard drives easily available. Is that enough to set up a pretty safe RAID setup or should I try to go with more? Can/should I use three or is it best to keep even numbers? 

Is this something an old inspiron 570 will be well enough suited for? If for some reason the whole computer dies will it be easy enough to move the HDs to another computer and keep on going? 

Anything else I should look out for?

---

### Post by HermanAB on 2014-05-15
Linux is Linux is Linux...

I.e. it doesn't matter how you do it.

The important things are:
1. Install a UPS.  It will extend the life of the server, by protecting it against power surges and dips.
2. Use software RAID (mirror).
3. Make a regular backups (RAID is NOT a backup, since any screw-up is instantly propagated).
4. Use loooooooooong (12 characters or more) passwords.

That's about it.

If you are more concerned about security, then do set up App Armor (could be difficult), or use Red Hat Linux, since it has mandatory access control by default.

---

### Post by HiImTye on 2014-05-15
you'll likely find that either btrfs or zfs are safer than doing a software raid, as they are both copy on write and have snapshot features. you should absolutely still do regular backups on top of this.
you need to consider what the use case is for the server, and then set it up accordingly. for instance, is it going to serve web pages? is it going to hold employee information that you don't want to be internet accessible? before beginning you should have these questions, and answer them, and then you can begin to figure out what will be the best fit.

---

### Post by yoshimitsuspeed on 2014-05-16
The only vital role of this server will be to host the floating license for my CAD program. 
I need to get more info on this end I guess. The issue is that there is very strict rules and safeguards keeping you from installing it on multiple computers. This makes me think that if this server died and I couldn't salvage the OS in a functional unit then I would have to get them to help me install it on another computer. 
Here is the main issue. 
Option a. is to pay $1000 per year for their "support". In this case if something happened I just call them up and they help me fix it, install it on another computer or whatever I need. 
Option b. is save $1000 per year and make dang sure that I don't need their help. Now I think it's pretty messed up that after dropping $4k on software you need to pay that much for support but it's how they all operate so those are my options. 
So I need to learn more about this but moral of the story is I don't think backups will help me but maybe I'm wrong. Whatever the case I would like to avoid spending that $1k/y and would like to make a server that would minimize the chances of needing their help in any sort of way.

---

