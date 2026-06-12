---
title: "GoogleTalk"
date: 2005-08-24
forum: General Help
---

### Post by Weav on 2005-08-24
GoogleTalk is out : [http://www.google.com/talk/](http://www.google.com/talk/)
I installed it with wine and installation just said that would you like to continue even though its not Windows. I clicked yes and it was able to install.
However when you start the program it loads and you can see the control window but it says application must close.

Anyone out there able to get it working under wine or ubuntu for that matter?

Thanks for any help/suggestions!

---

### Post by supernaut on 2005-08-24
[QUOTE=Weav]GoogleTalk is out : [http://www.google.com/talk/](http://www.google.com/talk/)
I installed it with wine and installation just said that would you like to continue even though its not Windows. I clicked yes and it was able to install.
However when you start the program it loads and you can see the control window but it says application must close.

Anyone out there able to get it working under wine or ubuntu for that matter?

Thanks for any help/suggestions![/QUOTE]
 You can just use Ubuntu's included GAIM, there are instructions on how to do this here: [http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073) The only catch is that it doesn't support the voice functions (yet).

There's also the excellent Gossip client if you're just planning on using Google Talk and no other services (e.g. AIM, MSN). I believe it's in Universe, if not the main repository.

---

### Post by slux on 2005-08-24
What's best about it is that it's a completely standard Jabber implementation. Personally I use [Psi](http://psi.affinix.com/) to connect.

For once I love Google for doing this. They display a great support for open standards.

I've been a Jabber user for many years now and hope the MSN Messenger hegemony will be weakened by this move. After all, who doesn't use google? Besides, Gmail's cool so talk must be. :)

---

### Post by tom-ubuntu on 2005-08-24
Agree, I really like it that they are using Jabber as protocol. What I do not like so far, is, that you can only talk to people using the google talk server. I hope, this is only during the beta phase, and they will open it when they go public. 

Gaim works without any problems, tested it this morning. Works like a charm :D Nice one so far, Google!

---

### Post by kblood on 2005-08-24
It seems the VoIP feature of Google Talk is also based on SIP, so I am hoping soon we will find a way to use it from Linux!

Ideally with Gaim as well :)

---

### Post by tom-ubuntu on 2005-08-24
I am sure, Gaim will add support for it in its next version. Let's pray, ehm hope ;)

---

### Post by Weav on 2005-08-24
ok thanks i got it working with gaim but i just have an overall question:

Whats so good about the jabber protocol? Is it more secure or something? What makes this any different then just using Gaim or Aim already? I thought the whole idea was the application Google was releasing not just using the Jabber protocol.

---

### Post by Snakey on 2005-08-24
Jabber = opensource

BTW: google doesn't allow other servers because they say they are afraid for SPAM (:s), In future, they will only allow servers they have a agreement with :(

---

### Post by earobinson on 2005-08-24
Yaaa Google

---

### Post by kblood on 2005-08-24
[QUOTE=Weav]ok thanks i got it working with gaim but i just have an overall question:

Whats so good about the jabber protocol? Is it more secure or something? What makes this any different then just using Gaim or Aim already? I thought the whole idea was the application Google was releasing not just using the Jabber protocol.[/QUOTE]

Well, I like that Google has decided to use the Jabber/XMPP protocol because it's open source, unlike the MSN, Yahoo, ICQ/AIM protocols.

Basically, if Jabber ever changes, all the clients that use it will know exactly what, how, and why, and they can adapt the software in a clean and open way, with all the info available.

If MSN/Yahoo/whatever ever changes, all the unofficial clients that use those protocols need to start reverse-engineering the communication dumps of the new version of the official client, and after hard work, come up with an open source update, which hopefully will work well and be complete, keeping fingers crossed.

So this could mean a major push to the Jabber protocol, making our lives easier :)

---

### Post by Mishura on 2005-08-24
> GoogleTalk is out : [http://www.google.com/talk/](http://www.google.com/talk/)
I installed it with wine and installation just said that would you like to continue even though its not Windows. I clicked yes and it was able to install.
However when you start the program it loads and you can see the control window but it says application must close.

Did the same for me.  I tried it merely to see if it was compatible.  Before I tried, I had Google Talk working with my Gaim client, anyways.  Only thing missing, is SIP support, but since I don't have a mic, it's really not important for me right now.  Maybe to others, as the integration would rock.  (Skype killer?)

If you check their website, and read through the FAQ, or something, they do say "Linux and OS X versions are pending" .. or something quite close to that.  Linux native version of Google Talk?  Maybe.  Good for me and you?  Depends.  We like Free Software in the GNU sense, or well most of us. :)   Good for the newbie?  Hell yeah.  I just hope that if they *do* port it, that they don't leave it very far behind like the official Yahoo! and AIM clients for Unix/Linux (Yes, they did support Linux.. back in the late 90's.. the clients wouldn't work on our updated libc libraries.. and Gaim kills both without trying)

I also tried with Kopete, but Kopete had issues connecting last night.. I may try again here.

What I'd like to see is some support for AIM, MSN, whatever, transports like some Jabber servers support.  May not happen, but if it does, then the Google/Gmail Talk account would be the only one I need, instead of the 3 that I do have.

---

### Post by earobinson on 2005-08-24
Good point, I have always loved jabber, and I have always loved google (even though a lot of there programs are windows only :(, kinda sucks) it was really cool when the did the summer of code [http://code.google.com/summerofcode.html](http://code.google.com/summerofcode.html), and it is also really cool that google wants to make google talk work with non gmail users "it isn't possible to call or chat with non-Gmail users through Google Talk (but we're working on it)." [http://www.google.com/support/talk/bin/answer.py?answer=23907](http://www.google.com/support/talk/bin/answer.py?answer=23907) so they are not trying to push msn out. gmail is great, [http://www.google.com/ig](http://www.google.com/ig) is great. The company really has the "do no evil" thing down. They have done so many good things (even tried to host Wikipedia [http://www.eweek.com/article2/0,1759,1764349,00.asp](http://www.eweek.com/article2/0,1759,1764349,00.asp)) and I wish the google team the best of luck.

ps im just a little bit of a google nut

---

### Post by evilmrt on 2005-08-24
Those wondering about Google Talk support for linux should check out Michael Robertson's blog about it [HERE](http://www.michaelrobertson.com/archive.php?minute_id=187) 

Sounds like the [Gizmo Project](http://www.gizmoproject.com/) will be our ticket. Only text IM works for now with Google Talk, voice will work soon, he says.

A debian build is available on the gizmo site, has anyone tried it?

---

### Post by earobinson on 2005-08-24
[QUOTE=evilmrt]Those wondering about Google Talk support for linux should check out Michael Robertson's blog about it [HERE](http://www.michaelrobertson.com/archive.php?minute_id=187) 

Sounds like the [Gizmo Project](http://www.gizmoproject.com/) will be our ticket. Only text IM works for now with Google Talk, voice will work soon, he says.

A debian build is available on the gizmo site, has anyone tried it?[/QUOTE]
 looks very cool, i will try to install it when i get home from work

---

### Post by rwabel on 2005-08-24
[QUOTE=earobinson]looks very cool, i will try to install it when i get home from work[/QUOTE]
 it depends on bonjour. I've no idea where to get that package! On the gizmo project forum I've read to download mDNSResponder-107.1 from [http://developer.apple.com/darwin/projects/bonjour/](http://developer.apple.com/darwin/projects/bonjour/). I've tried the ubuntu version of mDNSResponder..
no luck. If anyone has an idea, please post it here

---

### Post by Weav on 2005-08-24
I hope they release a Linux version soon, I would really like to use Google's app because many of its features seem very interesting.

---

### Post by Weav on 2005-08-24
ok i got mDNS to install.

To get it to work download from the main page [http://developer.apple.com/darwin/projects/bonjour/](http://developer.apple.com/darwin/projects/bonjour/)
Extract the contents, then:
```

cd mDNSResponder-107.1/mDNSPosix
sudo make os=linux
mv build/prod/libdns_sd.so /usr/lib/ 

```
kudos for teh_choon for figuring that out

So now we can try and install the dependency lib file for gizmo but it still says it requires bonjour. ANd bonjour is basically mDNSResponder.

This forum is the main Gizmo forum and some people have gotten it to work by linkinh certain thigns which i do not know how to do. We need to figure out how to get gizmo working on Ubuntu. So lets do it!!
[http://forum.gizmoproject.com/viewtopic.php?t=346&postdays=0&postorder=asc&start=0&sid=cca9c481be284548b6abae2ea57a5c18](http://forum.gizmoproject.com/viewtopic.php?t=346&postdays=0&postorder=asc&start=0&sid=cca9c481be284548b6abae2ea57a5c18)

---

### Post by earobinson on 2005-08-24
I broke my gtalk, lol i have to accounts earobinson, and edward.a.robinson i can use one and not the other :(

---

### Post by Mishura on 2005-08-25
Have you guys heard of PhoneGaim?  (Search google for it).  Last I heard, it was a Gaim fork with VOIP stuff in it, developed by Linspire.  (Same guy who runs the Gizmo Project, owns Linspire).

If this does, what I think it does, it could be THE Google Talk Client for Linux.  With a little bit of Gmail integration, it could rock, and be GPL at the same time.  Best option for Google if they decide to port, I think.

---

### Post by npaladin2000 on 2005-08-25
Not bad.  They only need a couple of things:

1. Webcam support.  Come on, everyone else has it.  They should get with the Gaim-VV Project. ;)

2.  A nice indicator for forums to go along with the AIM, MSN, and Yahoo indicators. :)

---

### Post by rwabel on 2005-08-25
problem solved: they've put the bonjour package on the webpage
[http://www.gizmoproject.com/download/bonjour_107.1-0.0.0.50.linspire0.2_i386.deb](http://www.gizmoproject.com/download/bonjour_107.1-0.0.0.50.linspire0.2_i386.deb)

---

### Post by Weav on 2005-08-25
oh thanks rwabel for finding the download!

Gizmo is up and running:
[http://img296.imageshack.us/my.php?image=screenshot6sk.png](http://img296.imageshack.us/my.php?image=screenshot6sk.png)

Now to figure out how to get GoogleTalk running on it.

---

### Post by rwabel on 2005-08-25
[QUOTE=Weav]oh thanks rwabel for finding the download!

Gizmo is up and running:
[http://img296.imageshack.us/my.php?image=screenshot6sk.png](http://img296.imageshack.us/my.php?image=screenshot6sk.png)

Now to figure out how to get GoogleTalk running on it.[/QUOTE]
 you're welcome. But it's still very alpha :-) no preferences yet.

---

### Post by earobinson on 2005-08-29
[QUOTE=rwabel]you're welcome. But it's still very alpha :-) no preferences yet.[/QUOTE]
 [http://www.phonegaim.com](http://www.phonegaim.com) so far only for linespire :(

ps google still has not fixed my gtalk account think i should bug report it again (all ready done it 2 times) and no reply

EDIT: anyone know what could be wrong? i know i have the right password

---

### Post by earobinson on 2005-08-29
anyone have the answer to this sorry for the double post

so check that out im using the exact same setings for the 3 gmail accounts but only one will work

---

### Post by djSeverin on 2005-08-29
I'm having the same problem... Have checked my settings, they're all correct according to talk.google.com howto, but it won't authenticate...  :-?

---

### Post by earobinson on 2005-08-29
google goten back to you? i reported this like 4 ish days ago still nothing :(

cheers

---

### Post by rps63ifid on 2005-08-30
[QUOTE=earobinson]google goten back to you? i reported this like 4 ish days ago still nothing :(

cheers[/QUOTE]

I submitted this to the google folks, too, and have heard nothing back from them. I can use their Windows client without problem, but I can't get Gaim to connect on either my Windows boxes or under Linux.

---

### Post by earobinson on 2005-08-30
[QUOTE=rps63ifid]I submitted this to the google folks, too, and have heard nothing back from them. I can use their Windows client without problem, but I can't get Gaim to connect on either my Windows boxes or under Linux.[/QUOTE]
 blast, at least some one has the same problem as me, ill post here if they get back to me

---

### Post by earobinson on 2005-08-31
problem has fixed its self i can now connect under linux and windows

---

### Post by Elrohir on 2005-08-31
I'm curious... I just realized there is a "Register" button... what is it for?

---

### Post by earobinson on 2005-09-01
[QUOTE=Elrohir]I'm curious... I just realized there is a "Register" button... what is it for?[/QUOTE]
 If your talking about gaim thats for other jabber servers, eg jabber.com or is it org? That let you sign up on the fly. google jabber for more info.

---

