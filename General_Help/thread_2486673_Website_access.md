---
title: "Website access"
date: 2023-05-08
forum: General Help
---

### Post by Y^2om&amp;#7sgP on 2023-05-08
Hope someone here can assist.
I purchased a new PC, and installed.......windows, then dual booted with Ubuntu 22.04.
In Ubuntu I cannot access certain website, Youtube and Amazon are two I have found.
Reboot to windows and both work fine.
I did wonder if 23.04 may help, but eactly the same problem.
I've googled the issue and find it goes back over 10 years.
Suggestions were disable IPv6, did that no difference
Change DNS, did that no difference
Use a VPN, did that no difference
Does anyone know how to fix this issue so that everything works.
Oh, and as an after thought, I have a second PC running 22.04 and everything works fine, including the websites mentioned
I've asked the supplier of the PC, but all they say is that they don't support Linux :-(

---

### Post by Y^2om&amp;#7sgP on 2023-05-08
Update, I've just tried looking for updated drivers and there apparently are none

---

### Post by Y^2om&amp;#7sgP on 2023-05-11
Any suggestions please?

---

### Post by Rubi1200 on 2023-05-11
Hi, not sure I can really help but I do have some suggestions.

1. try a different browser on the machine that seems to be a problem

2. unless you are not comfortable with it, try reinstalling Ubuntu on the machine

3. post the output of ```
cat /etc/resolv.conf
```

Perhaps someone will come along and have some other ideas.

---

### Post by Y^2om&amp;#7sgP on 2023-05-12
Thanks for the suggestions Rubi1200

I've tried re-installing and different browsers, but no luck

output of resolv.conf

nameserver 127.0.0.53
options edns0 trust-ad
search .

---

### Post by yancek on 2023-05-12
Seems an odd problem.  What happens specifically when you try to contact the sites you mention?  Does it time out?  Do you get any messages on screen?

---

### Post by Y^2om&amp;#7sgP on 2023-05-12
Only the website cannot be found. It doesn't happen with all sites, so far Amazon and YouTube

---

### Post by tea for one on 2023-05-12
> **hattpa said:**
> I've googled the issue and find it goes back over 10 years.
As you can use Google, what happens if you use Google apps (top right of Google home page) to access YouTube?

---

### Post by tea for one on 2023-05-12
I've just noticed that this is not the first time you have experienced this?
July 2022 - [https://ubuntuforums.org/showthread.php?t=2476896](https://ubuntuforums.org/showthread.php?t=2476896)
December 2022 - [https://ubuntuforums.org/showthread.php?t=2482361&p=14125098#post14125098](https://ubuntuforums.org/showthread.php?t=2482361&p=14125098#post14125098)

---

### Post by Rubi1200 on 2023-05-12
Which browser have you been using and do you have extensions like NoScript installed and active?

Perhaps try temporarily disabling any extensions one by one and see if that resolves the problem.

---

### Post by TheFu on 2023-05-12
Cannot access is a bit vague.  Can you ping the website you are trying to view using the name or the IP address?  Can you ping other websites?

Are you in place in the world where the ISP or govt might limit access to specific websites?  I remember during travel to a country that I didn't think filtered the internet, but found that the hotel did, while the SIM card for my travel phone provided access to the website I couldn't reach using the hotel's connection.  Lots of countries block parts of the internet.  I know I've been surprised at how often this happens, even from generally open and democratic countries.

Also, sometimes, usually for just a few hours, a human mistake, or nefarious actor, can prevent entire parts of the internet from being accessed by screwing up routing tables across the entire internet.  These are about 20% accidental and 80% nefarious based on history.  [https://www.wired.com/story/google-internet-traffic-china-russia-rerouted/](https://www.wired.com/story/google-internet-traffic-china-russia-rerouted/)  There are easily 20 other similar stories of odd routing being perpetrated by govts.

---

### Post by Y^2om&amp;#7sgP on 2023-05-16
Tea for one, yes I did and never found a resolution.
 We're currently on vacation so I'll try your suggestion when I get home

---

### Post by Y^2om&amp;#7sgP on 2023-05-23
Just tried pinging amazon, reply received but still can't browse to it???

---

### Post by tea for one on 2023-05-23
```
nameserver 127.0.0.53
options edns0 trust-ad
search . 
```
Above is your resolve.conf from post 5

```
nameserver 127.0.0.53
options edns0 trust-ad
search lan
```
This is my resolve.conf from 23 May 2023 and I do not have any trouble accessing websites.

You can see that I have [COLOR="#0000FF"]search lan[/COLOR] in the last line and yours is missing [COLOR="#0000FF"]lan[/COLOR].
Unfortunately, my knowledge of network protocols is severely limited and this may be unimportant.
Hopefully, somebody can step in and offer some germane advice.

---

### Post by Y^2om&amp;#7sgP on 2023-05-24
Thanks for the suggestion tea for one, I updated resolv.conf, but it makes no difference. I can still ping the sites but still unable to browse them.

---

### Post by Rubi1200 on 2023-05-24
Are you on a wireless or wired connection?

If wireless, please run the info script and post the results [https://github.com/UbuntuForums](https://github.com/UbuntuForums)

I am no expert in this field, but there are others on the forums who do know how to read and interpret the script results.

---

### Post by tea for one on 2023-05-24
In post no. 1, you mentioned that your other PC with Ubuntu 22.04 did not have this website access problem.
Can you compare the UEFI settings to see if an option needs attention?

---

### Post by TheFu on 2023-05-24
> **tea for one said:**
> ```
nameserver 127.0.0.53
options edns0 trust-ad
search . 
```
Above is your resolve.conf from post 5

```
nameserver 127.0.0.53
options edns0 trust-ad
search lan
```
This is my resolve.conf from 23 May 2023 and I do not have any trouble accessing websites.

You can see that I have [COLOR="#0000FF"]search lan[/COLOR] in the last line and yours is missing [COLOR="#0000FF"]lan[/COLOR].
Unfortunately, my knowledge of network protocols is severely limited and this may be unimportant.
Hopefully, somebody can step in and offer some germane advice.

The 'search lan' means that hostname.lan is your local DNS domain. If you don't run a DNS or the local DNS domain isn't "lan" (case-insensitive), then . is the correct answer ... or just delete the line.

For example, my local domain is th.foo  so my DNS server has entries for hadar.th.foo and regulus.th.foo.  My search is 'th.foo' in resolv.conf and DNS will resolve local machine lookups  using either 'hadar.th.foo' or just 'hadar' ... all thanks to the 'search' entry in /etc/resolv.conf.  BTW, if you have a local DNS, then you don't need to use the local DNS cache that Ubuntu added around 18.04 with systemd-resolved. It is wasted.  Mask that service and point your resolv.conf directly at your LAN DNS server(s). Let them do the caching, not your local system.

Of course, if you have a laptop that moves off your LAN, then having the local DNS caching server wouldn't be bad, but for a desktop or server with a local DNS, it is pretty useless.

---

### Post by Y^2om&amp;#7sgP on 2023-05-25
Tea for one, on the other machine I have no issues at all. As an update for an unknown reason, YouTube now works, but...... still can't get to amazon.co.uk. frustrating..

---

### Post by ActionParsnip on 2023-05-25
Do you use a proxy for web access? or a VPN?

---

### Post by tea for one on 2023-05-25
> **hattpa said:**
> YouTube now works, but...... still can't get to amazon.co.uk. frustrating..
Some may say that Amazon being out of reach is a feature not a bug.
I could not possibly comment ;)

You could try via the terminal:-
```
xdg-open https://www.amazon.co.uk
```
The terminal output may offer a clue?

---

### Post by Y^2om&amp;#7sgP on 2023-05-26
OK, so have found a workaround.  If I browse to [www.amazon.co.uk](www.amazon.co.uk), it fails, I had the idea that if I could ping the address, which I can, I 'should be able to get there.  I searched google for amazon uk, and I can get in, login and it all works.  I've bookmarked the site, and can now get there.
I have tried adding the IP address into the hosts file, but that still fails.
Any ideas anyone?
Not a problem now, as such, but it would be nice to know how to fix this?
Cheers

---

### Post by Y^2om&amp;#7sgP on 2023-05-26
tea for one, the last idea you suggested also works. Thanks for that

---

