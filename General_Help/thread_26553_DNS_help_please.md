---
title: "DNS help please"
date: 2005-04-13
forum: General Help
---

### Post by minimole on 2005-04-13
hey just installed hoary hedgehog and i have a small problem which i am conviced is dns related but i really have no i dea how to fix it. i cant connect to any websites using the domain name (google.com etc) but i can via the ip however i can ping google.com and it does resolve any ideas how to fix this please.

---

### Post by minimole on 2005-04-13
o yeah and i am using DCHP and my router does all my dhcp

---

### Post by az on 2005-04-13
Does /etc/resolv.conf change after you do a 

sudo /etc/init.d networking restart

Post your /etc/networking/interfaces.

Have you changed the settings on your router?

---

### Post by arctic on 2005-04-13
hi there. :)

you are another one who should read this howto. (yes, many users needed to go through this hassle... routers can be so annoying :D)
[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

and next time, please do a search before posting. ;)

---

### Post by az on 2005-04-13
[QUOTE=arctic]hi there. :)

you are another one who should read this howto. (yes, many users needed to go through this hassle... routers can be so annoying :D)
[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

and next time, please do a search before posting. ;)[/QUOTE]

Can you

1. Be more rude
2. Explain how what you propose in your thread fixes the problem?

pump is used to make a dhcp connection.  Installing it does not make the Ubuntu networking use it, it will continue to use dhcp-client.  dnsmasq is for dns masquerading.  Unless you are acting as a dns server, it should not do anything.
Relsovconf may act on your /etc/resolv.conf but you are making that read-only in your next step.  It is not clear what you are suggesting?

Thanks.

---

### Post by minimole on 2005-04-13
right /etc/resolv.conf didnt change when i  tryed 
sudo /etc/init.d/networking restart 

i will try /etc/networking/interfaces but i cant seem to find atm i am a noob with linux lol

---

### Post by arctic on 2005-04-15
[QUOTE=azz]Can you

1. Be more rude
2. Explain how what you propose in your thread fixes the problem?

pump is used to make a dhcp connection.  Installing it does not make the Ubuntu networking use it, it will continue to use dhcp-client.  dnsmasq is for dns masquerading.  Unless you are acting as a dns server, it should not do anything.
Relsovconf may act on your /etc/resolv.conf but you are making that read-only in your next step.  It is not clear what you are suggesting?

Thanks.[/QUOTE]
 1. i don't think that i was rude at all. if this is yor impression, then i am sorry. it was never my intention to be somehow "rude". i was just stating that he should take a look at the howto.
2. have you read the howto? have you tried it on a box which does have these problems? i have used these options on several boxes and it works. so can claim dozens of other linux-users (not only ubuntu users ;))

just a quick explanation. pump WILL be used instead of the standart dhcp-client, once it will be installed together with the other packages (the old client will be removed from the box automatically). pump seems to have no configuration or auto-enabling for ipv6, so it will not show the same problems, once it is used. but if you install pump without the two other packages, the system will not enable any networking at all. don't ask me why this is so, but it is just like that. btw. this information was mailed around on the debian-developer-mailing lists long time ago.
anyway, i always recommend to hack the files before installing an alternative dhcp-client.

---

### Post by az on 2005-04-15
[QUOTE=arctic]1. i don't think that i was rude at all. if this is yor impression, then i am sorry. it was never my intention to be somehow "rude". i was just stating that he should take a look at the howto.
2. have you read the howto? have you tried it on a box which does have these problems? i have used these options on several boxes and it works. so can claim dozens of other linux-users (not only ubuntu users ;))

just a quick explanation. pump WILL be used instead of the standart dhcp-client, once it will be installed together with the other packages (the old client will be removed from the box automatically). pump seems to have no configuration or auto-enabling for ipv6, so it will not show the same problems, once it is used. but if you install pump without the two other packages, the system will not enable any networking at all. don't ask me why this is so, but it is just like that. btw. this information was mailed around on the debian-developer-mailing lists long time ago.
anyway, i always recommend to hack the files before installing an alternative dhcp-client.[/QUOTE]


1.  When I read your post, I feared that the user would not come back.  Anyway, it is not my place to tell you how to express yourself...

2- I have no doubt that the fix works, it just requires packages that are not on the cd.  Users have to hack their way onto the net and install universe packages to ge tthe net working.  It is unelegant and unintuitive.  It also does not really describe the problem.
Has there been a bug report filed about this by anyone from the forums?  I found these: 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=4433](https://bugzilla.ubuntu.com/show_bug.cgi?id=4433)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=5868](https://bugzilla.ubuntu.com/show_bug.cgi?id=5868)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7992](https://bugzilla.ubuntu.com/show_bug.cgi?id=7992)

It would be really great if everyone who followed the advice on the howto were to add to the relevant bug reports so that the problem could be solved.


I am sorry for being a grumpy wet-willy.

---

### Post by jmpmjmpm on 2005-04-15
[QUOTE=azz]1.  When I read your post, I feared that the user would not come back.  Anyway, it is not my place to tell you how to express yourself...

2- I have no doubt that the fix works, it just requires packages that are not on the cd.  Users have to hack their way onto the net and install universe packages to ge tthe net working.  It is unelegant and unintuitive.  It also does not really describe the problem.
Has there been a bug report filed about this by anyone from the forums?  I found these: 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=4433](https://bugzilla.ubuntu.com/show_bug.cgi?id=4433)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=5868](https://bugzilla.ubuntu.com/show_bug.cgi?id=5868)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7992](https://bugzilla.ubuntu.com/show_bug.cgi?id=7992)

It would be really great if everyone who followed the advice on the howto were to add to the relevant bug reports so that the problem could be solved.


I am sorry for being a grumpy wet-willy.[/QUOTE]
 Just to add my opinion I find all requests to "do a search" rude and have said so in many forums, the way I see it if you believe that something asked has been asked and resolved before the point in the right direction (as has been done here). If you are ticked off that someone has posted without searching then simply don't reply to the post, if the moderators think the person should "do a search" I'm sure that they will say so, but other users have absolutely no right at all in telling someone how to go about their query. I'm not saying that this is the case here but I have found that those people whose reaction to a post is to tell the poster to "do a search" is for one of two reasons, they don't know the answer themselves and to feel better about themselves and post something implying they know but can't be bothered to tell and the other reason is they want to improve their posting rating and do so by having the words "do a search" stored in their clipboard and have wore the print off their ctrl and v keys!

IMHO, I always lock my resolv.conf file when I have them at a setting that works for me. If you have a dns problem then you could try editing the properties of your internet connection (or the connection that supplies the net) with your isp's dns servers values if you don't like to edit the resolv.conf file manually, then when dns is working you could lock the file so it can't be overwritten.

---

### Post by arctic on 2005-04-15
[QUOTE=azz]
2- I have no doubt that the fix works, it just requires packages that are not on the cd.  Users have to hack their way onto the net and install universe packages to ge tthe net working.  It is unelegant and unintuitive. [/quote] yes, i agree that it is not the most elegant solution but the little howto explains how you can access the mirrors for downloading while you so have the ipv6 problem.
>  It also does not really describe the problem. yupp... i think i should add more information there, eh?
> Has there been a bug report filed about this by anyone from the forums?  I found these: 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=4433](https://bugzilla.ubuntu.com/show_bug.cgi?id=4433)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=5868](https://bugzilla.ubuntu.com/show_bug.cgi?id=5868)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7992](https://bugzilla.ubuntu.com/show_bug.cgi?id=7992)

It would be really great if everyone who followed the advice on the howto were to add to the relevant bug reports so that the problem could be solved.
i will put them in there. and... the bug had been reported on several distributions and not even one developer was willing to disable ipv6 by default although they have been thinking about a little tool that might do that. i don't know however if that idea got lost in the swamps of packages and bugfixes.

> Just to add my opinion I find all requests to "do a search" rude and have said so in many forums, the way I see it if you believe that something asked has been asked and resolved before the point in the right direction (as has been done here). yes, such requests are somewhat rude. agreed. but i did not write rtfm, because this would be really rude. but if we don't point users to the search-tool we will continue to have 500 identical posts day in and day out. and i am not able to review and answer 500 topics per day. sorry, but my time is as limited as  that of any other user. and an additional problem will be that 1.) no one might answer the topic and 2.) the original poster of the topic cannot find his topic again and thus not see the probable answer for his question.  :?

---

