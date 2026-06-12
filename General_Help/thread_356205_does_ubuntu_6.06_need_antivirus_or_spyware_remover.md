---
title: "does ubuntu 6.06 need antivirus or spyware remover?"
date: 2007-02-08
forum: General Help
---

### Post by stonerrob420 on 2007-02-08
does ubuntu 6.06 need a antispyware or antivirus? I have read pages and pages that say no but arent there any linux virus on the net?????????????:confused:

---

### Post by ardchoille42 on 2007-02-08
I don't think so. In order to get something like this, you'd have to intentionally download it, switch to the root user, chmod it executable, and then run it. I think Linux users are smart enough to not do that with strange packages/binaries :)

Besides that, there aren't any active viruses for Linux right now. One of the reasons for that is that it is a complete waste of time to write a virus for Linux. In order to get the virus to work, your victim has to go through all the trouble (as mentioned above) of getting it to run system-wide.

Some people claim that if Linux were as wide-spread as Windows is now, then viruses would be a regular thing. That is simply not true. Virus authors want to cause as much trouble as possible on as many systems as they can, that's not easy with Linux (Linux users are usually too smart) so they don't waste their time writing viruses for Linux.

Yay for an OS that makes you actually learn how to use it!

---

### Post by TitanKing on 2007-02-08
> **stonerrob420 said:**
> does ubuntu 6.06 need a antispyware or antivirus? I have read pages and pages that say no but arent there any linux virus on the net?????????????:confused:

The chances that you will ever need these are very unlikely! Remember the virus/spyware will need to be a user and know the password before it will ever be able to do anything. And guess what those are the two things it does not have. 

So I in the years of using Linux never had one problem!

---

### Post by stonerrob420 on 2007-02-08
ok guys thanks for your help......i great appreciate it........:)

---

### Post by emarkay on 2007-02-08
Of course if you dual boot with any Window$ version OR share files with a Window$ user, it's a good idea to scan the files for ANY virusses (virii?) before passing them on, IMHO...

---

### Post by huygens on 2007-02-08
> **ardchoille42 said:**
> I don't think so. In order to get something like this, you'd have to intentionally download it, switch to the root user, chmod it executable, and then run it. I think Linux users are smart enough to not do that with strange packages/binaries :)

Not necessarily, that's why they are security updates on Linux ;-) because they are security holes and one virus could use them to gain root privileges. No need for user interaction in this case...

> **ardchoille42 said:**
>  Besides that, there aren't any active viruses for Linux right now. One of the reasons for that is that it is a complete waste of time to write a virus for Linux. [...] 

There are quite a few rootkits for Linux, you should always be aware of that.

> **ardchoille42 said:**
> Some people claim that if Linux were as wide-spread as Windows is now, then viruses would be a regular thing. That is simply not true.

Yep, this is sadly true. If it was more wide spread, there would be more viruses for this platform. You are perhaps updating regularly for security updates, but what about unknown security holes? As it is open source, one could find one, not make it public and create a virus that would spread over the whole lot of computer. It would take several days for security teams to reverse engineer it or analyse the attack method to find out the security hole and make a patch. Enough time for a virus to spread :-(
In addition, not every user update there system regularly, some even on purpose, not to break the running services to the customers.

An easy attack would be someone who post on a forum a repository of files with some really cool (that everyone wanted) packages. Everyone add it to synaptic and use the packages. Then, the responsible of the repository or a pirate who managed to hack the repository server puts a new file which will replace a system package. Most user won't notice it and install it, just like a security update. Well, this could stay invisible for a couple of times (a spyware type of virus) or get quite virulent... who knows!

So not enough virus for the moment to absolutely require an anti-virus. But I won't be surprise that this kind of software gains importance if Linux spreads further into homes.

---

### Post by ardchoille42 on 2007-02-08
> **huygens said:**
> Not necessarily, that's why they are security updates on Linux ;-) because they are security holes and one virus could use them to gain root privileges. No need for user interaction in this case...
And how often has this scenario happened?


> **huygens said:**
> There are quite a few rootkits for Linux, you should always be aware of that.
Yes, but his question wasn't about rootkits, was it? rootkit != virus

> **huygens said:**
> Yep, this is sadly true. If it was more wide spread, there would be more viruses for this platform.
I feel that you aren't familiar with the inner workings of a virus or Linux. Please don't perpetuate this myth.

> **huygens said:**
> An easy attack would be someone who post on a forum a repository of files with some really cool (that everyone wanted) packages. Everyone add it to synaptic and use the packages. Then, the responsible of the repository or a pirate who managed to hack the repository server puts a new file which will replace a system package. Most user won't notice it and install it, just like a security update. Well, this could stay invisible for a couple of times (a spyware type of virus) or get quite virulent... who knows!
Ah, but that isn't following common sense security practices is it? The proper way to admin a distro is:

1) Only use the repos provided by the distro.
2) Never compile anything unless you have audited the code.
3) Never use sources/packages unless they were:
   a) Designed for that distro
   AND
   b) Created by a community-trusted source
4) Run security apps once per day - including (but not limited to) rkhunter, chkrootkit and snort.
5) Backup your important files once per day. Yay for cronjobs :)
6) Never share files between a Windows box and a Linux box. I would recommend never touching Windows. I haven't used it since 2000 and I don't miss it.

If one finds that this would make for a boring Linux experience, one should learn a programming language.. I did.

I'll probably get flamed for my responses, but there has to be a reason why I haven't had any major problems on any distro in years.

I have used Linux since 2001 and I have been writing security software since 1996. Just because my bean count is low, doesn't mean I am a newbie to Linux ;)

---

