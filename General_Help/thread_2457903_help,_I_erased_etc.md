---
title: "help, I erased /etc"
date: 2021-02-12
forum: General Help
---

### Post by vgraux on 2021-02-12
I did a mistake, I erased /etc.
So I lost /etc/passwd of course and I cant sudo cp /var/backups because sudo is refused ("who are you")

With the rescue mode I would probably be able to recover /etc/passwd but the problem is more important, as I deleted all files in /etc

Can I recover a working system without reinstalling ?

Any idea from you ?

---

### Post by HermanAB on 2021-02-12
It would be easier and much less work to reinstall.  Boot from install media and save your data.

---

### Post by ajgreeny on 2021-02-12
A lot of the files in /etc will be specific to your user and almost unrecoverable except by reinstalling. 

So unless you have a backup image of the OS itself from which you can restore /etc, not just your home , it makes total sense to bite the bullet and start again, as Herman says.

---

### Post by guiverc on 2021-02-12
I did some stupid things when I was starting.

One fix I used (*a number of times*) was to install on another box a *like* system, equivalent to the one I'd destroyed, then copy the files I'd removed from that *like* system, over to the system I'd stupidly corrupted.  The results were usually perfect, but it wasn't quick.

For desktop installs, that is more effort than it's worth (a desktop install is so easy to fix via re-install; as only system directories get erased & re-installed using an *unclean* install).

(*unclean* = *manual partitioning or something else, use existing partitions and do not format*)

---

### Post by QIII on 2021-02-12
Anyone who tries to say that they didn't make 100 similar mistakes while they were learning is a liar.  We've all done it.

I also recommend recovering your important files and re-installing.  It's just about impossible to piece /etc back together.

There are lots of odd bits and pieces in /etc.  It got that name in the old days because that is where everyone put things when they couldn't figure out where to fit them in the standard hierarchy.  "et cetera" --> "etc".  It's like the kitchen odds and ends drawer of the 'Nix world.

---

### Post by mIk3_08 on 2021-02-12
me too. When I first start in Ubuntu a lot of things that make me crazy here.so stupid enough to what was I'm doing in my O.S (Ubuntu Linux). Many bad Idea to explore more about I have. But in the long run, I have learn a lot specially joining here in the community and reading some forum conversations. its quite fun though.

---

