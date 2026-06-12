---
title: "This version of Chrome is no longer supported"
date: 2017-02-09
forum: General Help
---

### Post by amjjawad on 2017-02-09
Hi everyone,

I have Xubuntu 14.04 with 3.13.0-107-generic.

I got this message on my **Chromium Browser** version:
```
Version 53.0.2785.143 Built on Ubuntu , running on Ubuntu 14.04 (64-bit)

```

This message is:
```
This version of Chrome is no longer supported. Please upgrade to a supported browser. Dismiss
```

I checked the supported browser and I found:
[https://support.google.com/mail/answer/6557?hl=en-GB](https://support.google.com/mail/answer/6557?hl=en-GB)

I know [Google will stop Hangout service in April this year]("https://techcrunch.com/2017/01/06/hangouts-api-shut-down/") but did they decide to stop Chromium too?

I did:

```
apt-get dist-upgrade
```

but did not find any update for Chromium.

I'm wondering what should I do?

Thanks in advance :)

---

### Post by A.Zan on 2017-02-09
I'm using Google Chrome and I'm getting this weird message too.

So I run the system update AND also [COLOR=#111111][FONT=Consolas]sudo apt-get upgrade google-chrome-stable [/FONT][/COLOR]but Chrome did not update anyway.
My Ubuntu is 16.04 LTS

I fixed it adding the PPA of Chrome, then running a system upgrade

---

### Post by howefield on 2017-02-09
> **amjjawad said:**
> I'm wondering what should I do?

As far as I am aware Chromium is not dependant on Chrome, if anything it is the other way around. Chrome cannot shut down Chromium.

You have the latest Chromium package for you distribution : [http://packages.ubuntu.com/search?keywords=chromium](http://packages.ubuntu.com/search?keywords=chromium) - not sure why Trusty hasn't gotten version 55.0.2883.87 yet as Xenial and Yakkety have, although the development version is still on 53.0.2785.143.

I'd think it is just a matter of waiting for the Trusty repos to catch up.

---

### Post by vasa1 on 2017-02-09
> **howefield said:**
> ... not sure why Trusty hasn't gotten version 55.0.2883.87 yet as Xenial and Yakkety have, although the development version is still on 53.0.2785.143.

I'd think it is just a matter of waiting for the Trusty repos to catch up.
According to [http://askubuntu.com/a/878682](http://askubuntu.com/a/878682), there was or is a problem with building higher versions for Trusty.

---

### Post by oldrocker99 on 2017-02-09
Google has announced that the 32-bit version of Chrome is defunct; no more versions will be released. Try Firefox or Opera, or...

---

### Post by mastablasta on 2017-02-09
> **oldrocker99 said:**
> Google has announced that the 32-bit version of Chrome is defunct; no more versions will be released. Try Firefox or Opera, or...

nah, that's not it. OPs version is 64 bit:

> running on Ubuntu 14.04 (64-bit)

---

### Post by howefield on 2017-02-09
> **oldrocker99 said:**
> Google has announced that the 32-bit version of Chrome is defunct; no more versions will be released. Try Firefox or Opera, or...

The OP is confusing but it seems that it is Chromium, not Chrome that is the issue.

---

### Post by oldrocker99 on 2017-02-09
> **mastablasta said:**
> nah, that's not it. OPs version is 64 bit:

Oops.:oops:

---

### Post by amjjawad on 2017-02-09
> **howefield said:**
> The OP is confusing but it seems that it is Chromium, not Chrome that is the issue.

No, I am not confused. I do have Chromium and I know I was talking about it. I just copied and pasted the error message I am seeing on the top of Chromium when I open my Gmail. That message only on Gmail. 

[ATTACH=CONFIG]273603[/ATTACH]

Also, check the 3rd line of my original post ;)

---

### Post by howefield on 2017-02-09
> **amjjawad said:**
> No, I am not confused. I do have Chromium and I know I was talking about it. I just copied and pasted the error message I am seeing on the top of Chromium when I open my Gmail. That message only on Gmail. 

Sigh. I didn't say you were confused, I said that your OP (original post) was confusing. Perhaps that difference is too subtle for you.

Using a title like "*This version of Chrome is no longer supported*", even if that is the actual error,  when you are talking about Chromium is bound to lead to confusion.

Anyway, you now know the answer, as vasa1 kindly researched for you.

---

### Post by amjjawad on 2017-02-09
> **howefield said:**
> Sigh. I didn't say you were confused, I said that your OP (original post) was confusing. Perhaps that difference is too subtle for you.

Using a title like "*This version of Chrome is no longer supported*", even if that is the actual error,  when you are talking about Chromium is bound to lead to confusion.

Anyway, you now know the answer, as vasa1 kindly researched for you.

I was copying the same error message and didn't want to modify anything because when other people will search, they will not find this post if they'll write "chromium" which will not show up on their browser anyway. Google does not list Chromium as a browser on this page:

[https://support.google.com/mail/answer/6557?hl=en-GB](https://support.google.com/mail/answer/6557?hl=en-GB)

I can't see Chromium on the list!

> **vasa1 said:**
> According to [http://askubuntu.com/a/878682](http://askubuntu.com/a/878682), there was or is a problem with building higher versions for Trusty.

But I don't have any PPA for Chromium. I just installed it by:

```
sudo apt-get install chromium-browser
```

---

### Post by vasa1 on 2017-02-09
> **amjjawad said:**
> ...

But I don't have any PPA for Chromium. I just installed it by:

```
sudo apt-get install chromium-browser
```
There is/was difficulty building chromium-browser for Trusty. That refers to the regular browser as well.

---

### Post by amjjawad on 2017-02-10
> **vasa1 said:**
> There is/was difficulty building chromium-browser for Trusty. That refers to the regular browser as well.

And?

---

### Post by deadflowr on 2017-02-10
> **amjjawad said:**
> I was copying the same error message and didn't want to modify anything because when other people will search, they will not find this post if they'll write "chromium" which will not show up on their browser anyway. Google does not list Chromium as a browser on this page:

[https://support.google.com/mail/answer/6557?hl=en-GB](https://support.google.com/mail/answer/6557?hl=en-GB)

I can't see Chromium on the list!

There is key wording in that page;
> Gmail can be used with the current and previous versions of most browsers, including:
this infers that the list is not exhausted and that their may be other browsers that do support gmail.
And indeed there are, such as Opera and Vivaldi among many many others.
They just are not going to list the 20 different browsers that do, only the most popular.
Chromium is not popular, or not as popular as google-chrome is.
And to google, google-chrome and chromium are mostly synonymous anyway, with the few google goodies(non-free and proprietary goodies) google-chrome has by default being the exceptional difference.

> **amjjawad said:**
> And?

to what?

The best we know is something beyond version 53 causes an incompatibility with whatever comes in Ubuntu 14.04 and is preventing it to built beyond that version for 14.04.
I guess an option if you really must have chromium, is to see about installing it from source, or at least attempt to:
[https://www.chromium.org/Home]("https://www.chromium.org/Home")

Not really sure what problem is has that google-chrome does not, as google-chrome runs just fine fully up-to-date on 14.04...

---

### Post by fremsley on 2017-02-12
Joined Ubuntu forums just to say am surprised by lack of Chromium updates.  Current stable 64-bit version is 56.0.2924.87 and as the OP found, Trusty is on 53.0.2785.143.  According to the release data from Chromium, this is six months old; not good for the security of any browser.

sudo add-apt-repository ppa:canonical-chromium-builds/stage
sudo apt-get update
sudo apt-get install chromium-browser

just informed me I have the current version.

---

### Post by vasa1 on 2017-02-12
> **fremsley said:**
> Joined Ubuntu forums just to say am surprised by lack of Chromium updates. ... not good for the security of any browser.
...
Not much we can do here :( We're all just users like yourself.

There's no telling if the issues blocking Chromium from being updated for 14.04 will persist. You could try contacting the ppa's maintainer for some insight.

---

### Post by fremsley on 2017-02-12
I'm surprised mainly because it is the first time in a long time that something I'd consider to be mainstream has fallen down.  Agreed that this humble (very humble) user isn't doing squat except complaining, but hope that could be seen as 'raising awareness of this issue'.  :)

I've been a Unix user since 1990, Redhat since 1998, Ubuntu for a decade, Mint for my laptop for last few years. Perhaps it says something that I could pretty much always find an answer to previous queries and that the errors were pretty much always at my end?

---

### Post by amjjawad on 2017-02-15
A bug has been reported:
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1664883](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1664883)

---

### Post by termibuntu on 2017-02-15
Hi. What you dont get is that if you download from the ubuntu software center, sometimes you can get unsupported programs, such as i got virtualbox from the software center, and it was unsupported. You should get it from googles website instead, as they always put up the newest versions of chrome and chromium. Hope this helps.

---

### Post by amjjawad on 2017-04-22
```
Version 57.0.2987.98 Built on Ubuntu , running on Ubuntu 16.04 (64-bit)
```

Problem solved by upgrading to 16.04 :)

Thank you!

---

