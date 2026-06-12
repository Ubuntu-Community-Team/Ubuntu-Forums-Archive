---
title: "strange large files with very long names appeared in /root/ What are they?"
date: 2014-06-18
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-06-18
I have a script I run pretty frequently that amoung other things looks for files over 145 miB in places where there shouldn't be any large files. Normally that would be something like an iso I downloaded and accidentally put in ~/.

But this time it found 2 strange large files with absurdly long names in /root/:

tmpI_ylNqnhHl3-JJ.fnlI0_lMwDHmQyeUKR9h9pCii7e2j_lj.pp2oE8kmDCi69RdU1KrNw8Q-DP9OA0hh-.utmpmpPsdyU0_quXNVqj.6gCD0m1XbSDd9bJQYyrV4sKA-DQ6i1B_XboxlBS2O3yGDk1NDrQRLTpmeLxbl4TRh9ip2bwcMda8YtJvF43QLOB5EzYiugrDCU6fjvBEIC6KGF-hRYx Hw57 m3_cZTq1WqE33q8f86QrEQTgTzl

which is 217 miB

and
tmptm8Wya4wxT4hV07P21sIguvshXjf2IyHeUHpwH4nHnyQzh.41xhufzs0fQL2fzSAsjZhijxB068YI8no5FcON_leqkvTCE7A9NXUni_69g.IHXEo6B4mjNjS0 dTIf0iYQbC75fz6EA3O6-uJr6XMNRH k6nC5dUo3u_0CTxReJW93rijIgPXBMsCI74Rmlu4uPrx4TnkMsyqo9RQ2aqW1lWcq4kr. 5f6O4mhBHceVFjlP.DJVIwpN_bFe

which is 155 miB.

I looked inside one with evim and it's the same sort gibberish that the filename is. Can anyone tell me what these are? The mod time on one was 2 days ago and they can't have been there much longer.

---

### Post by ajgreeny on 2014-06-18
When you say they are in /root do you mean in the folder which is root's home  in the filesystem, or just sitting in the top level of the OS?

Can you show the full pathway of these files, which I assume your script will tell you.

The name would tend to suggest they are temporary files, but unfortunately it does not tell us why they are where they are, instead of in /tmp.

PS:
Is you filesystem encrypted?  I will have to bow out of this discussion if so, as I know nothing about using encryption of the whole filesystem or /home folder.

---

### Post by Habitual on 2014-06-18
Have you, or do you use bleachbit?

---

### Post by Dreamer Fithp Apprentice on 2014-06-19
Thanks for responding, AJGreeny.
> **ajgreeny said:**
> When you say they are in /root do you mean in the folder which is root's home  in the filesystem, or just sitting in the top level of the OS?
The former. The potential for confusion is why I explicitly put the leading and trailing /s, like a path.  Heck of a nomencatural gotcha though, isn't it -- to have a a directory named "/" we call "the root directory" and another actually named "root" we tend to call "root's home"? Sounds like something Lewis Carol would have dreamed up. I've often wondered if we inherited this madness from AT&T Unix or if it was homegrown.> **ajgreeny said:**
> Can you show the full pathway of these files . . .Sure.```
root@ubuntu:~# ls /root/tmp*
/root/tmpI_ylNqnhHl3-JJ.fnlI0_lMwDHmQyeUKR9h9pCii7e2j_lj.pp2oE8kmDCi69RdU1KrNw8Q-DP9OA0hh-.utmpmpPsdyU0_quXNVqj.6gCD0m1XbSDd9bJQYyrV4sKA-DQ6i1B_XboxlBS2O3yGDk1NDrQRLTpmeLxbl4TRh9ip2bwcMda8YtJvF43QLOB5EzYiugrDCU6fjvBEIC6KGF-hRYx  Hw57 m3_cZTq1WqE33q8f86QrEQTgTzl
/root/tmptm8Wya4wxT4hV07P21sIguvshXjf2IyHeUHpwH4nHnyQzh.41xhufzs0fQL2fzSAsjZhijxB068YI8no5FcON_leqkvTCE7A9NXUni_69g.IHXEo6B4mjNjS0  dTIf0iYQbC75fz6EA3O6-uJr6XMNRH  k6nC5dUo3u_0CTxReJW93rijIgPXBMsCI74Rmlu4uPrx4TnkMsyqo9RQ2aqW1lWcq4kr.  5f6O4mhBHceVFjlP.DJVIwpN_bFe
root@ubuntu:~#
```> **ajgreeny said:**
> Is you filesystem encrypted?No. Interesting subject and I'll try it as soon as I get around to it but for now I already have enough to confuse me, so my OSs are all en claire, just my brain is en muddy.

Thanks, Habitual.
> **Habitual said:**
> Have you, or do you use bleachbit?Aha! Yes and yes, respectively. I run it on an OS before I back it up to cut the size of the archive some. And recently I decided out of curiosity and the irresistable urge to tinker to try checking 2 of the options I normally don't - overwrite freespace and memory. Surprisingly, it didn't seem to take much longer than usual. The memory option does have a "caution - experimental" (or some words to that effect) warning. Is your idea that these are files left over from wiping freespace that should have been deleted? That, perhaps because of the "experimental" memory option, it terminated abnormally and left them? Or that the reason it didn't seem to take any longer than usual was that it hadn't really finished?

---

### Post by Bucky Ball on 2014-06-19
Be VERY careful with Bleachbit. You can cause some serious damage.

I generally use:

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

---

### Post by Dreamer Fithp Apprentice on 2014-06-19
Thanks, Bucky Ball. Yes, those are useful commands, I use them. But if you use them in that order I believe autoclean will do nothing because clean will have already gotten everything that autoclean gets and more. I might be mistaken, but I believe it's redundant, like doing:```
sudo apt-get dist-upgrade
sudo apt-get upgrade
```What is your specific concern with Bleachbit? I've been using it regularly for years and this is the first time I've had any problem with it, assuming these are bleachbit files. Of course, as I mentioned, this is the first time I've tried those 2 options.

---

### Post by Bucky Ball on 2014-06-19
Sure. Use them the correct way. And incidentally, never use these:

```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... before using this:

```
sudo apt-get update
```

... but you probably know that ...

---

### Post by Dreamer Fithp Apprentice on 2014-06-21
SOLVED:
Habitual hit the nail on the head. I'm not speculating now. I've tested and confirmed this. These are files Bleachbit creates when the "Free Disk Space" option is checked. Normally it deletes them at the end of the run. I'm not sure why it didn't that time but there must be a dozen possible reasons. BleachBit is a resource hog and occasionally it will get really slow and the window goes blank as my wimpy graphics card screams for mercy. I doubt it is truly hung, probably just very, very slow, and slowing everything else up too.  So I might have siced xkill on it. Or some such. There must be six and ninety ways for a program to terminate abnormally on occasion.

Thanks, gentlesapients.

---

### Post by Habitual on 2014-06-21
> **Dreamer Fithp Apprentice said:**
> Is your idea that these are files left over from wiping freespace that should have been deleted? While I don't use bleachbit, your summary analysis sounds about right.

---

### Post by jal9904 on 2014-06-22
Those files have tmp in the beginning which means temporary so they might not be there forever.

---

