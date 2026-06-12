---
title: "Desktop locks"
date: 2021-11-19
forum: General Help
---

### Post by bitrat2 on 2021-11-19
Hi, 

I'm currently on Ubuntu 18.04.5 LTS with i7 and 16G

Certain apps (usually with the initials FF) consume all RAM and lock my system, yet htop shows no swap in use whenever I look.

I can sometimes get another terminal, but usually have to use alt-sysreq B or even the power button.

How can I make the system use swap before it locks (priority?  what's that?  Not explained in any man page).

I'll upgrade soon, probably to debian and icewm, but I'd like to know how to fix this issue.

[FONT=lucida console]$ swapon -s -h -v
Filename                Type        Size    Used    Priority
/swapfile                                  file        2097148    0    -2
[/FONT]

Cheers,
bitrat

---

### Post by TheFu on 2021-11-20
18.04.[COLOR="#FF0000"]6[/COLOR] is current.

swapon doesn't support -h switch. I think you may want to double the swap as a first step.  I run firefox in a constrained firejail, to prevent it from claiming (which it doesn't actually grab) more RAM than I'd like. --rlimit-as= is the option.  I also force my DNS, so whatever funky choice Mozilla makes can't get anywhere but to my DNS.

Firefox isn't actually taking all the RAM - top/htop are being misread/misunderstood.
**free -hm** is a nicer display of used RAM.
The manpage for top/htop explains what the different columns are actually showing.

I've not had RAM issues on systems with 16+G of RAM, but for desktop systems with less RAM, I consider 4.1G the only size of swap to be used for a number of reasons.  Also, I don't use swapfiles, but that's more about me never doing it that way the last 25 yrs and knowing that swapfiles had/have some flaws that don't work in all situations.

---

### Post by Impavidus on 2021-11-21
16GB ram should be more than enough for normal use. I've got 8GB, running Firefox with 6 tabs:```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          7,7Gi       1,3Gi       4,8Gi       222Mi       1,6Gi       5,9Gi
Swap:         8,5Gi          0B       8,5Gi
```(Yes, my swap is somewhat oversized. The installer decided to make it like this and, with plenty of hard drive space, I see no reason to change it.)

Of course, you may be one of those people who open 100 tabs in Firefox. With very long uptime, buff/cache increases and swap may eventually be used if the OS decides that swapping may be better than dropping some cache.

---

### Post by Holger_Gehrke on 2021-11-21
> **bitrat2 said:**
> (priority?  what's that?  Not explained in any man page).


There is an option '-p' / '--priority' to the swapon program and the man page for swapon (man 8 swapon) tells you to look at the man page for the swapon system call (man 2 swapon) for an explanation of priorities. It's all about which swap area to use if you've got more than one.

Holger

---

### Post by bitrat2 on 2021-11-21
Thanks, firejail look like the ticket!  Thanks for xman hint too.  :)

---

### Post by bitrat2 on 2021-11-21
So the priority setting has no meaning other than to order the use of multiple swaps.  That's what I thought..  The default is -1 but mine (I only have one) reports it's set to -2.  Maybe that means disabled, but I don't see any mention of that setting in man.

Thanks, I'll experiment!  :)

---

### Post by bitrat2 on 2021-11-21
> **Impavidus said:**
> 
Of course, you may be one of those people who open 100 tabs in Firefox. With very long uptime, buff/cache increases and swap may eventually be used if the OS decides that swapping may be better than dropping some cache.

Yup, that's me.  It would be nice to have a tab management tool.  Pretty sure chrome had one once, but I think these have disappeared as browsers have worked to sandbox individual tab processes.

---

### Post by HermanAB on 2021-11-22
Well, then you need a lot more swap space for Firefox, or a lot more RAM, or both.

---

### Post by TheFu on 2021-11-22
> **bitrat2 said:**
> Yup, that's me.  It would be nice to have a tab management tool.  Pretty sure chrome had one once, but I think these have disappeared as browsers have worked to sandbox individual tab processes.

I have about 20 tabs open most of the time, but for tabs I want to read, just not now, I use wallabag running in a Linux Container to save off content.  I find it handy.  

Wallabag is a webapp has a browser addon to make it trivial to save most pages and the android client will sync what's been read or deleted as needed.  A few weeks ago, I was on jury duty - which is hours of sitting around, waiting, for 10 minutes of talk, then more hours of waiting.  Took a tablet and read about 50 articles that I'd been meaning to read - 100% offline.  Some articles I want to keep as reference for a month. Others I want to keep for years. Once in a while, explosive articles get posted, usually about govt stuff, then removed 2 hrs later and the publisher acts like it was never posted and every other publisher that typically re-publishes articles removes it from their feeds too.

But mainly wallabag is a way to have access to interesting (to me) articles for later without all the advertising and header/footer/side-bar junk unrelated to the article.  It basically makes it like the "reading mode" in browsers.  Some articles can't be "bagged" but the vast majority can.  If I were a student and wanted to make a bibliography, wallabag making a time-stamped copy of the content would be very helpful.  I suppose there are other tools for that purpose too .... but I'm a linux server person, so that sort of solution is where I look.
```
Filesystem               Size  Used Avail Use% Mounted on
lxd/containers/wallabag   11G  [COLOR="#008000"]978M[/COLOR]  9.2G  10% /
```
That's the size of the wallabag server ... less than 1GB of storage. Mine has over 1,000 articles saved over the last few years w/ about 600 not marked as read.  It has simple categories and tagging.  I tend to read more in spring time, out back, laying in a hammock.  There's always more to read than time to read it.  Wallabag knows how fast I read and estimates how long each article will be to read, so if I know I have 3 minutes to wait or 20 minutes, then I can pick the article that fits in that time.

---

