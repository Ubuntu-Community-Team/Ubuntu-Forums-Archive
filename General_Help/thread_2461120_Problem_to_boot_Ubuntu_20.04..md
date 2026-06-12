---
title: "Problem to boot Ubuntu 20.04."
date: 2021-04-24
forum: General Help
---

### Post by ckrles on 2021-04-24
Hi, I'm using ubuntu 20.04 (dual boot with W10)

I have google and tried everything I found to no succes. I got this message a few weeks ago, but it was solved on a second reboot. The funny thing is that I tried for a while to solve it with no success. I left it for 2 hours and it did boot normally. After that, the next reboot brought the problem back. My / partition is low on space. Could it be the cause or related to it? Any ideas.

It suddenly stopped booting and I get an this message: [COLOR=#242729][FONT=Consolas]dev/sda5 clean ####/#### files ######/###### blocks[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]
Thanks.

I have tried clean, remove, update commands and installing and reconfiguring gdm3.

[/FONT][/COLOR]

---

### Post by yancek on 2021-04-24
>  My / partition is low on space. Could it be the cause or related to it? Any ideas.


Yes, that is a common cause of being unable to boot.  If you are able to still boot into Ubuntu, open a terminal and run the following command and post the output here.  You need a space between the df and the -h

```
df --h
```

Common problems are log files so you could take a look at the /var/log and see if you have a lot of older log files which you can delete.

---

### Post by Impavidus on 2021-04-25
> **ckrles said:**
> 
It suddenly stopped booting and I get an this message: ```
[COLOR=#242729][FONT=Consolas]dev/sda5 clean ####/#### files ######/###### blocks[/FONT][/COLOR]
```[COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR]
That message is fairly common and indicates no error. It's supposed to be hidden by the splash screen, but that doesn't work very well. Failure to boot in a reasonable time is of course a problem.

---

### Post by ckrles on 2021-04-25
I can't access my pc now. I'll post the output asas. Thanks.

---

### Post by ckrles on 2021-04-25
I know it's a problem. I just want to solve it. Any suggestions?

---

### Post by dragonfly41 on 2021-04-25
There are a few threads around if you just google that pattern .. [here is one]("https://askubuntu.com/questions/882385/dev-sda1-clean-this-message-appears-after-i-startup-my-laptop-then-it-w")

---

### Post by ckrles on 2021-04-25
I have already checked that website. I couldn't fix my problem.

---

### Post by ckrles on 2021-04-25
I've been able to fix it by using a previous kernel in the advanced options boot. Once there I emptied space in /var/log/journal and set the maximum size of the folder to 200Mb.

---

