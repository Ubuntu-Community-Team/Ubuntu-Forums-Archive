---
title: "Skype: Skype Out failing after first call"
date: 2005-10-30
forum: General Help
---

### Post by Doc.Caliban on 2005-10-30
I can make one call with Skype Out and every attempt after that will fail with "Call Failed" until I restart Skype.

I have the latest version of gnomemeeting installed.

Ideas?

This is the last hurdle in my quest to be Windows free.

-Doc

---

### Post by dickmorrell on 2005-10-31
I am getting this too and it's getting on my t*ts.

I've searched all the threads...

Am using 

[http://www.paul.sladen.org/debian/skype/skype_1.2.0.17-1-fixed1_i386.deb](http://www.paul.sladen.org/debian/skype/skype_1.2.0.17-1-fixed1_i386.deb)

CallOut works fine first call then every next attempted call fails.

Anyone got a clue - this is driving me batty

Richard

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=dickmorrell]I am getting this too and it's getting on my t*ts.

I've searched all the threads...

Am using 

[http://www.paul.sladen.org/debian/skype/skype_1.2.0.17-1-fixed1_i386.deb](http://www.paul.sladen.org/debian/skype/skype_1.2.0.17-1-fixed1_i386.deb)

CallOut works fine first call then every next attempted call fails.

Anyone got a clue - this is driving me batty

Richard[/QUOTE]

Is this something that Skype should support?  (Do they support the linux version?)

-Doc

---

### Post by Felipe_U on 2005-10-31
I'm having the same problem. Luckily I don't use SkyOut that much ;) 

Greetings,
Felipe

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Felipe_U]I'm having the same problem. Luckily I don't use SkyOut that much ;) 

Greetings,
Felipe[/QUOTE]


Skype is my primary telephony method.  Skype Out and Skype In, so I need it to work badly enough that it will be a deal breaker for Linux.  This is the LAST deal breaker of the list I started with; everything else works for me now.

-Doc

---

### Post by Felipe_U on 2005-10-31
> Skype is my primary telephony method. Skype Out and Skype In, so I need it to work badly enough that it will be a deal breaker for Linux. This is the LAST deal breaker of the list I started with; everything else works for me now.

-Doc

I guess that if SkypeOut calls to Ecuador were not as expensive as they are, I would be bitching more about restarting skype for every SkypeOut call. Hehehehe.

Greetings,
Felipe

BTW: Is it just me, or the sound of the call is better in linux than in windows???

---

### Post by Doc.Caliban on 2005-10-31
I wouldn't even really mind if Skype didn't also take 30 seconds to load!  I can live with one or the other, but not both.

I'm on a call now and it sounds the same to me.

-Doc

---

### Post by Doc.Caliban on 2005-10-31
If anyone is familiar with the inner workings of Skype, this may shed some light on the issue:

If I enter a number manualy instead of using my contact list, I can call that number again without having to restart, but only by doing so again manualy.

If I try to call a different number by entering it manualy, or by using a contact entry, that call will fail, as will any other attempt to call the original number.

-Doc

---

### Post by sailor420 on 2005-10-31
Is it just skypeout that isnt working? Or is all of skype not working? There's a well known bug with the way Skype handles its connection with the sound daemon that requires the app to be restarted after every call--the link below fixed that for me though. Don't know if these problems are related...

Linkage: [http://juljas.net/linux/skype/](http://juljas.net/linux/skype/)

---

### Post by randcoop on 2005-11-04
How did you install the skype_dsp_hijacker program?  Is it just unzipping the files and then 

sudo make && make install

?

Or did you have to change paths to get it to work?

---

### Post by ekravche on 2005-11-05
I have the same problem. So I'm very eager to find  a solution to this problem.

---

### Post by johannal on 2006-04-02
[QUOTE=sailor420]Is it just skypeout that isnt working? Or is all of skype not working? There's a well known bug with the way Skype handles its connection with the sound daemon that requires the app to be restarted after every call--the link below fixed that for me though. Don't know if these problems are related...

Linkage: [http://juljas.net/linux/skype/](http://juljas.net/linux/skype/)[/QUOTE]

I just wanted to confirm that workaround #1 mentioned in the link above worked perfectly for me. I had the exact same problem that people have been describing  in this thread. That is, whenever I had made a skypeout call to a number I would always have to restart skype to make another call.

I simply removed the hangup sound file by renaming it and now I can make skype out calls one after the other without having to restart Skype.

Hope it will help others as well.

---

