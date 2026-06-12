---
title: "Setting up a headless server"
date: 2007-09-21
forum: General Help
---

### Post by Tyke91 on 2007-09-21
i've gotten ubuntu server edition and I'd like to install it as a headless server that i can acess from any computer i please. I'll also need to be able to upload files to it that i can then download onto any computer i need to.

i've never done this before, so can anyone point me to a tutorial or give me some starter tips?:)

---

### Post by tekati on 2007-09-21
> **Tyke91 said:**
> i've gotten ubuntu server edition and I'd like to install it as a headless server that i can acess from any computer i please. I'll also need to be able to upload files to it that i can then download onto any computer i need to.

i've never done this before, so can anyone point me to a tutorial or give me some starter tips?:)

Seeing as you have so many posts I find it hard to believe that I can be of any assistance to you.  But if I understand you correctly and thinking about if I needed to do something like this myself.  I would simply install the server then install openssh-server which would enable you to SSH in to the server for a shell and SFTP or SCP files to and from that headless server.  If I did not want to install a SFTP or SSH client on every machine I need to download files to then I would probably just install apache and a self signed certificate on to the same machine and maybe password protect the directory that I was going to serve files from.  Now thats all if it needed to be secure file transfers.  

This would enable you to have shell access and file transfers anytime from anywhere you can reach the server.

Again seeing all of your prior posts I must be missing something as I am sure it can not be that easy of an answer for you.  In which case I apologize for wasting your time.

---

### Post by Tyke91 on 2007-09-22
post count has nothing to do with experience in certain matters.

yes i have a number of posts, but those were mostly on topics of installing and configuring ubuntu for a desktop (and running ubuntu in general)... which i have gotten pretty good at doing :D


i'd never used a server before so i count myself a n00b in all respects there, so i appreciate your help :)

---

### Post by Tyke91 on 2007-09-22
strange problem...

the server cd wont boot... i've tried 2 different cds downloaded twice...

my xubuntu cd that i used to install ubuntu boots fine, but crashes out when i select the "start or install ubuntu" button. the server cd fails to boot entirely and isn't even recognized as a bootable cd.

I've tried both cds in my computer and they seem to work fine... at least the serrver one is recognized and boots. I have no clue as to the system specs of this computer, my dad just got it from his company after they fired a lazy tech worker.

---

