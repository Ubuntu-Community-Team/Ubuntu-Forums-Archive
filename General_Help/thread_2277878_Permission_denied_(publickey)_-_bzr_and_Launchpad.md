---
title: "Permission denied (publickey) - bzr and Launchpad"
date: 2015-05-12
forum: General Help
---

### Post by amjjawad on 2015-05-12
Hi everyone,

I am trying to build my very first package. All the steps are done.

When I am trying to push that to Launchpad using:

```
[COLOR=#333333][FONT=Ubuntu]bzr push lp:~amjjawad/+junk/[/FONT][/COLOR]*BRANCHNAME*
```

I get this pain in the neck error:


```
Permission denied (publickey).ConnectionReset reading response for 'BzrDir.open_2.1', retrying
Permission denied (publickey).
bzr: ERROR: Connection closed: Unexpected end of message. Please check connectivity and permissions, and report a bug if problems persist. 



```

Yes, SSH Key and GPG Key are both uploaded.

Yes, I followed all the steps on the documentation, such as: [http://packaging.ubuntu.com/html/getting-set-up.html](http://packaging.ubuntu.com/html/getting-set-up.html)

Yes, I did search on Google but all the results I found so far were unhelpful.

Yes, I asked on #ubuntu channel on IRC but no answer.

So, this is my last chance to seek some answers, hopefully here :)

Thanks in advance!

---

### Post by amjjawad on 2015-05-12
Sorry, forgot to mention that I have tried everything I could or came to my mind on Xubuntu 12.04.5 then thought it might be an issue with 12.04 for whatever reason, that is why I tried again on Ubuntu GNOME 14.04.2 but sadly, the same result so I don't think there is something wrong with the system I am using, it might be a bug or something wrong somewhere :(

---

### Post by amjjawad on 2015-05-18
5 days without a reply??!! hopefully someone knows how to fix this unsolved issue!

Thanks in advance.

---

### Post by ian-weisser on 2015-05-18
Permission Denied is a rather specific error.
Are you *absolutely certain* that your current GPG public key is the same one uploaded to Launchpad?

---

### Post by Bashing-om on 2015-05-18
amjjawad; Hello;

+1 to Ian's comment, I did have such a problem. Took me a while to see it and re-do the GPG public key.
It has been a while, and I do not recall how I isolated it to my invalid key.

[INDENT][INDENT][INDENT]security
[INDENT][INDENT]you is you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by amjjawad on 2015-05-19
> **ian-weisser said:**
> Permission Denied is a rather specific error.
Are you *absolutely certain* that your current GPG public key is the same one uploaded to Launchpad?

Hi and thanks for your reply :)

Yes, I am sure because I have done it more than once, not only on one system but two different systems:
Xubuntu 12.04.5
and
Ubuntu GNOME 14.04.2

Same, I just can't pass that error :(

---

### Post by Elfy on 2015-05-19
Did you do this yet? 

> and report a bug if problems persist.

---

### Post by dino99 on 2015-05-19
have you pm the launchpad maintainer team ?

---

### Post by amjjawad on 2015-05-20
> **Elfy said:**
> Did you do this yet?

Hi and thanks for your post :)

Truth to be told, I did not. Against what exactly should I report that bug? bzr?

---

### Post by amjjawad on 2015-05-20
> **dino99 said:**
> have you pm the launchpad maintainer team ?

Hi and thanks for posting :)

No, I have not yet. I don't think sending private message should do any help. However, I guess it is time to report a bug!
Not yet sure though against which package should I report that bug? bzr? not very sure.

---

### Post by Elfy on 2015-05-20
> **amjjawad said:**
> Hi and thanks for your post :)

Truth to be told, I did not. Against what exactly should I report that bug? bzr?

That's where I would start for sure - if it's not right someone will move it.

---

### Post by flaymond on 2015-05-24
amjjawad, are you trying to upload the source code and packaging it as .deb? If it's only source code, I tried it by uploading ssh key, and just -

```
           bzr launchpad-login myname
           cd /to/directory # I cd to branch, and not the root
           bzr push lp:~my-team/root/branch

```

I uploaded the code, smooth and fine. For that, I need a team and a project. I believe you wanna upload and publish it as ppa, or you just want to experiment it, like me? Thanks.

Update - For personal branch, I just bzr push lp:~myname/+junk/branch, and somehow it's worked. I did it without any GPG pub keys. Only SSH.

---

### Post by amjjawad on 2015-05-29
> **Elfy said:**
> That's where I would start for sure - if it's not right someone will move it.

You're correct. I will then report that against bzr and if that's the wrong package, someone else - as you mentioned - will do the needful ;)

Many thanks, Elfy :)

---

### Post by amjjawad on 2015-05-29
> **InterProg said:**
> amjjawad, are you trying to upload the source code and packaging it as .deb? If it's only source code, I tried it by uploading ssh key, and just -

```
           bzr launchpad-login myname
           cd /to/directory # I cd to branch, and not the root
           bzr push lp:~my-team/root/branch

```

I uploaded the code, smooth and fine. For that, I need a team and a project. I believe you wanna upload and publish it as ppa, or you just want to experiment it, like me? Thanks.


Hi,

Launchpad does not accept .deb so you need to upload the source code and then, Launchpad will build the rest for you. I am stuck at the upload stage as something is wrong and I can't upload anything. The source code and all has been built on my machine. I just need to upload it and here is my problem - I just can't so far.




> Update - For personal branch, I just bzr push lp:~myname/+junk/branch, and somehow it's worked. I did it without any GPG pub keys. Only SSH.

As per the documents I did read, both must be there. I did that more than 3 times on 2 different systems (12.04.5 and 14.04.2) but the same result.

I will follow Elfy's advice and report a bug :)

---

### Post by flaymond on 2015-05-30
[QUOTE=amjjawad]Launchpad does not accept .deb so you need to upload the source code and then, Launchpad will build the rest for you.[/QUOTE]

That's correct. I thought you only want to upload it to launchpad, not to build farm is as .deb for ppa. That's why I give the commands to upload. Unfortunately, for .deb ppa, I don't know how to do that. :(

Maybe you can ask Israel for help though, he taught me using this VCS and stuff.

or it's really a bug. If yes, I hope it will be fixed soon.

Thanks

---

### Post by amjjawad on 2015-06-16
Hi,

Finally, got sometime to report a bug:
[https://bugs.launchpad.net/ubuntu/+source/bzr/+bug/1465579](https://bugs.launchpad.net/ubuntu/+source/bzr/+bug/1465579)

I hope someone will see that quickly and find a fix or a workaround, at least :)

Thank you!

---

