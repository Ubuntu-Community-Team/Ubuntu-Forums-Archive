---
title: "Ubuntu affecting Windows partition?"
date: 2006-07-26
forum: General Help
---

### Post by Third Thoughts on 2006-07-26
This is going to be a somewhat vague email because it isn't happening on my computer, but on a friend's computer that I convinced her to dual boot on. She loves ubuntu, but has still been switching back and forth and she came across this strange error. Today when she booted up windows it came up to a Cream colored screen with a version number on the lower left side, saying "Please enter CD/DVD #1." She inserted the Microsoft XP Cd and it proceeded to re-install. It did a recovery install, so it didn't erase her files or overwrite the MBR. So nothing seriously bad has happened. However I'm worried it could be an ubuntu so I wanted to see if other's have had similar issues. 

Basically I partitioned her hard drive about a week ago using gparted and the live CD. We got things up and running and both the Ubuntu and Windows systems were working fine. A day later she, (on her own using the How-to on these forums) installed the 3g-ntfs read/write driver. In the week or so she's had that though, she hasn't actually used it (by which I mean she hasn't written to her windows partition), so I don't think that could be the problem. 

If anyone has had similar experiences, let me know. I'd like for my friend to like Linux, not see it as a source of problems.

~Andrew S.

~Andrew S.

---

### Post by kurniawands on 2006-07-26
haven't seen anything like that. think it might happen because of an unperfect partitioning/formatting or something. but i'm sure that the problem is on her hdd. see what happen if you re-format and re-install both OS.

ntfs-3g ? they were saying that ntfs-3g is still beta and not recommended to used on a production machine... is it = on some cases, it can screw your hdd ?? could be... but i haven't got any problem with it, till now at least (i hope never). :-D

---

### Post by Third Thoughts on 2006-07-26
> **kurniawands said:**
> haven't seen anything like that. think it might happen because of an unperfect partitioning/formatting or something. but i'm sure that the problem is on her hdd. see what happen if you re-format and re-install both OS.


Ehh.... I realllly don't want to do that. If this was my comp I might, but since its here it would me going to her place, or her coming to mine for a couple hours while we backed up, reformatted, and re-installed both OS's. Just too much of a hassle. Since things are working again I may just sit wait and see how things go.

> 
ntfs-3g ? they were saying that ntfs-3g is still beta and not recommended to used on a production machine... is it = on some cases, it can screw your hdd ?? could be... but i haven't got any problem with it, till now at least (i hope never). :-D

From what I had heard was that ntfs-3g was technically still beta, but that it had been put through its paces and was probably good for most users. I sent her links to the ntfs-3g How-to and the normal, ntfs read only How-to, explained the basic differences and let her choose which one to install. She's a fairly tech savy girl, so she didn't have any trouble getting things going. Plus since she didn't really use it, I'm reluctant to put the blame on it yet. So far my only really explanation is partitioning issues (though its odd it took so long to come up) or the windows catch all, viruses(though she has symantec anti-virus installed and up to date, and there's no virus threats last I checked). So in other words, I dont really have an explanation.

~Andrew S.

---

### Post by kurniawands on 2006-07-27
yup you're right.. ntfs-3g is still beta...hmmm if i said that...might be... since windows use cluster as it wants (unorganized, sometimes - that's what i think), you/she made partition on some windows used cluster... is it possible ??? or might be a bad hdd writing ??? hmm... think i have no more idea than that... by the way what kind of hdd she have ? since ppl said that matrox is not supposed to be your choice if you do format a lot (also bad on electric shock)... :confused:

---

### Post by Third Thoughts on 2006-07-29
> **kurniawands said:**
> yup you're right.. ntfs-3g is still beta...hmmm if i said that...might be... since windows use cluster as it wants (unorganized, sometimes - that's what i think), you/she made partition on some windows used cluster... is it possible ??? or might be a bad hdd writing ??? hmm... think i have no more idea than that... by the way what kind of hdd she have ? since ppl said that matrox is not supposed to be your choice if you do format a lot (also bad on electric shock)... :confused:

I'm not sure what kind of hard drive she has. I think the problem seems to have solved itself though, she says things are working now. Hopefully it won't happen again.

~Andrew S.

---

