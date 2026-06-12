---
title: "Home directory of user root"
date: 2018-11-27
forum: General Help
---

### Post by Skaperen on 2018-11-27
traditionally user root has a home directory of [FONT=courier new]/root[/FONT].  on my system it ends up collecting large amounts of data that is better suited for the [FONT=courier new]/home[/FONT] directory.  so my current thought is to change root's home directory to be [FONT=courier new]/home/root[/FONT] while also leaving [FONT=courier new]/root[/FONT] in existence for anything still expect (or hard coded) to use that.  what i would like to ask is if there are any known pitfalls or issues in having things this way.

---

### Post by CatKiller on 2018-11-27
More importantly, why is your root account accumulating personal files? The root account shouldn't run, essentially, anything.

---

### Post by QIII on 2018-11-27
I'd not fiddle around with /home/root.

More than just "traditional", /root as root's home is an established convention of the HFS.

It would be helpful to know what sorts of files you are talking about in /root.

---

### Post by QIII on 2018-11-27
Also, are you doing work while actually logged in as root?

---

### Post by Skaperen on 2018-11-27
log files are the biggest accumulation.  i have it set up so that everything done as root is logged.  i try to keep them for at least 2 years.  right now i have them back as far as 4 years.

many things i do involve constructing chroot images (or for unshared containers).  being _[FONT=courier new]sudo -i[/FONT]_'d in for a while makes the various steps a lot easier.  that's the only way i "login" as root (i use "sudo -i").  root itself has no usable password)  diagnosing various issues is another bunch of things i do.  these are my computers so i can choose my means.  i know, or find out, the risks.  just because i didn't include asking about something in my post, don't assume i don't know of its relevance.  i've been working on Unix since 1983 and Linux since 1994.  my question in this thread is asking about experiences with any specific things that can be problems, such as some program that stores data in the looked up root home directory then accesses it at the hard coded path that begins with [FONT=courier new]/root[/FONT].  i regularly uses non-root users for everything that does not need root to do, and that includes rsync-ing files that need privileged metadata to AWS EC2 instances without setting a login password or SSH key for root.

---

### Post by Skaperen on 2018-11-27
i'm looking for a technical reason not to do this, not a humanitarian reason.  i could leave it unchanged, but that would result in a lot more work after i move the files away.  it's already enough work to minimize the exposure.  so i'll need to understand good justification to accept the extra work.

---

### Post by lisati on 2018-11-27
I'd recommend against being in the habit of logging in as root, because greater care is needed than for a "regular" user in order to prevent unintentional damage to your system.

---

### Post by Skaperen on 2018-11-28
> **lisati said:**
> I'd recommend against being in the habit of logging in as root, because greater care is needed than for a "regular" user in order to prevent unintentional damage to your system.

but, do you have a specific reason *not* to change the root user home directory from [FONT=courier new]/roo[/FONT]t to [FONT=courier new]/home/root[/FONT]?

---

### Post by QIII on 2018-11-28
Yes:  root's home is /root, its established place in the HFS and the place where the whole ecosystem expects it to be.  If you create /home/root, it'll be ignored.  If you decide to start putting things there, it'll be a dead-letter file.  The rest of the system won't see it.  

The problem is not that.  You are barking up the wrong tree.  The problem is that you are generating too much superfluous logging that you cannot possibly examine and you are letting it pile up over a long time.  Why are you convinced that holding on to those logs for years is of any value?  What are you using them for?

---

### Post by CatKiller on 2018-11-28
If your install is all on one partition, changing the location of root's home directory is breakage with no benefit.

If you have /home as a separate partition you could symlink /root to a location in the /home partition.

---

### Post by spjackson on 2018-11-28
I would be reluctant to change root's home directory from the conventional /root. Would it break anything? I'm not sure.

I don't know whether this applies any more, but once upon a time, when booting in single user mode for maintenance/recovery purposes /home/root would not have been available until /home was manually mounted. Would this prevent single user mode login? Don't know. Is it still relevant when the root account is only accessible via sudo? Don't know.

If I was trying to do a similar thing, I'd would keep root's home as /root and write whatever big stuff needs writing to /home/root or /home/roots-big-stuff or whatever.

Symlinking /root to /home/root would have the same potential problem: not available when /home is not mounted. But I can't think of a reason why subfolders can't be symlinked e.g. /root/logs to /home/root/logs.

---

### Post by Skaperen on 2018-11-28
yes, there is too much logging. i have thought about not doing that. but i have needed to go look up some things a few times.  if i had never needed it i might really consider stopping it now.

what if i bind mount /home/root over /root?  then /etc/passwd remains unchanged.  i never use single-user mode.  i have never seen anything in /root that is needed to boot or init so a mostly empty /root should be OK.  whatever a fresh install puts in there should be enough to bring the system to when the bind mount happens.  if i need extreme maintenance i boot one of many backup systems that have a full suite of tools and capabilities.

---

### Post by Skaperen on 2018-11-28
> **CatKiller said:**
> If your install is all on one partition, changing the location of root's home directory is breakage with no benefit.

If you have /home as a separate partition you could symlink /root to a location in the /home partition.

you refer to "breakage" yet no one has said what breaks.

i've experienced issues with symlinks.  i think bind mount would be better.

---

### Post by QIII on 2018-11-28
You have been given advice by those of us who have been doing this a long time.  Personally, I have been at this since the 1970s.

You seem reluctant to harken to the voice of experience.  

You may do as you wish, but this thread has become an ouroboros.

---

### Post by lisati on 2018-11-28
> **Skaperen said:**
> you refer to "breakage" yet no one has said what breaks.

The short answer is that there is a very real risk that your computer won't work as expected, or at all. /root is an integral part of any *nix-like system, and even a simple typo when making changes can make a huge difference to the usability of your system.

On a side note, this community is made up of volunteers with a wide range of experience. Many of us have been using computers of one form or another for 30 years or longer. No doubt there are many tales of breakages and misadventure that could be related here, but would likely sidetrack us from addressing your initial question.

If it turns out that it's your system logs that are causing a problem, there are options available that can help keep their size more manageable. I'm sure that someone will be able to offer suggestions if asked nicely.

---

### Post by Skaperen on 2018-12-05
yes, sda1=/ and sda4=/home.  but i still do not understand what breaks.

---

### Post by Skaperen on 2018-12-05
it's not system logs, but program output logs.  many programs are run under a command called logcmd that runs itself and then the command, under the script command.  things that get logged include my backups going to AWS S3.  i then have script that scan these logs for patterns of problems.  it's not AI, but it is doing a lot of analysis.

---

### Post by lisati on 2018-12-05
There's a whole bunch of things that can go wrong. For example, if, in your tinkering, you set file permissions incorrectly, some programs will be unable to run. Another thing that can go wrong when logged in as root is if you are in a different directory/folder to where you think you are, a misplaced move or delete will make life difficult. These are two of several possibilities.

I repeat QIII's question from earlier in this thread, are you actually doing work while logged in as root?

---

### Post by HermanAB on 2018-12-05
Hmm, some things to think of: symlinks, hardlinks, /etc/logrotate.conf

---

### Post by Skaperen on 2018-12-05
> are you actually doing work while logged in as root?

i am never logged in as root.  root has a long random generated password string to avoid any assumption that lack of password means free to become root.  i never see that password.  _i use sudo_.  but not everything runs well under sudo such as my backup script (sometimes authority is not inherited) and my background system (sessions get mixed and/or lost).  in cases like these i do [FONT=courier new]sudo -i[/FONT] and type the commands in there.

so the issue is more about what path is in [FONT=courier new]/etc/passwd[/FONT] than it is about where you end up after doing [FONT=courier new]cd ~root[/FONT]?

---

