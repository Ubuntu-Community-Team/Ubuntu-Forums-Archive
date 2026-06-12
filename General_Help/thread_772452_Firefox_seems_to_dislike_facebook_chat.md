---
title: "Firefox seems to dislike facebook chat"
date: 2008-04-28
forum: General Help
---

### Post by airbornemist6 on 2008-04-28
Has anyone else noticed this? I'm running Hardy Heron and it seems like since a certain update, it has not worked properly. When you try and send a message it the message times out, but when you go to another page the message and the responces to that message show up. As far as I can tell it only happens on FireFox 3, and I have only seen it on 64 bit systems (in other words, it's happening on my systems, but my school's are unaffected). I also experienced this in Windows Vista 64-bit (leave me alone, it's my gaming rig) so I am thinking it's actually something with firefox 3. I want to ask, has anyone had any problems with this? If so does anyone know a workaround?

---

### Post by Islington on 2008-04-28
I had just assumed that firefox knew that I should really be studying for finals... :D



j/k  it doesnt seem to affect me, is there any terminal output?

---

### Post by Nathan_M on 2008-04-28
Yeah, I've had the problem. There doesn't seem to be any relevant terminal output.

It tells my friends that I am "offline" even when I'm not, and when I send a message, it tells me that it couldn't connect, but it actually (from the point of view of my friends) sets me to "online" just for a second... the message sends, but they can't reply because it tells them I'm offline again straight away.

---

### Post by airbornemist6 on 2008-04-28
> **Islington said:**
> I had just assumed that firefox knew that I should really be studying for finals... :D



j/k  it doesnt seem to affect me, is there any terminal output?

Well color me embarassed, I totally forgot to check that. I shall check after my class and post my findings.

---

### Post by Nathan_M on 2008-04-28
something else a bit weird... It was working fine until Friday (25th). Facebook chat came out for me on Wednesday, and I used it for two days without any problems. I've had a look at my upgrade history in Synaptic, and there were no updates on Thursday or Friday! So Facebook must have changed something.

---

### Post by airbornemist6 on 2008-04-28
> **Nathan_M said:**
> something else a bit weird... It was working fine until Friday (25th). Facebook chat came out for me on Wednesday, and I used it for two days without any problems. I've had a look at my upgrade history in Synaptic, and there were no updates on Thursday or Friday! So Facebook must have changed something.

Yep, it was working fine before for me too. It died Friday, and so did my happiness. Alas, I see no terminal output as well.

---

### Post by airbornemist6 on 2008-04-28
*bump*

Actually, after digging around, it appears Firefox has been having issues with Javascript lately. Of course, I don't know if this is v2 or v3. But, it does explain a part of the problem.

---

### Post by Nathan_M on 2008-04-29
> **airbornemist6 said:**
> Yep, it was working fine before for me too. It died Friday, and so did my happiness. Alas, I see no terminal output as well.

Yeah, I can't believe that one site has actually convinced me to apt-get install firefox-2! I love FF3, and I'm still using it most of the time, but I have to fire up FF2 to chat.

---

### Post by Hooya on 2008-04-29
Well, soon enough there'll be a Pidgin plugin for Facebook chat and this won't be an issue any more.

And when it does it'll spell doom for the AIM protocol.

---

### Post by aheckler on 2008-04-29
Facebook chat seems to work fine for me on Hardy 64-bit. No problems.... yet lol.

---

### Post by airbornemist6 on 2008-04-29
Lucky... it still won't....

...

Hey it's working again!

---

### Post by elicoten on 2008-05-25
I'm also noticing same problem. But I think its not necessarily Firefox - needs more testing but I seem to recall that using Opera had the same problem - though I didn't really test that well with Opera.

I'm on Hardy 32 bit.

---

### Post by greendblink182 on 2008-06-02
I to am having the same problem.  Running Hardy 32 bit.  It works fine for Firefox on my Mac and my Windows machine.  Really frustrating.  Should there be a bug report for this?

---

### Post by elicoten on 2008-06-02
Which version of Firefox are you using on your Mac and Windows machines? It is possible that the problem is actually in Firefox 3.

I'm getting round it by installing a browser called Swiftweasel which is currently based on Firefox 2 (though when Firefox 3 comes out, they will no doubt update it). Either way, its a real pain.

---

### Post by abhiroopb on 2008-06-05
check this out: [http://ubuntuforums.org/showthread.php?t=763822&page=8&highlight=pidgin+facebook](http://ubuntuforums.org/showthread.php?t=763822&page=8&highlight=pidgin+facebook)

It is interesting, certain programs in Ubuntu will crash (for example VLC) just when I know I should be studying instead of say viewing a video :P

---

### Post by rossjman1 on 2008-09-07
I have the same problem, anyone know of a fix yet? I don't really want to use Pidgen for Facebook chat.

---

### Post by fain on 2009-03-27
I am having this problem as well. It's really annoying.

---

### Post by boredman on 2009-06-15
Exactly the same problem I'm having. 

I Managed to get Pidgin & Facebook plugin working for a couple of hours, but Pidgin closes itself whenever it feels like it.

My solution: Use Epiphany browser, the standard Facebook chat works without any problems for me.

---

### Post by Racy on 2009-07-12
I had this problem when using the non-branded firefox 3.5 called Shiretoko. It turned out that it was the useragent string that wasn't recognized by Facebook.
Check your general.useragent.extra.firefox value and make sure that it is 

Firefox/3.0.11
or
Firefox/3.5

depending on which browser you have.

If it reads
Shiretoko/3.5
or something like that, then Facebook doesn't recognize your browser as Firefox.

To see what your useragent string is, just type about:config in the address bar and find the value.

---

### Post by He4dShOt on 2010-02-18
> **Racy said:**
> I had this problem when using the non-branded firefox 3.5 called Shiretoko. It turned out that it was the useragent string that wasn't recognized by Facebook.
Check your general.useragent.extra.firefox value and make sure that it is 

Firefox/3.0.11
or
Firefox/3.5

depending on which browser you have.

If it reads
Shiretoko/3.5
or something like that, then Facebook doesn't recognize your browser as Firefox.

To see what your useragent string is, just type about:config in the address bar and find the value.

I changed the value from Namoroka/3.6.2 to Firefox/3.6 and now the chat works! Thank you!

---

